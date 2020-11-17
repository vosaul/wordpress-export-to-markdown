---
title: "Type Driven Development and Idris With Edwin Brady"
date: "2020-04-07"
---

In this episode dives deep into Type Driven Development and Idris with Edwin Brady.

I interviewed Edwin the creator of the Idris programming language and Author of the book Type-Driven Development with Idris and a computer science lecturer.

Discover the about dependent types, type holes, interactive and type-driven development, theorem provers, Curry–Howard correspondence, dependant Haskell, total functional programming, British vs American spelling and much more.

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/6170562/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

"It is a theorem. It's a fairly trivial theorem. But as you start adding a little bit more precision into your type system, and you start looking at the relationships between what is a type and what is a theorem you start getting rather more interesting properties of your programs." - Edwin Brady

"It's not always total. So this is one of the all of the decisions that I made quite early on this, that I'm checking that something is total is important because it's a check that allows you to be certain various properties of your program." - Edwin Brady

"I write programs where I kind of, I know the happy path or I've got a rough idea of what the happy path is." - Edwin Brady

### **Transcript**

**This is a machine-translated transcript. Podcast page for [this episode is here](https://corecursive.com/006-type-driven-development-and-idris-with-edwin-brady/)**

**Adam:** Welcome to CoRecursive, where we bring you discussions with thought leaders in the world of software development. I am Adam, your host.

Edwin Brady is the creator of the Idris programming language and author of the book Type-Driven Development with Idris and a computer science lecturer. The book, the language, and Edwin himself all seem to be chock full of ideas for improving the way computer programming is done by applying ideas from programming language theory.

And this interview, we discussed dependent types, type holes, interactive and type-driven development theory improvers Curry-Howard Correspondence, dependent Haskell, total functional programming, and of course, British versus American spelling. It's a really fun interview and I hope you'll enjoy it.

Edwin Brady is the creator of the Idris programming language and the author of Type-Driven Development with interests. Edwin, welcome to the show.

**Edwin:** Good afternoon. Thanks for having me.

**Adam:** So I have your book here in front of me. I enjoy it. I have not gotten through it, but I've learned a lot.

## **What is a Type?**

**Adam:** I thought. Before we dig in. Maybe we need to lay down some terminology. So What is a Type?

**Edwin:** This is a surprisingly hard question to answer. I think if you ask a hundred computer scientists, you'll get at least a hundred answers. So I would say that a Type is a way of classifying data. So it's a way of putting some kind of meaning to the data that you're working with.

But I think depending on the kind of context you're in, Type can mean something different. So you know if you're the computer, then the type is a way of describing how data is laid out. And if you're a programming language, that a type is a way of making sure the data is interpreted consistently.

But as far as the programmer is concerned what we're all interested in. So Type is a way of describing the data we have.

## **First-Class Types Can Make It More Precise**

**Adam:** What then is a dependent type?

**Edwin:** So dependent type is, I've at least am preferring to use the phrase first-class types. The reason being that if you so when we talk about the functional program, we are programming and what distinguishes it from say, imperative operator into programming or what additional features it gives us.

We like to say that. Some functions are a first-class part of the language that is, you can assign functions to variables. You can pass functions to other functions. You can return functions and so on. So when I say dependent types of first-class types, I mean the same kind of idea, but for types that as you can assign types to variables.

Because you can write functions, which compute types you can pass types as arguments to functions and so on, what makes this dependent is the fact that you can then use types or use values to more precisely describe the data that you're working with. So types can be computed from or depend on other bits of data.

So the classic introductory example of this is,  imagine you have a list and then you can make that more precise by saying, okay, I have a list where all of the elements of the list are the same type. And then I can make that even more precise by saying, I have a list where all the elements of the say are of the same type. And it has specific lengths. So lists with length is the example of calculating the type from a number being the length but that's the essence of it. The fact that types become first-class and you can compute types from values to some extent, vice versa.

## **Introduction to Idris** 

**Adam:** So what is Idris?

**Edwin:** So Idris is a programming language that I've been working on really as a, as a part of my research in programming language design and software correctness. So it's a purely functional programming language. It takes a lot of its ideas from a Haskell, largely because of I quite like Haskell and it's something I've been using to put into practice a lot of the research ideas that have been coming from all sorts of people over the last, I don't know, 20, 30 years in using programming languages to better express correctness of software. So all these wonderful ideas have come out of various places such as the Cocke- theorem improvers that come out of  France, the axial programming language to come from the group in Charmaz, in Sweden and research dating back to your paramount in nerf in the 70s.

And I think that all of this stuff is wonderful and it allows us to be very precise about the programs we want to write and very precise about the data we're working with. But it's not something that mainstream programmers can, pick up and run with. And the one thing I would like to do with Idris and possibly with most likely with success assessments is making these techniques available to practitioners and software developers.

Cause it's cool and I want people to use it.

## **What is a Theorem Prover?** 

**Adam:** What is the theorem prover?

**Edwin:** So when we talk where to start, theorems prover in programming in some very real sense, the same thing. There's something when you write a program, let's say you write a program that we'll stick with functional programming. So you write a program that takes an integer as an input and gives you and ensures an output to just something as simple as that. Then if you can write that program, that is, that program constitutes proof that it's possible to take an int and give you back an int so you can read it as, as the theorem int implies int now that as a theorem is not particularly exciting.

Nevertheless. It is a theorem. It's a fairly trivial theorem. But as you start adding a little bit more precision into your type system, and you start looking at the relationships between what is a type and what is a theorem you start getting rather more interesting properties of your programs.

So if I think of a nice, simple example, I did say. A simple theorem such as if A is true and B is true, then  A is true. Okay. So A and B apply A. So in terms of a program, what are the, so this is just some logical propositions, simple logical proposition in terms of a program. What is that?

Well, it's a proof that it's a program that takes a pair of an A and a B and returns an A, so this would be taking the first projection of a pair, for example. So as you start adding more interesting features into your types, so you start adding even more interesting features into your theorems, such as if you have a type that represents a sorted list and you have another type that represents an unsorted list.

So if you can add that level of precision, then a program that goes from unsorted list to sorted list is with certain extra assumptions and properties added. You've got a function that is guaranteed to be a function that's also a list. So the question is, is that proof or is it a program?

Is it proof that this algorithm sorts of lists or is it a program that does sort a list? And the answer is it's both. So I mean I came into academia from having been a C ++ programmer in the industry for a couple of years.

Yeah, I went to a talk and on theorem proving and decided this would be more fun. And so went into the other directions and started doing the theorem proving and then generating implementations of sorting algorithms from specifications. And started thinking, well, how, what is the relationship between these, the C++ programming that I've been doing?

And the seek this very abstract theorem proving that these people have been teaching me something. Well, there's a very close relationship. So this is people often when people talk about this idea, you'll hear it referred to as the Curry-Howard correspondence. So it's a pretty well-known idea.

It's been known for decades now, but it's not something that people typically think about when the programming, but you very much are using these concepts that the programs are proofs.

## **Is Idris Pacman Complete?**

**Adam:** And when you say that Idris is Pacman complete, I think this is a reference to the fact that these other dependently typed languages don't run or?

**Edwin:** Not so much that. So people ask questions about it. Programming languages, like when it's theory incomplete and you know that's a people are worried about this sort of thing because you know it's your incompleteness means that you can solve all of the interesting covetable problems. But I just don't think theory completeness itself is a very interesting property of a practical programming language.

For example, C++  templates are theory complete, but you probably wouldn't write Pacman using only C++ templates and make files are probably theory complete white space. The programming languages, theory companies, I mean, all these things that have tiering complete, but you couldn't write Pacman in them.

Whereas it's not beyond the realms of possibility that you could take a language that isn't quite a theory complete. That is you can, you can always guarantee that the program terminates in a certain finite time and you could still write Pacmanin it. If you had the graphics libraries and the operating system interface libraries provided that you had a suitable author band on the amount of the time, that program is going to wrap.

I think it's a much more interesting property of a practical programming language that it is that you could write Pacman in it then that you could solve any computable problem in it. What you mean this is opening quite a can of worms Gloss over some of them, some of the details, but seer improvers like Kako actors, generally the ones we talk about in worldly dependent type programming they require programs to be a total, which means that they need to cover all well-typed in pots.

And programs or functions need to produce a non-empty finite prefix of the output in finite time. That is to say, they need to do some useful work in finite time. An, unless you do a few little tricks, this can mean that your language isn't theory complete because a theory, complete programming language, you can't solve the halting problem in general because.

Wealthier. You can't ride the program that says whether any given program with any given input is going to terminate. But in a theory proving, everything has to terminate. So that's that kind of suggests that it can't possibly be theory incomplete. But the question is, what kind of useful things can you do, or rather what useful things can't you do?

And I haven't yet found a useful thing. I can't do a be by disallowing programs looping forever and not producing any output on the way.  I'm not entirely convinced these programs to exist. something that merely makes my machine get off there while it's running is probably not something that's going to be useful to me.

Now it does make some programs a little bit harder to write cause I have to start, I have to, I have to produce some guarantees that this thing is going to produce some output. eventually. On the other hand, the payoff is that I know for certain that this program is going to give me some, a result at some point.

So. I mean, if nothing else it's a useful technique for ruling after silly mistakes. Anyway, all of that is why I think Pacman completeness is more interesting is because, again, I can still ride pack band within these constraints but if you've picked some arbitrary, your incomplete thing, that amazing number of things, I accidentally theory incomplete, but you can't write Pacman in them.

## **Totality in Idris**

**Edwin:** It's quite hard to be accidentally Pacman complete.

**Adam:** So I take by implication, Idris is a total language. Is it always total or?

**Edwin:** It's not always total. So this is one of the all of the decisions that I made quite early on this, that I'm checking that something is total is important because it's a check that allows you to be certain various properties of your program.

And so, I remember early on I was talking about programs and proofs being the same thing.  and while this is true in a theory complete programming language your proofs come under the assumption that your program is also total that all your program produces a result. So all your proof, my intern intake sample, it's only a proof that the, that an intern plies into if this program terminates, if your language is total, then it is proof that and will return it.

So in Idris, it will always check whether something is total. Because if something, if you know something is total the machine tells you that. I am convinced it as total, you can place a lot more trust in it than if it's not total. However, there is this goal of being accessible to the more mainstream software developers and bringing it closer to what people do in practice.

And I think you have to take things a little bit slower if you want people to adopt your ideas.

## **The Concept of Language Strangeness Budget**

**Edwin:** And there's a very nice concept I came across only quite recently that I think it's due to Steve Klabnik, who's very heavily involved in Rust, so he calls it the Language Strangeness Budget.

So if you make a new programming language you have a target audience. So in my case, it was kind of Haskell ML, low camel developers to a lesser extent, scholar developers. So you pick your target audience and then you decide how many things you're going to do. That is away from what they used to.

So how many odd concepts you're going to introduce. And those odd concepts have to have some at least, well, I would say some clear value maybe not an obvious value, but over time,  those concepts become clear and you could only have so many of them. And my feeling at the time was, although I didn't know that under this name, my feeling at the time was that if I were to require totality for totality as a default rather than non-totality as a default, then I would have blown my language training budget many times over. I've got a feeling that first-class types are already spending that stranger's budget and that's enough. That's enough for people to deal with as, as a first step. So I think future versions or future languages that,  hopefully, they will be future languages that are inspired by Idris.

Hopefully, they will take this idea of totality much further than as people get used to the idea so I, I think you know it once the tools are better for detecting where the programs are terminating this, it's going to be just like these days you have the arguments between dynamic typing fans and static typing fans.

Maybe in the future that will have arguments between the total language fans and nontotal language fans, but I like

**Adam:** I like this concept.

**Edwin:** I think it's lovely, explains and explains so much about language design choices.

**Adam:** Although there's a certain amount of, I don't know, disappointing this that's even a word, because like, languages seem to take decades to reach popularity, and if it can only defer two steps in one direction

**Edwin:** Yeah but I think that we're talking here about. Mainstream languages. So if you look in the academic research community, the kinds of languages that are people are coming up with. So if you go to the, one of the academic conferences, like principles of programming languages, say people tend to come up with new languages to demonstrate your point, and they will,  they'll have all the exciting features, linear types or a session types or total programs.

And, and if the best of the very best ideas come out of these languages and then get adopted by mainstream languages. Then as academics, I think we've won, and then the side goes for Idris I mean a, I don't have the resources for Idris to be a mainstream language that's adopted by the world now, but if people were to take the ideas, like even just to totality checking and reporting errors or warnings, if things are not total and people put them in mainstream languages.

## **Dependently Typed Java**

**Edwin:** Scholar or even, you know Java, C++, and then we're winning. So, if you keep an eye on the academic community, there are all sorts of interesting ideas coming out.

**Adam:** So, is it possible to take first-class types and bring them to it to an existing language?

**Edwin:** I don't see why not in principle, there would be all kinds of interesting challenges to get them to interact with the type system as it stands. So, sometimes I see discussions on, I occasionally get tagged on discussions about ascensions to the Rust type system, for example, which would be pretty cool to get a bit dependent types in that.

But the difficulties, I suppose, is to do with a mutation. So how do you make types which are known at compile time? Interact nicely with mutable variables. So something true about value at the start of a function's execution might become not true after things are modified.

So it is, we don't have a problem with that because Idris is a purely functional language and things can't update so you might have to introduce some restrictions on what you can do, but in principle, we've, we've thought about side effects and dependent types. We thought about interaction with the outside world and, and dependent types.

So if we find the right restrictions for the type-level language, then, it's something that could be doable. So what I mean, if Idris being purely functional. It means that it's all about evaluation. So, an Idris program or the when we talk of what it means to be a first-class type, we're only allowing things to evaluate.

We're not allowing things to execute. So to get for a purely functional program to execute in the outside world. You just think of it as an operating system, executing the description of the actions that have been computed by the functional program. So if you start putting or let's say hypothetically, you add first-class types to Java and you start saying, okay, now everything that's a Java program can go into type. Well, at that point, you're able to execute arbitrary IO actions while you're compiling the program, which is ideal. It's probably not a good idea you get it wrong, you get a compile error, you delete your source code, that sort of thing.

So usually you need to be a little bit careful about the restrictions and you need to think carefully about how it interacts with subtyping for example. No, I'm sure it's stable.

**Adam:** I thought you were going to say the reverse, that it wasn't possible that we would need a, a new language.

**Edwin:** So maybe a new language is a better place to experiment with these ideas. So as languages evolve, they do tend to get a very big moment. If you look at C++, now we're even Haskell now it's not clear that everyone is using the same language when they say they're writing a Haskell program.

Well, they're not using the same language when they say they're writing a Haskell program. So, I think it wouldn't make sense to rationalize the ideas into a new system. But of course, if you make a new language, people aren't going to use it cause they're heavily invested until it already exists.

## **Things We Can Learn from Rust**

**Edwin:** So. I don't know. I don't know how to solve that problem. I'm just here to throw out ideas and prototype implementations people run with,

**Adam:** Yeah. It's interesting like you mentioned Rust, which is, which is quite a new language. And they, they've managed to kind of, coalesce a whole community around themselves. And seem to be in the process of rewriting everything a C++ developer would need using Rust. I don't know how they

**Edwin:** I mean, Rust seems to be taking off and  I should get into learning it to be honest. Cause it has all sorts of interesting ideas and that, that I think we could pick up and triumph.

## **Dependent Haskell vs Idris**

**Edwin:** They've got people to adopt it. So I guess part of it is if you have an organization like Mozilla behind it, and you have this flagship system that you're developing, I think that's going to help to some extent. In Idris, we don't have a half that has those resources, but maybe it helps. I don't know.

**Adam:** You mentioned high school I saw a talk by a, I think it's Stephanie Weirich about dependent Haskell. So she did a pretty cool demo with like a RepLib library. It was really neat. But then she showed me, like, I didn't understand how it was written at all but using it was quite cool because you had the types of RepLib, they're kind of at a compile-time but my question is, so why, why do we need Idris?

**Edwin:** I think it comes back to this point about languages evolving and getting bigger and bigger over time. It's good to rationalize these extensions. So it's their one single extension or the small number of extensions that could capture all of the ideas that are in the many, many extensions that Haskell has now. I think it's fantastic that all of these things are coming in to ask, cause it's brilliant. I mean, it, it sends a funny to be to, to call Haskell a wider mainstream audience by, yes, from where I'm sitting it is. So the fact that these ideas that we talk about it, in the full dependent types world are.

Being increasingly adopted by people but not only in Haskell but in scarless thanks to the work of people like Miles Simon. So people, people assigned to see what we're doing in a context that they can use in their day to day life. So that's brilliant. But as the question of why do we need this, I mean, we, it's, I think it's always good to experiment with new ideas without the constraints of decades of, of, of design decisions, languages, things that have come before. So if you're to go with Haskell for example, you are going to have to take a lazy evaluation, for example, something that may or may not be a good thing. I'd say that I think that's up to individuals to decide you're going to have to deal with the fact that types and values are distinct things, so you'll, you don't have truly first-class types. There may be plans to improve that, but you, you sort of have to work with the tools you've already got. Whereas if you take a new language, you're free of that.

You can make your own decisions but I think just, just this idea of, of, of Idris is significantly simpler than Haskell. When you take the fact that you've got the first-class types you can do you can do all of the fancy things that can happen in Haskell's type system, and you only have to learn one notation to do it.

So I kind of feel that. If I'm teaching Haskell, which  I do to undergraduate here in St. Andrews. I'm not going to teach them pendant types. I'm going to teach them more than Haskell ‘98, but the modern Haskell without any of the extensions. I will teach them that, but I'm not going to teach them any of the advanced features just because they've got enough to deal with already while they can compare to moving from  Java, which they've done pretty much exclusively so far.

Moving on to Haskell. On the other hand, if I'm teaching Idris, I feel that I can move on to dependent types early. You see this in the book that in the, in, within the first chapter, I give an example of, of computing types and by chapter three we're on to here's a thing that just allows you to compute the length of a list in the type.

And I don't feel like I'm adding anything any new language features to do that. It's just a natural thing that happens if you're able to compute the types. And that's not the case in Haskell, in my opinion.

**Adam:** Yeah, I agree. It's, it's pedagogically kind of much simpler. Like, I don't understand all of these extensions that were turned on to do the dependent Haskell. And I have a feeling that she did,

**Edwin:** She's been heavily involved in creation in which probably helps and that,  I’ve seen some of her talks and that sort of fantastic stuff that they're doing that so. So, yeah, I mean, it's great to see, but  I think at some point that the, I would say needs to be a new language, which is not necessarily Idris what probably not Idris, but some new language that takes these ideas.

## **Interactive Editing in Idris**

**Edwin:** It brings them all together and, and has enough people behind it that it, that it can become,  robust and production-ready. But we'll see. 

**Adam:** One of my favorite things from this book is the interactive editing. So that's something new to me. I wonder if you could describe it.

**Edwin:** Right. So this is if you use IDs for, which,  many people do, particularly if you're using.

A statically typed language. You're kind of used to the idea that writing a program is not just a case of you type a load of stuff and then you feed it to, to,  the Oracle and it says, you know what, it says, It tells you why your program doesn't work.

 but if you're using an IDE, it's, it's not just writing a program and feeding it to the system. You've got this interaction by giving suggestions for completing method names. And so on. So if you have a precise type system that gives the machine more to work with, the machine should be able to help you write your program a lot more than if you just have a fairly simple type system.

So, I think this is a much more interesting thing about types, than what people often say, which is about correctness and refactoring. So people always come up with this argument that if you have a static type language you can be more confident that you've done the right thing and they will be fewer bugs.

While I think in practice, we don't tend to see that because unit testing is a very useful thing. So far more interesting to me is this idea of interactive editing. The fact that you can use what you've said about the program to help you end up at the right program with the machine’s help. So the idea is right, the type first, ask the machine to give you a small candidate definition that matches that type. And then just refine the program, get a few more details into the program according to what the machine might be suggesting. So, to pick an example, we always go back to vectors. Let's say you're writing a program to let's say you've got two vectors of the same length.

Two vectors, of integers of the same length, and you want to add the corresponding values in each factor so what do you do? You say, okay, what?  well, if, if both of the vectors are empty, then the result is empty. If both of the vectors have a head element and the tail, then I will add the corresponding head elements and I will add together everything in the tape, and there are no other cases. So the types tell me that they can not possibly be any other cases. So what I'll do is I'll write the type, vect <int> N to vect <int> N to vect <int> N so the output is vect <int> N. And then I will say to the machine, tell me all of the possible values of the first input.

And somehow this seems odd to describe in words rather than on a screen. Then we will persist so so I say to the machine, tell me all of the things that first input can have, and it will split the definition. Give me two possibilities. Then I will say for one of those two possibilities, I will say.

Tell me all of the values that this could have. So we're in the first case where the first input is empty, I will say, tell me all of the possibilities for the second int. And it will tell me only the empty input is possible. So already I've got something out of the interactive editing here and I have something at the types.

So I haven't had to write any of this definition other than saying to the machine. I'll tell the machine the steps we're going to take and the machine will tell me what the program looks like. Then even then I can go a little bit further and it'll say,  what is, what is the output?

If both of the inputs are empty and it will tell me, well, the output you're looking for must be a vector of length 0. There is only one vector length 0. So I say to the machine, you tell me what the output will be and it will tell me so that you get more commands to bite by having a bit more information to type, you get more commands for interacting with the machine.

So, so not just things like telling me what functions or what methods work with these input types, but tell me exactly what. What, what values can this input be? Which, which values are ruled out?  what values can the app, but they just search for the output for me? So, it becomes much more of an interaction.

It becomes much more of a conversation with the machine than programming. Typically is. And, and I think really in the end if we're going to be if we're going to write programs that work. It needs to be an interactive process. It needs to be a conversation.

It's almost, to some extent, pair programming with the machine as your pair rather than just riding the program on your own. No, that's sad. But we've only just scratched the surface of what's possible here. So as types get more complicated, we have some engineering needs to be done.

So the Idris as it stands just gets a bit too slow once you have, once you have much larger programs it's still useful, but,  you tend to be waiting a few seconds for the reply rather than, rather than getting the reply instantly. So I think we've there's a lot of work we need to do here, but if we start thinking about what, what, how can we get machines to support it.

Type driven development that goes way beyond what IDs can currently do. I think that's an interesting topic to explore, which do a lot more deeply the probably the key concepts, then I think all languages can adopt, or at least all types or statically typed language can adopt.

There's this concept of a-holes. So a hole is a part of a program that you haven't written yet, but that is nevertheless syntactically valid. So it's an address. You would mark that as a question mark something. So it's a question mark. Then names are question marks, and then I can ask the machine, what is the type of food and it will tell me what's available and what type needs to go there.

So, I might have some fairly complex program with some tricky manipulation to do. And I'm in the middle of a definition and I just need to know the types of all the variables that I need to know the types that go in that hole. And if the machine can tell me that, then that helps with development.

Because I very rarely have a program that. It doesn't compile as a result of this. It's like, instead of, instead of writing,  coming up with some plausible but wrong implementation. What I typically do is write as much as the implementation, as I'm sure I understand and leave a hole for the rest is basically to say to the machine over to you telling you, give me more information.

And. It almost gets to a point where, people say type errors are really difficult to understand if you have a fancy type system, and you know it's not quite true, but you can almost say what type errors? I don't get type errors because, because I write the part of the program, I understand. And I asked the machine to tell me what I need.

## **Type Driven Development**

**Edwin:** So rather than giving the program to the machine and the machine says your problem, let's say to the machine, tell me what I need here to be right. Sorry. It's of course, it's not true to say what type of errors in practice, but you do tend to find it type areas aren't.  they're not, they don't come up so often when you ha, you don't spend so much time scratching your head over them when you can just replace the wrong bit of a program with a hole and see what the machine's expectation.

**Adam:** I think yeah. It's odd to talk about just an audio form, but yeah, you've really. Turns the development model inside out, right? So rather than, writing a program and then trying to see, Oh, well, what type should this return? The method here is,  write out the type, use the sort of built-in features to have this expanded and so you sort of, I guess that's the title, right? That's why it's like Idris's development. And I'm assuming that's also. That's also why it says with Idris rather than using Idris, I'm guessing, right?

**Edwin:** Because well, yeah, I mean, it was originally intended as, as just a book on address, and then it was like, okay if, if we're trying to sell this as a mainstream publisher, nobody's heard of Idris.

So what are, what do we do to sort of bringing out the details for a wider audience? So it was, the focus in the end became. I mean, even though we'd call does a book about there's a lot more of the process ha how you arrive at the program, not just how you write the program.

So that's kind of why the book is full of all of these steps of type, define, refine, start with the programs. Here are all the intermediate steps. There's kind of a tricky thing to do in writing rather than animation.  Nevertheless, that is the key idea. Well, you can follow the ideas in other languages too. That's, the tools aren't a vast much, but I hope they will be.

**Adam:** And the concept of the whole a, if I can just describe it a little bit so I could write a Java program and whenever I don't quite know what goes here. I could write, throws new, not implemented exception and the program will compile so in a way that's kind of like a hole, except the holes.

**Edwin:** The difference is that it's a runtime failure rather than compile-time information. So you wouldn't get the information about what type, what type needs to go in that hole you would be able to run a partially written program.

Which is of course useful. I do it all the time I mean, I compile and run programs with holes all the time and just, accept it. The hole is going to crash. Fine but yeah, it's really about getting the information at compile time. It's like the compiler knows this information. Your Java compiler knows exactly what needs to go there because it has to know that it is checking.

So it's like, why is it keeping the information to itself? This is like an obstructive coworker that doesn't want you to get you, get your program written.

It's, it just, I mean, I have, I haven't done much development with IDs in Java lately. So for all I know, this is, this is something that IDs do if they don't, then they should, uh.

**Adam:** Yeah, it's certainly not as well as, like Idris, as interest does it, which is interesting  I feel like the tooling just using the examples in the book and the tooling and it's quite a process. Like I found even like maybe the example doesn't have to be Java, but if, if I was writing Haskell and I just put in. Like undefined, like the type, all get-go will say like it's, it's bottom or something. It won't.

**Edwin:** Yeah.

**Adam:** At least the last time.

**Edwin:** Haskell, the latest versions of Haskell. So exactly. When this came in a couple of years ago. Anyway, so you can now put an underscore in a program. And it will tell you all of the information it has about that hole, so it will give you a compile error, but it's a compiler that says, okay, this is what you have, this is what you need.

So it's, it's, they call them to type holes, I think and that's, that's pretty much the same concept. It doesn't have the editing, but it's telling you all the information that has so useful there. 

**Adam:** This concept is kind of working its way. 

**Edwin:** sure. Yeah. Um.

**Edwin:** Yeah, it's an idea that I have the impression it'san idea that people like, and I mean, it's, it's certainly not an idea.

I came up with it. It's an idea that's been around for quite some time, particularly in the theorem proving a community. So if you're working through, if you're doing a proof in Cocke, for example, or any of the. The earliest systems you're developing the proof interactively and you have holes in the proofs that you're filling in just by learning more information about the program.

So it's, it's I guess this is one of the ideas that's coming out of this improving background but is useful for programming too.

## **Expression Search**

**Adam:** Makes sense. Yeah. To me,  it seems like magic, but it makes a lot of sense. So the expression search, you have an example in the book where I think you do insertion sort. And I don't think you write anything. It almost seems like you write the type and then

**Edwin:** You're not quite giving enough information about the program. So if I remember rightly, the example in the book is a, is an insertion, so on vectors. So then, what you’re getting is the right length, but you have to put a little bit in yourself to get the things in the right order. But the one there is one in the book, which is transposing a matrix so I can end by him vector to M by N vector, and there's very little that you have to write there. So you kind of have to know roughly overall what you need to do.

But I mean, genuinely, when I was coming up with that example, I was thinking, how on earth do you transpose a vector? This is a classic example of this. How on earth do you do it? And then, in the end, I just thought, why don't I ask the computer? Why am I even thinking about this?

Let's ask the machine to do it. And I pretty much eat at each step tells you what to do. But I could eat it. The interest expression searches are embarrassingly simple, and there are much more sophisticated systems. So so as a, as another dependent decide programming language so I think it's more, more aim towards the theorem improving sides and the programming, but it's still a programming language.

There's a tool, a thought of that called ante which can. Which goes way further. It tells you more about pattern matching as well as the expression search. So there's, there's a lot more we can do I'm willing to Idris does, is it just does a brute force search for the first thing it finds that matches to type.

And if you give enough information, it's, it's almost embarrassingly  good how well it does give them how much or how little effort has gone into it

**Adam:** In the book, you go through an example of printf. So is printf required dependent types to be done?

**Edwin:** So point is, it's almost the first example of a dependent type program that a lot of people see. You learn how to print something out and see, then you say, okay, well, the types of the arguments to printf depend on the string. That's the first argument to printf so they're computed at compile time. A-C compiler will tell you if you've got it wrong which is interesting cause a printf is, is not as far as I'm aware, part of the C language standard.

So, so the only way you could do that, I see not being a dependent type language, this is something that has to be hardcoded into the compiler. So, the reason I picked that example is just cause it's a fairly meaty example, of what it means to do a calculation of types of compile time.

And it's an example that's familiar to a lot of programmers, at least people who have some kind of C background and it's nice to see how you can extend it with,  different types, for example. So it's something that allows you to see what's going on in a, in a concept. You understand

**Adam:** The dependent part is that based on the format string than the type the of the next parameters change.

**Edwin:** Right? Exactly. Yes. You calculate the input type from the format string and you calculate the output type from basically the rest of the format string. And as soon as the format string is empty, the output type is just string.

**Adam:** So we go through this example in interest in both ends like the first thing that comes to my mind, of course, cause in the interest example,  these secondary parameters are calculated based on the first input but at compilation, so, how does this work? If I'm feeding it a format string,

**Edwin:** Essentially what's happening here at compile time is it's checking with the information it has and at runtime, it doesn't have that information.

So this is, this is the basis of the problem and the question. So basically what it means is if you want it to compile based on a runtime format string. You're going to have to check that format string at run time and the only way it's going to compile is if the machine is convinced that you have checked the format string to get the right input.

So if you imagine you're doing this in C, what would you do if you are doing the same thing in a string? Well, the user types in a format string. What do you expect the next arguments to printf to be in your program? I think you're struggling to get that right. So if, if you're allowing the user to type in what the form of the data is, you're going to have to check that data before you, before you make any progress in the program.

So it's almost going to be like if you've maybe in, C, maybe you would do some check that says that pauses is the format string at runtime and says, okay, if I have %S %D in that order and nothing else, then you're allowed to call this version of printers. So you, I mean, I don't know exactly how you do it.

But you'd have to do something similar in this program, but it would be checked at compile time that you had done the appropriate run-time checks so just to, I mean, there is a simpler version of this that's easier to think about, but it would scale up into, which is an example of a fairly contrived example.

But back to vectors again. So reading in. Well, I'll tell you this vector of numbers example again, why not? Because we've already talked about that.  let, let's say where we're reading in two vectors of numbers from the user and we're feeding it to our carefully designed and guaranteed vectors. The input factors are the same length addition function.

So we ask the user to enter one vector than another. Do we assume that those vectors are the same length? Well, we can't, users are not motive for typing in the input that we need them to have. So the only way the machine is going to let me call the vector addition function is if I've checked that the inputs are the same length, and if they're not the same length, maybe I've, I modify them somehow to become the same length.

So this, by having more precise types, we're not well, not freeing the program or from having to do run-time checks, but we are freeing the programming from having to do unnecessary runtime checks. And we are telling the programmer exactly where those run-time checks have to be. So if I read a vector that's going to be a vector of some length, and if I read it in another vector, that's going to be a vector of some lengths M so the next thing I have to do is check that N equals M.

So I just saw the compiler is going to complain if I don't do that check. This sort of thing has really important implications, particularly if you're interested in security. So if you're taking some arbitrary unchecked input from a user and you have a reasonably precise type that says.

I know this input is safe, provided I can get it to match this type. So, you know I can't think of an example off the top of my head.  But the info has to take a particular form and I've written a, a function that only accepts the type that makes you have an exact date, exact form. But the input I've read is a string and there's no way I'm going to be able to run my function.

Unless I can convince myself that the string I've read in is legitimate. So of course, this is something that we should be doing anyway. If you're writing any kind of security-sensitive program, every program is security-sensitive these days, isn't it? So if you're got any kind of program you need to be checking that string, you need to be checking that it's the exact form that your function is going to take and, and just, you don't just assume that the things are going to work out.

But if your types aren't by precise enough, then it might be the. Well, you don't make those assumptions, but there's something you forgot about. The print example is, it's kind of a tricky one, and you probably wouldn't be taking runtime strings, but in the situations where you are taking runtime strings, you need to have a check.

That would have been the short answer. You need to check at runtime. That's all it is.

**Adam:** Well, I think that yeah, my bad, bad example and an interesting one would be so, and I think it's in your book, is if you have a just a vector of four elements and you're like the user provides a number.

**Edwin:** Yeah, so one of them is, one way of doing it is to say to the user, no, I, I'm going to make you provide those number and another way, it's like she's got over a network and you've got no guarantee that's going to be intact so that then another way of doing it is to say, well, well, we'll take whatever they use it gives us, but we're going to make sure that it's right. So yeah,

**Adam:** It was interesting to me to seem like there's a finite, finite type of integers. So you could have an interesting class that constraints to the possible values of the,

**Edwin:** Yeah. So this is. Yeah. Not numbers find likely abandoned by some upper limit. So the natural example for this would be an array lockup. So it's, you're getting compiled time checks on the band for the array.

So again, this is something where a user might type in something that's out of bands. You can only call the function. It's in bands. So the machine is going to tell you, by the way, you need to do a check here. So I think this is, this is one of the things that the people get annoyed about with types and they're annoyed about with,  I, I have to do these checks, but I want to try the program without doing these checks.

I want to just do some exploratory programming. So I think when, when it comes to the type-driven interactive editing, this is something that we have to think about. Can we either make it so easy to put these checks in that there's no Idris for not doing it? Or can we make it easy for people to just sort of?

Incrementally arrive at, a program that does the right thing. Just leaving a hole for, for what you haven't done the necessary checks. So that is where we can go a lot better with the tooling. Can I help exploratory programming by having better tooling for exploring?

**Adam:** Because the concept of the compiler will force the developer to validate all of the inputs that come in from the user. Like, that is a great concept you're saying the problem is getting to that final program cause in the middle step, you don't want to have to already ever written all the valves.

**Edwin:** This is what I do not talk about. I mean I, I write programs where I kind of, I know the happy path or I've got a rough idea of what the happy path is.

I'll code the happy path, but I'll just leave a load of holes for the error checking. And I will test the program out within, but that I know is okay and it will be fine. And then I'll test it out within, but if it’s ok and it'll go into one of my holes and it will crash and it'll tell me which hole it went to.

So I'll fill that hole in. So I find this quite a nice way of working to, to just write in there, be able to write in complete programs and just how's the compiler, build them. And I could still test them even though they're not finished. But I have, I have a machine to tell me which bits I need to do to make my program robust.

So it's a. I mean maybe that could be improved tooling that allows us to hide bits of the breast, almost like programming with text as the problem here factor, the fact that programming language is fundamentally still text-based things means the sort of things we might want to do as perfectly reasonable things while developing just hide bits of programs. Things we aren't able to do quite yet.

But to be honest, that's the next thing I want to work on is making this process of interactive editing and just nicer.  Sort of my dream is to have a, like a, maybe a tablet app or something like that where, where, I program essentially by waving hands around on the screen.

So I write the types and then I fill in the program by waving, waving my hands around, pulling in bits of programs from different sources. But I know that's some way off. 

**Adam:** Well that would be a, a hell of a demo.

**Edwin:** Yeah. Well, we'll see. Well, I don't, I haven't, I don't even know where it's not a tablet programming yet.

I think I'll need help with that one. Yes. That's a that's a dream.

**Adam:** Yeah. I mean, I've liked the keyboard. I don't know if text.  I've heard this comment before, like why do we just have files with texts when, when programs are so much more structured than that? But I think it's a good lowest common denominator.

**Edwin:** It's always going to be text in the end, but ways of interacting with this, as I say, it's always going to be tested in the end. It's probably not always going to be texted in the end, but that's just the limitations of my imagination but having. Having better ways of interacting with it, even if it is still texts, I think is important.

So it's what are the limitations of, of the text editors? We have back. It only interviews if you're using pretty much any modern text editor. It's, it's, it's, it's amazing what you can do with them just by, by, I mean, the Athan mode for, for Idris, it's, it's essentially it's talking to an Idrisprocess in the background so we can get it to do anything as long as, as long as we can explain it to Idris as part of a, just a text command.

So there are all sorts of stone for interesting new ways of editing programs I think I did,

**Edwin:** I was just going to say that if you start, I'm imagining new things like writing a program, writing a monomorphic program, but there is a polymorphic version of, it that may be already in the library.

I just sort of imagined writing that program in the interactive type-driven mode. And then the machine says. Oh, by the way, you've already written this program. It's called a map, or it's called zip. I just, once you start imagining what you can do if the machine knows more about your program, I think there are all sorts of the cool stuff we could be doing in there.

**Adam:** Yeah. I think like a linter kind of can do that sometimes. Say like, Hey, it seems like you're using Map but yeah, it's not  maybe it is interactive with the right

**Edwin:** Extend. So, linting tools can do this as all sorts of tools that can detect this, but I reckon it should be something that the machine can spot itself. You shouldn't need to code up these specific examples of higher-order functions by the way, again, that's a dream world, but it would be nice to have.

## **Quick Answers**

**Adam:** Okay. So I have a bunch of a yes or no questions that are maybe a little bit silly that I'm going to hit you. You can say yes or no, or you can refuse to answer or expand. So. Does Idris compile to PHP?

**Edwin:** Yes and no in that you can generate PHP for co-Idris, programs, but it only does the absolute basics so I did that back end as a bet, as you do. It in principle, yes, but don't use it.

**Adam:** Haskell, having two colons for a type annotation is a mistake?

**Edwin:**  It was historically the right choice at the time.

I don't think people necessarily know why it has two columns instead of one so as far as I know, the reason is that it came out of the evolved in various ways from another language, Miranda. So by David Turner and that had type inference and David Turner, his idea was that he would be writing a lot more, list than he would be writing types, therefore, single colon for lists or single colon for types.

What do you pick? The one that you pick the shortest thing for the thing you do more. So completely sensible because single colon for lists, well, in Idris, I think I'm writing a lot more types than the list, so it's the other way around but anyways, that, as far as I'm aware, that was the reason for the single colon.

That was a completely sensible thing too. But that doesn't mean we should. Keep the decision because it was the sensible thing to do in 1980

**Adam:** Having a programming language with lazy evaluation by default is a mistake? 

**Edwin:** No, true or false. Yes, there are pros. I'm not, I'm doing nothing. Violent, yes or no here so there are lots of arguments in favor of lady evaluation.

There are lots of arguments in favor of strict evaluation.  I like both I would like a language that could read my mind as to what I wanted and when, but that's even more of a dream than the other things. So, I mean, I, I picked a strict for Idris just cause a while ago I'd implemented a lazy language and I wanted to implement strict one this time that was the real reason there's a better reason, which has come up later, which is a. I want a type to precisely say what the data is at runtime. So if, if the type is int, I want the representation of that to be an int. I don't necessarily want it to be a bit pattern that represents an int.

So, that's why I argue for strict now, but, both, they both got married.

**Adam:** Hmm. What do you mean by a pattern that matches it?

**Edwin:** Yeah, so uh. If you see like in C, for example, if you see the data type int, you know that the, if you look at those bits and you interpret them, you will get the number that is represented by that.

Int in Haskell, what you will get is a pointer to a computation that will get you an int. It might be, it might be an int, or it might be a function that will calculate an int. And I'm just thinking now that if, if I do want the times to be precise, then if it's an int, if the type says it's an int, it should be an int.

If it's a computation that calculates an int, the type would say to computation the calculating int. So that's why an interest we call lazy int. So we've got this lazy type. That is merely true for Idris. That's not, that's not something that I believe to be universally true. It is merely the decision that we've taken for Idris.

So I don't think there is a universally right answer, too lazy or strict. They're both useful in their settings. So yeah, I realize,  this is going out on the internet and therefore I should be controversial, but I'm not going to, it's, it's more, it's more complicated.

**Adam:** All right. Here's a controversial one that I saw from one of your talks, Americans are spelling colors.

**Edwin:**  Oh, I just do that to keep it's very sad to me that just one of the final things that happened with the book before going to print is that they changed it into the Haskel style and they broke all my spelling but I've, I, whatever. It doesn't matter, does it?

 but in, in, in the source code for Idris spell color with the U and, and we spell normalize with an S and, and all of that, however, there are some things does one of the colors, whether U or without U is also not one of them, but it keeps us busy on the internet. So there you go.

**Adam:** Well, I want to be conscious of your time, Edwin. it's been great to talk to you about interests and the book, and thank you so much for taking the time to talk with me.

**Edwin:** Great. Well, thank you for having me.
