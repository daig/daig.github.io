This post walks through the construction of Polynomial Functors  in Agda based on my old code [here](https://github.com/ToposInstitute/poly/tree/main/code-examples/agda/poly)

The Category Poly has some of the richest structure of any category, only some of which will be touched here. Because we're focusing on constructive properties and using Agda, I'll think in terms of types rather than categories but the two approaches are essentially equivalent by the Curry-Howard-Lambek correspondence.

We can think of Polynomial Functors (the objects of Poly) as a Categorification of regular polynomials e.g. $y^2 + 2y + 1$ with more structure.

In this sense, a Polynomial Functor is just a particular sort of presheaf
```agda
_^ : Set → Set -- Presheaf
I ^ = I → Set
```

Working constructively, it's easier to work with _representations_
```agda
∫ : Set
∫ = ∃ _^
```
which is to say, polynomials $P$ are _dependent pairs_ $(P^+ : Type,P^- : P^+ → Type)$, thinking of $P^+$ as the *coefficients* and $P^-(p)$ as the _exponent_ for the variable at that index.

e.g our first polynomial
$$y^2 + 2y + 1$$ can be represented by
$$({\bf4},\{1 \mapsto {\bf 2}; 2 \mapsto {\bf 1}; 3 \mapsto {\bf 1}; 4 \mapsto {\bf 0}\})$$
i.e.
- The first "index" gets mapped to the exponent ${\bf 2}$ in the $y^2$ term
- The second and third _both_ map to the exponent ${\bf 1}$ in the $2y \equiv y + y$ term
- The final "index" gets mapped to ${\bf 0}$ in the constant term $1$

In future, we will omit $P^+$ where it's obvious and only give the explicit mapping for $P^-$

There's many ways to interpret these polynomial descriptions, but I like to think of them as formal descriptions of Algebraic Datatypes, where the "coefficients" represent _constructors_/_shapes_ and the "exponents" represent _positions_ in that shape.

Polynomial descriptions can be _interpreted_ as Polynomial Functors / _linear_ data _type constructors_
```agda
_⦅_⦆ : ∫ → Set → Set -- Interpret as a polynomial functor
(A⁺ , A⁻) ⦅ y ⦆ = Σ[ a⁺ ∈ A⁺ ] (A⁻ a⁺ → y)
```

For example, the type
```haskell
data MaybeEither a = Nothing | JustLeft a | JustRight a
```

can be represented by the polynomial

$$
\{\text{Nothing} \mapsto \text{Void}; \text{JustLeft} \mapsto (); \text{JustRight} \mapsto ()\}
$$
which gets interpreted as (in pseudo-haskell)

```haskell
data MaybeEitherConstructor = Nothing_ | JustLeft_ | JustRight_
type MaybeEither' a = ('Nothing_,Void → a) | ('JustLeft_,() → a) | ('JustRight_, () → a)
```
which is isomorphic to the original because
```haskell
absurd ∷ () → (Void → a)
absurd () = case {}

const ∷ a → (() → a)
const a = \() -> a
```
are the only inhabitants of their respective types.

Seeing them as recipes for a datatype, where the constructor names can differ unlike anonymous coefficients, makes it clear why we want to think of coefficients separately rather than lumping them together.

As a mere polynomial, the above representation for `MaybeEither` looks like $1 + 2a$.

So that's the objects in ${\bf Poly}$, but what makes ${\bf Poly}$ really interesting are the _morphisms_.

## Morphisms in Poly

The morphisms in ${\bf Poly}$ are _dependent_ [_lenses_](https://hackage.haskell.org/package/lens)

```agda
module _ (A@(A⁺ , A⁻) B@(B⁺ , B⁻) : ∫) where
  ∫[_,_] : Set
  ∫[_,_] = (a⁺ : A⁺) → Σ[ b⁺ ∈ B⁺ ] (B⁻ b⁺ → A⁻ a⁺)
module _ {A@(A⁺ , A⁻) B@(B⁺ , B⁻) : ∫} where
  lens : (get : A⁺ → B⁺)
         (set : (a⁺ : A⁺) → B⁻ (get a⁺) → A⁻ a⁺)
       → ∫[ A , B ]
  lens g s = λ a⁺ → g a⁺ , s a⁺
  get : (l : ∫[ A , B ]) → A⁺ → B⁺
  get l = π₁ ∘ l
  set : (A↝B : ∫[ A , B ]) → (a⁺ : A⁺) → B⁻ (get A↝B a⁺) → A⁻ a⁺
  set l = π₂ ∘ l
```
Unpacking the above:
A morphism `f : ∫[(A⁺ , A⁻),(B⁺ , B⁻)]` between polynomial representations has:
- a _getter_ `get : A⁺ → B⁺`
- a _setter_ `set : (a⁺ : A⁺) → B⁻ (get a⁺) → A⁻ a⁺`
In the definition above we combine get and set into a single operation of type `(a⁺ : A⁺) → Σ[ b⁺ ∈ B⁺ ] (B⁻ b⁺ → A⁻ a⁺)` - getting both the value and the "pre-applied" setter in one go. This matters for _linear lenses_, guaranteeing that we only use the input once - but for our cases its equivalent and easier to work with separate getters and setters.

Compare this to a regular non-dependent `Lens s t a b`
- a getter `get : s → a`
- a setter `set : s → b → t`

So $(A^+,A^-)$ is kinda like $(s,t)$ while $(B^+,B^-)$ is kinda like $a,b$

For normal lenses, we usually think of `s` and `t` being related somehow (e.g as polymorphic containers of different types like `s ~ [a]` and `t ~ [b]`), so this makes _some_ sense for `t` to "depend on" `s`, although it's actually kinda weirdly askew if you think about it hard enough - more on that later.

Thinking of ${\bf Poly}$ morphisms on containers, what they're doing is:
- Map each constructor name to another constructor name
- For each constructor name, associate each position in the constructor of its image _back_ to a position in the original
This encodes an advanced form of _structural subtyping_, where $P \to Q$ means there's a $Q$ implicit in the $P$ structure. This allows us to _lift_ operations on $Q$ structures _back_ onto an operation on $P$ structures, by first extracting the $Q$ structure then applying the operation and putting it back.
Notice that this operation of lenses on _data type constructors_ is _different_ from how we usually think of lenses on _data types_. Instead of "extracting values from a container", we extract _structure_ from the container.
These sorts of lenses are called _algebraic ornaments_.

It makes more sense with an example:

Our `MaybeEither` type has a lens to the normal `Maybe` type:
- `get` maps $$\{\text{Nothing} \mapsto \text{Nothing}; \text{JustLeft} \mapsto \text{Just};\text{JustRight} \mapsto \text{Just}\}$$
- `set` associates the single `a` position in `Just` back to the single `a` position in `JustLeft` or `JustRight` depending which branch we're already in.

This lets us do some nice things like
- automatically lift `isJust` from `Maybe` to `MaybeEither` (by pre-applying `get`) so that it will be true if we're in either `JustLeft` or `JustRight`
- Turn `Maybe` into a [_Monad Module_](https://hackage.haskell.org/package/bound-2.0.5/docs/Bound-Class.html) over `MaybeEither` which behaves like the normal monad instance for `Maybe` except it "stays in its lane" for `JustLeft` or `JustRight`

## Poly is a category
Finally, we want to show that lenses over polynomial representations do indeed form a category.

```agda
record Category {O : Set} (𝒞[_,_] : O → O → Set) : Set where
  constructor 𝒾:_▸:_𝒾▸:_▸𝒾:
  infixl 8 _▸_
  field
    𝒾 : ∀ {x} → 𝒞[ x , x ]
    _▸_ : ∀ {x y z} → 𝒞[ x , y ] → 𝒞[ y , z ] → 𝒞[ x , z ]
    𝒾▸ : ∀ {x y} (f : 𝒞[ x , y ]) → (𝒾 ▸ f) ≡ f
    ▸𝒾 : ∀ {x y} (f : 𝒞[ x , y ]) → (f ▸ 𝒾) ≡ f
```
We encode a category as a record of data:
- An identity `𝒾 : ∀ {x} → ∫[ x , x ]`
- A composition map `_▸_ : ∀ {x y z} → ∫[ x , y ] → ∫[ y , z ] → ∫[ x , z ]`
Together with laws for how identity and composition interact:
- `𝒾▸ : ∀ {x y} (f : ∫[ x , y ]) → (𝒾 ▸ f) ≡ f`
`▸𝒾 : ∀ {x y} (f : ∫[ x , y ]) → (f ▸ 𝒾) ≡ f`
(Technically we should also include associativity but it's tedious and uninformative to prove :p)

```agda
instance
    lens-cat : Category ∫[_,_]
    lens-cat = 𝒾: (λ a⁺ → a⁺ , id)
               ▸: (λ l1 l2 a⁺ → let b⁺ , setb = l1 a⁺
                                    c⁺ , setc = l2 b⁺
                                in  c⁺ , setb ∘ setc)
               𝒾▸: (λ _ → refl)
               ▸𝒾: (λ _ → refl)
```

- Identity is simply given by the normal identity functions
- Composition proceeds as normal non-dependent lens composition, composing the getters and saving the intermediate values to feed back into the setters in the opposite direction.
- The proofs are trivial
