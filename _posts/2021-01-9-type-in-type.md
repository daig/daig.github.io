---
permalink: Type.html
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

Agda's type heirarchy is more complex.

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
`Lvl` is a magic type. It isn't possible to pattern match on levels, and they're erased at runtime.

When multiple polymorphic levels appear in a type, the resulting level must bound all of them. This is achieved with the max operator. Eg the dependent pair:

<pre class="Agda"><a id="2307" class="Keyword">record</a> <a id="Σ"></a><a id="2314" href="Type.html#2314" class="Record">Σ</a> <a id="2316" class="Symbol">{</a><a id="2317" href="Type.html#2317" class="Bound">ℓa</a> <a id="2320" href="Type.html#2320" class="Bound">ℓb</a><a id="2322" class="Symbol">}</a> <a id="2324" class="Symbol">(</a><a id="2325" href="Type.html#2325" class="Bound">A</a> <a id="2327" class="Symbol">:</a> <a id="2329" href="Type.html#111" class="Primitive">Type</a> <a id="2334" href="Type.html#2317" class="Bound">ℓa</a><a id="2336" class="Symbol">)</a> <a id="2338" class="Symbol">(</a><a id="2339" href="Type.html#2339" class="Bound">B</a> <a id="2341" class="Symbol">:</a> <a id="2343" href="Type.html#2325" class="Bound">A</a> <a id="2345" class="Symbol">→</a> <a id="2347" href="Type.html#111" class="Primitive">Type</a> <a id="2352" href="Type.html#2320" class="Bound">ℓb</a><a id="2354" class="Symbol">)</a> <a id="2356" class="Symbol">:</a> <a id="2358" href="Type.html#111" class="Primitive">Type</a> <a id="2363" class="Symbol">(</a><a id="2364" href="Type.html#2317" class="Bound">ℓa</a> <a id="2367" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="2369" href="Type.html#2320" class="Bound">ℓb</a><a id="2371" class="Symbol">)</a> <a id="2373" class="Keyword">where</a>
  <a id="2381" class="Keyword">field</a>
    <a id="Σ.fst"></a><a id="2391" href="Type.html#2391" class="Field">fst</a> <a id="2395" class="Symbol">:</a> <a id="2397" href="Type.html#2325" class="Bound">A</a>
    <a id="Σ.snd"></a><a id="2403" href="Type.html#2403" class="Field">snd</a> <a id="2407" class="Symbol">:</a> <a id="2409" href="Type.html#2339" class="Bound">B</a> <a id="2411" href="Type.html#2391" class="Field">fst</a>
</pre>
So universe levels create a nice heirarchy that statically gaurentee we only have a finite depth of meta types, but things get weird when we try to quantify over level polymorphic types. What level should we give this type?

<pre class="Agda"><a id="very-meta"></a><a id="2653" href="Type.html#2653" class="Function">very-meta</a> <a id="2663" class="Symbol">=</a> <a id="2665" class="Symbol">(</a><a id="2666" href="Type.html#2666" class="Bound">ℓ</a> <a id="2668" class="Symbol">:</a> <a id="2670" href="Type.html#167" class="Postulate">Lvl</a><a id="2673" class="Symbol">)</a> <a id="2675" class="Symbol">→</a> <a id="2677" href="Type.html#111" class="Primitive">Type</a> <a id="2682" href="Type.html#2666" class="Bound">ℓ</a>
</pre>
# Russel's Paradox

To understand this better let's see what goes wrong in the classic example that inspired universe levels: [Russel's Paradox](https://en.wikipedia.org/wiki/Russell%27s_paradox)

Russel's paradox relies on _comprehension_, which lets us construct a class by quantifying over sets satisfying a predicate.
eg $$\{ x | x ∈ ℕ , \textrm{even?} x \}$$

We can encode this as:

<pre class="Agda"><a id="3086" class="Keyword">module</a> <a id="russel"></a><a id="3093" href="Type.html#3093" class="Module">russel</a> <a id="3100" class="Keyword">where</a>
  <a id="3108" class="Keyword">data</a> <a id="russel.TYPE"></a><a id="3113" href="Type.html#3113" class="Datatype">TYPE</a> <a id="3118" class="Symbol">:</a> <a id="3120" href="Type.html#125" class="Primitive">Typeω</a> <a id="3126" class="Keyword">where</a> 
    <a id="russel.TYPE.[_∋_]"></a><a id="3137" href="Type.html#3137" class="InductiveConstructor Operator">[_∋_]</a> <a id="3143" class="Symbol">:</a> <a id="3145" class="Symbol">∀</a> <a id="3147" class="Symbol">{</a><a id="3148" href="Type.html#3148" class="Bound">ℓ</a><a id="3149" class="Symbol">}</a> <a id="3151" class="Symbol">(</a><a id="3152" href="Type.html#3152" class="Bound">X</a> <a id="3154" class="Symbol">:</a> <a id="3156" href="Type.html#111" class="Primitive">Type</a> <a id="3161" href="Type.html#3148" class="Bound">ℓ</a><a id="3162" class="Symbol">)</a> <a id="3164" class="Symbol">→</a> <a id="3166" class="Symbol">(</a><a id="3167" href="Type.html#3167" class="Bound">pred</a> <a id="3172" class="Symbol">:</a> <a id="3174" href="Type.html#3152" class="Bound">X</a> <a id="3176" class="Symbol">→</a> <a id="3178" href="Type.html#3113" class="Datatype">TYPE</a><a id="3182" class="Symbol">)</a> <a id="3184" class="Symbol">→</a> <a id="3186" href="Type.html#3113" class="Datatype">TYPE</a>
</pre>Notice a comprehension isn't a normal `Type`, it's a [proper class](https://en.wikipedia.org/wiki/Class_(set_theory)): (`TYPE`)!
It won't typecheck as Type without `--type-in-type`, because the resulting type wants its level to be `ℓs ℓ` for _every_ `ℓ` - ie it wants an infinite level.
Agda doesn't have an an infinite level `ω`, but it does have a `Typeω` which could be thought of as `Type ω` if one did exist.
`Typeω` exists for precisely this reason - `TYPE` will typecheck as `Typeω` even without `--type-in-type`.
In general, `((ℓ : Lvl) → Type ℓ) : Typeω` and the only constructor that can be applied to expressions of kind `Typeω` is `→`.

We can encode a few example [natural number](https://en.wikipedia.org/wiki/Set-theoretic_definition_of_natural_numbers) `TYPE`s by quantifying over basic `Type`s.

<pre class="Agda">  <a id="russel.∅"></a><a id="4018" href="Type.html#4018" class="Function">∅</a> <a id="russel.⟨∅⟩"></a><a id="4020" href="Type.html#4020" class="Function">⟨∅⟩</a> <a id="russel.⟨∅,⟨∅⟩⟩"></a><a id="4024" href="Type.html#4024" class="Function">⟨∅,⟨∅⟩⟩</a> <a id="4032" class="Symbol">:</a> <a id="4034" href="Type.html#3113" class="Datatype">TYPE</a>
  <a id="4041" href="Type.html#4018" class="Function">∅</a> <a id="4043" class="Symbol">=</a> <a id="4045" href="Type.html#3137" class="InductiveConstructor Operator">[</a> <a id="4047" href="Type.html#415" class="Datatype">⊥</a> <a id="4049" href="Type.html#3137" class="InductiveConstructor Operator">∋</a> <a id="4051" class="Symbol">(λ())</a> <a id="4057" href="Type.html#3137" class="InductiveConstructor Operator">]</a>                    <a id="4078" class="Comment">-- 0</a>
  <a id="4085" href="Type.html#4020" class="Function">⟨∅⟩</a> <a id="4089" class="Symbol">=</a> <a id="4091" href="Type.html#3137" class="InductiveConstructor Operator">[</a> <a id="4093" href="Type.html#437" class="Record">⊤</a> <a id="4095" href="Type.html#3137" class="InductiveConstructor Operator">∋</a> <a id="4097" class="Symbol">(λ</a> <a id="4100" href="Type.html#4100" class="Bound">⋆</a> <a id="4102" class="Symbol">→</a> <a id="4104" href="Type.html#4018" class="Function">∅</a><a id="4105" class="Symbol">)</a> <a id="4107" href="Type.html#3137" class="InductiveConstructor Operator">]</a>              <a id="4122" class="Comment">-- 1</a>
  <a id="4129" href="Type.html#4024" class="Function">⟨∅,⟨∅⟩⟩</a> <a id="4137" class="Symbol">=</a> <a id="4139" href="Type.html#3137" class="InductiveConstructor Operator">[</a> <a id="4141" href="Type.html#473" class="Datatype">𝔹</a> <a id="4143" href="Type.html#3137" class="InductiveConstructor Operator">∋</a> <a id="4145" class="Symbol">(λ{</a><a id="4148" href="Type.html#488" class="InductiveConstructor">𝕗</a> <a id="4150" class="Symbol">→</a> <a id="4152" href="Type.html#4020" class="Function">⟨∅⟩</a><a id="4155" class="Symbol">;</a> <a id="4157" href="Type.html#495" class="InductiveConstructor">𝕥</a> <a id="4159" class="Symbol">→</a> <a id="4161" href="Type.html#4018" class="Function">∅</a><a id="4162" class="Symbol">})</a> <a id="4165" href="Type.html#3137" class="InductiveConstructor Operator">]</a> <a id="4167" class="Comment">-- 2</a>
</pre>
The trouble comes when we try to examine the elements of a comprehension:

<pre class="Agda">  <a id="russel._∈_"></a><a id="4262" href="Type.html#4262" class="Function Operator">_∈_</a> <a id="4266" class="Symbol">:</a> <a id="4268" href="Type.html#3113" class="Datatype">TYPE</a> <a id="4273" class="Symbol">→</a> <a id="4275" href="Type.html#3113" class="Datatype">TYPE</a> <a id="4280" class="Symbol">→</a> <a id="4282" href="Type.html#111" class="Primitive">Type</a> <a id="4287" class="Comment">-- This won&#39;t typecheck without --type-in-type</a>
  <a id="4336" href="Type.html#4336" class="Bound">a</a> <a id="4338" href="Type.html#4262" class="Function Operator">∈</a> <a id="4340" href="Type.html#3137" class="InductiveConstructor Operator">[</a> <a id="4342" href="Type.html#4342" class="Bound">X</a> <a id="4344" href="Type.html#3137" class="InductiveConstructor Operator">∋</a> <a id="4346" href="Type.html#4346" class="Bound">f</a> <a id="4348" href="Type.html#3137" class="InductiveConstructor Operator">]</a> <a id="4350" class="Symbol">=</a> <a id="4352" href="Data.Product.html#1369" class="Function">∃</a> <a id="4354" class="Symbol">λ</a> <a id="4356" href="Type.html#4356" class="Bound">x</a> <a id="4358" class="Symbol">→</a> <a id="4360" href="Type.html#4336" class="Bound">a</a> <a id="4362" href="Agda.Builtin.Equality.html#151" class="Datatype Operator">≡</a> <a id="4364" href="Type.html#4346" class="Bound">f</a> <a id="4366" href="Type.html#4356" class="Bound">x</a>

  <a id="russel._∉_"></a><a id="4371" href="Type.html#4371" class="Function Operator">_∉_</a> <a id="4375" class="Symbol">:</a> <a id="4377" href="Type.html#3113" class="Datatype">TYPE</a> <a id="4382" class="Symbol">→</a> <a id="4384" href="Type.html#3113" class="Datatype">TYPE</a> <a id="4389" class="Symbol">→</a> <a id="4391" href="Type.html#111" class="Primitive">Type</a>
  <a id="4398" href="Type.html#4398" class="Bound">a</a> <a id="4400" href="Type.html#4371" class="Function Operator">∉</a> <a id="4402" href="Type.html#4402" class="Bound">b</a> <a id="4404" class="Symbol">=</a> <a id="4406" class="Symbol">(</a><a id="4407" href="Type.html#4398" class="Bound">a</a> <a id="4409" href="Type.html#4262" class="Function Operator">∈</a> <a id="4411" href="Type.html#4402" class="Bound">b</a><a id="4412" class="Symbol">)</a> <a id="4414" class="Symbol">→</a> <a id="4416" href="Type.html#415" class="Datatype">⊥</a>
</pre>
We can now encode Russell's paradoxical class directly as the `TYPE` of all `TYPE` that don't contain themselves:

<pre class="Agda">  <a id="russel.Δ"></a><a id="4549" href="Type.html#4549" class="Function">Δ</a> <a id="4551" class="Symbol">:</a> <a id="4553" href="Type.html#3113" class="Datatype">TYPE</a>
  <a id="4560" href="Type.html#4549" class="Function">Δ</a> <a id="4562" class="Symbol">=</a> <a id="4564" href="Type.html#3137" class="InductiveConstructor Operator">[</a> <a id="4566" class="Symbol">(</a><a id="4567" href="Data.Product.html#1369" class="Function">∃</a> <a id="4569" class="Symbol">λ</a> <a id="4571" href="Type.html#4571" class="Bound">t</a> <a id="4573" class="Symbol">→</a> <a id="4575" href="Type.html#4571" class="Bound">t</a> <a id="4577" href="Type.html#4371" class="Function Operator">∉</a> <a id="4579" href="Type.html#4571" class="Bound">t</a><a id="4580" class="Symbol">)</a> <a id="4582" href="Type.html#3137" class="InductiveConstructor Operator">∋</a> <a id="4584" class="Symbol">(λ{(</a><a id="4588" href="Type.html#4588" class="Bound">t</a> <a id="4590" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4592" href="Type.html#4592" class="Bound">t∉t</a><a id="4595" class="Symbol">)</a> <a id="4597" class="Symbol">→</a> <a id="4599" href="Type.html#4588" class="Bound">t</a><a id="4600" class="Symbol">})</a> <a id="4603" href="Type.html#3137" class="InductiveConstructor Operator">]</a>
</pre>
This does indeed capture the right notion we can prove that a class is in `Δ` if and only iff it doesn't contain itself:

<pre class="Agda">  <a id="russel.x∈Δ→x∉x"></a><a id="4742" href="Type.html#4742" class="Function">x∈Δ→x∉x</a> <a id="4750" class="Symbol">:</a> <a id="4752" class="Symbol">∀</a> <a id="4754" class="Symbol">{</a><a id="4755" href="Type.html#4755" class="Bound">X</a><a id="4756" class="Symbol">}</a> <a id="4758" class="Symbol">→</a> <a id="4760" href="Type.html#4755" class="Bound">X</a> <a id="4762" href="Type.html#4262" class="Function Operator">∈</a> <a id="4764" href="Type.html#4549" class="Function">Δ</a> <a id="4766" class="Symbol">→</a> <a id="4768" href="Type.html#4755" class="Bound">X</a> <a id="4770" href="Type.html#4371" class="Function Operator">∉</a> <a id="4772" href="Type.html#4755" class="Bound">X</a>
  <a id="4776" href="Type.html#4742" class="Function">x∈Δ→x∉x</a> <a id="4784" class="Symbol">((</a><a id="4786" href="Type.html#4786" class="Bound">Y</a> <a id="4788" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4790" href="Type.html#4790" class="Bound">Y∉Y</a><a id="4793" class="Symbol">)</a> <a id="4795" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4797" href="Agda.Builtin.Equality.html#208" class="InductiveConstructor">refl</a><a id="4801" class="Symbol">)</a> <a id="4803" class="Symbol">=</a> <a id="4805" href="Type.html#4790" class="Bound">Y∉Y</a>

  <a id="russel.x∉x→x∈Δ"></a><a id="4812" href="Type.html#4812" class="Function">x∉x→x∈Δ</a> <a id="4820" class="Symbol">:</a> <a id="4822" class="Symbol">∀</a> <a id="4824" class="Symbol">{</a><a id="4825" href="Type.html#4825" class="Bound">X</a><a id="4826" class="Symbol">}</a> <a id="4828" class="Symbol">→</a> <a id="4830" href="Type.html#4825" class="Bound">X</a> <a id="4832" href="Type.html#4371" class="Function Operator">∉</a> <a id="4834" href="Type.html#4825" class="Bound">X</a> <a id="4836" class="Symbol">→</a> <a id="4838" href="Type.html#4825" class="Bound">X</a> <a id="4840" href="Type.html#4262" class="Function Operator">∈</a> <a id="4842" href="Type.html#4549" class="Function">Δ</a>
  <a id="4846" href="Type.html#4812" class="Function">x∉x→x∈Δ</a> <a id="4854" class="Symbol">{</a><a id="4855" href="Type.html#4855" class="Bound">X</a><a id="4856" class="Symbol">}</a> <a id="4858" href="Type.html#4858" class="Bound">X∉X</a> <a id="4862" class="Symbol">=</a> <a id="4864" class="Symbol">(</a><a id="4865" href="Type.html#4855" class="Bound">X</a> <a id="4867" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4869" href="Type.html#4858" class="Bound">X∉X</a><a id="4872" class="Symbol">)</a> <a id="4874" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4876" href="Agda.Builtin.Equality.html#208" class="InductiveConstructor">refl</a>

  <a id="russel.x∈Δ↔x∉x"></a><a id="4884" href="Type.html#4884" class="Function">x∈Δ↔x∉x</a> <a id="4892" class="Symbol">:</a> <a id="4894" class="Symbol">∀</a> <a id="4896" class="Symbol">{</a><a id="4897" href="Type.html#4897" class="Bound">X</a><a id="4898" class="Symbol">}</a> <a id="4900" class="Symbol">→</a> <a id="4902" class="Symbol">(</a><a id="4903" href="Type.html#4897" class="Bound">X</a> <a id="4905" href="Type.html#4262" class="Function Operator">∈</a> <a id="4907" href="Type.html#4549" class="Function">Δ</a><a id="4908" class="Symbol">)</a> <a id="4910" href="Type.html#501" class="Function Operator">iff</a> <a id="4914" class="Symbol">(</a><a id="4915" href="Type.html#4897" class="Bound">X</a> <a id="4917" href="Type.html#4371" class="Function Operator">∉</a> <a id="4919" href="Type.html#4897" class="Bound">X</a><a id="4920" class="Symbol">)</a>
  <a id="4924" href="Type.html#4884" class="Function">x∈Δ↔x∉x</a> <a id="4932" class="Symbol">=</a> <a id="4934" href="Type.html#4742" class="Function">x∈Δ→x∉x</a> <a id="4942" href="Agda.Builtin.Sigma.html#236" class="InductiveConstructor Operator">,</a> <a id="4944" href="Type.html#4812" class="Function">x∉x→x∈Δ</a>
</pre>Now the infamous contradiction is direct: `Δ` both does and does not contain itself!

<pre class="Agda">  <a id="russel.Δ∉Δ"></a><a id="5052" href="Type.html#5052" class="Function">Δ∉Δ</a> <a id="5056" class="Symbol">:</a> <a id="5058" href="Type.html#4549" class="Function">Δ</a> <a id="5060" href="Type.html#4371" class="Function Operator">∉</a> <a id="5062" href="Type.html#4549" class="Function">Δ</a>
  <a id="5066" href="Type.html#5052" class="Function">Δ∉Δ</a> <a id="5070" href="Type.html#5070" class="Bound">Δ∈Δ</a> <a id="5074" class="Symbol">=</a> <a id="5076" class="Symbol">(</a><a id="5077" href="Type.html#278" class="Field">π₁</a> <a id="5080" href="Type.html#4884" class="Function">x∈Δ↔x∉x</a><a id="5087" class="Symbol">)</a> <a id="5089" href="Type.html#5070" class="Bound">Δ∈Δ</a> <a id="5093" href="Type.html#5070" class="Bound">Δ∈Δ</a>

  <a id="russel.Δ∈Δ"></a><a id="5100" href="Type.html#5100" class="Function">Δ∈Δ</a> <a id="5104" class="Symbol">:</a> <a id="5106" href="Type.html#4549" class="Function">Δ</a> <a id="5108" href="Type.html#4262" class="Function Operator">∈</a> <a id="5110" href="Type.html#4549" class="Function">Δ</a>
  <a id="5114" href="Type.html#5100" class="Function">Δ∈Δ</a> <a id="5118" class="Symbol">=</a> <a id="5120" class="Symbol">(</a><a id="5121" href="Type.html#291" class="Field">π₂</a> <a id="5124" href="Type.html#4884" class="Function">x∈Δ↔x∉x</a><a id="5131" class="Symbol">)</a> <a id="5133" href="Type.html#5052" class="Function">Δ∉Δ</a>

  <a id="russel.paradox"></a><a id="5140" href="Type.html#5140" class="Function">paradox</a> <a id="5148" class="Symbol">:</a> <a id="5150" href="Type.html#415" class="Datatype">⊥</a>
  <a id="5154" href="Type.html#5140" class="Function">paradox</a> <a id="5162" class="Symbol">=</a> <a id="5164" href="Type.html#5052" class="Function">Δ∉Δ</a> <a id="5168" href="Type.html#5100" class="Function">Δ∈Δ</a>
</pre>
So how bad is this? What's actually going on?

If we're using Agda as a proof assistant, it's pretty terrible: we can now prove anything we like!
This is why Agda uses such onerous level checking by default.

But Russel's paradox is quite weird, and one might wonder how easy it is to accidentally violate well-foundedness.

we can unroll `paradox` to see what's happening computationally:

<pre class="Agda"><a id="5576" class="Comment">{-
  _ : paradox ≡ paradox
  _      = paradox
       ≡⟨⟩ Δ∉Δ                          Δ∈Δ
       ≡⟨⟩ (x∈Δ→x∉x Δ∈Δ)                Δ∈Δ
       ≡⟨⟩ (x∈Δ→x∉x (x∉x→x∈Δ Δ∉Δ))      Δ∈Δ
       ≡⟨⟩ (x∈Δ→x∉x ((Δ , Δ∉Δ) , refl)) Δ∈Δ
       ≡⟨⟩ Δ∉Δ                          Δ∈Δ ∎
-}</a>
</pre>
If you try to compile the above commented code the typechecker will hang, but we can see why: `Δ∉Δ Δ∈Δ` reduces to itself!

It turns out that _all_ unsound uses of `--type-in-type` [result in typechecking non-termination](http://www.cs.nott.ac.uk/~psztxa/publ/msfp08.pdf), so we'll never construct an ill-typed value at runtime.

For this reason we follow haskell's example and include `--type-in-type` by default, to maintain clarity by reducing noise.

When checking a serious proof it's worth reintroducing `Level`s for consistency,
but for interactive exploratory work or didactic communication it's nearly always a hinderance.
