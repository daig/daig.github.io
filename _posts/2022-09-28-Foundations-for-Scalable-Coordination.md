"Collective Epistemics" deals with how individual sense-making can be combined into _even better_ sense-making between multiple individuals. CE isn't a given - sometimes people consistently make bad-for-everyone decisions as a group, for any number of reasons, where they wouldn't as individuals. CE asks which questions can be reliably answered, with which arrangements of individuals, with which beliefs/goals, and how to arrange all this to answer the reliably questions we care about.

CE deals with coordination of collective action as much as it does collective belief. "Scalability" means the entire system doesn't implode on itself, through strife or collective delusion, as we continue adding more participants. A generalization on the one hand of mechanism design striving to align collective action, and rational inquiry on the other striving to maintain true beliefs.

(I claim) It is the greatest common denominator between all the major existential risks from AI alignment to Biosecurity, as well as the bottleneck in _asymmetrically positive_ scientific progress.

I have a unique perspective on SCE, amounting to a technical research agenda, from my uniquely cross-discipline career trajectory.
This agenda has been brewing for many years, built on my work in computational biology, information security, formal logic, and research strategy.

My deepest lesson from New Science is the affirmation that (asymmetrically positive) progress is not (currently) bottlenecked by expertise, but by ontology bandwidth - the rate that experts are willing and able to communicate their low-level "pre-paradigmatic" models. Part of this is an incentive problem: low-level models are necessary for mastery but furthest from shiny new results. Part of it is a technical problem: as of yet, ontology transfer happens merely by accident - we have no reliable way to hasten or deepen it. We have some handles: aristocratic tutoring / mentorship, rivalry, and intrinsic (vs instrumental) intellectual motivation seem correlated. We have historic examples of small, deeply aligned yet diverse groups performing orders of magnitude better: Xerox PARC, Bell Labs, Cold Spring Harbor, The Manhattan Project, etc. but we really have no idea why, none of the common accounts hold water, they aren't reproducible.

My current approach takes this low-level "_context sensitive_" exchange bandwidth as primary while analyzing stability. It has the benefit of being asymmetrically-positive, AFAICT avoiding the capabilities slant inherent in traditional game theoretic and machine learning approaches to coordination. It merely discovers and glues existing sense-making in a shear-minimizing way. "Perfect Coordination" is _local_ and _unique in context_. In particular, "Perfect Coordination" with "enemies" is possible - it's only a sign flip.
It is _NOT_ a recipe for a perfect utopia conditional on "the good guys win".
Utopia is extremely sus; I hope you will see why.

As pre-paradigmatic content, there is no one-size-fits-all entry-point.

In the absence of a digestible narrative for "SCE done right", below is an annotated reading list with the necessary foundations, which is itself sufficient to "get" the agenda.
The following constitutes a major conceptual leap, should any one individual master all pieces simultaneously. Perhaps it is too big to master. Perhaps solving collective epistemics is itself necessarily an exercise in collective epistemics. 

Each topic weaves back into the others as part of the broader agenda so the sections are unordered, while the linear ordering within sections is approximate and meant to be interleaved asynchronously. These references are meant to cover core ideas but are neither fully essential nor complete, depending on the background of readers. Many texts are applicable to multiple sections. Start wherever seems independently most compelling - the broader motivation will become more apparent with each piece.

## Top-down Modeling

### [Introduction to the Theory of Mechanism Design](https://academic.oup.com/book/2244)
Mainly useful as a familiar introduction to top-down reasoning, bridging the more exotic approaches below, and exhaustive no-go results for perfect mechanisms.

### [Foundations of Neuroeconomic Analysis](https://academic.oup.com/book/5514)

A bridge between the top-down modeling typical of economics/mechanism design, and bottom-up modeling typical of neuroscience. A generally useful philosophical framework for bridging top-down with bottom-up systems that does not rely on statistical physics.

### [Lectures on Statistical Field Theory](https://www.damtp.cam.ac.uk/user/tong/sft.html)
Rigorous top-down approaches are common and most advanced in statistical field theory - it is useful to see this perspective aspirationally as a completion to the above two "soft-science" approaches, though the specific technical results will not be used directly.

### [Behavioral Mereology: A Modal Logic for Passing Constraints](https://arxiv.org/abs/2101.10490)

A top-down framework for modeling that works better than bottom-up ("reductive") modeling for certain long-term behaviors and integrity of open systems.

### [When the map is better than the territory](https://arxiv.org/abs/1612.09592)

A concrete account for the emergence of top-down behavior as a way to maximize causal channel capacity over a system.

## Optics

### [Categories of Optics](https://arxiv.org/abs/1809.00738) 

Comprehensive foundation for mathematical lenses

### [Generalized Lens Categories via Functors C^op -> Cat](https://arxiv.org/abs/1908.02202) 

Exposes lenses as morphisms of tangent bundles, which connects them with [categories of containers](https://www.cs.nott.ac.uk/~psztxa/publ/fossacs03.pdf)/[algebraic ornaments](http://plv.mpi-sws.org/plerg/papers/mcbride-ornaments-2up.pdf) and [categorical logic](https://ncatlab.org/nlab/show/logic)

### [Dioptics: a Common Generalization of](http://events.cs.bham.ac.uk/syco/strings3-syco5/papers/dalrymple.pdf)

[Open Games and Gradient-Based Learners](http://events.cs.bham.ac.uk/syco/strings3-syco5/papers/dalrymple.pdf) 

Connects ‘compositional game theory’ with ‘backprop as a functor’ through a highly general construction

### [The Safari of Update Structures: Visiting the Lens and Quantum Enclosures](https://arxiv.org/abs/2005.05293)

Early work connecting optics with the quantum-classical construction

### [Bayesian Updates Compose Optically](https://arxiv.org/abs/2006.01631)

Grounding Bayesian reasoning in optics foundations. Related to but distinct from the Backprop connection.

### [Polynomial Functors: A general theory of interaction](https://topos.site/poly-book.pdf)

The canonical deep dive into polynomial functors. Lenses (optics) are the morphisms between polynomial functors. Polynomial functors themselves represent dynamical systems. This gives something like a "representation theory" for how optics act on dynamical systems, which are independently well understood.

## (Open) Game Theory

### [Embedded Agency](https://arxiv.org/abs/1902.09469)
The fundamental problem for reasoning about agency "from the inside", either as an individual extrapolating goals, a participant of collective action, or a bootstrapping AI attempting to safely select a successor.  

This agenda proposes embedded agency can be accommodated by modeling actors as particular dynamical systems (rather than e.g. discrete ensembles of game-theoretic agents or Bayesian networks), which behave like belief networks under ideal circumstances, but remain well-defined even in the absence of "digital" logic-like attractors at the phase transition between valid belief states (ie during the physical process of updating, which might be "circular" in an embedded setting).

Another way to put this is that dynamical systems give operational semantics to the (traditionally) atomic, ill-founded, lobian update.

### [Fixing Incremental Computation](https://arxiv.org/abs/1811.06069)
A discrete technique for computing derivatives of fixed-points (eg self-consistent belief networks, game theoretic equilibrium, etc.) which might be unified with the continuous dynamical systems approach. 

Optics were originally developed to model database updates, and polynomial functors originally to model database queries, so there is much prior overlap but the logic programming and dynamical systems community rarely communicate.

### [compositional game theory](https://arxiv.org/abs/1603.04641)

seminal paper for open games, a technique for modeling composable systems of agents

### [The game semantics of game theory](https://arxiv.org/abs/1904.11287)

more recent reformulation of open games to expose them as a game semantics using dialectica interpretation between (jointly controlled) "System"/"Prover" and "Environment"/"Refuter". Related to Chu Construction

### [Pipes](https://hackage.haskell.org/package/pipes-4.3.16/docs/Pipes-Tutorial.html)
A computational approach to bidirectional proxies, reminiscent of Dioptics and a practical playground for open-game semantics

## Dynamical Systems

### [Introduction to the theory of complex systems](https://academic.oup.com/book/25504)

Synthesis text for techniques in complex systems analysis, which is useful mainly for inspiration towards top-down modeling and some specific no-go theorems.

### [Control Theory from the Geometric Viewpoint](https://link.springer.com/book/10.1007/978-3-662-06404-7)

Control Theory from the perspective of Differential Geometry, forming a bridge with the poly approach and differential privacy

In particular, this book covers the Chronological Calculus essential for Vibrational Control.


### [Vibrational control: A hidden stabilization mechanism in insect flight](https://www.science.org/doi/10.1126/scirobotics.abb1502)

A technique for adaptive _sensor-free_ Extremum-Seeking Control for finding unstable equilibria _without_ depending on faster/finer sensing than the source of instability.

This is can be eg useful for stabilizing mesa-optimizers that are hard to inspect directly and react to.

Further, it works by _adding_ local degrees of freedom (for oscillation), maintaining low-level information flow rather than clamping down the entire system, while nevertheless stabilizing the join system at larger scales.

## (Resource) Logic

### [Logical Induction](https://arxiv.org/abs/1609.03543)
A computable bootstrapping algorithm for generating uninformative priors. The the technique exhibits polarization behavior between individual generative "traders" and global reactive "market makers", reminiscent of the optical techniques throughout the bibliography.
Logical induction has not  been revisited in a long time due to lacking foundational machinery, but unifying it with open-game theoretic approaches now seems tractable.

### [Affine Logic for Constructive mathematics](https://arxiv.org/abs/1805.07518)

A practical and in-depth intro to generalized affine logic. 

### [The 2-Chu-Dialectica construction and the polycategory of multivariable adjunctions](https://arxiv.org/abs/1806.06082)
 
Following from the previous paper, generalizing the construction of linear logic from classical logic to vastly more spaces

### [On the Unity of Duality](http://noamz.org/papers/unity-duality.pdf)

A type theory for polarized linear logic. Introduces operational distinctions between constructive and non-constructive proof ("data"/"beliefs")/refutation ("continuations"/"actions"). Constructive Refutations can be a simpler foundation for coinduction.

### Blog series: [Embracing and extending the Levy language](http://requestforlogic.blogspot.com/2011/08/embracing-and-extending-levy-language.html) through [Clowns to the left of me, jokers to the right](http://requestforlogic.blogspot.com/2011/09/clowns-to-left-of-me-jokers-to-right.html)

Concrete examples for type system based on linear logic deeply linked with data-type derivatives. Useful for gaining hands-on intuition.

### [Practical Coinduction](https://www.cs.cornell.edu/~kozen/Papers/Structural.pdf)

Coinduction works more naturally than Induction with open systems and can generalize to work with dynamical systems based logic. It unifies with classical induction under the polarization duality between data and continuations.

## Complementarity

###  [Integral Transforms and the Pull-Push Perspective](https://golem.ph.utexas.edu/category/2010/11/integral_transforms_and_pullpu.html)

Huge generalization of Fourier transform / Pontryagin duality into all sorts of spaces via spans and pullbacks/pushworwards. Useful for understanding CNN in a semantic-preserving way (a form of interpretability), and bridging Signal Processing techniques with formal logic

### [Cartesian Frames](https://arxiv.org/abs/2109.10996) / [Finite Factored Sets](https://arxiv.org/abs/2109.11513)

Cartesian frames and its more combinatorially flavored sister finite factored sets are approaches to generalize the notion of causal agent by characterizing all the ways to cleave the system into an "agent" and "environment", exposing different _complementary_ causal structures depending on which "coalitions" are viewed as the causal agents.

Cartesian frames are based on Chu Space, directly relating it with open game theory and lens constructions, while set factorizations are deeply related to the Dirichlet Product (a way of representing concurrency) of Combinatorial Species (a sister concept to polynomial functors)

### [Picturing Quantum Processes](https://www.amazon.com/Picturing-Quantum-Processes-Diagrammatic-Reasoning/dp/110710422X)

- Great introduction to string diagrammatic reasoning

- Describes the doubling construction to build a quantum dynamics out of classical stochastic dynamics, related to the Chu Construction and Dioptic construction

- Intuition for complementary bases which seem important for phenomenology

Essential points are broken down in individual freely-accessible papers:  

 - [Categorical Quantum Mechanics I: Causal Quantum Processes](https://arxiv.org/abs/1510.05468)
 - [Categorical Quantum Mechanics II: Classical-Quantum Interaction](https://arxiv.org/abs/1605.08617)

although the book is much better presentation.

- [Dagger Compact Closed Categories and Completely Positive Maps](https://www.sciencedirect.com/science/article/pii/S1571066107000606) 

A seminal paper with an older but more categorical doubling construction as above.

### [Active Inference](https://mitpress.mit.edu/9780262045353/active-inference/)

active inference is a specific example of complementarity between action and belief - putting fundamental limits on the rate of informed causal impact an agent can have over a system. Acts as a bridge between more rigorous approaches and practical applications.

## Machine Learning / Statistics

### [Generalization in Adaptive Data Analysis and Holdout Reuse](https://arxiv.org/pdf/1506.02629.pdf)
A regularization framework for preventing over-fitting while adaptively (i.e. the next analysis chosen depends on the result of the first) composing ML algorithms - based on differential privacy with a rich background in information geometry

### [The simple essence of automatic differentiation](https://arxiv.org/abs/1804.00746)

Vast generalization of automatic differentiation, unifying forwards and backwards modes, and exposing backpropagation as a special case

### [Backprop as a functor](https://arxiv.org/abs/1711.10455)

Founding paper on compositional learning algorithms

### [Lenses and Learners](https://arxiv.org/abs/1903.03671) 

Exposes backprop-as-a-functor approach as a particular lens construction unifying with the optics agenda

### [Hands-on reservoir computing: a tutorial for practical implementation](https://iopscience.iop.org/article/10.1088/2634-4386/ac7db7)

Reservoir Computing is a sister technique to Recurrent Neural Networks, taking a more Dynamical System flavor. It illuminates some questions of Interpretability for RNN, has desirable stability properties in the absence of perfect control over your network weights, and is more amenable to top-down modeling.
