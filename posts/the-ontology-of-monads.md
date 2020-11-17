---
title: "The ontology of Monads"
date: "2019-08-17"
---

We understand our overwhelmingly complex reality through abstraction and decomposition: we form neat, limited-scope mental models, and we arrange groups of mental models into more complex models. According to Bartosz Milewski, author of Category Theory for Programmers\[link\], Category Theory gives us an explicit way to reason about this process of decomposition and composition: "it's a very good description of how our minds work."

Programmers may find the ontological implications interesting. A Semigroup, for example becomes something like an ADD x86 instruction: it represents our minds' ability to take two distinct entities within a models and derive a third entity. Just like we can form a Semigroup with the set of integers and addition, we can form a Semigroup with the set of all sets of human and the operation "joined." My mental arithmetic when Jan and Bob Smith arriving at my dinner party has something in common with 3+4=7.

More interestingly, consider a category representing a mental model whose objects are also mental models. Imagination becomes an Endofunctor. I take my mental model of world leaders and their relationships, and imagine them as heads of different countries. Through the looking glass, the President of Vietnam becomes the President of South Korea, and the President of China becomes the President of the US. In a simplistic model in which personal relationships drive policy, I'm now exploring an alternate reality in which South Korean has a much cooler relationship with the US.

I tell stories with Monads, starting from our shared mental model of the world, proposing one imaginative change after another, each one evolving a vision of a hypothetical world.

If category theory makes our human instruction set explicit, does programming with it represent the ultimate level of abstraction (describing what we want done using the atoms of our own thought)? Is trying to represent our algorithims in terms of how humans operate ignoring their implementation on actual computers a misguided effort built on a leaky abstraction? Might there be formal systems for capturing expressing the structure of human thought that are more useful to programmers?

<iframe style="border: none" src="//html5-player.libsyn.com/embed/episode/id/10876695/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" height="90" width="100%" scrolling="no" allowfullscreen webkitallowfullscreen="" mozallowfullscreen="" oallowfullscreen="" msallowfullscreen=""></iframe>

**Bartosz thanks for joining me on the podcast. People who listen to this, they might hear different terms that come up over the course of episodes like functors and algebraic data types, applicatives, sum types, product types. Like where do these terms come from?**

Oh, they come from category theory.

**And what is category theory?**

Yeah, category theory is a branch of mathematics. It's a very, very abstract branch of mathematics. And really surprisingly this extremely abstract branch of mathematics has applications in programming. Which is really a big surprise. I talked to some mathematicians and they were also surprised. When you are a mathematician and you want to study category theory, usually you first go through all other branches of mathematics. So you have to be like fluent in topology and Algebra and Analysis. You know, it's all these things because -- group theory -- because they use examples when they teach category theory they use examples that are familiar to mathematicians. So they use examples from every branch of mathematics because it's like a theory that abstracts over all other branches of mathematics.

**So what does it have to do with programming?**

Well, because programming really is mathematics. You know, whether we know this or accept this or not. It really is and it's all about structure. And mathematics is all about structure. I mean mathematics is just building structures from essentially from nothing. You know, you put some axioms and then you derive stuff from it and so on. But it all has tremendous structure, right? Everything is structured. There's this follows from that, you know this, you divide things, you categorize things, you say, you know, well we have things like groups. We have things like monoids. We have things like measures, topology, open sets and so on. So that you categorize things and you say like, you know, you have all kinds of sets but there are some special sets like open sets and so on. And how do you characterize these things? Well, you characterize them by saying what properties they have.

So how they interact with other things that you already know or other things of the same type. And this is very much like what we do in programming. We define things and then we describe them by how they interact with other things. Like in object oriented programming. Okay, I mean mostly category theory is used in functional programming, but object oriented programming also has very rigid structure, right? So you do things like data hiding for instance. What does it mean to hide your data? It means that you want to describe your object, not by how it's implemented, but how it interacts with other objects. Namely its methods, right? What are messages, like what kind of messages can you send to this object and how it will respond to these messages by sending other messages and so on. So this view of things, you know -- that you have objects that interact with each other by sending messages, for instance -- that's like the essence of category theory. A category is just a bunch of objects and arrows between them. That's all. And this is perfect model for programming.

**So there's an abstract branch of math that deals with objects and arrows.Then somebody realized this looks a lot like what we're doing with software development. Is that kind of the view of it?**

Historically speaking?

**No.**

No, no. You know, I mean people were always... Like computer scientists were always interested in like what is programming really? Right? So there are like these two schools of thought, the Turing School of Thought that says: "Well the computer is just a device that has like a sort of like a printing head and the reader and so on, and it just moves the tape and infinite tape and moves them." So this is a very mechanical kind of approach. And then there is this very abstract approaching mathematics. Or like what is computation? Because normally in math you define things like functions and you say, "well function is just a value that is related to the argument of the function." So there's argument and there is value. You know, its like function is defined and this is argument. This is value. Give me an argument, I'll give you a value. It doesn't ask you, you know "well, but how long will it take you to calculate this value?" Right? No, it's just there. Right?

But in computer science you have to think about, well if I want the value I'll have to derive it from the argument somehow and I have to go through some steps. Right? And so I have to decompose this bigger question into smaller question. And just answer every single smaller question and then combine them into one big result. Right? So being able to decompose bigger problems into smaller problems and then combine the solutions. That's essentially the description of, well I don't know. It depends on who you are. You will say, oh, that's a description of what I'm doing as a programmer. And a mathematician would say other, this is a description of what I'm doing as a mathematician and you know. I feel this is, we'll say that's what I'm doing as a physicist and so on. It's like everybody is doing this. This is like the essence of all human activity.

**That's interesting. It makes sense to me that that's what I do as a programmer. Like, if I'm given some requirements, then you know, I feel how they might break into like modules and then build those modules and then combine them back. I would've never thought that that's what a mathematician does, but maybe I don't understand what mathematicians do.**

Well, when you're a mathematician, you also like divide your work into, okay, "I have to prove this theorem first, and in order to prove this theorem I have to prove this lemma. I have to define like a new maybe space or object in my space and so on." So it's like, yeah, you are. And then if you have like a huge, huge problem, you want to split it into smaller problems. Like if you want to prove Fermat's Last Theorem, right? It's not just like you think for a moment and then you say, oh, I got it, right? No. You said, you know, I have to study first elliptic curves. And there was this theorem in elliptic curves that I have to prove. Oh, and somebody tried to prove it, but they failed because they couldn't prove a certain lemma. Maybe I can do this. And so on. So you always split things into smaller pieces, right? And then sometimes when you work in a team, right, you have to split, your work into individual tasks and so on. So like everything we humans do is always composable.

**So what does category theory bring to the table?**

Yeah, category theory essentially studies all the different ways in which things can be composed and decomposed. That's like the goal of category theory, you know, it's like it says like what is the structure of things? So what is a structure? Structure is like what parts something has and how these parts interact. I mean we don't even ask ourselves these questions like what is structure? But it's an obvious thing, right? But it is structure is that you can decompose something into smaller pieces and you can describe how they interact that structure. Right? Otherwise you have like one huge morass of stuff.

**Why does categories theory seem to... Or why is it more used in the world of functional programming? Why not imperative programming or object oriented programming?**

It's mostly because functional programming is much more restricted, less hacky. I mean, I came from imperative programming. I mean I programming C++ the last four years, so you know, I'm familiar with this stuff and I can do that. Right? But things in imperative programming are not very well defined. It's like they don't really have this nice mathematical structure. It's more of an expert system programming. Like there are rules, you know, you're not supposed to do that. It's mostly like you're not supposed to do things, right? I get a lot of teaching of imperative programming. Its don't do that, don't do that. And they slap you over the head, you know, this is like come dereference this pointer, okay? You're not supposed to do that, right? Now in functional programming, it's more like there is a mathematical structure behind it and let's just stick to it, right? And if you have this mathematical structure, then you don't have to slap people over the head and say don't do that because it's impossible to do certain things, right?

**You mentioned before like Turing machines versus lambda calculus. I mean, computers really are imperative, aren't they? In there execution. So why do we need something that models things abstractly when they execute concretely, step after step?**

Well, because there is this other thing on the other side of the computer and that's the human programmer. Okay? So programming is not just about the computer, it's about the interaction between the human and the computer. And the computer doesn't really care about, you know, how structured your code is. Why do we avoid goto's? You know, it's like computers love goto's. Give me goto's. Yeah, I can execute them. I mean it's like the processor has one of the basic instructions jump, right? Why not let me jump all the time. Right? So why do we avoid goto's? Not because computers don't like goto's, right? It's because we humans, if we have too many goto's, we just lose track of stuff and start making mistakes. Right? So I don't think this is like the requirement, you know, for the computer architecture or the programming language should reflect the architecture of the computer.

I think the computer language should reflect the architecture of the human mind and the human mind works differently, right? I mean we have to do this thing with what we call understand things, right? So the computer doesn't understand things, but we have to, right? We have to understand things and understanding again, it means that we have to like divide problems into smaller things. Give them names, right? And we give them names. The computer doesn't care what names you give like X1, X2, X3 there just fine, right? Why do we come up with these names for variables that, you know, it's like a factory of a lists or something like that. Right?

**I read some story about how the library differs from like an Amazon warehouse, right? So in the library you have like a Dewey decimal system where people can locate where books are. In the Amazon warehouse, Amazon has a very simple way of organizing things. They just put things wherever and just remember where they put them. Cause it's a computer, they don't need it. So it seems like what you're saying is category theory is for people not for computers. Is that the idea?**

Yes, absolutely. Yeah.

**So in category theory there's like arrows and objects. What does that, what are arrows and objects?**

Well that's the wrong kind of question. You're not supposed to look inside objects or arrows. They are just the basic thing. I mean they have certain properties, right? So you've described them not by what they are, but how they behave. So objects are really...you can think of objects as being labels for beginnings and ends of arrows. That's all. Because you have to say arrow goes from A to B. Right? So this is why you need A and B.

So an arrow can go there.

Yeah. So then the arrow can connect that. So you have objects as these end points for arrows. And you have arrows that can be composed? And this is what it's all about, about composition. So if you have an arrow from A to B and an arrow from B to C, then there's automatically an arrow from A to C. Which is a composition of these arrows. And that's the principle of category theory. That things are composable.

**That's it. We're done.**

Well, there's one more thing. You know there has to be an identity arrow for every object. Which means it's an arrow that when you compose with some other arrow, you get back that arrow again. So it's like multiplying by one or adding zero. Right? That's an identity arrow. So that's all the requirements. You know, you have to be able to compose arrows. There has to be a unit arrow for every object that the identity arrow and also the composition has to be associative so that you don't have to parentheses. Did they first compose these two and then compose it with the third one or did I do it in that different, right.

**So what is an example of a category where that has some meaning?**

The category that we are using as programmers, that's the category that underlies programming languages. Objects in that category are called types and arrows are called functions, pure functions. This is why it's so nice to talk about functional languages because in functional languages you have these pure functions, right? So you automatically are in category theory. And in fact this is like maybe the best way of defining what you're doing as abstractly as a programmer. If you ask somebody what is a type? What is a function? People think of types as sets of values, okay? That's one possible approach. But sets for my categories, it's like to the lowest approximation. You can say, well it's a category of sets and functions.

**So I can think about like my method, like to string or show, it just takes say the set of things, the set of integers and maps it to a set of strings. So I kind of the--**

Yes.

**It is the arrow that does that map.**

Yeah, exactly. And you can compose them, right? I mean you can first say two string and then you can say upper case, right? And you have a composition of these two things. You can say uppercase, two string or something like that. That's a new function that is a composition of these two. Of course there is an identity function that we don't even think much about but its a function that returns this argument without changing it.

**Yeah. So the identity on my integers example just returned to the same integer.**

Yeah.

**And so is the value there that category theory gives us sort of a language to look at things from the outside? To just look at the types and the mappings?**

Well this is just sort of the beginning because the category has more structure. You can add additional structure to the category or you can discover additional structure in this category. So for instance, in programming we are dealing with data structures, right? So what are data structures? Again, you know you have to start with some elementary types, right? And then from these types you form more complex types. Like, how do you define a structure struct, right? I mean you say, well I'll put an int there and I will put a string there and maybe a bullion, right? So you are combining things together, right? So you take several types, which are objects in your category and you put them into one bigger type that combines them. That's called a product category theory. Or you do things like creating a data structure in which I either have a string or an integer like a union type or something. That also can be describing in a category theory as as a sum type and so on. So you get product types, you get sum types and you can do Algebra on them and you get Algebraic data types.

**Yeah. One critique that I sometimes hear about functional programming is that the terminology can be confusing, right? That it can be not friendly to newcomers that we call it Algebraic data types and some types of product types. And do you think that's like a valid criticism?**

No, I don't think so.

**No?**

I mean a name is a name, you know? Why should we invent, I mean there are some cultures in the programming that invent languages and libraries where they come up with weird names that are supposed to be easier to understand than the ones they get from mathematics. But then it's sort of like blocks you from going back to mathematics and trying to learn what's the theory behind that? Right? So you go to a mathematical paper and they use completely different language and you don't know what is that? I don't know what the sum is, what the, what our product is. Right? So I don't know why use a different language there and here? Anyways if I call something, you know like in object oriented programming, if I call something an object that's so meaningful, right? Just try to define what you mean by an object in a programming language. Just because you took a word from English language that everybody thinks they understand, that doesn't mean that an object in C++ for instance, is immediately obvious. Oh, that's an object. Oh, I know what an object is because I learned it when I was an infant, right?

**Yeah. And then wouldn't you have objects that are like nouns or you know, like the factory builder you were talking about? How is that an object?**

Yeah, exactly. People try to give them names like mappable I think. So functor is mappable and a monad is bindable. Like, is that really easier to understand?

**Mappable is not bad. I don't think bindable is good. Monad could be like combinable maybe?**

Combinable, yeah.

**There we go. See we've already improved things. So you mentioned C++. So how did you get here from doing C++ development to writing about category theory?**

Well, I was always interested in... How do you write good programs, right? How do you make your programs reliable and that made me interested in the theory behind programming. I was always interested in exploring the boundaries. Like what is the hardest thing in C++ that you can think of? Well, I guess template method programming. Right? Template method programming. So I got into template method programming and it was fascinating because it was so different from regular programming. Because it's done at compiled time there is no mutation, right? So how do you program without mutation? Okay. So I started reading these books about template method programming in C++, and it was really hard to understand. Then I found that they actually take all these ideas from functional programming. You know, some of these people are truly know Haskell and they just translate it into C++ and say, Hey, I came up with this great thing. So I discovered this and I started my own franchise. I started blogging about, oh, this is how you can do using template method programming, this fancy thing here and fancy thing there. You know, it's like, oh, okay, cool. People were amazed that you can do these things in C++. Right? But it was really cheating. You know, I was taking something from Haskell that in Haskell it's just like a one liner and I'm in translating it. So eventually I decided to cut the middle man and just go directly to Haskell and see how it works.

**It's a cheat code.**

Yeah.

**It's a way to understanding functional programming was like a shortcut for you to be able to understand template method programming. Being able to think in Haskell but write in C++ was your advantage.**

Yeah. And then I even started talking to C++ programmers saying that even if you program in C++, it's a good idea to learn some Haskell and maybe use it as pseudo-code. You know, I just think a lot of people from the C++ they don't like functional programming because of performance. Because it's true, performance it depends on what kind of programming you're doing. But if you're doing string processing, maybe Haskell would not be the fastest language to do this. And if you start dealing with performance issues, then your Haskell code, I mean you can optimize stuff and then your Haskell code becomes uglier, not so clean. That clean code doesn't really perform very well. So thats the problem. But you know, it's like if you solve your problem first in Haskell and then you translate it into C++ you will probably get better quality code at the end and better performing.

**And so how did you get from Haskell to category theory?**

Well, because of the language, you know, because they use these terms, the functor, monad and so on. So I was curious where do these terms come from and what's the meaning of that. So I started looking into mathematical foundation on that, trying to understand. And then again, you know, it's like, I know I don't do much programming, mostly just testing some ideas, mostly testing the types, do they work together and so on. Because even the Haskell is too constraining but there are certain ideas in math that are difficult to translate to Haskell. So again, I'm finding the boundaries of what can be expressed in Haskell and then going beyond them as category theory. There is a whole area in between which is dependent types. So dependent types are very interesting. And I'm trying to learn Idris, which is a dependent type language and figure things out.

**Nice. Yeah. I've had a couple episodes about dependent types. Edwin Brady was on the podcast.**

Okay. Yeah.

**Yeah. So I think what you're saying is you went from writing C++, but thinking about it in Haskell to writing Haskell, but thinking about it in category theory.**

Yes.

**So is there a notation or something for category theory? What do your thoughts look like? Is it in a mathematical notation?**

A lot of my thoughts when I do them on paper, on the whiteboard, they are diagrams. Yeah. So you know, arrows between dots. That's how you work in category theory.

**So it's purely visual. Now your thinking is actually all diagram based.**

Yeah. And it's very good for me because this is that different people have different types of thinking. Some people are better at kind of Algebraic thinking where they think in terms of symbols and formulas. Yeah, I don't do that. I have a problem with that. I am very visual and I like pictures. I draw lots of pictures and that helps me.

**Yeah, that's interesting. I don't know, am I a visual thinker? I think I'm somewhat of like a oral, like I think, I think in like a soundtrack, you know what I mean? So what's the most successful? What's been a success that's come out of applying category theory to software?**

Yeah, I think the whole language. Haskell is very solid because it's based on mathematical foundations and category theory particular. So I think, well, okay. Monads probably monads are like the most successful thing in functional programming because when people started working in Haskell, it was a purely functional language. It still is a purely functional language. But with the purely functional language you have this problem of how do I print something? It's a side effect. Okay, how do I get input from a file from the user, right? That's not a function. You know, it's like get character, get string, you know it's not a function because every time you call it, it returns a different value possibly. Right?

**Yeah.**

So how do you describe this in terms of categories? And so instead of like doing the easy way out, like most other languages, including functional language, Haskell is probably the only, well there are some others, but the strict functional pure language, right? Like even ML is cheating. So they started thinking, you know, how can we do this without cheating? Right? So this is a really hard problem. And because scientists like hard problems, unlike engineers who will try to find shortcuts and do it quickly because there is a--

Deadline.

Deadline pending and their salary depends on it. And scientists like is interested in will there be a publication out of it? Right? So if it's a hard problem then the publication will be good. Right? So they figured out this and they found out that other way to do this is to use monads and then once monads came into functional programming, they are now spreading to other languages.

**Yeah, definitely. I had Phil Wadler as a guest on the podcast. I think he did the implementation of bringing monads to Haskell.**

Yes, yes he did. It's like it was Eugenio Moggi who first introduced monads into computer science. But it was very theoretical and then Phil Wadler read his paper, talked to him and came up with something that was actually very practical and worked.

**An interesting thing about Phil was that he was saying that he thinks these mathematical concepts like blamed the calculus specifically, that these are like kind of innate to the universe. Maybe he wouldn't quite say it that way, but he thinks that they are.**

Yeah, he would, he would. Yes. I had discussions with him about this, you know, I totally disagree. He said later in this a lot of mathematicians are Platonists. They believe that there are just things inherent... like mathematics is built into the universe. I totally disagree.

**So what's your perspective on it? Why do you disagree?**

I think mathematics is something that is inherent to human beings. This is the only way we can deal with our environment is because we have small brains. It's like compared to the size of the universe, this is just like a tiny, tiny thing. And it evolved from apes that were trying to solve problems, like how to run away from a predator or how to kill an animal and eat it, start a fire and so on. So the way we deal with complexity is by dividing into smaller tasks, solving them and then recombining the solutions. And that's what we do with everything. We just don't know how to deal with things that are not decomposable. I mean one part of life is that every living being has to have some kind of model of the environment.

So it has to create a simplified model of the environment. I mean we humans have this sort of we can even think about the model as opposed to reality, right? We have a model of the environment in our brains and we know it's simplified, right? But the fact that you can take the environment, the universe, and simplify it, meaning throwing away some things and decomposing in the smaller things that's just an amazing thing. And people think, well, isn't that amazing that the universe is decomposable? And I think no it's not amazing that, I mean, it is amazing that this part of the universe that we live in the particular scales, like the meter scale is decomposable, right? But like you can go like a 10 levels down to like micro scales and suddenly things are completely different. Right? You know, this is why we don't have life at the Planck scale because it's not decomposable, you know, at our level of universe, things are nicely decomposable and this is what makes life possible. And as humans

**Yeah, I would think that it's like has to do with where we evolved, right? Like we have trouble understanding things at the quantum level because that's just foreign to us, right? The same way we have a hard time understanding how approaching the speed of light works. It's just cause humans never existed in a world where they went that fast. So it doesn't fit in the model of our brain.**

But humans never existed at atomic scales because its impossible for life to exist at the atomic scale. Why is it impossible? Why can't there be a life on the surface of the nucleus of Hydrogen, right. Why?

**Well, what would it be made out of?**

Exactly. Right, right.

**Oh, I see.**

Yeah, cause you're saying made of means decomposable, right?

**Ah, yeah.**

There's nothing to compose or decompose.

**I see. Yeah. That makes sense. You had some talk that you sent the link to me where you posit that the world is a not round or that the world is flat. I think.**

Oh, well it was tongue in cheek. Yeah. Yeah.

**Could you explain that point? Like how is the world flat?**

Because people often confuse, well Platonists will confuse the thing that we understand about the world with what the world is really, right? The ontology of the world.

**Because the world isn't really a sphere I guess, right?**

Yeah, yeah. The Earth is not a sphere. It's like if you start arguing that the world is a sphere, you're talking about some kind of ideal of a world, right? A model, right? So you can model the Earth to some approximation as a sphere and that's good. You know, but the Earth is not a sphere. You have to understand the Earth is not a sphere. There is a tiny difference, you know, several kilometers, you know, in some places. Right. So it's--

**It has to do with your decomposition thought. I think, right? Cause you're saying like for me to understand what the world looks like, I need to come up with some model and it has to fit inside my head, right?**

Yeah, exactly.

**So it has to be, it has to get rid of some of the details.**

This is what we call abstraction. Abstraction is getting rid of some details and getting a nice model. So yeah, so I mean you can describe the Earth as a sphere to some approximation. Then you can describe the Earth as flat. Mathematically it's okay. You know, it's like there is a system of coordinates in which the Earth is flat and it would be much, much harder to work with that system of coordinates because you would constantly have to do adjustments. You know, like, yeah, you move towards the South Pole for instance. What we consider the South Pole? You know, and like your coordinates would just blow to infinity.

**So this abstraction I think so at the level of my code, right? Like I just have imperative code that runs on the computer. Like it does jumps and whatever. And then like I have my actual like maybe I have my functional programming code, it's like a level operate it hides some details and then I'm trying to connect this all back. So then I think what you're saying is there's like category theory is like something that gets rid of some of these details even more so it's like if you want to look at the flat, if you, you can assume the world is flat when you're measuring a hundred meter race, like that's fine. Right? But then when you want to zoom out and go to the South Pole, you maybe you want to assume it's a sphere and then like at each level of detail, if you want to do a foundation for your house, like at the lowest level, you can't assume the world is flat. You have to actually know where the bumps and cracks are.**

Yeah.

**So category theory is a way to hide some of the details so that we can fit it in our head. So it's not something. I'm trying to understand your perspective it's like it's not something innate to the mathematical underpinnings of the world. It's a way that humans use to fit big, hairy concepts into their heads.**

Yeah, exactly. Category theory is a very good description of how our minds work. It has nothing to do, well maybe that's just a harsh statement, but you should not confuse mathematical model with reality. And I hear this very often when you know, especially talking to mathematicians, they say, okay, we have them in this category. We have like this category described the world and inside this category we have a model of the world, right? But the world is also a category. It's like no, the world is not a category. The world is already in a category, its already a model in our brain, right? So there is this problem occurs in mathematics and in physics. You know, its like in physics you have quantum physics, you know, and then you have an external observer always. You know, its like --

**That never sat right with me.**

Yeah. And you know, I mean, as a physicist you kind of get used to it, but never really, you know, it's like, you know that there's something wrong with quantum mechanics at some level There's always this classical observer thats observing quantum effects. Like, so it means that quantum theory is incomplete and every single theory that we have is incomplete.

**Cause there just models.**

And even true in mathematics, you know, there's an incompleteness theorem, right? Godel's incompleteness. So it's like everything we do is incomplete.

**So why should people learn category theory?**

Why should people do anything?

**Is it fun? Is it practical? Is it both?**

For a programmer for instance? Like it doesn't make sense to learn category theory. Will it make you a better programmer? I think it will. It will sort of make you a higher level programmer. You know, it's like being able to lift yourself above your program. It's like otherwise you, you know, you're just like a little ant working in an anthill, right? And the only things you see are the things that are close around you, right? It's like your never able to like lift yourself above the anthill and see how it's related to the rest of the world and so on. And category theory provides these ways, these extractions that otherwise you wouldn't even think of. You know, it connects things. It says, well, a list is in a way... A list data structure is somehow similar to an optional in some ways. How is it similar? Well, because its a monad, right? Unless you have this word monad, you know, and the description of what a monad is, you will never see the similarity between a list and optional or a function.

**Well you could just say it's a list of a maximum one arguments, like a list of Max size one.**

Okay. Yeah. Good.

**But maybe that would get you towards the concept of a monad. I don't know.**

Yeah, yeah, yeah. It probably would. Yeah.

**If it became widely understood as a language where we talk about software development using these terminology, like how would that influence software development? It would make us feel smarter because we'd have all these abstract Algebra terms to throw around.**

I think it's already changing the way we program. I mean the development of programming and programming languages is sort of from goes from bottom up. So we start working to solve particular problems, right? And then we discover that there are similarities between these problems and that we could simplify our lives instead of redeveloping the same thing over and over and over. Maybe we can abstract over it, right? And a lot of programming languages evolve. Every programming language really evolves this way that it just adds abstractions on top. And I saw this in C++, you know, I was always really happy when new features came to C++ because like oh I can do more stuff. Right? But they were always like slapped on top of the existing stuff you know, and it was, there was like a, this really ugly syntax of templates, right? You know, it's like there were even problems, like if you have a template inside the template, then the two greater than signs would collide then the compiler would think this is like your all or this is a right shift. You know? It's like that's crazy, right? It just says, you know, this language was not developed to think at this high level of obstruction. Right? And it was just added to it. So there are new languages which lets you program more abstractly, which means that you can reuse your code, that you can write code that will solve different kinds of problems using the same methods. I mean, you know, there is, there's like this whole industry of patterns, right? There is the gang of four pattern book and so on. That was a great thing when it came out, but it showed this tremendous weakness of programming languages that you have to describe these patterns in a book, right?

**Yeah.**

And then ask the programmer, Oh, here you have a particular, you know, write your code according to this book instead of use this library. Right? Because we've solved this problem before. Right? So the gang of four solved a certain bunch of problems. Right? But they could not express it in a language.

**What was a stumbling block that you hit or that people hit when trying to learn about category theory?**

The biggest stumbling block is that mathematicians, they just don't explain things the way that's easy to understand. Let me describe it this way. I don't know. It's like when you read a mathematical paper or a book, you know it's written in a certain style.

**Is it that it's written for mathematicians to understand but not for programmers or is it mostly...**

I think it's a culture. It's a culture thing. You know, it's like there is even, I mean, being a physicist, you know, I see the difference in culture between physics and mathematics. Like in physics, you know, we had this great guy, Feynman who was like, he would always try to explain things in the simplest terms. And he loved giving talks to outsiders trying to explain, you know, the quantum field theory. You know, stuff like this. And mathematicians don't do that. They write these abstract papers and if you don't get it, you know, it's sort of like you're stupid because you don't get it. You know, you shouldn't be reading this. I was fine when I had the opposite. It's like if I can't explain it, it means I don't understand it. You know, if I can't explain it in simple terms, I don't understand.

**And is this why you started your series explaining category theory for programmers?**

Yes, yes. This and because I thought there was this problem that mathematicians will use examples from other branches of mathematics. And so what if you don't know these other branches of mathematics. Does it mean that the category theory is useless to you? No, it's not. It's just that, you know, you have to like rewrite category theory using different examples. And there's plenty of examples in programming that I could use to explain concepts in category theory. And it turns out that these concepts are not that hard if you have the right examples.

Yeah, that totally makes sense. It's interesting. Like I guess one thing I never thought of before I started talking to you was, so there's this field called category theory. My understanding is that somebody noticed a whole bunch of similarities between a whole bunch of branches of math. Right?. And that's where it came from. But what you're saying is I think that those similarities aren't to do with math. They're to do with the people who created math.

Yeah. Yes, exactly. And you see these things not only in mathematics but also in physics, in programming. It's like in every area of human activity you see the same patterns, the same structures. I sometimes am amazed, you know it's like reading a paper in some area of mathematics and they are using the same ideas that I found in some other area of mathematics. Then thinking about are these the only patterns that we humans are able to discern and we are just describing the same patterns over and over and over again in different contexts.

**Does that mean that there's things we'll never figure out because they're not part of the patterns we can find?**

We have figured some things out and there are so many other things that we haven't figured out. We always think that like we already understand 99% of stuff and there's this 1% missing. And I think this is completely wrong. We understand the 0.001% if that even makes sense, right? And there's so much stuff missing if we just ignore the stuff that we don't understand.

**Do you know what we're ignoring?**

Well, yeah, there are certain things that we know that are sort of beyond the scope of what we can do right now. And we think, well eventually we'll figure these things out. But in physics, obviously there was this humongous problem of we have general relativity in gravity on the one side and quantum mechanics on the other side. And we just don't know how to connect that. And we think, well maybe string theory, maybe this, maybe that, you know, it's like, and the deeper we go into it, the more we understand that we don't understand stuff and maybe these things just don't decompose. You know, that's the obvious solution. Okay? And if they don't decompose, then we can't really describe them. We can't have a model, right? It's like does everything have to have a model? Can it be simplified? Why should it be?

**You can always come up with approximates for things. Can't you?**

Why?

**Like how the globe is it?**

Because this is what's been happening in the history of humankind. Whether you can also understand this as like we are discovering things that are possible for us to understand and we just ignore everything else.

**Yeah. I don't know a lot about physics, but, and this'll probably get cut from the actual episode, but like a dark matter that doesn't seem to make sense. They're like, okay, well the universe has to have so much mass to it and there's not enough. So let's just postulate something that weighs the rest of it. That seems like cheating, right?**

Yeah. I mean, and a lot of people think it is cheating. Yeah.

**Crazy stuff.**

There's dark matter. There's dark energy. Yeah.

**Maybe that's the difference between physicists and mathematicians. I don't know.**

Well, physicists are very pragmatic, you know, if it works, it works. Okay. If I can calculate something and then test it, then it's great. In this way, physicists are more like programmers. If it works let's ship it.

**So what's next for you after category theory?**

I'm interested in homotopy type theory, but this is really hard.

**Has to do with the quality. I know that much. So thank you so much for joining me. It was a lot of fun.**

Okay, thank you. Thank you for having me.
