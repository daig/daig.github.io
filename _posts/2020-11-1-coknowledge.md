### Coherentism

I've been thinking a lot about primitives for [epistemic justification](https://iep.utm.edu/epi-just/). In particular Foundationalism vs Coherentism, their relationship to induction vs coinduction, with [Productivity](https://bentnib.org/productive.pdf) as the Coherentist analog to grounded arguments, ensuring that each step (of a potentially cyclic proof) does some useful and necessary work.
Foundationalism is the standard for formal logic, and has gotten us quite far.

> ["According to the __foundationalist__ option, the series of beliefs
> terminates with special justified beliefs called “basic beliefs”:
> these beliefs do not owe their justification to any other beliefs from
> which they are inferred."](https://iep.utm.edu/coherent/#:~:text=According%20to%20the%20foundationalist%20option,from%20which%20they%20are%20inferred.)

It accounts for how truth is preserved in composition, flowing from true assumptions and avoiding circular reasoning. It has deep connections with computation via [curry-howard](https://en.wikipedia.org/wiki/Curry%E2%80%93Howard_correspondence) where well-founded [constructive proofs](http://adam.chlipala.net/cpdt/html/InductiveTypes.html) correspond to terminating computable functions.

On the other hand, it appears to have limits - raising an obvious question of how to prefer some axioms over others. In practice too there seem to be a vast class of knowledge unaccounted for - mostly in the domain of psychology and medicine, but also behind the scenes of every successful visionary, institutional knowledge, artistic muse, and pre-paradigmatic field

 Mathematicians for example spend years carrying strong intuitions, letting them solve a host of concrete problems, before being able to write down a general grounded theory of those problems.
The foundationalist view is that such intuitions are clever heuristics which must still be grounded to be justified - but why should this be the case when intuition is in some sense prior to propositional knowledge.
At its worst, foundationalistm leads to Goodharting on legible arguments to the exclusion of obvious intuitive objections.

> ["Coherentism, however, proposes a 'holistic' view of justification. On
> this kind of view, the primary bearer of epistemic justification is a
> system of beliefs."](https://iep.utm.edu/coherent/#SH2b)

This is a compelling stance for natural reasoning via self-trust, where our only foundation is embedded coherence by birthright. Care must be taken however to avoid __circular__ reasoning, and the difficulty of doing so is part of why coherentism has fallen out of favor.

Just as every foundationalist justification must terminate on basic beliefs, coherentist justifications have an analogous soundness criteria:

- A mesh of interlocking beliefs, each part of which is both __necessary__ (produces a part of the meaning), and coherent (connects with all other parts without contradicting any other part).

This may seem like an arbitrary criteria, but it follows directly as a complement to foundationalist justification by analogy to mathematical logic, and turns out to be exactly what you need to avoid circular reasoning in a very precise sense.

---

### Coinduction

Foundationalist justifications map via [curry-howard](https://www.youtube.com/watch?v=IOiZatlZtGU&t=1s) to inductive proofs, and well-foundedness translates to __termination__ of such proofs.
Correspondingly, Coherentist justifications map to __coinductive__ proofs, and well-foundedness [translates](https://arxiv.org/abs/1707.01541) to __productivity__ of such proofs.
Whether a statement is inductive or coinductive is [__determined by the structure of the statement itself__](http://blog.sigfpe.com/2007/07/data-and-codata.html), and so inherits a natural justification.


#### A Toy Example:

Consider the inductive type of ([Peano](https://en.wikipedia.org/wiki/Peano_axioms)) natural numbers
`data Nat = Z | S Nat` (A natural number is either zero or the successor of some natural number)
It inherits a natural inductive operation which uniquely characterizes __all__ functions out of it.

 ```haskell
 induct :: forall r. (r , r -> r) -> (Nat -> r)
 induct (init, step) = recurse where
   recurse Z = init
   recurse (S n) = step (recurse n)
 ```

 where we can prove that every function of type `Nat -> r` can be written as an application of `induct` to some inductive step function `step :: r -> r` and initial return value `init :: r`

notice that we must compute the recursive call `recurse n` __before__ making the inductive `step`, relying on the fact that we'll eventually reach the base case `Zero` to ground out in our basic belief `init`.

On the other hand consider infinite [streams](https://agda.readthedocs.io/en/v2.5.2/language/coinduction.html) of data:
`data [a] = a : [a]` with no base case at all! (A stream of type `a` is a head element and a tail stream)
Nevertheless we can have well-formed data of this form - rather than giving it by cases, we must describe a process to generate the entire stream:

```haskell
unfold :: (a -> a, a) -> [a]
unfold (step, init) = init : unfold (step, step init)
```

which uniquely describes all ways of constructing streams similarly to how `induct` characterizes all ways of destructing naturals.
For example:
`numbers :: [Nat]
numbers = unfold (S , Z)`
creates the infinite stream `0 : 1 : 2 : 3 : 4 : ....`

notice that, in contrast to `induct`, `unfold` produces a part of the output (`init :`) __before__ the recursive call, so even if the `unfold` process never terminates (it doesn't), we produce some finite amount of output for every finite `step`.
This property is called __productivity__, dual to the notion of termination for inductive structures. It is exactly what is needed to rule out circular reasoning (where we spin forever without producing any intermediate results), just as termination is exactly what we need to rule out groundless inductive foundations.

#### On Circular Reasoning

Note that "avoiding circular reasoning" doesn't mean "avoiding loopy proofs" - indeed every coherentist proof necessarily loops back on itself, relying on its internal consistency for foundation. Sometimes looping back yields a contradiction, and the proof fails. The structural form of a coinductive proposition P guarantees that every implication (branch of the data) gets considered (in the Stream case, just the head and the tail), so that any difficulty that would arise causing P not to hold would manifest itself in the attempt to prove the coinductive step.

For example, we might like to prove that every element of the stream
`0 : 1 : 0 : 1 : ...`
is less than 2.
To do so, we need only prove that 0 and 1 are less than 2 (trivial), and coinductively rely on the fact that the stream loops back on itself to prove the remainder.

This form of reasoning looks a lot like transfinite induction, but I argue it's naturally more coherentist - and transfinite induction is a foundationalist attempt to squeeze it into that setting - complicating it in the process.
Despite its intuitive naturality, formal coinduction is seen as more complex than induction, in part because of a forward bias asymmetrically taking proofs as more fundamental than refutations.


### "CoKnowledge "

Consider the slogans for induction and coinduction:
["A property holds by induction if there is good reason for it to hold"
"A property holds by coinduction if there is no good reason for it not to hold"](https://www.cs.cornell.edu/~kozen/Papers/Structural.pdf)

seen this way, coinduction is most naturally about the __absence of refutation__.
In [polarized](https://pdfs.semanticscholar.org/b9dd/97a9ed29263923a2d7da195f1f7e790242d1.pdf) [inear logic](https://arxiv.org/pdf/1805.07518.pdf), for an __epistemic position__ `P := (P⁺,P⁻)` (interpreted as "what you'd accept as evidence", and "what you'd accept as counter-evidence") there is a [distinction](http://noamz.org/papers/unity-duality.pdf) between

```
immediate (linear) proofs      ---- P triv   := proof of P⁺
immidiate (linear) refutations ---- P absurd := proof of P⁻
justified refutations          ---- P false  := ¬ P triv
justified proofs               ---- P true   := ¬ P absurd
```

where in addition to the usual intuitionistic derived negation ¬ P := P → ⊥
there's a primitive dualization P† := (P⁻,P⁺) swapping the position.

So induction (and foundationalism) is about judgements "P triv" while coinduction (and coherentism) is about judgements "P true", which include many more dynamic inhabitants.

Standard (intuitionistic) Logic has gotten by so far by restricting itself to [static structure](https://www.microsoft.com/en-us/research/wp-content/uploads/2006/01/not-not-ml.pdf) (triv), banishing refutation to second-class (false). Linear logic by contrast is fundamentally about concurrent interacting [resources](https://plato.stanford.edu/entries/logic-linear/) moreso than platonic absolutes, and so more natural for a theory of [__embedded__](https://www.lesswrong.com/posts/i3BTagvt3HbPMx6PN/embedded-agency-full-text-version) reasoning which is necessarily dynamic in the world. Similarly, in practice coinduction is most often used to prove properties of [automata](https://agda.readthedocs.io/en/v2.6.1.1/language/sized-types.html) such as state machines, distributed protocols, and formal languages.

[Refutation-based reasoning](http://noamz.org/papers/polpol.pdf) is still poorly understood, but corresponds to __metasystematic proof search__, where primitive refutations are computationally interpreted as __continuations__, describing how to "backtrack" your process in case of contradiction, to root out incoherent assumptions.

---

### Synthesis

Neither story is complete on its own - and my aim is [towards](https://arxiv.org/abs/2001.05132) a synthesis which can describe the full epistemic capacity of intellect. including [symbol grounding](http://noamz.org/papers/lzh08focbind-tr.pdf) and [reflection](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.43.8213&rep=rep1&type=pdf)

Consider the complementary progress of knowledge:

- In math, we ride coherent intuition until we can distill a foundational theory.
- In science, we test hypothetical models until we can falsify them with empirical data (or fail to, so strengthening our beliefs).
- This empirical data is then used as intuition fuel to distill the next theory, and so on.