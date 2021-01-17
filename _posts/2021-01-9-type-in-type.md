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

<a id="Dynamic∀"></a><a id="1135" href="Type.html#1135" class="Function">Dynamic∀</a> <a id="1144" class="Symbol">:</a> <a id="1146" href="Type.html#111" class="Primitive">Type₁</a> 
<a id="1153" href="Type.html#1135" class="Function">Dynamic∀</a> <a id="1162" class="Symbol">=</a> <a id="1164" class="Symbol">∀</a> <a id="1166" class="Symbol">{</a><a id="1167" href="Type.html#1167" class="Bound">r</a> <a id="1169" class="Symbol">:</a> <a id="1171" href="Type.html#111" class="Primitive">Type₀</a><a id="1176" class="Symbol">}</a> <a id="1178" class="Symbol">→</a> <a id="1180" class="Symbol">((</a><a id="1182" href="Type.html#1182" class="Bound">Ty</a> <a id="1185" class="Symbol">:</a> <a id="1187" href="Type.html#111" class="Primitive">Type₀</a><a id="1192" class="Symbol">)</a> <a id="1194" class="Symbol">→</a> <a id="1196" href="Type.html#1182" class="Bound">Ty</a> <a id="1199" class="Symbol">→</a> <a id="1201" href="Type.html#1167" class="Bound">r</a><a id="1202" class="Symbol">)</a> <a id="1204" class="Symbol">→</a> <a id="1206" href="Type.html#1167" class="Bound">r</a>
</pre>
Contrast this with the identity type, which is at the same level as `Ty` because it takes it as a generic parameter, rather than existentially quantifying over it.

<pre class="Agda"><a id="1386" class="Keyword">record</a> <a id="Identity"></a><a id="1393" href="Type.html#1393" class="Record">Identity</a> <a id="1402" class="Symbol">(</a><a id="1403" href="Type.html#1403" class="Bound">Ty</a> <a id="1406" class="Symbol">:</a> <a id="1408" href="Type.html#111" class="Primitive">Type₀</a><a id="1413" class="Symbol">)</a> <a id="1415" class="Symbol">:</a> <a id="1417" href="Type.html#111" class="Primitive">Type₀</a> <a id="1423" class="Keyword">where</a>
  <a id="1431" class="Keyword">field</a> <a id="Identity.term"></a><a id="1437" href="Type.html#1437" class="Field">term</a> <a id="1442" class="Symbol">:</a> <a id="1444" href="Type.html#1403" class="Bound">Ty</a>

<a id="Identity∀"></a><a id="1448" href="Type.html#1448" class="Function">Identity∀</a> <a id="1458" class="Symbol">:</a> <a id="1460" href="Type.html#111" class="Primitive">Type₀</a> <a id="1466" class="Symbol">→</a> <a id="1468" href="Type.html#111" class="Primitive">Type₀</a>
<a id="1474" href="Type.html#1448" class="Function">Identity∀</a> <a id="1484" href="Type.html#1484" class="Bound">Ty</a> <a id="1487" class="Symbol">=</a> <a id="1489" href="Type.html#1484" class="Bound">Ty</a>
</pre>
It would be annoying to figure out which type level to use on our own, so types are polymorphic over _universe level_.
`Type` alone is sugar for `Type₀`, which is itself sugar for `Type ℓ0`, and `Type₁` is sugar for `Type (ℓs ℓ0)` etc.
The full polymorphic type is `Type : (ℓ : Lvl) → Type (ℓs ℓ)`, for a special `Lvl` type:

<pre class="Agda"><a id="1832" class="Comment">-- postulate Lvl : Type</a>
<a id="1856" class="Comment">-- {-# BUILTIN LEVEL Lvl #-}</a>
<a id="1885" class="Comment">-- {-# BUILTIN LEVELZERO ℓ0  #-} -- : Lvl</a>
<a id="1927" class="Comment">-- {-# BUILTIN LEVELSUC  ℓs  #-} -- : Lvl → Lvl</a>
<a id="1975" class="Comment">-- {-# BUILTIN LEVELMAX  _⊔_ #-} -- : Lvl → Lvl → Lvl</a>
<a id="2029" class="Comment">-- infixl 6 _⊔_</a>
</pre>
`Lvl` is a magic type. It isn't possible to pattern match on levels, and they're erased at run-time.

When multiple polymorphic levels appear in a type, the resulting level must bound all of them. This is achieved with the max operator. e.g. the dependent pair:

<pre class="Agda"><a id="2321" class="Keyword">record</a> <a id="Σ"></a><a id="2328" href="Type.html#2328" class="Record">Σ</a> <a id="2330" class="Symbol">{</a><a id="2331" href="Type.html#2331" class="Bound">ℓa</a> <a id="2334" href="Type.html#2334" class="Bound">ℓb</a><a id="2336" class="Symbol">}</a> <a id="2338" class="Symbol">(</a><a id="2339" href="Type.html#2339" class="Bound">A</a> <a id="2341" class="Symbol">:</a> <a id="2343" href="Type.html#111" class="Primitive">Type</a> <a id="2348" href="Type.html#2331" class="Bound">ℓa</a><a id="2350" class="Symbol">)</a> <a id="2352" class="Symbol">(</a><a id="2353" href="Type.html#2353" class="Bound">B</a> <a id="2355" class="Symbol">:</a> <a id="2357" href="Type.html#2339" class="Bound">A</a> <a id="2359" class="Symbol">→</a> <a id="2361" href="Type.html#111" class="Primitive">Type</a> <a id="2366" href="Type.html#2334" class="Bound">ℓb</a><a id="2368" class="Symbol">)</a> <a id="2370" class="Symbol">:</a> <a id="2372" href="Type.html#111" class="Primitive">Type</a> <a id="2377" class="Symbol">(</a><a id="2378" href="Type.html#2331" class="Bound">ℓa</a> <a id="2381" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="2383" href="Type.html#2334" class="Bound">ℓb</a><a id="2385" class="Symbol">)</a> <a id="2387" class="Keyword">where</a>
  <a id="2395" class="Keyword">field</a>
    <a id="Σ.fst"></a><a id="2405" href="Type.html#2405" class="Field">fst</a> <a id="2409" class="Symbol">:</a> <a id="2411" href="Type.html#2339" class="Bound">A</a>
    <a id="Σ.snd"></a><a id="2417" href="Type.html#2417" class="Field">snd</a> <a id="2421" class="Symbol">:</a> <a id="2423" href="Type.html#2353" class="Bound">B</a> <a id="2425" href="Type.html#2405" class="Field">fst</a>
</pre>
So universe levels create a nice hierarchy that statically guarantee we only have a finite depth of meta types, but things get weird when we try to quantify over level polymorphic types. What level should we give this type?

<pre class="Agda"><a id="very-meta"></a><a id="2667" href="Type.html#2667" class="Function">very-meta</a> <a id="2677" class="Symbol">=</a> <a id="2679" class="Symbol">(</a><a id="2680" href="Type.html#2680" class="Bound">ℓ</a> <a id="2682" class="Symbol">:</a> <a id="2684" href="Type.html#167" class="Postulate">Lvl</a><a id="2687" class="Symbol">)</a> <a id="2689" class="Symbol">→</a> <a id="2691" href="Type.html#111" class="Primitive">Type</a> <a id="2696" href="Type.html#2680" class="Bound">ℓ</a>
</pre>
# Russel's Paradox

To understand this better let's see what goes wrong in the classic example that inspired universe levels: [Russel's Paradox](https://en.wikipedia.org/wiki/Russell%27s_paradox)

Russel's paradox relies on _comprehension_, which lets us construct a class by quantifying over sets satisfying a predicate.
e.g. $$\{ x | x ∈ ℕ , \textrm{even?} x \}$$

We can encode this as:

<pre class="Agda"><a id="3102" class="Keyword">module</a> <a id="russel"></a><a id="3109" href="Type.html#3109" class="Module">russel</a> <a id="3116" class="Keyword">where</a>
  <a id="3124" class="Keyword">data</a> <a id="russel.TYPE"></a><a id="3129" href="Type.html#3129" class="Datatype">TYPE</a> <a id="3134" class="Symbol">:</a> <a id="3136" href="Type.html#125" class="Primitive">Typeω</a> <a id="3142" class="Keyword">where</a> 
    <a id="russel.TYPE.[_∋_]"></a><a id="3153" href="Type.html#3153" class="InductiveConstructor Operator">[_∋_]</a> <a id="3159" class="Symbol">:</a> <a id="3161" class="Symbol">∀</a> <a id="3163" class="Symbol">{</a><a id="3164" href="Type.html#3164" class="Bound">ℓ</a><a id="3165" class="Symbol">}</a> <a id="3167" class="Symbol">(</a><a id="3168" href="Type.html#3168" class="Bound">X</a> <a id="3170" class="Symbol">:</a> <a id="3172" href="Type.html#111" class="Primitive">Type</a> <a id="3177" href="Type.html#3164" class="Bound">ℓ</a><a id="3178" class="Symbol">)</a> <a id="3180" class="Symbol">→</a> <a id="3182" class="Symbol">(</a><a id="3183" href="Type.html#3183" class="Bound">pred</a> <a id="3188" class="Symbol">:</a> <a id="3190" href="Type.html#3168" class="Bound">X</a> <a id="3192" class="Symbol">→</a> <a id="3194" href="Type.html#3129" class="Datatype">TYPE</a><a id="3198" class="Symbol">)</a> <a id="3200" class="Symbol">→</a> <a id="3202" href="Type.html#3129" class="Datatype">TYPE</a>
</pre>Notice a comprehension isn't a normal `Type`, it's a [proper class](https://en.wikipedia.org/wiki/Class_(set_theory)): (`TYPE`)!
It won't type-check as Type without `--type-in-type`, because the resulting type wants its level to be `ℓs ℓ` for _every_ `ℓ` - i.e. it wants an infinite level.
Agda doesn't have an an infinite level `ω`, but it does have a `Typeω` which could be thought of as `Type ω` if one did exist.
`Typeω` exists for precisely this reason - `TYPE` will type-check as `Typeω` even without `--type-in-type`.
In general, `((ℓ : Lvl) → Type ℓ) : Typeω` and the only constructor that can be applied to expressions of kind `Typeω` is `→`.

We can encode a few example [natural number](https://en.wikipedia.org/wiki/Set-theoretic_definition_of_natural_numbers) `TYPE`s by quantifying over basic `Type`s.

<pre class="Agda">  <a id="russel.∅"></a><a id="4038" href="Type.html#4038" class="Function">∅</a> <a id="russel.⟨∅⟩"></a><a id="4040" href="Type.html#4040" class="Function">⟨∅⟩</a> <a id="russel.⟨∅,⟨∅⟩⟩"></a><a id="4044" href="Type.html#4044" class="Function">⟨∅,⟨∅⟩⟩</a> <a id="4052" class="Symbol">:</a> <a id="4054" href="Type.html#3129" class="Datatype">TYPE</a>
  <a id="4061" href="Type.html#4038" class="Function">∅</a> <a id="4063" class="Symbol">=</a> <a id="4065" href="Type.html#3153" class="InductiveConstructor Operator">[</a> <a id="4067" href="Type.html#415" class="Datatype">⊥</a> <a id="4069" href="Type.html#3153" class="InductiveConstructor Operator">∋</a> <a id="4071" class="Symbol">(λ())</a> <a id="4077" href="Type.html#3153" class="InductiveConstructor Operator">]</a>                    <a id="4098" class="Comment">-- 0</a>
  <a id="4105" href="Type.html#4040" class="Function">⟨∅⟩</a> <a id="4109" class="Symbol">=</a> <a id="4111" href="Type.html#3153" class="InductiveConstructor Operator">[</a> <a id="4113" href="Type.html#437" class="Record">⊤</a> <a id="4115" href="Type.html#3153" class="InductiveConstructor Operator">∋</a> <a id="4117" class="Symbol">(λ</a> <a id="4120" href="Type.html#4120" class="Bound">⋆</a> <a id="4122" class="Symbol">→</a> <a id="4124" href="Type.html#4038" class="Function">∅</a><a id="4125" class="Symbol">)</a> <a id="4127" href="Type.html#3153" class="InductiveConstructor Operator">]</a>              <a id="4142" class="Comment">-- 1</a>
  <a id="4149" href="Type.html#4044" class="Function">⟨∅,⟨∅⟩⟩</a> <a id="4157" class="Symbol">=</a> <a id="4159" href="Type.html#3153" class="InductiveConstructor Operator">[</a> <a id="4161" href="Type.html#473" class="Datatype">𝔹</a> <a id="4163" href="Type.html#3153" class="InductiveConstructor Operator">∋</a> <a id="4165" class="Symbol">(λ{</a><a id="4168" href="Type.html#488" class="InductiveConstructor">𝕗</a> <a id="4170" class="Symbol">→</a> <a id="4172" href="Type.html#4040" class="Function">⟨∅⟩</a><a id="4175" class="Symbol">;</a> <a id="4177" href="Type.html#495" class="InductiveConstructor">𝕥</a> <a id="4179" class="Symbol">→</a> <a id="4181" href="Type.html#4038" class="Function">∅</a><a id="4182" class="Symbol">})</a> <a id="4185" href="Type.html#3153" class="InductiveConstructor Operator">]</a> <a id="4187" class="Comment">-- 2</a>
</pre>
The trouble comes when we try to examine the elements of a comprehension:

<pre class="Agda">  <a id="russel._∈_"></a><a id="4282" href="Type.html#4282" class="Function Operator">_∈_</a> <a id="4286" class="Symbol">:</a> <a id="4288" href="Type.html#3129" class="Datatype">TYPE</a> <a id="4293" class="Symbol">→</a> <a id="4295" href="Type.html#3129" class="Datatype">TYPE</a> <a id="4300" class="Symbol">→</a> <a id="4302" href="Type.html#111" class="Primitive">Type</a> <a id="4307" class="Comment">-- This won&#39;t typecheck without --type-in-type</a>
  <a id="4356" href="Type.html#4356" class="Bound">a</a> <a id="4358" href="Type.html#4282" class="Function Operator">∈</a> <a id="4360" href="Type.html#3153" class="InductiveConstructor Operator">[</a> <a id="4362" href="Type.html#4362" class="Bound">X</a> <a id="4364" href="Type.html#3153" class="InductiveConstructor Operator">∋</a> <a id="4366" href="Type.html#4366" class="Bound">f</a> <a id="4368" href="Type.html#3153" class="InductiveConstructor Operator">]</a> <a id="4370" class="Symbol">=</a> <a id="4372" href="Data.Product.html#1369" class="Function">∃</a> <a id="4374" class="Symbol">λ</a> <a id="4376" href="Type.html#4376" class="Bound">x</a> <a id="4378" class="Symbol">→</a> <a id="4380" href="Type.html#4356" class="Bound">a</a> <a id="4382" href="Agda.Builtin.Equality.html#151" class="Datatype Operator">≡</a> <a id="4384" href="Type.html#4366" class="Bound">f</a> <a id="4386" href="Type.html#4376" class="Bound">x</a>

  <a id="russel._∉_"></a><a id="4391" href="Type.html#4391" class="Function Operator">_∉_</a> <a id="4395" class="Symbol">:</a> <a id="4397" href="Type.html#3129" class="Datatype">TYPE</a> <a id="4402" class="Symbol">→</a> <a id="4404" href="Type.html#3129" class="Datatype">TYPE</a> <a id="4409" class="Symbol">→</a> <a id="4411" href="Type.html#111" class="Primitive">Type</a>
  <a id="4418" href="Type.html#4418" class="Bound">a</a> <a id="4420" href="Type.html#4391" class="Function Operator">∉</a> <a id="4422" href="Type.html#4422" class="Bound">b</a> <a id="4424" class="Symbol">=</a> <a id="4426" class="Symbol">(</a><a id="4427" href="Type.html#4418" class="Bound">a</a> <a id="4429" href="Type.html#4282" class="Function Operator">∈</a> <a id="4431" href="Type.html#4422" class="Bound">b</a><a id="4432" class="Symbol">)</a> <a id="4434" class="Symbol">→</a> <a id="4436" href="Type.html#415" class="Datatype">⊥</a>
</pre>
We can now encode Russell's paradoxical class directly as the `TYPE` of all `TYPE` that don't contain themselves:

<pre class="Agda">  <a id="russel.Δ"></a><a id="4569" href="Type.html#4569" class="Function">Δ</a> <a id="4571" class="Symbol">:</a> <a id="4573" href="Type.html#3129" class="Datatype">TYPE</a>
  <a id="4580" href="Type.html#4569" class="Function">Δ</a> <a id="4582" class="Symbol">=</a> <a id="4584" href="Type.html#3153" class="InductiveConstructor Operator">[</a> <a id="4586" class="Symbol">(</a><a id="4587" href="Data.Product.html#1369" class="Function">∃</a> <a id="4589" class="Symbol">λ</a> <a id="4591" href="Type.html#4591" class="Bound">t</a> <a id="4593" class="Symbol">→</a> <a id="4595" href="Type.html#4591" class="Bound">t</a> <a id="4597" href="Type.html#4391" class="Function Operator">∉</a> <a id="4599" href="Type.html#4591" class="Bound">t</a><a id="4600" class="Symbol">)</a> <a id="4602" href="Type.html#3153" class="InductiveConstructor Operator">∋</a> <a id="4604" class="Symbol">(λ{(</a><a id="4608" href="Type.html#4608" class="Bound">t</a> <a id="4610" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4612" href="Type.html#4612" class="Bound">t∉t</a><a id="4615" class="Symbol">)</a> <a id="4617" class="Symbol">→</a> <a id="4619" href="Type.html#4608" class="Bound">t</a><a id="4620" class="Symbol">})</a> <a id="4623" href="Type.html#3153" class="InductiveConstructor Operator">]</a>
</pre>
This does indeed capture the right notion we can prove that a class is in `Δ` if and only iff it doesn't contain itself:

<pre class="Agda">  <a id="russel.x∈Δ→x∉x"></a><a id="4762" href="Type.html#4762" class="Function">x∈Δ→x∉x</a> <a id="4770" class="Symbol">:</a> <a id="4772" class="Symbol">∀</a> <a id="4774" class="Symbol">{</a><a id="4775" href="Type.html#4775" class="Bound">X</a><a id="4776" class="Symbol">}</a> <a id="4778" class="Symbol">→</a> <a id="4780" href="Type.html#4775" class="Bound">X</a> <a id="4782" href="Type.html#4282" class="Function Operator">∈</a> <a id="4784" href="Type.html#4569" class="Function">Δ</a> <a id="4786" class="Symbol">→</a> <a id="4788" href="Type.html#4775" class="Bound">X</a> <a id="4790" href="Type.html#4391" class="Function Operator">∉</a> <a id="4792" href="Type.html#4775" class="Bound">X</a>
  <a id="4796" href="Type.html#4762" class="Function">x∈Δ→x∉x</a> <a id="4804" class="Symbol">((</a><a id="4806" href="Type.html#4806" class="Bound">Y</a> <a id="4808" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4810" href="Type.html#4810" class="Bound">Y∉Y</a><a id="4813" class="Symbol">)</a> <a id="4815" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4817" href="Agda.Builtin.Equality.html#208" class="InductiveConstructor">refl</a><a id="4821" class="Symbol">)</a> <a id="4823" class="Symbol">=</a> <a id="4825" href="Type.html#4810" class="Bound">Y∉Y</a>

  <a id="russel.x∉x→x∈Δ"></a><a id="4832" href="Type.html#4832" class="Function">x∉x→x∈Δ</a> <a id="4840" class="Symbol">:</a> <a id="4842" class="Symbol">∀</a> <a id="4844" class="Symbol">{</a><a id="4845" href="Type.html#4845" class="Bound">X</a><a id="4846" class="Symbol">}</a> <a id="4848" class="Symbol">→</a> <a id="4850" href="Type.html#4845" class="Bound">X</a> <a id="4852" href="Type.html#4391" class="Function Operator">∉</a> <a id="4854" href="Type.html#4845" class="Bound">X</a> <a id="4856" class="Symbol">→</a> <a id="4858" href="Type.html#4845" class="Bound">X</a> <a id="4860" href="Type.html#4282" class="Function Operator">∈</a> <a id="4862" href="Type.html#4569" class="Function">Δ</a>
  <a id="4866" href="Type.html#4832" class="Function">x∉x→x∈Δ</a> <a id="4874" class="Symbol">{</a><a id="4875" href="Type.html#4875" class="Bound">X</a><a id="4876" class="Symbol">}</a> <a id="4878" href="Type.html#4878" class="Bound">X∉X</a> <a id="4882" class="Symbol">=</a> <a id="4884" class="Symbol">(</a><a id="4885" href="Type.html#4875" class="Bound">X</a> <a id="4887" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4889" href="Type.html#4878" class="Bound">X∉X</a><a id="4892" class="Symbol">)</a> <a id="4894" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4896" href="Agda.Builtin.Equality.html#208" class="InductiveConstructor">refl</a>

  <a id="russel.x∈Δ↔x∉x"></a><a id="4904" href="Type.html#4904" class="Function">x∈Δ↔x∉x</a> <a id="4912" class="Symbol">:</a> <a id="4914" class="Symbol">∀</a> <a id="4916" class="Symbol">{</a><a id="4917" href="Type.html#4917" class="Bound">X</a><a id="4918" class="Symbol">}</a> <a id="4920" class="Symbol">→</a> <a id="4922" class="Symbol">(</a><a id="4923" href="Type.html#4917" class="Bound">X</a> <a id="4925" href="Type.html#4282" class="Function Operator">∈</a> <a id="4927" href="Type.html#4569" class="Function">Δ</a><a id="4928" class="Symbol">)</a> <a id="4930" href="Type.html#501" class="Function Operator">iff</a> <a id="4934" class="Symbol">(</a><a id="4935" href="Type.html#4917" class="Bound">X</a> <a id="4937" href="Type.html#4391" class="Function Operator">∉</a> <a id="4939" href="Type.html#4917" class="Bound">X</a><a id="4940" class="Symbol">)</a>
  <a id="4944" href="Type.html#4904" class="Function">x∈Δ↔x∉x</a> <a id="4952" class="Symbol">=</a> <a id="4954" href="Type.html#4762" class="Function">x∈Δ→x∉x</a> <a id="4962" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4964" href="Type.html#4832" class="Function">x∉x→x∈Δ</a>
</pre>Now the infamous contradiction is direct: `Δ` both does and does not contain itself!

<pre class="Agda">  <a id="russel.Δ∉Δ"></a><a id="5072" href="Type.html#5072" class="Function">Δ∉Δ</a> <a id="5076" class="Symbol">:</a> <a id="5078" href="Type.html#4569" class="Function">Δ</a> <a id="5080" href="Type.html#4391" class="Function Operator">∉</a> <a id="5082" href="Type.html#4569" class="Function">Δ</a>
  <a id="5086" href="Type.html#5072" class="Function">Δ∉Δ</a> <a id="5090" href="Type.html#5090" class="Bound">Δ∈Δ</a> <a id="5094" class="Symbol">=</a> <a id="5096" class="Symbol">(</a><a id="5097" href="Type.html#278" class="Field">π₁</a> <a id="5100" href="Type.html#4904" class="Function">x∈Δ↔x∉x</a><a id="5107" class="Symbol">)</a> <a id="5109" href="Type.html#5090" class="Bound">Δ∈Δ</a> <a id="5113" href="Type.html#5090" class="Bound">Δ∈Δ</a> 

  <a id="russel.Δ∈Δ"></a><a id="5121" href="Type.html#5121" class="Function">Δ∈Δ</a> <a id="5125" class="Symbol">:</a> <a id="5127" href="Type.html#4569" class="Function">Δ</a> <a id="5129" href="Type.html#4282" class="Function Operator">∈</a> <a id="5131" href="Type.html#4569" class="Function">Δ</a>
  <a id="5135" href="Type.html#5121" class="Function">Δ∈Δ</a> <a id="5139" class="Symbol">=</a> <a id="5141" class="Symbol">(</a><a id="5142" href="Type.html#291" class="Field">π₂</a> <a id="5145" href="Type.html#4904" class="Function">x∈Δ↔x∉x</a><a id="5152" class="Symbol">)</a> <a id="5154" href="Type.html#5072" class="Function">Δ∉Δ</a>

  <a id="russel.paradox"></a><a id="5161" href="Type.html#5161" class="Function">paradox</a> <a id="5169" class="Symbol">:</a> <a id="5171" href="Type.html#415" class="Datatype">⊥</a>
  <a id="5175" href="Type.html#5161" class="Function">paradox</a> <a id="5183" class="Symbol">=</a> <a id="5185" href="Type.html#5072" class="Function">Δ∉Δ</a> <a id="5189" href="Type.html#5121" class="Function">Δ∈Δ</a>

  <a id="5196" class="Keyword">open</a> <a id="5201" class="Keyword">import</a> <a id="5208" href="Data.Nat.html" class="Module">Data.Nat</a> <a id="5217" class="Keyword">using</a> <a id="5223" class="Symbol">(</a><a id="5224" href="Agda.Builtin.Nat.html#192" class="Datatype">ℕ</a><a id="5225" class="Symbol">)</a>
  <a id="russel.x"></a><a id="5229" href="Type.html#5229" class="Function">x</a> <a id="5231" class="Symbol">:</a> <a id="5233" href="Agda.Builtin.Nat.html#192" class="Datatype">ℕ</a>
  <a id="5237" href="Type.html#5229" class="Function">x</a> <a id="5239" class="Symbol">=</a> <a id="5241" class="Number">3</a>
</pre>
So how bad is this? What's actually going on?

If we're using Agda as a proof assistant, it's pretty terrible: we can now prove anything we like!
This is why Agda uses such onerous level checking by default.

But Russel's paradox is quite weird, and one might wonder how easy it is to accidentally violate well-foundedness.

we can unroll `paradox` to see what's happening computationally:

<pre class="Agda"><a id="5647" class="Comment">-- _ : paradox ≡ paradox</a>
<a id="5672" class="Comment">--  _      = paradox</a>
<a id="5693" class="Comment">--       ≡⟨⟩ Δ∉Δ                          Δ∈Δ</a>
<a id="5739" class="Comment">--       ≡⟨⟩ (x∈Δ→x∉x Δ∈Δ)                Δ∈Δ</a>
<a id="5785" class="Comment">--       ≡⟨⟩ (x∈Δ→x∉x (x∉x→x∈Δ Δ∉Δ))      Δ∈Δ</a>
<a id="5831" class="Comment">--       ≡⟨⟩ (x∈Δ→x∉x ((Δ , Δ∉Δ) , refl)) Δ∈Δ</a>
<a id="5877" class="Comment">--       ≡⟨⟩ Δ∉Δ                          Δ∈Δ ∎</a>
</pre>
If you try to compile the above commented code the type-checker will hang, but we can see why: `Δ∉Δ Δ∈Δ` reduces to itself!

It turns out that _all_ unsound uses of `--type-in-type` [result in type-checking non-termination](http://www.cs.nott.ac.uk/~psztxa/publ/msfp08.pdf), so we'll never construct an ill-typed value at run-time.

For this reason we follow Haskell's example and include `--type-in-type` by default, to maintain clarity by reducing noise.

When checking a serious proof it's worth reintroducing `Level`s for consistency,
but for interactive exploratory work or didactic communication it's nearly always a hindrance.
