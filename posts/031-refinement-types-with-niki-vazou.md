---
title: "Refinement Types with Niki Vazou"
date: "2019-05-15"
---

Formal verification and type systems - how do they relate? Niki Vazou is on a mission to bring better formal verification to the masses.

I have done a couple of episodes about dependent types and my feeling is that dependent types are super powerful and have some conceptual simplicity ( Types are a first class concept ) but are somewhat tricky to wield in practice.

Refinement types are something simpler. A refinement is a predicate that narrows the meaning of a type. What if instead of divide taking two ints, one was Int i where i != 0. This is a refinement type, a type that has been refined, the set of possible values narrowed, using simple predicates.

Niki is the creator of Liquid Haskell, a system that extends Haskell to support refinements. It actually goes farther than that. She has also worked on refinement types in Ruby and explained refinement types to scala community at various conferences, but her heart lies with the Haskell community. We talk about refinement types, theorem proving, formal verification, SMT solvers, and working with GHC.

This interview is also a great place to hear me asking stupid questions of a very smart person. Niki and her work are way outside my comfort bounds but hopefully my struggles to understand the topic will help make the power of refinement types approachable to a wider audience. Ruby developers, js developers, and everyone, refinement types are for you as well.

**Links:**

- [Liquid Haskell Talk](https://www.youtube.com/watch?v=SmRo7q_6oG8&t=285s)
- [Programming with Refinement Types](http://ucsd-progsys.github.io/lh-workshop/)
- [Liquid Haskell Tutorial](http://ucsd-progsys.github.io/liquidhaskell-tutorial/)
    
- [Niki's Ph.D. Thesis](http://goto.ucsd.edu/~nvazou/thesis/main.pdf)
- [Real World Liquid Types](http://goto.ucsd.edu/~nvazou/real_world_liquid.pdf)
- [Refinement Types for Ruby](https://nikivazou.github.io/static/VMCAI18/paper.pdf)
- [Liquid Haskell Proofs](https://www.youtube.com/watch?v=fRBIR2RJIIo)
- [Refinement Types for Scala](https://github.com/fthomas/refined)
