---
title: "Algebraic Domain Modeling using Functions With Debasish Ghosh"
date: "2020-07-19"
---

### Abstract Algebra Provides Tools for Building Better Software

Domain-driven design pushes software architects to model a solution architecture. An algebraic approach to domain modeling using functions may prove to be the best approach.

In today’s episode, Debasish Ghosh explains how to model a complex problem domain in a functional paradigm. His solution focuses on modeling the behavior of the software system rather than nouns it will contain.

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/6147984/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

“I first come up with what I call the algebra of the behaviors. The algebra of the behaviors refers to the basic contract, which the behavior is supposed to support, which the behavior is supposed to honor. So that's the algebra.” -Debasish Ghosh

“You can use an applicative in order to execute things in parallel.” -Debasish Ghosh

“The advantage is an abstraction. You need to develop at the proper level of abstraction. Because if you pollute your algebra with implementation constraints, then later it becomes difficult to generalize.” -Debasish Ghosh

### **Transcript**

_This is a machine-translated transcript. Podcast page for [this episode is here](https://corecursive.com/005-algebraic-domain-modelling-using-functions-with-debashish-ghosh/)_

### **Introduction**

**Adam:** Welcome to CoRecursive where we bring you discussions with thought leaders in the world of software development. I am Adam, your host. In object-oriented languages, modeling a complex problem domain is a well-understood process. Books like Domain Driven Design contain techniques for breaking down a problem domain and earlier books like Gang of Four catalog design patterns for modeling these domains in an object-oriented way. 

In today's interview, Debasish Ghosh explains how to model a complex problem domain in a functional paradigm. His solution focuses on modeling the behavior of the software system rather than the nouns it will contain. He also focuses on an algebraic approach to API design and discusses how abstract algebra provides tools for building better software. 

Debasish is the author of [Functional and Reactive Domain Modeling book by Manning,](https://www.manning.com/books/functional-and-reactive-domain-modeling) and also works for Lightbend. Welcome to CoRecursive! Thank you. 

**Debasish:** Thanks a lot. 

**Adam:** I have your book in front of me really enjoying it.  it has a lot of terminologies, even just in the title. SI thought maybe we'd start with some definitions. What is domain modeling? 

## **What is domain modeling?**

**Debasish:** Yeah, that's one of the very common questions which I hear, because domain modeling is not what most people think it is. I would like to emphasize that when we are talking about domain modeling, it's really about the problem domain. All the logic, all the interactions, all the behaviors, all the objects that you find in the problem domain consists of the domain model. It has nothing to do with the solution domain.

So as a software architect it's our job to model the problem domain into a solution architecture. So also, if you look at the definition that Wikipedia has on domain modeling, it refers to the problem domain. It focuses on the problem domain. So that's the moot point of domain modeling.

You need to interact, you need to understand the problem domain and model the behaviors of those domains and how the various actors or various objects, and various entities interact amongst themselves. In order to achieve a specific use case. 

**Adam:** A lot of this terminology I think comes out of domain-driven design. Could you give a summary of the domain-driven design before we dig into functional aspects of it? 

**Debasish:** Yeah. Actually a domain-driven design also focuses mostly on the domain model. It relies on the idea that the domain model is the core thing that you need to abstract well, in order to have your system up and running and ensure that your system is reliable, your system is maintainable, your system is modularized. So what area it focuses on in this entire book on domain-driven design is how to come up with solution architecture for a problem domain that is modularized, that is robust and that's reliable to all the exceptions. 

So the core concept is how to abstract the various aspects of the domain model in order to make it more reliable and modularized. 

**Adam:** So your book I think is taking where he left off and taking his ideas and applying it to maybe a functional programming paradigm. What made you want to explore that kind of intersection of these concepts?

**Debasish:** Yeah, actually, it was sort of an experiment for me because at one point in time I was working extensively with Java and I was working on a domain model, which was a very complicated domain model for the financial security system. In fact, if you look at my book most of the examples are from that domain only. And when I was really architecting that system as one of the team members, I was trying to modularize the system. I was trying to find out how to come up with the best abstraction for the system. Incidentally, at that point in time, I was using Java and I was not very familiar with the concepts of functional programming.

But ultimately the system got implemented, the system got deployed, and in fact, for the last 10 years or so, it's still running. So from that point of view, you would say that it was a successful deployment, successful endeavor. Later in my life, I found Scala, and I got to know more about the aspects of functional programming. I thought that any domain model, any non-trivial domain model can be modeled in a better way if we applied the principles of functional programming.

This was a passing thought at that point in time. And the more I learned about functional programming, the more I delved into the details of libraries like ScalaZ, Catz, and things like that. I was almost confident that functional programming has some features. It has some of the addresses, some of the core issues of modularity which will ultimately lead to better reliability and better modularization of a nontrivial domain model. So that was really the start.

So after that, I went back to some of the basic papers of functional programming, especially Why Functional Programming Matter by John Hughes and ultimately I thought that I should give it a shot. And then in my next project, I was incidentally working on a similar kind of domain and I tried my experiment, I tried to apply the principles of functional programming and the result was great.

So one thing led to another so here we are, I'm now a most confident guy with functional programming, we'll work on domain models, which are fairly complicated and which are fairly detailed. 

**Adam:** You mentioned the I, this is just on the aside, Why Functional Programming Matters -- that's the paper that kind of goes through a fold, right, where it does recursion and then it abstracts out the higher-order functions until it has a fold?

**Debasish:** Yeah, actually that’s one of the basic papers and functional programming that John Hughes wrote, I think around 1990 and it focuses on the modularity aspect. It focuses on the laziness part of it and how you can compose programs, compose larger programs out of smaller ones. Fold is one of the examples, besides that, what he focuses on is that functional programming is basically programming with pure values and when you have pure values, you don't have assignments and those values really turn into expressions. So functional programming is also known as expression-oriented programming. When you compose smaller expressions, smaller abstractions to build larger ones. And that's one of the foundational principles, which I also followed when I tried to apply the principles of functional programming to domain modeling.

**Adam:** And so, an expression as compared to a statement, I'm assuming, right. Where an expression is like two plus two equals four and a statement is like a print line?

**Debasish:** Exactly and an expression is something that is pure values. It doesn't have any side effects. Whereas a statement or an assignment is one, which has a side effect.

**Adam:** Okay. So, if you're doing classic domain driven design in Java or some object-oriented language, right? I'm going to kind of come up with a list of like nouns and I'm going to make those classes. So, how does that differ if I'm taking this, you know, functional expression oriented path?

## **Taking the Functional Expression Oriented Path**

**Debasish:** Yeah. I actually follow our practice where I start from the start from a specific use case. So you have a specific use case if we were using Java or if you are using object-oriented principles, in that case, you would start with the nouns, right? What I usually do when I,  start with the use cases, I usually start with the domain behaviors.

I first come up with what I call the algebra of the behaviors. The algebra of the behaviors refers to the basic contract, which the behavior is supposed to support, which the behavior is supposed to honor. So that's the algebra. It has nothing to do with the implementation of it.  Once you have the behaviors, the algebra of the behaviors of a specific use case, you can now think of modularizing them.

The related behaviors go into one module and usually every functional programming language has support for modules. For example, in Scala, we have traits, so you can use the traits in order to modularize your behaviors. So the first step is to come up with the algebra of the behaviors. The next step is to refine the algebra if required, and the third step is modularized into modules. And the next step is to think of the compositionality aspects because those behaviors are not standalone ones, right? Those behaviors need to be composed semantically in order to come up with larger behaviors. 

And how do you do this composition? There are multiple semantics of compositionality. For example, if you have, if one use case has four steps, you may be able to do all those four steps in parallel, or you may have to do them sequentially. So all of these lead you to different algebras of compositionality in the first case when you can do everything in parallel, you can go for the applicative model of compositionality.

You can use applicatives in order to execute things in parallel. While, if you have a strictly sequential compositionality mode, in that case, you need to go for monads. You need to go to monadic compositionality. So I have given several talks and one of my talks is also coming up on, actually, it's on domain-driven design, DDD Europe, which is coming early next month, and I am going to speak about the same thing.  How to start with the algebra for use cases and how to define the compositionality without knowing anything about the implementation of each of these functions, the algebra themselves will define the compositional semantics for you.

**Adam:** Going through your book, one of the things I appreciated was how far you take things without actually doing an implementation of the function? But rewinding a little bit, so you use this term algebra, then I think that coming to terms with what that means is, at least for me, it was a little bit tricky and maybe for our listeners, so, let's define an algebra. As an example I think you had was like the natural numbers under an addition operation. Is that an algebra?

## **Defining an Algebra**

**Debasish:** I would go for a slightly more basic one. Suppose I consider a set a set of objects. When I say a set of objects, I don't specify what type of objects that is, and I can actually define an algebraic structure based on a set. But this definition, no hard state what type of objects the set contains, and I can define operations on this set without going into the details of the implementation of the type of object. So this is the definition of the algebra of sets. 

So one of the specializations of this definition, one of the specializations of this algebra is to define a set of integers. If I can define my behavior at the abstract level of a set, in that case, I'm doing algebraic programming, it's becoming much more generic. If I take an example, consider the definition of a monoid; if we look at the contract of a monoid and it's completely generic, it's completely parametric on the type of which it encodes. 

**Adam:** Let's define the Monoid.

## **What is a Monoid?**

**Debasish:** Monoid is an algebra which basically supports two operations -- one is the identity and one is an associative append operation. So any object for which you have support for these two operations for a monoid. And this definition is completely generic, whenever we define a monoid in, say, Haskell or Scala, we define it in terms of a type parameter, we call it parametric polymorphism. The type monoid - the algebra of monoid is defined in terms of a polymorphic type say A. We don't have any constraint on what this A has. 

The only thing which we need to look after is that this will support two operations. One is the identity operation and the other is an associative append kind of operation. So we can define a monoid for an integer. Then we're specializing the algebra for the integer type. In that case, suppose we define a monoid for integer addition. In that case, the identity is the number zero. Because adding zero to any number gives you the same number. And then append operation is the operation of addition - you add two numbers to get one more number. So addition is associative, here I have defined a monoid for the class of integers where we derive from the generic algebra. 

Not only this, that since I mentioned the term associatively, but this is also one of the laws of the monoid operations. Any such generic or parametric algebra usually is governed by a set of laws. For example, in the case of a monoid, we have the laws for identity operation, and for the addition operation or upend operation, which has to be associated, binary associated. So these are the lawful algebras. A monoid is an example of a lawful algebra. So my point is that if we can abstract our domain behaviors in terms of these algebras, in that case, our behaviors become much more reusable. Our methods become much more reusable and we can reason about these in terms of the laws, which these algebras honor.

**Adam:** So in some ways, so the algebra of Monoid is, it can be specified by a trait or a type class. And in another way, it's sort of like a design pattern that you might see in the object-oriented world. Do you think it's a pattern you can pull off the shelf, you can see that my, my money class fits this pattern, so I can extend from monoid?

## **Patterns of Functional Programming**

**Debasish:** Yeah. It's interesting that you mentioned the term pattern. In fact,  I call these algebras the patterns of functional programming. So if you go to this canonical definition of a design pattern, which Christopher Alexander points out, you'll see that a pattern is a solution to a problem in context, right?

So when you define a pattern in terms of functional programming, you have a very clear delineation of this -- Pattern thing and the context thing; the pattern is the algebra and the context is one of its implementations. So given you mentioned the money class, a money class provides you the right context to implement a pattern in terms of the two operations, which money supports in order for itself to become a monoid.

So money can be a monoid, but that's an instance of the pattern. The basic pattern is the monoid itself, so I call these lawful algebras the patterns of functional programming. 

**Adam:** And the interesting thing is, I mean, to me, design patterns like from the Gang of Four Book, you have to, you have to implement them if you want to use the decorator pattern as you implemented.

Whereas if you want to use a monoid, you don't have to implement it, right? You can, you can use a parametric monoid trait and kind of you get this a behavior for free. Do you agree?

**Debasish:** Exactly. In fact, I gave a talk in December at Scala exchange where this was the theme of the talk. The functional patterns and implementations. Actually I mentioned the patterns which are there which we learned in the Gang of Four Books using Java or C++, you need to write lots of boilerplate. Every time you implement a decorator pattern, you need to write lots of boilerplatey code, which needs to be repeated everywhere if we did it for every context. But here you straight get the algebra as a reusable artifact. So that's the beauty of functional programming patterns. 

**Adam:** Okay. There's an algebra of the monoid, it has certain things you can call on it:  identity, associative operation, but then you also talk about kind of the algebra of your problem, I guess, or the algebra of your, of your design. How does that differ? 

## **Three Core Things of Algebra**

**Debasish:** Yeah. Actually, what I like to say is that, when I define the algebra for monoid, the algebra of any abstraction consists of the data types, the operations it supports, and the laws it honors. These three are the core things of an algebra. And this definition is valid, whether you consider a monoid or a specific abstraction for your domain. For example, if you have a domain-specific abstraction, say you are modeling a trade security trade. An abstraction supports a number of operations and each of those operations that take a set of values to return some values.

And those operations are bound by some laws. For example, when you are doing a trade in the stock market, you are bound by the laws of the market, right? There are various laws that you need to honor in order to execute the trade. There are laws for computing taxes and fees. Then there are geographic-specific laws, et cetera.

**Adam:** So how are laws different than, than a business rule? 

## **Laws are the Business Rules**

**Debasish:** Laws are the business rules. The various business rules are laws, and they are part of the algebra of the domain. So when I'm modeling a domain, and when I'm saying that I'm defining the algebra of the domain behaviors, I am defining the types, I'm defining the operation and I'm defining the various laws, which that particular behavior needs to honor. Now the point is, our idea is to make these laws verifiable, right? Make the algebra verifiable. Much of this we can do through types. For example, say,  genericity or parametric polymorphism gives you a tool to make these, make some of these laws verifiable.

For example, you can put constraints on the type parameter. For example, say you are defining behavior that takes a data type, which takes a type of trade, which takes a type of an account, but this account may have some specific constraint associated with it.

For securities trading operations and accounts can be of multiple types. It can be a client account, it can be a broker account, it can be a trading account. It can be a settlement account. But the, but this account, which this behavior takes, maybe it has to be a first specific type. So, in that case, we can use type constraints. We can constrain the parametricity of the type and enforce the law there itself.

The advantages that we are having, we are enforcing the laws statically and we don't have to write a single line of test for it because we have encoded the laws as part of the type system. This is one of the reasons why I am much more excited about the dependent types, languages like Idris you can do, you can do a lot more with those, but even with Scala you can, you can go a lot of ways. And for those laws, which you cannot verify with your type system, you can do it through your algebraic properties and plugging in property-based testing suites.

**Adam:** So for, type constraints. What kind of type constraints can you do in Scala? Or do you need dependent types or do you need what? 

**Debasish:** No, actually, in Scala, when you are defining an abstraction, which is parametric on a type T, you can specify that this type T needs to satisfy this constant, this type T needs to be, it has to be a subtype of a trading account. So in that case, the compiler will ensure that you cannot pass any of the types of account when you are defining the abstraction and when you are implementing the abstraction. So the compiler acts as your tester. The compiler writes the test for you. You don't have to do anything for it. 

**Adam:** It's funny you mentioned Idris. I'm doing an interview with Edwin, later next week actually, so it will be interesting to talk to him about Idris. I think it would be helpful if we dig into a specific example. So I have your book open, and this might be a little challenging over audio, but you have this trait account service. An account service takes three type parameters, account, amount, and balance.

So. I think this is what you're describing, right? The actual account type is actually just a type variable. It's not defined in the implementation of this trait. And then..

**Debasish:** Yeah, this idea actually stems from the same idea that I was talking about the theories of algebraic development. When I'm defining a behavior, when I'm defining a trait, a module, or behavior, I have no idea what my account entity will end up with. Right. I don't have any idea of the implementation. 

**Adam:** That makes sense. So, just to summarize, when you're saying “I start my domain modeling by doing the behaviors” what you mean is you're not even writing out what the, what the account type looks like you, you're starting with this trait where it's totally parametric over the type of account?

**Debasish:** Exactly. So I constraint the implementation when I'm going to write the implementation for the trait. But initially, I started with only the algebra. And, as far as the algebra is concerned, I parameterize anything and everything, which comes to mind and which might play a role in the domain model.

Some of them may go away in a when I do refinement of the algebras, but I don't want any of the implementation constraints to creep into my definition of the algebra. 

**Adam:** So this makes the trait sound very abstract, but it's interesting in your example. So you do this trait that parameterized over the account. It has a debit and it has a credit, right? And so these are two methods you can call that take an account and an amount, and then return an account. And the interesting thing is there's no implementation for these, but then, you further use that to define a transfer method. 

**Debasish:** Right, the transfer method doesn't need the implementation of credit and debit right?

**Adam:** Exactly.

**Debasish:** So that's the point of algebraic development. I have a more meaty example, possibly later in the book. When I talk about trading systems. And I also kind of repeat that same example in most of my talks where it models the use case of the trading system. It models the various steps as security goes through in order to,  starting from the client or the, till the trade is done. So this entire use case can be modeled using pure algebra and without any constraint of implementation on it. So yeah, it makes a good example.

**Adam:** What's the advantage?  I guess. What's the advantage of writing my transfer method without even knowing what an account is? 

## **Developing the Advantage of Abstraction**

**Debasish:** Yeah. The advantage is abstraction. You need to develop at the proper level of abstraction. Because if you pollute your algebra with implementation constraints, then later it becomes difficult to generalize. For example, if I have a complete program based on algebra. For some definition of the program. It can be a single-use case also.  In that case, I have lots of flexibility later when they go into the implementation phase. For example, I can define my algebra in the form of a free monad, and then when they have the free monad, it's just a pure data structure. There is no semantics in it. It's a pure data structure, and then when I define the interpreter for the free monad, I have the flexibility of doing all sorts of implementation constraints there. I can even have multiple interpreters. In fact, that's a very common technique when you use one of the interpreters for testing. For example, in my algebra, I return for some of the methods I want to do them non-blocking and the returns the future. 

**Adam:** Could you explain what a free monad is? 

## **Free Monad**

**Debasish:** Yeah. A free monad is one of the techniques to separate decouple an abstraction from the implementation. So what you do is you define each of your behavior as an algebraic data type. And then by some magic, you can make each of them monadic. It's difficult to do the details over audio, but for the timing, let's say that you have some magic that turns each of those abstract algebraic data types into a monad. So the moment you have the monads, you can compose all of them.

Using a four comprehension kind of syntax because, and this way you could define the exact sequence of the use case. You can define four comprehensions, which will define the sequence of your use case just from the algebraic data type. We don't have any semantics attached to each of them. So when you have the final four comprehensions, you have the full use case, but you have it as a, your data.

It's just another algebraic data type you have. 

And now we can write an interpreter or you can write multiple interpreters for this free monad. And in the interpreter, you can come up with all sorts of implementations specific constraints that you wish. For example, I may have a trading process defined as a big monadic structure and I'm going to define an implementation for it. I can choose to base my implementation based on the future, or I can choose to base my implementation based on Catz IO or based on M Task or based on the ScalaZ task. I have this flexibility when they go for my implementation and my algebra is completely unaffected.

I have a generic algebra which models the entire process, and they may have multiple implementations. So this gives the flexibility to decouple the algebra from the implementation, so it makes your code much more modular. 

**Adam:** It seems like the free monad is the ultimate example, of what you're saying here, right? Taking the algebra and the actual implementation totally apart, into separate steps. Why doesn't your book just say, always do everything as a DSL written in a free monad style?

**Debasish:** Free monad is one of the techniques. It has its disadvantages also. Another technique is what we call the tagless final approach. If you're Google for the tagless final,  you will find lots of papers on it. That's one other way to decouple your algebra from the implementation. The drawback of the free monad is that it's not easy to compose multiple free monads because, in case of when you have a fairly complex domain model, you have multiple use cases, right? And those use cases may, again, interact with each other. So, in that case, there are situations where you may have to compose multiple free monads, and that's not easy. That at least in Scala, you need to write quite a bit of boilerplate code in order to compose multiple free Monads.

**Adam:** Can you compose them after you interpret them?

**Debasish:** But that loses the benefit. You want to compose it before interpretation or you want to build a bigger abstraction out of smaller ones before I interpret the entire thing. So the plus point with free monad is stack safe. You can implement the free monad in a complete stack safe way. Your stack will never blow out and that's all, that's a disadvantage with the tagless final approach. Tagless final is not stack safe if but the tagless final are easier to compose. So there are trade-offs, these are all trade-offs, and they will need to choose whatever option fits for you. But, personally, in recent times, I'm using more of tagless final approach rather than the free monads because of the compositionality. 

**Adam:** OK,  I noticed that you, you, in the past, wrote a book about DSL. So I was just curious,  how does this relate?  It seems like a free monad or tagless final is a way to write a DSL.

**Debasish:** Yeah, actually true. When I wrote the book on DSL, I was not aware of some of these techniques of free monads and taglines final. Maybe they were also not very commonly used, at least on the JVM. Today, if I want to write a second edition of that book, I will definitely consider using free monads and tagless final approaches to encode the DSL.

In fact,  there are some examples, there are some examples in the Catz ecosystem where they have developed DSLs based on free monads and based on, tagless final approach.

**Adam:** Interesting. Yeah. I wondered if there was a connection there. Rewinding back, we have this account service example where we have this trait, and it's parameterized over the account and also the amount and the balance like basically all the nouns are just type parameters in your example. So, we have these methods, let's say we, so far we have debit and credit and transfer and so debit, obviously debit takes money off an account credit,  adds money to the account and then transfers just sort of composes the two of them, right? So if I give you two accounts and I say, “I want to debit this one and credit this one.” So this is our example. Now let's say that we have this, and because of our business requirements, we actually need some sort of a configuration. So before we debit, we need to look up some value in some sort of configuration. How would that change things?

## **Monad Dependency Injection**

**Debasish:** Yeah. Actually there's an algebra for that in order to inject configurations, there's a reader, monad. You can use the algebra of reader monad to do dependency injection in functional programs. I think there are some examples also in this book or if you're a Google for a reader monad dependency injection, you will get lots of examples. You can, you can compose, compose that algebraically to. You can inject your dependencies or inject your configuration parameters completely algebraically as part of your algebra. When you are defining algebra, you can define what to inject and the precise implementation will follow as part of your implementation of the trait.

**Adam:** What's your opinion on using this kind of reader monad versus alike using your standard dependency injection? Like, off-the-shelf, wire things up when it builds the object? 

**Debasish:** No, actually I prefer to use the power of the language. Whatever comes with the language and reading the monad is one of the nice abstractions, which I find. If my language supports a seamless implementation of a reader monad and if it offers, then I usually prefer that in,  instead of going for some libraries or frameworks. 

**Adam:** The reader, then you're passing into the, like when you run the function you're passing and things where if you use a more traditional dependency injection style, you usually have some class, right?

And you're doing constructor injection and then calling the methods, right?

**Debasish:** Right, if you are in the functional programming world and using things like reader monad the beauty of this thing is that all of these things compose because all of them are based on functions. So reader monad is a monad, the list is a monad, the option is a monad. So here we have this basic general algebra for monad, which embraces all of these things. So whatever you do,  you have the ability to compose monads in some way or the other. But beware, not all monads are composable. You need monad transformers for those things. But generally, monads compose or applicatives compose or I should say that functions compose. So that's the basic building block, the compositionality.

**Adam:** So if we go back to that example, and now, before we add, we credit an account and the return type is a try of account because the, you know, the account could be closed or something so we returned some sort of error status and now we want to have this reader T. So now we have a reader to try, of account, and now you've mentioned monad transformers. Could you kind of expand on how that works? 

## **Multiple Monads Through Transformers**

**Debasish:** Yeah, actually you can compose multiple monads using a transformer. Say you mentioned reader T you can use reader T to compose reader with some other monad and the result is also a monad transformer. So that's the advantage of using monad transformers. You can compose composite monads out of multiple simpler ones. So you can structure your program monadically, and yet you can use the power of both the monads together.

**Adam:** I guess, as, as we add requirements, does that mean, you know, we're gonna end up with like, you know, a stack of transformers that are like a reader, writer, state.

**Debasish:** Exactly, that's the idea. That's like the, in Scala, after a certain time it becomes a little more cumbersome because of some lack of type inferencing. But that's the idea. You can compose multiple monads using monad transformers, and as your requirements increase you can go on adding stuff, elements to the stack. And in the context of this,  I will say that there are some alternative techniques also since using a basic monad transformer, turns out to be a bit of verbose in Scala. There are some additional abstractions that people have come up with. For example, there's this  EFF monad, if you Google it you'll find it. There's this EFF monad, which, which implements one of the recent papers of Oleg,  where he has, where he's talking about the, freer monads of what he calls them as free or monad. More free monads kind of thing, where you can include all of your monadic stuff inside one monad and then you peel off as you need. So compositionality gets a bit better there, but for all practical purposes, I have found that monad transformers come up as a, as quite handy option.

**Adam:** If we have this big stack of monads,  what does that encode like in our -- I mean, we're talking here about the domain modeling, but what does this represent?

## **The Monadic Comprehension and Sequence**

**Debasish:** Sequenciality, sequential composition. When you have a, when you have a monadic comprehension you can execute the various steps in sequence. So one step completes, and then the other step can begin. So that's the basic principle for monadic composition.

And suppose you have multiple monads stacked together, and when you do the sequentiality, you can directly reach to the innermost with a single step of comprehension. So that way you reduce verb verbosity. And without using monad transformers, you need to peel off each layer successively. One by one, so your code verbosity increases. It becomes much more verbose and after a certain number of elements in the stack, it becomes almost unbearable. 

**Adam:** It allows sort of factoring out of certain common things that aren't part of the business domain, I guess. Right? Like, you don't need to have specific exception handling because you have that. That try or that either in there and it will short circuit on its own without having to throw exceptions. 

**Debasish:** Exactly, the exception, the happy part, as well as the exceptional part. Both of them are taken care of by these abstractions themselves. You don't have to write specific cases, you don't have to write specialized branches of code in order to encode the exceptions. 

**Adam:** So, I guess we have our account service example. It's parametric over these types, and now our debit and credit, you know, they return an account, but it's within this transformer stack. So at what point do we start writing implementations of the account or balance or et cetera?

**Debasish:** Yeah. Once you have the algebra defined, once you have the total abstraction defined, anyone satisfied with the algebra in that, then you can, you can start writing the implementations. The usual technique, which I follow, is that whenever I write an implementation for abstraction, I keep an eye on the testability part of it. So, for example, suppose I want to have, as part of the implementation or suppose,  let me start from earlier. Suppose I have a method. I need a function that needs to return the future. So I can have this future thing as part of my algebra right. The disadvantage is that whenever you have a future if you have an abstraction like the future as part of your algebra, in that case, when you write tests for this abstraction you need to have those execution contexts and you need to define futures, right? Yeah. If you kind of think of the future as a monad, which people tend to think of, then it's better to have your algebra defined in terms of a monad instead of a future. The advantage is that in your implementation, you can specialize the monad to a future, and for the testing part of it, you can specialize in the monad as an identity monad, So in that way, your test code becomes much simpler. It becomes much easier to test without any of the engineering or any of the intricacies of having to deal with execution, context, and futures. 

**Adam:** Okay I like this idea because I have this problem and I think I know the answer, but let's say I have some method and right now it does things, it uses tasks, right? Monix task,  It's actually a monix. Inside, it calls a bunch of things, which are all async and return tasks. But let's say it calls a method on task like to say, gather an order. Right? Which kind of does them serially, so you're sorry, it does them. In parallel, so I mean that that seems to limit me, right? I can't just have it over some generic type because I'm actually making some assumptions based on the type it is in the service. 

**Debasish:** Exactly. 

**Adam:** I'm doing something wrong, I guess is what you're saying? 

**Debashish:** Yeah. The idea is to keep the algebra as generic as possible because if you have a generic algebra, then it's easier to modularize. It's easier to write tests also

**Adam:** So in this case, I guess because they can be run out of order, they should be like applicatives and something should magically run them out of order?

**Debasish:** Right. And there are API is, if you look at the latest releases, their API is where you can run things in parallel if it's an applicative, they're so kind of a parallel type class, I think, which has essentially been released.

**Adam:** So I should do things in terms of that. And then in my tests, I don't need to actually use an async?

**Debasish:** Using things like monix as part of your unit test doesn't make much sense to me, 

**Adam:** So it doesn't make sense to me. It's just where I live. When I opened up my ID.

**Debasish:** Yeah.

Adam Something I really liked in your book,  which I had heard of before but, but hadn't really quite understood is,  Phantom Types. I wonder if you could explain Phantom types. 

## **Phantom Types**

**Debashish:** Yeah. Actually,  Phantom types are there to honor some of the constraints. It's not a business type per se, it doesn't have any business connotation, but the trick is that you can, you can use the power of the type system in order to ensure that invalid abstractions are never instantiated.

**Adam:** Okay. Do you have an example?

**Debasish:** It's difficult in the audio, but yeah, there was a very nice paper from Jane Street OCaml -- Make Illegal States Unrepresented on Representable. I think the title of the article was written by an OCaml person from Jane, I forgot his name. So, yeah that has a nice example and I think in my book also, there's an example where I talk about how it was a use case for loan approval or something like that. Where it was not possible to pass an illegal state as part of the API. 

Adam Yeah, I think that's exactly the example. So if you have like a loan application process and you have some sort of loan object. And then the key thing, I think you're introducing a type that doesn't do anything except it, you know, enforce the type system something like implied. 

**Debasish:** That's what I was telling, that it doesn't have any business connotation. The types don't have any business implications. It's there in order just in order to ensure that the user cannot pass anything to the abstraction, which is illegal, so the illegal states are by definition inadmissible. So that's the basic spirit of Phantom types, making illegal states unrepresented. 

**Adam:** So let's say you have a loan. And it has to go through like, two phases of approval so this loan object goes into approval stage one, and it comes out with something like this approved, you know, bit flipped, right? And then it goes into the second approval stage. You know, there, it gets this bit flip, but the problem, with that, right, is like, you never want it to go to stage two. If it hasn't first hit stage one I may be butchering, well, from the book, the idea is we add a type parameter and the type parameter just says like stage one, stage two, for instance. It's like a sealed trait of two different stages. And then you make this loan have this type parameter, stage one, and then when you return it from stage one, you actually just return a new object, which has the type parameters stage two it, it's actually the exact same object, right? 

**Debasish:** Right. 

**Adam:** But it means that you can never write code. Like it's almost like a developer ergonomics thing, right? A developer can never code the calls, the second stage, if they have an object that's in the first stage. 

**Debasish:** Yes. Alternatively, you could do this validation in runtime,  in the, in the, in the, as part of the business logic. But I thought that doing it through the type system was kind of neat because first, it enforces these constraints during compile time. You don't need to write any tests for this. So I kind of need a part, this technique of using fandom types to enforce constraints.

**Adam:** Yeah. That's very true. Right? So you could have your stage two just check a flag and say like, “Oh, stage one wasn't passed.” Let return..

**Debasish:** Right. 

**Adam:** Yeah. That's very true. Phantom type makes that impossible. Right. You are encoding that if statement actually into the type system. 

**Debasish:** Yeah. Once again, that philosophy that the compiler will be your test the company that can test your code. You don’t need to write anything.

**Adam:** I thought it was a great example and a great phrase, make illegal states unrepresentable. 

**Debasish:** Yes. Yeah. Actually, this phrase was first used by Yarin Minsky of Jane Street. I think I acknowledged it also in the book that it's. It's not my terminology, it was first used by Yarin Minsky in a blog post on Phantom types OCaml. 

**Adam:** Yeah, It's a quote, how about the smart constructor? What's a smart constructor? 

## **Smart Constructor**

**Debasish:** Yeah. Smart construction is supposed to abstract you from some of them, once again, it enforces the construct,  enforces the construct when you are constructing an object, one of the core ideas of domain-driven design is that when you have a domain object, it cannot be an invalid one.

The constructor should ultimately spit out a completely validated object. And the idea of smart constructors is to act as a layer on top of the basic constructor to enforce these constraints. So, yeah. In one sense,  if you have an object, the constructor always gives you an instance of A but the smart constructor can give you an instance of an option A or an either or something like that, indicating that the construction process may fail also. Because not always, you can get a fully validated, fully constructed object, fully valid object out of your construction process.

So instead of throwing exceptions, which are not referentially transparent, a better idea will be to indicate once again as part of the type system that I am returning an option A which means that it may have failed. So the idea of smart constructor is to make this claim that, “If I hand you over a fully constructed domain object, then it will be a valid one.”

**Adam:** So,  an example maybe. So how would you do this? Let's say that you have your, your account and you want to create an account and you pass in,  money, which is your starting balance, but you want to enforce that that amount can't be negative. How would you do that?

**Debasish:** Yeah. So that's part of the validation. All these validations will go in the smart constructor, and if any of these validations fail, then you return a different data type means you return a disjunction like either or you return an option or some, something like that, or a try also. So, the idea is that once again, you cannot, you cannot publish a domain object, which is not valid, and you cannot throw an exception.

Because,  exceptions are not good citizens of functional programming. So the basic idea is this in force, to publish only valid domain objects or indicate to the user that I couldn't construct a domain object out of this and do this in a referentially transparent way through pure values and not to be an exception.

**Adam:** In your constructor, if you checked the balance and it was negative,  like all you could do is say, throw an exception.  and that's not referentially transparent. But if we, if we can return a noun, which we can't from, from just standard construction, but in our smart constructor, we could have whatever type, right?

**Debasish:** Right? So the standard technique is to make your constructors inaccessible to the general user instead, publish smart constructors.

**Adam:** And this is, this is sort of like a factory, I guess, in a sense?

**Debashish:** Oh, yeah.

**Adam:** So what is a Kleisli?

**Debasish:** Kleisli is one encoding of the reader, monad. It's basically a function application. But the abstraction Kleisli gives you a, it gives you a number of combinators which you can compose, compose together. So that's the advantage of using Kleisli, our native function application. So when I say Kleisli, option a, B, it actually means that a to option B or some, some, something like that if I forgot the order of this. But it takes an option, it takes an E and gives you an option to be.

So it's basically a function which takes an option and A and gives you an option B. But the moment you declare it as a Kleisli, in that case, you, you,  you have at your disposal, lots of competitors that Kleisli obstruct. So in the book, there are, there are, there are, I think there are some examples where you use combinators to design some DSL kind of thing, which makes the code much more readable and composable 

**Adam:** Yeah. Cause Kleisli gives you the a and then, right, you can kind of, you can kind of chain these things. And then,

**Debasish:** Yes

**Adam:** I mean, I guess like circling back to the, to the whole main topic, I guess, you know, that's one of the key points is I think if you're using these, these algebras like a Kleisli or a monoid there exists like combinators and higher-order functions that give you the functionality that you don't have to write.

Is that one of the advantages of this approach? 

**Debasish:** Yeah, that's one of the advantages. And the other advantage is that using algebra-based programming, there is a clear separation between the construction of your abstraction and the execution of your abstraction. For example, if you use a monix task, or if you use Cats IO you can build your entire abstraction before you can execute it. So there's a clear separation between the two phases  which is not so straight forward. If you use abstractions like the future, you don't have this delineation. 

**Adam:** Yeah. It's that separation. I think that makes a lot of sense.

**Debasish:** Yeah, that's true. 

**Adam:** So You work at Lightbend,  what, what is it like to work there? What, what are you working on?

**Debasish:** Yeah, actually, I'm working on a, working on a, on a team called fast data team where we are developing,  a toolset for a streaming platform. And very recently, over the last three or four weeks, I was working on a library on CAFCA streams and last week we opened-source it also. So CAFCA streams have a Java API, but those APIs are very painful to work with if you're, if you're working with Scala.

So we wrote a couple of libraries for Scala libraries and open-source state. And we are planning to have them integrated with the CAFCA community also. So I was mostly working on this over the last three, four weeks. But generally, I'm working on this streaming platform toolset, which we call the fast data platform of which for which  the general level a GA is out and  yeah, looks quite interesting and looks really exciting 

**Adam:** To me. So, what is the fast data? 

## **Fast Data as a Platform**

**Debasish:** Fast data is a platform where you get things like,  spark, Flink, CAFCA, et cetera. Built on top of DCOs. You're looking at adding the Kubernetes to the equation, and you can deploy your applications and the entire management of the resources and the monitoring part will be taken cared of by the platform.

**Adam:** I think this has been a great talk. Thank you so much for coming here. I really enjoyed your book. It took many, there were a lot of concepts that took me a little while to understand, but I think it's a great book about the design patterns of functional programming. Thank you so much for your time.

**Debasish:** Yeah. I loved talking to you as well. 

**Adam:** Yeah, we could do another one sometime. I thought you had a number of talks. I'd like to hear your thoughts about the ACA at some point. It sounds like a, maybe. 

**Debasish: ** Sure. All right. 

**Adam:** Alright. Take care. 

Thank you to Craig Treptow for podcast transcript help.
