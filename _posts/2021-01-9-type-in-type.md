---
permalink: agda/Type.html
---
<pre class="Agda"><a id="9" class="Symbol">{-#</a> <a id="13" class="Keyword">OPTIONS</a> <a id="21" class="Pragma">--type-in-type</a> <a id="36" class="Symbol">#-}</a>
<a id="40" class="Keyword">module</a> <a id="47" href="Type.html" class="Module">Type</a> <a id="52" class="Keyword">where</a>
<a id="58" class="Keyword">open</a> <a id="63" class="Keyword">import</a> <a id="70" href="Agda.Primitive.html" class="Module">Agda.Primitive</a> <a id="85" class="Keyword">public</a>
  <a id="94" class="Keyword">renaming</a> <a id="103" class="Symbol">(</a><a id="104" href="Agda.Primitive.html#326" class="Primitive">Set</a> <a id="108" class="Symbol">to</a> <a id="111" class="Primitive">Type</a><a id="115" class="Symbol">;</a> <a id="117" href="Agda.Primitive.html#381" class="Primitive">Setω</a> <a id="122" class="Symbol">to</a> <a id="125" class="Primitive">Typeω</a><a id="130" class="Symbol">;</a> <a id="132" href="Agda.Primitive.html#417" class="Primitive">SSet</a> <a id="137" class="Symbol">to</a> <a id="140" class="Primitive">SType</a>
           <a id="157" class="Symbol">;</a><a id="158" href="Agda.Primitive.html#597" class="Postulate">Level</a> <a id="164" class="Symbol">to</a> <a id="167" class="Postulate">Lvl</a><a id="170" class="Symbol">;</a><a id="171" href="Agda.Primitive.html#764" class="Primitive">lzero</a> <a id="177" class="Symbol">to</a> <a id="180" class="Primitive">ℓ0</a><a id="182" class="Symbol">;</a> <a id="184" href="Agda.Primitive.html#780" class="Primitive">lsuc</a> <a id="189" class="Symbol">to</a> <a id="192" class="Primitive">ℓs</a><a id="194" class="Symbol">)</a>
  <a id="198" class="Keyword">using</a>    <a id="207" class="Symbol">(</a><a id="208" href="Agda.Primitive.html#810" class="Primitive Operator">_⊔_</a><a id="211" class="Symbol">)</a>

<a id="214" class="Keyword">open</a> <a id="219" class="Keyword">import</a> <a id="226" href="Data.Product.html" class="Module">Data.Product</a> <a id="239" class="Keyword">using</a> <a id="245" class="Symbol">(</a><a id="246" href="Data.Product.html#1369" class="Function">∃</a><a id="247" class="Symbol">;</a> <a id="249" href="Data.Product.html#1167" class="Function Operator">_×_</a><a id="252" class="Symbol">;</a> <a id="254" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">_,_</a><a id="257" class="Symbol">)</a> <a id="259" class="Keyword">renaming</a> <a id="268" class="Symbol">(</a><a id="269" href="Agda.Builtin.Sigma.html#252" class="Field">proj₁</a> <a id="275" class="Symbol">to</a> <a id="278" class="Field">π₁</a><a id="280" class="Symbol">;</a> <a id="282" href="Agda.Builtin.Sigma.html#264" class="Field">proj₂</a> <a id="288" class="Symbol">to</a> <a id="291" class="Field">π₂</a><a id="293" class="Symbol">)</a>
<a id="295" class="Keyword">open</a> <a id="300" class="Keyword">import</a> <a id="307" href="Relation.Binary.PropositionalEquality.html" class="Module">Relation.Binary.PropositionalEquality</a> <a id="345" class="Symbol">as</a> <a id="348" class="Module">Eq</a> <a id="351" class="Keyword">using</a> <a id="357" class="Symbol">(</a><a id="358" href="Agda.Builtin.Equality.html#151" class="Datatype Operator">_≡_</a><a id="361" class="Symbol">;</a> <a id="363" href="Agda.Builtin.Equality.html#208" class="InductiveConstructor">refl</a><a id="367" class="Symbol">)</a>
<a id="369" class="Keyword">open</a> <a id="374" href="Relation.Binary.PropositionalEquality.Core.html#2647" class="Module">Eq.≡-Reasoning</a> <a id="389" class="Keyword">using</a> <a id="395" class="Symbol">(</a><a id="396" href="Relation.Binary.PropositionalEquality.Core.html#2803" class="Function Operator">_≡⟨⟩_</a><a id="401" class="Symbol">;</a> <a id="403" href="Relation.Binary.PropositionalEquality.Core.html#3044" class="Function Operator">_∎</a><a id="405" class="Symbol">)</a>

<a id="408" class="Keyword">data</a>   <a id="⊥"></a><a id="415" href="Type.html#415" class="Datatype">⊥</a> <a id="417" class="Symbol">:</a> <a id="419" href="Type.html#111" class="Primitive">Type</a> <a id="424" class="Keyword">where</a>
<a id="430" class="Keyword">record</a> <a id="⊤"></a><a id="437" href="Type.html#437" class="Record">⊤</a> <a id="439" class="Symbol">:</a> <a id="441" href="Type.html#111" class="Primitive">Type</a> <a id="446" class="Keyword">where</a> <a id="452" class="Keyword">constructor</a> <a id="⋆"></a><a id="464" href="Type.html#464" class="InductiveConstructor">⋆</a>
<a id="466" class="Keyword">data</a>   <a id="𝔹"></a><a id="473" href="Type.html#473" class="Datatype">𝔹</a> <a id="475" class="Symbol">:</a> <a id="477" href="Type.html#111" class="Primitive">Type</a> <a id="482" class="Keyword">where</a> <a id="𝔹.𝕗"></a><a id="488" href="Type.html#488" class="InductiveConstructor">𝕗</a> <a id="490" class="Symbol">:</a> <a id="492" href="Type.html#473" class="Datatype">𝔹</a><a id="493" class="Symbol">;</a> <a id="𝔹.𝕥"></a><a id="495" href="Type.html#495" class="InductiveConstructor">𝕥</a> <a id="497" class="Symbol">:</a> <a id="499" href="Type.html#473" class="Datatype">𝔹</a>
<a id="_iff_"></a><a id="501" href="Type.html#501" class="Function Operator">_iff_</a> <a id="507" class="Symbol">:</a> <a id="509" href="Type.html#111" class="Primitive">Type</a> <a id="514" class="Symbol">→</a> <a id="516" href="Type.html#111" class="Primitive">Type</a> <a id="521" class="Symbol">→</a> <a id="523" href="Type.html#111" class="Primitive">Type</a>
<a id="528" href="Type.html#528" class="Bound">p</a> <a id="530" href="Type.html#501" class="Function Operator">iff</a> <a id="534" href="Type.html#534" class="Bound">q</a> <a id="536" class="Symbol">=</a> <a id="538" class="Symbol">(</a><a id="539" href="Type.html#528" class="Bound">p</a> <a id="541" class="Symbol">→</a> <a id="543" href="Type.html#534" class="Bound">q</a><a id="544" class="Symbol">)</a> <a id="546" href="Data.Product.html#1167" class="Function Operator">×</a> <a id="548" class="Symbol">(</a><a id="549" href="Type.html#534" class="Bound">q</a> <a id="551" class="Symbol">→</a> <a id="553" href="Type.html#528" class="Bound">p</a><a id="554" class="Symbol">)</a>
</pre>
In GHC Haskell, every normal type has the kind `Type` (previously `*`), including `Type :: Type`.
Previously this behavior was turned on with [`-XTypeInType`](https://downloads.haskell.org/~ghc/latest/docs/html/users_guide/glasgow_exts.html#extension-TypeInType), but is now the default.

Agda's type hierarchy is more complex.

Instead of `Type : Type` we instead have `Type₀ : Type₁` and `Type₁ : Type₂` and so on.

Any type that quantifies over another type must be larger than it. For example:

<pre class="Agda"><a id="1068" class="Keyword">record</a> <a id="Dynamic"></a><a id="1075" href="Type.html#1075" class="Record">Dynamic</a> <a id="1083" class="Symbol">:</a> <a id="1085" href="Type.html#111" class="Primitive">Type₁</a> <a id="1091" class="Keyword">where</a>
  <a id="1099" class="Keyword">field</a>
    <a id="Dynamic.Ty"></a><a id="1109" href="Type.html#1109" class="Field">Ty</a> <a id="1112" class="Symbol">:</a> <a id="1114" href="Type.html#111" class="Primitive">Type₀</a>
    <a id="Dynamic.term"></a><a id="1124" href="Type.html#1124" class="Field">term</a> <a id="1129" class="Symbol">:</a> <a id="1131" href="Type.html#1109" class="Field">Ty</a>

<a id="Dynamic∀"></a><a id="1135" href="Type.html#1135" class="Function">Dynamic∀</a> <a id="1144" class="Symbol">:</a> <a id="1146" href="Type.html#111" class="Primitive">Type₀</a>
<a id="1152" href="Type.html#1135" class="Function">Dynamic∀</a> <a id="1161" class="Symbol">=</a> <a id="1163" class="Symbol">∀</a> <a id="1165" class="Symbol">{</a><a id="1166" href="Type.html#1166" class="Bound">r</a> <a id="1168" class="Symbol">:</a> <a id="1170" href="Type.html#111" class="Primitive">Type₀</a><a id="1175" class="Symbol">}</a> <a id="1177" class="Symbol">→</a> <a id="1179" class="Symbol">(((</a><a id="1182" href="Type.html#1182" class="Bound">Ty</a> <a id="1185" class="Symbol">:</a> <a id="1187" href="Type.html#111" class="Primitive">Type₀</a><a id="1192" class="Symbol">)</a> <a id="1194" class="Symbol">→</a> <a id="1196" href="Type.html#1182" class="Bound">Ty</a><a id="1198" class="Symbol">)</a> <a id="1200" class="Symbol">→</a> <a id="1202" href="Type.html#1166" class="Bound">r</a><a id="1203" class="Symbol">)</a> <a id="1205" class="Symbol">→</a> <a id="1207" href="Type.html#1166" class="Bound">r</a>
</pre>
Contrast this with the identity type, which is at the same level as `Ty` because it takes it as a generic parameter, rather than existentially quantifying over it.

<pre class="Agda"><a id="1387" class="Keyword">record</a> <a id="Identity"></a><a id="1394" href="Type.html#1394" class="Record">Identity</a> <a id="1403" class="Symbol">(</a><a id="1404" href="Type.html#1404" class="Bound">Ty</a> <a id="1407" class="Symbol">:</a> <a id="1409" href="Type.html#111" class="Primitive">Type₀</a><a id="1414" class="Symbol">)</a> <a id="1416" class="Symbol">:</a> <a id="1418" href="Type.html#111" class="Primitive">Type₀</a> <a id="1424" class="Keyword">where</a>
  <a id="1432" class="Keyword">field</a> <a id="Identity.term"></a><a id="1438" href="Type.html#1438" class="Field">term</a> <a id="1443" class="Symbol">:</a> <a id="1445" href="Type.html#1404" class="Bound">Ty</a>

<a id="Identity∀"></a><a id="1449" href="Type.html#1449" class="Function">Identity∀</a> <a id="1459" class="Symbol">:</a> <a id="1461" href="Type.html#111" class="Primitive">Type₀</a> <a id="1467" class="Symbol">→</a> <a id="1469" href="Type.html#111" class="Primitive">Type₀</a>
<a id="1475" href="Type.html#1449" class="Function">Identity∀</a> <a id="1485" href="Type.html#1485" class="Bound">Ty</a> <a id="1488" class="Symbol">=</a> <a id="1490" href="Type.html#1485" class="Bound">Ty</a>
</pre>
It would be annoying to figure out which type level to use on our own, so types are polymorphic over _universe level_.
`Type` alone is sugar for `Type₀`, which is itself sugar for `Type ℓ0`, and `Type₁` is sugar for `Type (ℓs ℓ0)` etc.
The full polymorphic type is `Type : (ℓ : Lvl) → Type (ℓs ℓ)`, for a special `Lvl` type:

<pre class="Agda"><a id="1833" class="Comment">{-
postulate Lvl : Type
{-# BUILTIN LEVEL Lvl #-}
{-# BUILTIN LEVELZERO ℓ0  #-} -- : Lvl
{-# BUILTIN LEVELSUC  ℓs  #-} -- : Lvl → Lvl
{-# BUILTIN LEVELMAX  _⊔_ #-} -- : Lvl → Lvl → Lvl
infixl 6 _⊔_
-}</a>
</pre>
`Lvl` is a magic type. It isn't possible to pattern match on levels, and they're erased at run-time.

When multiple polymorphic levels appear in a type, the resulting level must bound all of them. This is achieved with the max operator. e.g. the dependent pair:

<pre class="Agda"><a id="2310" class="Keyword">record</a> <a id="Σ"></a><a id="2317" href="Type.html#2317" class="Record">Σ</a> <a id="2319" class="Symbol">{</a><a id="2320" href="Type.html#2320" class="Bound">ℓa</a> <a id="2323" href="Type.html#2323" class="Bound">ℓb</a><a id="2325" class="Symbol">}</a> <a id="2327" class="Symbol">(</a><a id="2328" href="Type.html#2328" class="Bound">A</a> <a id="2330" class="Symbol">:</a> <a id="2332" href="Type.html#111" class="Primitive">Type</a> <a id="2337" href="Type.html#2320" class="Bound">ℓa</a><a id="2339" class="Symbol">)</a> <a id="2341" class="Symbol">(</a><a id="2342" href="Type.html#2342" class="Bound">B</a> <a id="2344" class="Symbol">:</a> <a id="2346" href="Type.html#2328" class="Bound">A</a> <a id="2348" class="Symbol">→</a> <a id="2350" href="Type.html#111" class="Primitive">Type</a> <a id="2355" href="Type.html#2323" class="Bound">ℓb</a><a id="2357" class="Symbol">)</a> <a id="2359" class="Symbol">:</a> <a id="2361" href="Type.html#111" class="Primitive">Type</a> <a id="2366" class="Symbol">(</a><a id="2367" href="Type.html#2320" class="Bound">ℓa</a> <a id="2370" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="2372" href="Type.html#2323" class="Bound">ℓb</a><a id="2374" class="Symbol">)</a> <a id="2376" class="Keyword">where</a>
  <a id="2384" class="Keyword">field</a>
    <a id="Σ.fst"></a><a id="2394" href="Type.html#2394" class="Field">fst</a> <a id="2398" class="Symbol">:</a> <a id="2400" href="Type.html#2328" class="Bound">A</a>
    <a id="Σ.snd"></a><a id="2406" href="Type.html#2406" class="Field">snd</a> <a id="2410" class="Symbol">:</a> <a id="2412" href="Type.html#2342" class="Bound">B</a> <a id="2414" href="Type.html#2394" class="Field">fst</a>
</pre>
So universe levels create a nice hierarchy that statically guarantee we only have a finite depth of meta types, but things get weird when we try to quantify over level polymorphic types. What level should we give this type?

<pre class="Agda"><a id="very-meta"></a><a id="2656" href="Type.html#2656" class="Function">very-meta</a> <a id="2666" class="Symbol">=</a> <a id="2668" class="Symbol">(</a><a id="2669" href="Type.html#2669" class="Bound">ℓ</a> <a id="2671" class="Symbol">:</a> <a id="2673" href="Type.html#167" class="Postulate">Lvl</a><a id="2676" class="Symbol">)</a> <a id="2678" class="Symbol">→</a> <a id="2680" href="Type.html#111" class="Primitive">Type</a> <a id="2685" href="Type.html#2669" class="Bound">ℓ</a>
</pre>
# Russel's Paradox

To understand this better let's see what goes wrong in the classic example that inspired universe levels: [Russel's Paradox](https://en.wikipedia.org/wiki/Russell%27s_paradox)

Russel's paradox relies on _comprehension_, which lets us construct a class by quantifying over sets satisfying a predicate.
e.g. $$\{ x | x ∈ ℕ , \textrm{even?} x \}$$

We can encode this as:

<pre class="Agda"><a id="3091" class="Keyword">module</a> <a id="russel"></a><a id="3098" href="Type.html#3098" class="Module">russel</a> <a id="3105" class="Keyword">where</a>
  <a id="3113" class="Keyword">data</a> <a id="russel.TYPE"></a><a id="3118" href="Type.html#3118" class="Datatype">TYPE</a> <a id="3123" class="Symbol">:</a> <a id="3125" href="Type.html#125" class="Primitive">Typeω</a> <a id="3131" class="Keyword">where</a> 
    <a id="russel.TYPE.[_∋_]"></a><a id="3142" href="Type.html#3142" class="InductiveConstructor Operator">[_∋_]</a> <a id="3148" class="Symbol">:</a> <a id="3150" class="Symbol">∀</a> <a id="3152" class="Symbol">{</a><a id="3153" href="Type.html#3153" class="Bound">ℓ</a><a id="3154" class="Symbol">}</a> <a id="3156" class="Symbol">(</a><a id="3157" href="Type.html#3157" class="Bound">X</a> <a id="3159" class="Symbol">:</a> <a id="3161" href="Type.html#111" class="Primitive">Type</a> <a id="3166" href="Type.html#3153" class="Bound">ℓ</a><a id="3167" class="Symbol">)</a> <a id="3169" class="Symbol">→</a> <a id="3171" class="Symbol">(</a><a id="3172" href="Type.html#3172" class="Bound">pred</a> <a id="3177" class="Symbol">:</a> <a id="3179" href="Type.html#3157" class="Bound">X</a> <a id="3181" class="Symbol">→</a> <a id="3183" href="Type.html#3118" class="Datatype">TYPE</a><a id="3187" class="Symbol">)</a> <a id="3189" class="Symbol">→</a> <a id="3191" href="Type.html#3118" class="Datatype">TYPE</a>
</pre>Notice a comprehension isn't a normal `Type`, it's a [proper class](https://en.wikipedia.org/wiki/Class_(set_theory)): (`TYPE`)!
It won't type-check as Type without `--type-in-type`, because the resulting type wants its level to be `ℓs ℓ` for _every_ `ℓ` - i.e. it wants an infinite level.
Agda doesn't have an an infinite level `ω`, but it does have a `Typeω` which could be thought of as `Type ω` if one did exist.
`Typeω` exists for precisely this reason - `TYPE` will type-check as `Typeω` even without `--type-in-type`.
In general, `((ℓ : Lvl) → Type ℓ) : Typeω` and the only constructor that can be applied to expressions of kind `Typeω` is `→`.

We can encode a few example [natural number](https://en.wikipedia.org/wiki/Set-theoretic_definition_of_natural_numbers) `TYPE`s by quantifying over basic `Type`s.

<pre class="Agda">  <a id="russel.∅"></a><a id="4027" href="Type.html#4027" class="Function">∅</a> <a id="russel.⟨∅⟩"></a><a id="4029" href="Type.html#4029" class="Function">⟨∅⟩</a> <a id="russel.⟨∅,⟨∅⟩⟩"></a><a id="4033" href="Type.html#4033" class="Function">⟨∅,⟨∅⟩⟩</a> <a id="4041" class="Symbol">:</a> <a id="4043" href="Type.html#3118" class="Datatype">TYPE</a>
  <a id="4050" href="Type.html#4027" class="Function">∅</a> <a id="4052" class="Symbol">=</a> <a id="4054" href="Type.html#3142" class="InductiveConstructor Operator">[</a> <a id="4056" href="Type.html#415" class="Datatype">⊥</a> <a id="4058" href="Type.html#3142" class="InductiveConstructor Operator">∋</a> <a id="4060" class="Symbol">(λ())</a> <a id="4066" href="Type.html#3142" class="InductiveConstructor Operator">]</a>                    <a id="4087" class="Comment">-- 0</a>
  <a id="4094" href="Type.html#4029" class="Function">⟨∅⟩</a> <a id="4098" class="Symbol">=</a> <a id="4100" href="Type.html#3142" class="InductiveConstructor Operator">[</a> <a id="4102" href="Type.html#437" class="Record">⊤</a> <a id="4104" href="Type.html#3142" class="InductiveConstructor Operator">∋</a> <a id="4106" class="Symbol">(λ</a> <a id="4109" href="Type.html#4109" class="Bound">⋆</a> <a id="4111" class="Symbol">→</a> <a id="4113" href="Type.html#4027" class="Function">∅</a><a id="4114" class="Symbol">)</a> <a id="4116" href="Type.html#3142" class="InductiveConstructor Operator">]</a>              <a id="4131" class="Comment">-- 1</a>
  <a id="4138" href="Type.html#4033" class="Function">⟨∅,⟨∅⟩⟩</a> <a id="4146" class="Symbol">=</a> <a id="4148" href="Type.html#3142" class="InductiveConstructor Operator">[</a> <a id="4150" href="Type.html#473" class="Datatype">𝔹</a> <a id="4152" href="Type.html#3142" class="InductiveConstructor Operator">∋</a> <a id="4154" class="Symbol">(λ{</a><a id="4157" href="Type.html#488" class="InductiveConstructor">𝕗</a> <a id="4159" class="Symbol">→</a> <a id="4161" href="Type.html#4029" class="Function">⟨∅⟩</a><a id="4164" class="Symbol">;</a> <a id="4166" href="Type.html#495" class="InductiveConstructor">𝕥</a> <a id="4168" class="Symbol">→</a> <a id="4170" href="Type.html#4027" class="Function">∅</a><a id="4171" class="Symbol">})</a> <a id="4174" href="Type.html#3142" class="InductiveConstructor Operator">]</a> <a id="4176" class="Comment">-- 2</a>
</pre>
The trouble comes when we try to examine the elements of a comprehension:

<pre class="Agda">  <a id="russel._∈_"></a><a id="4271" href="Type.html#4271" class="Function Operator">_∈_</a> <a id="4275" class="Symbol">:</a> <a id="4277" href="Type.html#3118" class="Datatype">TYPE</a> <a id="4282" class="Symbol">→</a> <a id="4284" href="Type.html#3118" class="Datatype">TYPE</a> <a id="4289" class="Symbol">→</a> <a id="4291" href="Type.html#111" class="Primitive">Type</a> <a id="4296" class="Comment">-- This won&#39;t typecheck without --type-in-type</a>
  <a id="4345" href="Type.html#4345" class="Bound">a</a> <a id="4347" href="Type.html#4271" class="Function Operator">∈</a> <a id="4349" href="Type.html#3142" class="InductiveConstructor Operator">[</a> <a id="4351" href="Type.html#4351" class="Bound">X</a> <a id="4353" href="Type.html#3142" class="InductiveConstructor Operator">∋</a> <a id="4355" href="Type.html#4355" class="Bound">f</a> <a id="4357" href="Type.html#3142" class="InductiveConstructor Operator">]</a> <a id="4359" class="Symbol">=</a> <a id="4361" href="Data.Product.html#1369" class="Function">∃</a> <a id="4363" class="Symbol">λ</a> <a id="4365" href="Type.html#4365" class="Bound">x</a> <a id="4367" class="Symbol">→</a> <a id="4369" href="Type.html#4345" class="Bound">a</a> <a id="4371" href="Agda.Builtin.Equality.html#151" class="Datatype Operator">≡</a> <a id="4373" href="Type.html#4355" class="Bound">f</a> <a id="4375" href="Type.html#4365" class="Bound">x</a>

  <a id="russel._∉_"></a><a id="4380" href="Type.html#4380" class="Function Operator">_∉_</a> <a id="4384" class="Symbol">:</a> <a id="4386" href="Type.html#3118" class="Datatype">TYPE</a> <a id="4391" class="Symbol">→</a> <a id="4393" href="Type.html#3118" class="Datatype">TYPE</a> <a id="4398" class="Symbol">→</a> <a id="4400" href="Type.html#111" class="Primitive">Type</a>
  <a id="4407" href="Type.html#4407" class="Bound">a</a> <a id="4409" href="Type.html#4380" class="Function Operator">∉</a> <a id="4411" href="Type.html#4411" class="Bound">b</a> <a id="4413" class="Symbol">=</a> <a id="4415" class="Symbol">(</a><a id="4416" href="Type.html#4407" class="Bound">a</a> <a id="4418" href="Type.html#4271" class="Function Operator">∈</a> <a id="4420" href="Type.html#4411" class="Bound">b</a><a id="4421" class="Symbol">)</a> <a id="4423" class="Symbol">→</a> <a id="4425" href="Type.html#415" class="Datatype">⊥</a>
</pre>
We can now encode Russell's paradoxical class directly as the `TYPE` of all `TYPE` that don't contain themselves:

<pre class="Agda">  <a id="russel.Δ"></a><a id="4558" href="Type.html#4558" class="Function">Δ</a> <a id="4560" class="Symbol">:</a> <a id="4562" href="Type.html#3118" class="Datatype">TYPE</a>
  <a id="4569" href="Type.html#4558" class="Function">Δ</a> <a id="4571" class="Symbol">=</a> <a id="4573" href="Type.html#3142" class="InductiveConstructor Operator">[</a> <a id="4575" class="Symbol">(</a><a id="4576" href="Data.Product.html#1369" class="Function">∃</a> <a id="4578" class="Symbol">λ</a> <a id="4580" href="Type.html#4580" class="Bound">t</a> <a id="4582" class="Symbol">→</a> <a id="4584" href="Type.html#4580" class="Bound">t</a> <a id="4586" href="Type.html#4380" class="Function Operator">∉</a> <a id="4588" href="Type.html#4580" class="Bound">t</a><a id="4589" class="Symbol">)</a> <a id="4591" href="Type.html#3142" class="InductiveConstructor Operator">∋</a> <a id="4593" class="Symbol">(λ{(</a><a id="4597" href="Type.html#4597" class="Bound">t</a> <a id="4599" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4601" href="Type.html#4601" class="Bound">t∉t</a><a id="4604" class="Symbol">)</a> <a id="4606" class="Symbol">→</a> <a id="4608" href="Type.html#4597" class="Bound">t</a><a id="4609" class="Symbol">})</a> <a id="4612" href="Type.html#3142" class="InductiveConstructor Operator">]</a>
</pre>
This does indeed capture the right notion we can prove that a class is in `Δ` if and only iff it doesn't contain itself:

<pre class="Agda">  <a id="russel.x∈Δ→x∉x"></a><a id="4751" href="Type.html#4751" class="Function">x∈Δ→x∉x</a> <a id="4759" class="Symbol">:</a> <a id="4761" class="Symbol">∀</a> <a id="4763" class="Symbol">{</a><a id="4764" href="Type.html#4764" class="Bound">X</a><a id="4765" class="Symbol">}</a> <a id="4767" class="Symbol">→</a> <a id="4769" href="Type.html#4764" class="Bound">X</a> <a id="4771" href="Type.html#4271" class="Function Operator">∈</a> <a id="4773" href="Type.html#4558" class="Function">Δ</a> <a id="4775" class="Symbol">→</a> <a id="4777" href="Type.html#4764" class="Bound">X</a> <a id="4779" href="Type.html#4380" class="Function Operator">∉</a> <a id="4781" href="Type.html#4764" class="Bound">X</a>
  <a id="4785" href="Type.html#4751" class="Function">x∈Δ→x∉x</a> <a id="4793" class="Symbol">((</a><a id="4795" href="Type.html#4795" class="Bound">Y</a> <a id="4797" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4799" href="Type.html#4799" class="Bound">Y∉Y</a><a id="4802" class="Symbol">)</a> <a id="4804" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4806" href="Agda.Builtin.Equality.html#208" class="InductiveConstructor">refl</a><a id="4810" class="Symbol">)</a> <a id="4812" class="Symbol">=</a> <a id="4814" href="Type.html#4799" class="Bound">Y∉Y</a>

  <a id="russel.x∉x→x∈Δ"></a><a id="4821" href="Type.html#4821" class="Function">x∉x→x∈Δ</a> <a id="4829" class="Symbol">:</a> <a id="4831" class="Symbol">∀</a> <a id="4833" class="Symbol">{</a><a id="4834" href="Type.html#4834" class="Bound">X</a><a id="4835" class="Symbol">}</a> <a id="4837" class="Symbol">→</a> <a id="4839" href="Type.html#4834" class="Bound">X</a> <a id="4841" href="Type.html#4380" class="Function Operator">∉</a> <a id="4843" href="Type.html#4834" class="Bound">X</a> <a id="4845" class="Symbol">→</a> <a id="4847" href="Type.html#4834" class="Bound">X</a> <a id="4849" href="Type.html#4271" class="Function Operator">∈</a> <a id="4851" href="Type.html#4558" class="Function">Δ</a>
  <a id="4855" href="Type.html#4821" class="Function">x∉x→x∈Δ</a> <a id="4863" class="Symbol">{</a><a id="4864" href="Type.html#4864" class="Bound">X</a><a id="4865" class="Symbol">}</a> <a id="4867" href="Type.html#4867" class="Bound">X∉X</a> <a id="4871" class="Symbol">=</a> <a id="4873" class="Symbol">(</a><a id="4874" href="Type.html#4864" class="Bound">X</a> <a id="4876" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4878" href="Type.html#4867" class="Bound">X∉X</a><a id="4881" class="Symbol">)</a> <a id="4883" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4885" href="Agda.Builtin.Equality.html#208" class="InductiveConstructor">refl</a>

  <a id="russel.x∈Δ↔x∉x"></a><a id="4893" href="Type.html#4893" class="Function">x∈Δ↔x∉x</a> <a id="4901" class="Symbol">:</a> <a id="4903" class="Symbol">∀</a> <a id="4905" class="Symbol">{</a><a id="4906" href="Type.html#4906" class="Bound">X</a><a id="4907" class="Symbol">}</a> <a id="4909" class="Symbol">→</a> <a id="4911" class="Symbol">(</a><a id="4912" href="Type.html#4906" class="Bound">X</a> <a id="4914" href="Type.html#4271" class="Function Operator">∈</a> <a id="4916" href="Type.html#4558" class="Function">Δ</a><a id="4917" class="Symbol">)</a> <a id="4919" href="Type.html#501" class="Function Operator">iff</a> <a id="4923" class="Symbol">(</a><a id="4924" href="Type.html#4906" class="Bound">X</a> <a id="4926" href="Type.html#4380" class="Function Operator">∉</a> <a id="4928" href="Type.html#4906" class="Bound">X</a><a id="4929" class="Symbol">)</a>
  <a id="4933" href="Type.html#4893" class="Function">x∈Δ↔x∉x</a> <a id="4941" class="Symbol">=</a> <a id="4943" href="Type.html#4751" class="Function">x∈Δ→x∉x</a> <a id="4951" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4953" href="Type.html#4821" class="Function">x∉x→x∈Δ</a>
</pre>Now the infamous contradiction is direct: `Δ` both does and does not contain itself!

<pre class="Agda">  <a id="russel.Δ∉Δ"></a><a id="5061" href="Type.html#5061" class="Function">Δ∉Δ</a> <a id="5065" class="Symbol">:</a> <a id="5067" href="Type.html#4558" class="Function">Δ</a> <a id="5069" href="Type.html#4380" class="Function Operator">∉</a> <a id="5071" href="Type.html#4558" class="Function">Δ</a>
  <a id="5075" href="Type.html#5061" class="Function">Δ∉Δ</a> <a id="5079" href="Type.html#5079" class="Bound">Δ∈Δ</a> <a id="5083" class="Symbol">=</a> <a id="5085" class="Symbol">(</a><a id="5086" href="Type.html#278" class="Field">π₁</a> <a id="5089" href="Type.html#4893" class="Function">x∈Δ↔x∉x</a><a id="5096" class="Symbol">)</a> <a id="5098" href="Type.html#5079" class="Bound">Δ∈Δ</a> <a id="5102" href="Type.html#5079" class="Bound">Δ∈Δ</a>

  <a id="russel.Δ∈Δ"></a><a id="5109" href="Type.html#5109" class="Function">Δ∈Δ</a> <a id="5113" class="Symbol">:</a> <a id="5115" href="Type.html#4558" class="Function">Δ</a> <a id="5117" href="Type.html#4271" class="Function Operator">∈</a> <a id="5119" href="Type.html#4558" class="Function">Δ</a>
  <a id="5123" href="Type.html#5109" class="Function">Δ∈Δ</a> <a id="5127" class="Symbol">=</a> <a id="5129" class="Symbol">(</a><a id="5130" href="Type.html#291" class="Field">π₂</a> <a id="5133" href="Type.html#4893" class="Function">x∈Δ↔x∉x</a><a id="5140" class="Symbol">)</a> <a id="5142" href="Type.html#5061" class="Function">Δ∉Δ</a>

  <a id="russel.paradox"></a><a id="5149" href="Type.html#5149" class="Function">paradox</a> <a id="5157" class="Symbol">:</a> <a id="5159" href="Type.html#415" class="Datatype">⊥</a>
  <a id="5163" href="Type.html#5149" class="Function">paradox</a> <a id="5171" class="Symbol">=</a> <a id="5173" href="Type.html#5061" class="Function">Δ∉Δ</a> <a id="5177" href="Type.html#5109" class="Function">Δ∈Δ</a>
</pre>
So how bad is this? What's actually going on?

If we're using Agda as a proof assistant, it's pretty terrible: we can now prove anything we like!
This is why Agda uses such onerous level checking by default.

But Russel's paradox is quite weird, and one might wonder how easy it is to accidentally violate well-foundedness.

we can unroll `paradox` to see what's happening computationally:

<pre class="Agda"><a id="5585" class="Comment">{-
  _ : paradox ≡ paradox
  _      = paradox
       ≡⟨⟩ Δ∉Δ                          Δ∈Δ
       ≡⟨⟩ (x∈Δ→x∉x Δ∈Δ)                Δ∈Δ
       ≡⟨⟩ (x∈Δ→x∉x (x∉x→x∈Δ Δ∉Δ))      Δ∈Δ
       ≡⟨⟩ (x∈Δ→x∉x ((Δ , Δ∉Δ) , refl)) Δ∈Δ
       ≡⟨⟩ Δ∉Δ                          Δ∈Δ ∎
-}</a>
</pre>
If you try to compile the above commented code the type-checker will hang, but we can see why: `Δ∉Δ Δ∈Δ` reduces to itself!

It turns out that _all_ unsound uses of `--type-in-type` [result in type-checking non-termination](http://www.cs.nott.ac.uk/~psztxa/publ/msfp08.pdf), so we'll never construct an ill-typed value at run-time.

For this reason we follow Haskell's example and include `--type-in-type` by default, to maintain clarity by reducing noise.

When checking a serious proof it's worth reintroducing `Level`s for consistency,
but for interactive exploratory work or didactic communication it's nearly always a hindrance.
