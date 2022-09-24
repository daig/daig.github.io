This post is literate haskell (ignoring the latex images) so before we set off

```haskell
> {-#LANGUAGE TypeOperators#-}
> import Control.Category
> import Prelude hiding ((.),id)
```

Haskell datatypes form an algebra, complete with sums $$(a + b \equiv \text{Either a b})$$

,products $$(a*b \equiv (a,b))$$

and even exponentials $$(b^a \equiv a \to b)$$

So what can we do with this correspondence? Well lots of things, but today I'm going to focus on type isomorphisms.
Notice first that all (unquantified) data declarations can be converted into a standard form. For example:

```haskell
data List a = Nil | Cons a (List a)
```

is converted to:

```haskell
type GenericList a = Either () (a,GenericList a)
```

This is the basis of Haskell Generics (ex. in GHC.Generics). By converting data into a universal form we can manipulate different structures in a uniform way. Essentially what we are doing here is just "stripping off the tags" that make isomorphic algebraic types distinct.
Each generic representation gives rise to a type equation.For list:

$$\text{List}(x) \cong 1 + x~\text{List}(x)$$

We can do some pretty mindbending stuff with these equations due to a [result](http://arxiv.org/abs/math/0212377) from category theory. By expanding the equation we get the generating function

$$[x] \cong 1 + x + x^2 + x^3 + \ldots$$

we can think of a list as either the empty list, a sequence of one element, a sequence of two elements, a sequence of 3 elements etc. etc.
But also, by manipulating the recursive equation into closed form, we see that

$$[x] \cong \frac{1}{1-x}$$

Even though this doesn't have any sensible interpretation as a datatype, we can take a jaunt through the complex numbers so long as we return to a form without division or subtraction and so long as no side is purely constant.
We need this last constraint to prevent things like shoving a tree into the unit type as follows:

```haskell
> data Tree a = O a | T (Tree a) (Tree a) deriving (Show,Eq)
```

$$T(a) \cong a + T^2(a)$$
	$$\Rightarrow T(a) \cong \frac{1\pm\sqrt{1-4a}}{2}$$

By setting

$$a=1$$

the unit type,  we get

$$T(1) \cong \frac{1\pm i \sqrt{3}}{2}$$

which is a sixth root of unity. So since

$$ T^6(1) = 1$$

we would expect an unlabeled tree to be equivalent to the unit type. But of course this makes no sense! As it turns out, One tree IS [equivalent](http://blog.sigfpe.com/2007/09/arboreal-isomorphisms-from-nuclear.html) to [seven](http://arxiv.org/abs/math/9405205) trees. There are an infinite number of trees, but the unit type has only a finite number of inhabitants (exactly 1!), which is why we make the stipulation that no final result be constant.
Notice that so far our data declarations only give us equations of the form

$$X = F(X)$$


Is it possible to get other types of equations? Specifically can we construct a "golden" datatype that satisfies the equation

$$G^2 \cong G+1$$

giving the closed form

$$G \cong \phi \equiv \frac{1+\sqrt{5}}{2}$$

, the golden ratio.

We already have our tree equation

$$T(x) \cong \frac{1\pm\sqrt{1-4a}}{2}$$

which resolves to $$\phi$$ when $$a=(-1)$$.

But what kind of type looks like $-1$? Well, looking back at our list equation

$$L(a) \cong \frac{1}{1-a}$$ 

resolves to $$-1$$ when $$a=2$$. So what's $$2$$? Why, it's just the Boolean type $$1+1$$!

So composing all these together we find our "golden type" to be a tree of lists of booleans, or equivalently, a tree with leaves labeled by (possibly empty) bitstrings.
Now this is a nice result, but it may leave you scratching your head about exactly how the the identity $$G^2 \cong G +1$$ holds.
So lets construct an isomorphism explicitly.
Lets first definite some convenience types

```haskell
> data a :+ b = L a | R b deriving (Show,Eq) -- Sum type
> data a :* b = a :* b deriving (Show,Eq) -- Product type
> infixl 6 :+
> infixl 7 :*
> type X = [Bool]
> type G = G = Tree X
> f # g = g . f -- this will come in handy later
Since we're talking about isomorphisms, we might as well make it explicit
> data a :~ b = ISO {to :: a->b, from :: b -> a}
> instance Category (:-) where
>     id = ISO id id
>     ISO f g . ISO f' g' = ISO (f . f') (g' . g)
> infixr 0 :-
And include some simple unrapping isomorphisms for trees and lists
> tWrap :: Tree a :- Tree a :* Tree a :+ a
> tWrap = ISO f g where
>     f (O a) = R a and even exponentials

So what can we do with this correspondence? Well lots of things, but today I’m going to focus on type is
>     f (T t1 t2) = L $ t1:*t2
>     g (R a) = O a
>     g (L (t1 :* t2)) = T t1 t2
> lWrap :: [a] :- a:*[a] :+ ()
> lWrap = ISO f g where
>     f [] = R ()
>     f (a:as) = L $ a:*as
>     g (R ()) = []
>     g (L (a:*as)) = a:as
```

The following derivation is based on the one presented in [This Week's Find](http://math.ucr.edu/home/baez/week203.html)
First notice that if we can decompose a type

$$Z \cong Z' + X$$

where `X=[Bool]` satisfies the equation of `lWrap`, then 

$$Z + X + 1$$

$$\cong Z' + 2X + 1$$

$$\cong Z' + X$$

$$\cong Z$$

```haskell
> lemma1 :: (z :~ z' :+ X) -> (z :+ X :+ () :~ z)
> lemma1 f = ISO ff gg where
>     ff zz = from f $ case zz of
>         R () -> R []
>         L (R xs) -> R (False:xs) > L (L z) -> case to f z of
>             R xs -> R (True:xs)
>             L z' -> L z'
```

Given an isomorphism

$$f : Z \leftrightarrow Z' + X$$

, we get an isomorphism

$$f' : Z \leftrightarrow Z + X + 1$$

Convince yourself that the above works and play with it a bit. It's only going to get messier from here.

Before we continue we should build some convenience functions to handle basic manipulations of generic terms. For everyday arithmetic we use the commutative, associative and distributive laws without giving it a second thought, but here we need to choose them explicitly. Note that our constructors are left associative and `:+` binds less tightly than `:*` , so for example `(a:+b:+c:+d:*e)` is the same as `(((a:+b):+c):+(d:*e))`

```haskell
> cP :: a :+ b :- b :+ a -- Commutativity of addition
> cP = ISO f f where; f x = case x of; L a -> R a; R b -> L b
> cT :: a :* b := b :* a -- Commutativity of multiplication
> cT = ISO f f where f (a :* b) = b :* a
> aP :: (a :+ b) :+ c :- a :+ (b :+ c) -- Associativity of addition
> aP = ISO f g where
>   f x = case x of
>     L (L a) -> L a
>     L (R b) -> R $ L b
>     R c -> R $ R c
>   g x = case x of
>     L a -> L $ L a
>     R (L b) -> L $ R b
>     R (R c) -> R c
> aT :: (a :* b) :* c :~ a :* (b :* c) -- Associativity of multiplication
> aT = ISO (\((a:*b):*c) -> a:*(b:*c)) (\(a:*(b:*c)) -> (a:*b):*c)
> unit :: a :- ():*a -- Multiplicative identity
> dist :: a:*(b:+c) :- a:*b :+ (b:*c) -- Distributive law
> dist = ISO f g where
>     f (a:*x) = case x of; L b -> L $ a:*b; R c -> R $ a:*c
>     g (L (a:*b)) = a:*(L b)
>     g (R (a:*c)) = a:*(R c)
{- Isomorphism combinators. These are analogous to the arrow opperators of the same name -}
> (+++) :: (a :- b) -> (c :- d) -> (a:+c :- b:+d)
> f +++ g = ISO (pp (to f) (to g)) (pp (from f_ (from g)) where
>     pp f' g' x = case x of; L a -> L (f' a); R b -> R (g' b)
> (***) :: (a :- b) -> (c :- d) -> (a:*c :- b:*d)
> f *** g = ISO (pp (to f) (to g)) (pp (from f) (from g)) where
>     pp f' g' (a:*b) = f' a :* g' b
```

Now we unwrap the tree into a list and a pair of trees, and unwrap the list into () or a bool and a list, giving

$$G \cong X + G \cong 2X + 1 + G^2$$

```haskell
> lemma2 :: G :~ B:*X :+ () :+ G:*G
> lemma2 = cP . (id +++ listWrap) . treeWrap
```

Now we apply this identity to

$$G^2 \cong (X+G^2)^2 \cong (2X + 1 + G^2)^2$$

and expand just enough to get a free `X` on the rightmost side. Since the expansion contains an `X` term, it is of the form `Z' + x` for some `Z'`. But really, we don't care what it is since it gets absorbed by `lemma1` , we just need to separate an `X`. Nevertheless, the tangle of commutation and association gets a bit hairy.

```haskell
> lemma3 :: B:*a :~ a:+a
> lemma3 = ISO f g where
>     f (b:*a) = case b of;Z -> L a; U -> R a
>     g x = case x of; L a -> Z:*a; R a -> U:*a
> lemma4 = -- Show that G^2 = Z' + X for some (ugly) Z'
> (lemma2 *** lemma2) # d # (d+++id) # aP # (id +++ cP) # inv aP # 
>   (id +++ id +++ (cP.aP.inv u . cT)) # > inv aP # > (id +++ lemma3) # 
>   inv aP
```

Fire up a GHCI session and try to follow each step of lemma4 to get a feel for how to manipulate complex expressions. This may seem messy but imagine trying to write a correct function like this with only case statements as we did for lemma1! Now that the heavy lifting is out of the way the rest falls into our laps

```haskell
> lemma5 :: G:*G :+ X :+ () :- G:*G
> lemma5 = lemma1 lemma4
```

And finally we get our isomorphism by unwrapping the left hand side and applying lemma5

```haskell
> golden :: G :+ () :- G:*G
> golden = (treeWrap +++ id) # lemma5
```

So what kind of mapping do we have? I'm not sure that derivation made it any clearer, but at least we have an honest isomorphism now.  With a bit of playing around we notice the following (much simpler) correspondence.

```haskell
L (O x) <=> O (True:False:xs) :* O []
R () <=> O [True] :* O []
(L (T t1 t2)) <=> t1 :* t2
```

Of course, this isomorphism is not canonical, the specifics depend on exactly how you wire lemma4, but it is an isomorphism nevertheless! We can prove this by simply following the types and ensuring that  all of our combinators are indeed isomorphisms and that composition of isomorphisms type is an isomorphism an exercise that i will leave for the motivated reader.
