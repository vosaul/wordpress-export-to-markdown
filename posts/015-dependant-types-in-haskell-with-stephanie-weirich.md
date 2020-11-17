---
title: "Dependant Haskell"
date: "2020-08-07"
---

At Strange Loop 2017, I wandered into a talk where I saw some code that deeply surprised me. The code could have been python if you squinted, passing dictionaries around, no type annotations anywhere.

Yet, key lookup in the dictionary was validated at compile time. It was a compile-time error to access elements that didn’t exist. Also, the dictionary was heterogeneous, the elements had different types, and it was all inferred and validated at compile time.

What I was seeing was Dependent types in Haskell. In today’s interview, Stephanie Weirich explains her efforts to add dependent types to Haskell and how that example worked.

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/6632816/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

### **Transcript**

_This is a machine-translated transcript. Podcast page for [this episode is here](https://corecursive.com/015-dependant-types-in-haskell-with-stephanie-weirich_)_

### **Introduction**

**Adam:** Welcome to CoRecursive, where we bring you discussions with thought leaders in the world of software development. I am Adam, your host.

**Stephanie:** Now, you called it magic, I call it programming.

**Adam:** That's strangely 2017 I wandered into a talk where I saw some code that deeply surprised me. The code could have been Python. If you squinted it was passing dictionaries around, no type annotation anywhere yet the key lookup in the dictionary, it was validated at compile time. 

It was a compile-time error to access elements that didn't exist. Also, the dictionary was heterogeneous. The elements had different types, and it was all inferred at compile time. What I was seeing was dependent types in Haskell. In today's interview, I tried to understand what was happening in that talk.

Stephanie Weirich is a professor at the University of Pennsylvania and works on extending the type system of GHC among many other things. 

**Adam:** Stephanie, welcome. Thank you for talking to me

**Stephanie:** Thank you for inviting me. I'm happy to be here.

## What are Dependent Types?

**Adam:** I saw a talk that you did a Strange Loop, I think last year and it kind of blew my mind. and, and it was about kind of extending the type system of Haskell to support dependent types. So, what are the dependent types?

**Stephanie:** That's a tricky question and it's a tricky question because there are lots of answers to that question. I, in some way, I created that talk just to answer that question because there are lots of definitions of what dependent types are, and those definitions can be technical where they classify some things as definitely being dependent types and some things are definitely not being the dependent types based on mechanism. But I prefer to think more about applications -- can you get your language and your type system in your language to do particular applications and use that kind of definition?

So in that talk, I walked through how Haskell, even though under some of the technical definitions, doesn't have dependent types yet. I walked through how it could already do quite a number of the activities that we want from dependent types and at the end kind of pointed out what still needs to go into Haskell to make it a full spectrum dependently typed language. Now that's, I guess that's not really asking, answering your question about what dependent types are but just to briefly summarize, dependent types are a way of having some kind of computation in your type system so you can use your types to express the main specific invariants about your program that the type checker uses to check your code, there's a lot of the inspiration that I get for extensions for Haskell's type system comes from Martin Lof Type Theory. So, this is a specific mathematical formalism that is used in the foundations of logic to create formal systems to describe what is provable and what is true.

**Adam:** I did an interview with Edwin Brady, who created Idris and he said he likes this term, I'm not sure if it just applied to Idris or in general, but he likes the term first-class types. He said you can think of dependent types as just like a programming language where you can manipulate types just like their values. How do you feel about that?

**Stephanie:** That captures quite a bit of what you get from dependently type languages. And this is one of my goals and Haskell is, it's very similar to what Idris provides, giving you, and this is what I mean, a bit in having your type system be as programmable as the rest of the language this lets you, again, let's you express why you think, your program has particular properties using the same language that you do to implement your system. So your logic and your programming languages have a really nice uniformity to them.

**Adam:** So, what makes dependent types useful?

## **What Makes Dependent Types Useful?**

**Stephanie:** So there are many levels to answer that question, right? Of course, type checking is useful because we want to use it to both identify bugs in our programs, but also to capture some structure while we are programming to be able to think about our programs, both in terms of what they do at run time, but also at a more abstract level.

What do we know is always true about our code versus what is true at this particular moment or what is true about this entire class of values versus, what is true about this particular value? So type systems naturally give us this form of abstraction and without dependent types, this kind of abstraction is limited in that you can only talk about it at the abstract level. You can't really go back and forth between, at this point, I kind of know this, but, I depend, but what I get from dependent types is the ability to be able to say, "based on this run time test, I know this about my, I know this about my compile-time value" So it lets you kind of gives you much more flexibility about the interaction between sort of your context-sensitive tests and what your type checker knows at compile time.

**Adam:** So I find that it is a tricky subject to grasp, the advantages, but you had this example that I really liked, so it was regular expressions, right? Could you describe the example you had of using dependent types?

## **Dependently Typed Regex**

**Stephanie:** Sure, so I use this example in the Strange Loop talk because I really could have captured what dependent types can give you in lots of different ways. So in the example, the nice thing about our regular expression is that most of the time you use very concrete, regular expressions, right? We're trying to, and I was using the example not just for matching regular expressions, but for doing something that's called Capture Groups, where you could take a regular expression and name specific parts of it and pull out parts of the texts, like a very primitive form of parsing and if you have a concrete, regular expression, you should be able to look at that regular expression and know exactly, what parts of the regular expression are gonna get captured, how many groups are going to get captured? Regular expressions allow you to name those groups. So what are the names of the subparts of the regular expression that can form a capture group and also because regular expressions allow you to alternate or have optional components, sometimes the capture groups will definitely give you an answer, and sometimes they might give you an optional answer, and sometimes they might give you several different answers, like for example if you're under the star and the type of the capture group might depend on where it appears inside that regular expression.

So in the Strange Loop talk, I go over designing a library for regular expression capture groups where the type checker can look at the regular expression and figure out what kind of result you're going to get from that particular regular expression. So when you get them, it's essentially a dictionary, but that dictionary sometimes it's going to match the name of a capture group to a string. Sometimes it's going to match it to an optional value. Sometimes it's going to match it to a list, but we know this at compile time. And so the type checker should help you, use this correctly because all the information is there when you type check your program.

**Adam:** I think it makes a lot of sense, but it's not something I've thought about before. So if you have a regular expression string and it has, like if it has something that ends in a question mark. Then that means that you may or may not get value. So if the type system could get hold of that information, it could be a maybe or an option, or if you have a few of a star then you might be matching actually maybe a star. If you have a capture group of the star, then you could get multiple matches, I guess. Right? So this information is embedded in this string, but it's without dependent types, you're not getting it in the type system, right?

**Stephanie:** Exactly. And the connection between how you interpret that string to, what the types of the system should think about that's not something, any language like should have built-in. This is something that the irregular expression library should be able to express via some kind of programming. This is, should be part of the design of the library that supports these regular expressions.

**Adam:** And so, the thing that really blew my mind, I guess. So, I take this regular expression. Your example was a matching, like Unix paths, so, you give it a path and, there could be multiple, like sub-directories and then a file name and an extension and you were giving these names, so you can get back, a match for the directories, a match for the base name and a match for the extension. You run your regex and you get back this dictionary and then you show. I think part of the magic is, you see, so you call into the dictionary, you say, get me the base name, and it comes back, but then you try to get back some other elements from the dictionary that wasn't part of your capture group and it's a compile-time exception. And I think that that's kind of when the light bulb went off for me, I was like there's something magic here well because I know that. I mean, that's not how I expect dictionaries to work, I guess and I know there's a whole class of languages where they spend a whole bunch of time throwing dictionaries around, and it's hard to validate, say, like in JavaScript, if you access some elements in this dictionary, and then it's like a runtime error if you make a spelling mistake, and pushing all that system, to the compiler, I guess. So how does this work?

## **Dictionaries**

**Stephanie:** And I think that's kinda what I like about the example is that it very much does relate to dictionaries and kind of shows you that even in Javascript and a lot of these dynamic languages, right? Parts of our dictionary when we create it are very dynamic, right? We don't know at compile-time, as like when I say compile time, I mean we don't know so much development time what we're going to get, but maybe, maybe we do. And if we do, we should be able to tell that to our compiler so that the compiler can help us out. Because once we've created this, this dictionary, if we know what its structural compile time, we should be able to have the compiler help us out, help us use it correctly.

Now, you called it magic, and I call it programming, right? So the talk kind of walks through how it works step by step, but sort of the, like, some of the key ideas are constructing the regular expressions with types that are rich enough to calculate and express what the capture groups are so that when you construct the regular expression, you know, just from its type, how those capture groups interact with each other, but the types themselves, they're a little more expressive than we usually see in programming languages because of the types of the regular expression operators like, for example, concatenation, where you do one regular expression and then another one right after it, right? You're combining two together, the type of that operator says, well, the capture group from this entire regular expression is going to be some merging of the capture groups that we get from the first regular expression and the capture groups that we get from the second regular expression and then we can write that merging as a functional program that takes this compile-time data, the capture group data and combines it together.

**Adam:** The part that's a little confusing about that, I guess is that we're providing a string.

## **Parsing a String to a Type**

**Stephanie:** Yes.

**Adam:** I think in this case, the magic is, I should stop saying the word magic, so we have a regular expression string. And you're saying we're going to turn this into a more, complex type. Now I'm not really familiar in my programming experience with taking a string and turning it into a type.

**Stephanie:** So part of the magic was using a feature of Haskell. And one of the great things about working in Haskell is it's a rich language, so it has a lot to draw on. So I can put many features together. So one of the features I was using was a feature that's called template Haskell, which is a way of doing it's another way of doing compile-time programming in Haskell. So it allows you to take things like a string and just run Haskell code on that string to produce Haskell abstract syntax, which then is type-checked and inserted into your program at that point. And so the very first step of that example was taking the regular expression string and creating a parser for that regular expression string that would replace the string with some regular expression constructors that I had developed from my library. So the parsing part is not so much dependent as being able to use this template Haskell feature.

**Adam:** So you are writing a parser as you would have to do, to write your normal regular expression library. Yes. The trick is, It's being called sort of like a macro at a..

**Stephanie:**..compile time, macro at compile time.

**Adam:** And then, somehow when this dictionary is returned, when I apply a match that the dictionary needs to know, all this type of information so that when I. When I ask for, Oh, I didn't even describe this one. I asked for the directories. Actually, you're coming back as a list because your red X knows that there could be multiple directories just based on its parsing and is, and is returning the type of the match. So how does it know how the dictionary type constraints, in that way?

## **Indexed Types**

**Stephanie:** Yeah. An important feature of dependent type systems is this idea of an indexed type. So this is a data structure that is indexed by some compile-time data and that compile-time data enforces constraints on that data structure. So you can imagine just a simple dictionary. The data structure is an association list where I can say I can map any string to any value, but the constraints might, we might want to say is not any association list association lists where the first association is between this string and this type of value and the second association is between this string and this type of value and there isn't any other anything else? Right? So we can go from a very, very general type arbitrary association list to a very, very specific dictionary type association list that has exactly this form. And the mechanism that we're doing there is the index type that the index on the dictionary constrains what the association list has to look like.

**Adam:** Why is it called an indexed type?

**Stephanie:** This is a terminology that it's adopting from dependent type theory. So if you think about it, you can think about it as the dictionary type is actually a function from its type argument to many, many different types, and the type argument as serving as an index to which particular type you actually mean.

**Adam:** So there is a function that takes a type, like a type of based directory, and then returns a dictionary that has a base directory. Am I on the right track?

**Stephanie:** I'm thinking of it. Is it a slightly different level? Right. So here's a very, very simple, example of an index type. It's very simple, it's indexed by a Boolean value. And if the Boolean is true, then our type is an integer. And if it's false, then our type is a character, right? And so we can have a general type that if we don't know what the Boolean is, we know it's either an integer or a character, but if we do know what the Boolean is, we know precisely which one it is.

**Adam:** I follow. So that is an index type actually I thought that was, type computation where you're taking an argument and computing a type or these related concepts?

**Stephanie:** They are related. what makes it an index type is that we actually are making a decision based on this, static information.

**Adam:** Okay.

**Stephanie:** This is just a distinguished thing like type parameters where we might take one type and give another type, but treat that type argument parametrically like for example, a list data type has a parameter for the elements in the list and so the list type constructor takes types and gives us new types from it. So that is still type that's still a type function, but it's a parametric type function. And so the type theory for working with a parametric type function, it works out fairly differently than if we can actually if the system allows you to make distinctions on what those arguments are.

**Adam:** And so there might be a theme of this interview of me asking you questions. However, a type function is, that's just a function that returns a type as it's output. There we go, so does this relate to a generalized algebraic data types?

## **Generalized Algebraic Data Types**

**Stephanie:** Yes. So the mechanism that we can use for index types and Haskell, so it's a way to so in Haskell you could express a standard Haskell, you have parametric data types, like list. Right? And each constructor treats that type argument to list parametrically. Right. you know, N is going to give you a list of that type and, cons also going to give you a list of whatever the type argument is and there's not that much interaction between your data constructors and that type argument because of this restriction to the parametricity with getting it You can have interaction between your type arguments and your data constructors. So when I get it, a very simple example of a GAT, it might be you have some type that takes in a Boolean, right?

And then this is going back making that earlier example, I gave you a little more precise, right? So our type of, let's call it T, takes in a Boolean as its index, and it has two constructors, one that takes in a char and another that takes in an int. And we know that based on, and we can reflect that in our Boolean to say that if we are using the constructor that takes on a char, we'll say, we don't create just T with an arbitrary Boolean. We'll take it as a T where the Boolean has to be true. And if we're going to do one with the constructor that takes an int, then that's going to force the Boolean to be false. And so what that means is elsewhere in our program, if we have T where we know that index is true, we know exactly what constructor made that value because one of the constructors gives us a type where the Boolean is true and the other constructor gives us a type or the Boolean is false.

And so it wouldn't even type check if we had used the other constructor. We know exactly which constructor we have, so we know exactly what the type of the argument should be. And we know we don't really have to, if we do a case analysis, we know we only ever need to do one brat. We don't have to do that other branch.

**Adam:** This is the, seems like the baby steps into crossing over these, these data and types are no, depending upon each other.

**Stephanie:** Exactly. Right. So this is capturing a connection between what's going on at compile time and what's going on at runtime?

## **Runtime vs Compile Time Data**

**Adam:** So back to this dictionary. We get this dictionary back after I run my regular expression match, and in it, I can look up by, I can say, give me the directories. So I pass this dictionary, the string directories, what's happening at compile time and what runtime? Where are we storing those strings, the lookup keys?

**Stephanie:** Yeah. So one neat thing about this example is because the type system keeps track of all the keys. We don't need to store them at runtime, right? So the way, the example, the way we had implemented that example, For a given regular expression, you knew what all the lookup keys are going to be. And so the type system would sort those keys into alphabetical order so it would know exactly where and the result dictionary, a particular lookup key had to be, right.

So from this particular record, regular expression, Well, like we were getting the directories and the extensions and the file names. So we knew the directories would be the first part of that dictionary. Because D comes before E and comes before F, right? So we don't need to actually go and look at any keys because we know, wherein the data structure we're going to store the values already. So, we're looking at via with this compile-time string and that's taking us to, it's accessing the part of the dictionary right of way.

**Adam:** It's pretty cool. And so not only do we have this dictionary in, which if we try to access it. an element that's not there. No. We get a compile-time exception, but also at runtime, like whatever the overhead of actually using a dictionary is gone because like the dictionary doesn't actually exist at runtime. It's just an array.

## **Dependent Types can be Faster**

**Stephanie:** It is a linked list and we do know where it is, which index in the linked list we want to access at compile time. I'm not quite sure how much enlightening goes on when the compiler when JFC compiles it to know whether it will specialize it to actually go right to that spot or whether you will have to actually go down to that point in the dictionary.

**Adam:** Okay. In a theoretical sense, I mean, dependent types could, in theory, make things faster at runtime because, or is there overhead to having this extra information?

**Stephanie:** So if they're radical sense, we have more information at compile time. So very much the compiler could take advantage of this information to make things faster and there are examples of people using dependent types to speed up their code to eliminate runtime pattern matching that they would have to do because they don't need it. Yeah. Like if you know, a check will always succeed, you can eliminate, the compiler, can eliminate, eliminate that check safely. So I'm thinking of, I don't know if you read Yara and Minsky's blog. He is, CTO of Jane Street and the, so the OCaml language also has GADTs, and about a year or two ago, he wrote a blog article about how they were able to use GADTs too, not just for the safety, but also to speed up part of their code by eliminating these redundant checks.

**Adam:** Oh, well, we're just giving more information so it can be used to optimize?

## **On Not Throwing Away Values**

**Stephanie:** Exactly.

**Adam:** So what happens if I'm throwing away these keys, what happens if I want to print out this dictionary like I want a nice, you know, key = value, key = value = value.

**Stephanie:** Yeah. So we're not throwing them away because the compiler still knows about them when it compiles the program. Right? Do it, the type checker. The key that we have is in the type and for printing. Right. In that part of the strange loop talk, I demonstrated how we could print out these dictionaries, and there I was taking advantage of Haskell's type classes, which are ways that. This is a mechanism Haskell allows you to use compile-time information to insert run-time values the equivalent in Scala I think are implicit arguments where you're using type information to control what argument you supply at run time. In this case, our implicit information is the name of the key, right? That's part of the type. And so, and the runtime information that we're going to insert with the, with the type class is the actual string that we're going to print out.

So, again, like part of a high-level theme is having a lot of flexibility between storing your information and the type at compile-time and having it available to you at run time. And when you're working in an expressive language like Haskell, you can go back and forth very easily where you can use the indices too, kind of capture the connection between the run time and the compile-time data. And you can use type classes to have your compile-time data control, what run time data is inserted by the compiler. and this works together very neatly. So, the programmer doesn't need to add a lot of annotations or a lot of duplications, even though, you know, some parts of the program are at one level and other parts of the program at a different level.

**Adam:** I think you called this double-duty data. That's a little hard to say.

## **Double Duty Data**

**Stephanie:** Yeah, it was kind of a tongue twister. So that's exactly what I mean in terms of having a compile-time view of your program and a run time view of your program, being able to use the same data to capture and variants about your code to med to as indices on your type.

Right. So we know that we have to have this key in our dictionary, so we're gonna. Use that key as part of our index. That's one way we're using that data and another way we're using that data is we need to have it at run time, so we need to use it to control what gets printed when we print out that dictionary and having the flexibility to be able to use that data in both ways is sort of, is what I meant by the double duty nature of it.

**Adam:** One thing. I think that is probably obvious to Haskell programmers, but maybe not others. Like there's no reflection. because I think it seems to me that the different run time versus compile time might break down if you were able to somehow inspect things like you can do in the JVM with reflection. Is that true?

**Stephanie:** It's very related but in perhaps nonobvious ways. Right. So one, and the reason I'm pausing is that one thing that dependent types allow you to do is. To encode a very principled form of reflection into your language. So Haskell actually does have some kind of reflection. It using a library called data.typable.

So this little library allows you to have runtime witnesses to types that usually are erased when you, when you run your Haskell program. So how could this be? Well, it's under. in terms of the type system, it's using several different mechanisms. So it's using type classes to keep track of which types have runtime evidence and which types do not.

And then it's using some of the same mechanisms that we use to implement GADTs to connect that runtime type information to the compile-time types so that as you use it, as you look at that run-time type information, you can do it safely. So, Haskell does have a form of reflection and that form of reflection is actually implemented using the same mechanism.

So instead of reflection getting in the way of dependent types, we have. Dependent types, allowing us to have a very safe form of reflection

## **On Reflection**

**Adam:** And data to a type of bullet. Is that related to like, like generic deriving and

## **Generic Deriving**

**Stephanie:** Generic

**Adam:** Scrap your boilerplate type stuff?

**Stephanie:** So no, that's a different feature. So generic deriving that's also, typable is mainly concerned with, runtime information about types based on their names, right? So whenever you create a data type in Haskell, you have a new name for a type, and the runtime information that it's storing, it doesn't. Remember, like what the structure of that data type definition is, it just remembers I have a type that's called this name and maybe it's applied to these arguments. for generic programming, you need that extra structure information. So generic programming in Haskell, especially generic derive in, it allows you to take the structure of a type and, and. Express, how you might drive particular operations that are dependent on that structure.

So, for example, if you are thinking about a show function for a type, for, for a particular data type, how you, you could. Get kind of far by just saying, well, I know it has these constructors and these constructors take these arguments and I know how to show all the arguments. So to show it, we could have a generic version of the show that just sort of looks at that structure information and figures out how to crawl over that tree and construct a string out of that data type. Right? But in order to do that, you need to know what that structure looks like. You need to know how many constructors there are for each of those constructors, what the arguments to the constructors are.

**Adam:** So, I guess the question that we haven't really touched on is, how are we adding features to Haskell? Haskell exists, but how are you making it dependent or pushing in that direction?

## **Extending GHC**

**Stephanie:** So Haskell is a research language, and so it has been very open to experimentation with new features. So, I have in the past and, and continue to collaborate with the Haskell developers with new ideas for type system features.

So, Haskell, the Glasgow Haskell compiler has the ability to introduce new features protected by language pragmatists. So these language pragmas they Mark, which. Source files adopt new features so that it gives a little bit more flexibility so that we can look at features that are quite, completely backward compatible.

So, to enable a new feature on your Haskell program, you have to specifically ask for it. But in turn, that means that the new feature doesn't have to behave exactly the same on the old source code. So as we're extending the father, we don't have to worry so much about breaking old programs as much as we're providing access to new programs now, of course, as a research project, Haskell has been going for many, many years, so there's quite a number of language features now and, and it can get a little bit ridiculous about. The number of language features that you might want to enable, especially since they are a nice thing about it as they are defined at a very small level of granularity.

This is good for research into programming languages because if we have small. Language features. we can think about how they interact in lots of different combinations as opposed to just throwing in every new feature that we want into one sort of monolithic, you know, enabled a pen of types that does everything.

We can kind of look and see that “Okay, this feature is good for dependent types”, but we also see people using scope type variables just for lots of other applications that perhaps we had not even thought about. And we can tease that apart from the sort of, our initial ideas about how new language features might be used.

## **Interacting Extensions**

**Adam:** Yeah. In your talk, I'll put a link in the show notes. I recall like one of the first slides is basically just entirely full of extensions that you're enabling. And, I mean that begs the question, “How do we do these things not interact negatively? How do we have all these language extensions?” It seems like there's an exponential amount of combinations of them. How do we have them cleanly sitting together? Or are there combinations that are verboten?

**Stephanie:** Usually they don't interact too much. I mean, that's a hard problem in general in language design, right? Generally, when we're looking at languages and we're thinking about new features, we may think about that new feature extended on a small core, but it's very, very difficult to think about how it interacts with every possible other combination.

Now, the compiler does have to answer that question on how do all these language features interact? Because it has to implement every single one of them at the same time. So there is that. But in terms of, “Will this feature interacts with that feature?” It has been the case in some compilers that two different features enabled at the same time could expose a whole in the type system one in this kind of gets me to some a recent research project that I'm looking at, is being able to use proof assistance to do some of the type safety proofs for our programming languages. Right? If you look at, so I'm specifically talking about type system extensions, right? Type system extensions.

We develop them by making a mathematical model of the type system, extending it, extending that model, and improving that. Whatever theorems we want to hold about our language still hold. Usually, its Serum that's called type soundness, that says that if your program type checks, we have captured all the behaviors, your program is not going to crash and we don't do, we do that feature by feature, but we don't typically define a model that has all of the features and I don't want and prove our type system sound for that really big model. And the reason is it's really big. That's a lot of, that's very. Detailed heavy-proof too and it's very easy to kind of miss all the cases. And so what I've been, one line of research that I have is let's do all those proofs in a proof assistant.

## **Proving Type Soundness of Type System Extensions**

So there are tools. So I use one that's called the Coq Proof Assistant that allows you to explain these mathematical models as programs in type theory in a logical system, and then write down a theorem in that system and then use programming to help develop those proofs. And so what that does, the benefit of that is you have the proof is a tint, checking your proofs and then you also, since it's since your proofs are kind of developed programmatically, you can automate a lot of the sort of boilerplate aspects of your proof. And I think that's going to allow us to look at our features and combinations, at a scale that we haven't been able to do in the past.

## **Haskell vs. Coq**

**Adam:** Interesting. An interesting thing I just thought of is, Coq is also a caucus dependently type language, right? And so I'm assuming that you kind of admit that maybe Haskell is not, it's not up to the burden of doing this proof within Haskell that the dependent type system isn't as, as feature-rich as, as, a proof assistant because you're going out to another language to prove these. Is that a true,

**Stephanie:** Yeah, so I'm using Coq there. It's definitely. The definite similarity here, right? Because they're both, Coq is an implementation of the dependent type theory that is an inspiration for Haskell's type system, or at least some of the extensions that I've made for it but there's one very big difference between, Coq type theory and Haskell's type theory. And the big difference is that in Coq, there's this in addition to having this type soundness property to know that because things type check, they don't crash. We also have a much stronger property, which says that this type of theory is consistent when we're looking at it as a logic, right?

And this is kind of looking at your programs and in a different way where you're looking at programs as if they were proofs, and then the types are the propositions that they're proving. So a proof on Coq is really saying, here is this type. I'm using the type to talk about something that I think should be true and I know it's true because I'm giving you this proof. But that proof is just a functional program that has that type. and to know things are consistent. Well, you have to be able to know that false propositions don't have proof. So in Coq, there's a, there's a particular proposition, it's just called false and there's no program that can have that type. So we have types that are empty and Haskell. Every single one of the types that we have in Haskell, there are functional programs that have that type. And the reason is we have, we have things like infinite loops in Haskell. You can write an infinite loop and you can give it whatever type you want.

And that 's the reason we can't use Haskell as the logical foundation in the same way that we can use Coq type theory because we don't have the termination analysis and Haskell that Coq does. And the type system hasn't made the decisions that Coq does to ensure this consistency of the language when we view it as logic.

## **Totality Checking**

**Adam:** This relates I think right to a totality, checking like, I know an address you can turn on or off totality checking.

**Stephanie:** Yeah. Yeah. This is exactly what I'm talking about. So an address, when you turn on the totality checking, you can use that part of the program to represent proofs but if you don't have the totality. Checker turned on then the programs that you write in that part of the system can only be interpreted as programs, so you can't treat them as proofs. And Haskell, we don't have a totality checker anywhere, so we can't really use it, in the same way, to encode proofs as we do in Coq dependently typed functional programming languages.

## **Equality Proofs**

**Adam:** No. In your talk, you, you did talk about, writing, I think a quality proof, in Haskell.

**Quality Proofs**

**Stephanie:** So in Haskell, there's actually another language embedded inside of Haskell that is the witness language for quality proofs. And users don't use that explicitly. But that language is manipulated by the Haskell type checker.

And that language actually, it turns out, is consistent. It's as odd as expressive as Coq, dependently typed language, but it has that same consistency property that Coq language has. And, when you're writing Haskell code, you can, you can use the Haskell type checker to encode specific equality proofs that you need to be able to, provide the, to provide the evidence that two types are equal, which is a lot of what you need to do when you're type checking, right?

So when you're type checking code, like the main question that you're asking when your type checking is, is this, you know, is the type of this functional approach. This argument appropriate to the type that this function expects. It's a lot of equality checking questions. And so being able to justify to the type checker why two types are equal, that does require work sometimes and some of the work that you can do is, controlling how these equality proofs are generated.

**Adam:** And to me, like I didn't really understand this, why this would be an important or hard thing until I started working through the interesting book. And as you start exposing this kind of, I guess, data at the type system, things get a little tricky. So like the easiest example that I hit was just like, you have like a vector. You know, and it has the length and code in the type, right? So, then you have a function that adds two vectors, right? And it's like vector N + M. but you want to pass it where it's like a vector-like just the arguments are reversed.

It's very simple to see, like for me, that these are the same, but I have to somehow tell the type system that. The endless m and m +, you know that this equivalence holds

**Stephanie:** Exactly. And that is what I mean, that where I say quality proofs are a very essential part of type checking, right? Because you end up with a lot of questions like this is this expression that I'm using as a type index equal to this other expression that I'm using as a type index. And, the type system itself is going to have a definition of when two things are equal. But that's not going to cover all of the cases when two types are equal.

Just like for example, the type system doesn't define this associativity of addition. This is something it doesn't know intrinsically. It's something that you have to justify to it via some kind of proof.

## **How is Extending GHC?**

**Adam:** So you have worked on a whole lot of extensions to the type system of Haskell. The one that I've actually used is the generalized algebraic data types. So how is it, what's the process of working on that? Was it a challenge? Fun?

**Stephanie:** Certainly fun. Yeah. so. So my role has been mostly on the theory side. So looking at the mathematical models and making sure that things work well with how tight Haskell does type in. And also, Haskell has this, statically typed core language that after type inference, it elaborates to this statically type core language. And that's where we want to make sure that it has this type soundness property. So, my role has been to work with Haskell developers like Simon Peyton Jones, just one of the main developers of the Haskell language, collaborating with him about nailing down precisely what these extensions look like and doing proofs to make sure that they have the properties that they have. And also working with some of my Ph.D. students who also assist him in extending the Glasgow Haskell compiler THC with these new capabilities.

## **Writing Papers About GHC**

**Adam:** And as an academic, how does it work? Like, do you see, so you're writing a paper about some extension? Is the extension written, along with that, after that, before that, the paper discusses it in retrospect?

**Stephanie:** Usually we work on implementation at the same time as we work on the theory, right? Because we want to have a complete view of what's going on with this extension. So the T theory kind of tells us what guarantees we can get from this extension, but it doesn't tell us that the Ascension is actually useful. So for that, it's good to have an implementation where you can try out examples and make sure that there are things that you want to use the extension for actually work.

**Adam:** In terms of usefulness, do you collaborate with the industry at all or, or how do you determine usefulness? Is it purely theoretical or is it looking at code?

## **Industry Usage of Singleton Types**

**Stephanie:** So we look at a lot of code -- a lot. There's a lot of open-source Haskell code out there. And, in particular, so there was a package that I developed with my former Ph.D. student, Richard Eisenberg, who's now an assistant professor at Bryn Mawr College, and we developed one package that's called the singletons package. And it was a way of encoding dependent types and Haskell using GADTs, without having actual dependent types. It was a way for us to kind of judge the youthfulness of dependent types before actually doing the full extension.

## **Dependent Types in Industrial Usage**

And the nice thing is that we can go to the Haskell package repositories and look for. All their packages that depend on this particular library. So we can see what people are using a dependent type like features for in practice. What kinds of code, how are they taking advantage of it? So that might be people in the industry that might be other research projects that are not about dependent types, but they want to take advantage of these Haskell features to do their particular application or it might be people who just want to code up. Interesting problems.

**Adam:** Do you see dependent types filtering out outside of Haskell, outside of this very research type industry into mainstream programming languages?

**Stephanie:** I hope so. I mean, so already things like get it right. So, OCaml also supports GADTs. If you look at Scala, actually Scala has its own mechanisms for encoding dependent types that take advantage of some of the features of Scala that are different from Haskell and Scala type system itself has already had to adopt a little bit of dependent type theory just to describe the interactions between the subtyping and objects and functional programming that happens in Scala.

And I've seen some really rate libraries that take advantage of that, to push that to have more dependent types like features and Scala itself. So, I would love to see more of that in Scala. I would love to see more of that in all sorts of languages with static type systems.

**Adam:** Yeah, I think your example, I mean, chose how it could be quite useful in an interesting way, which is your red X library as a user of it, you don't really need to know much about dependent types. The implementation uses them. Right. But the actual user, they just use it and get this extra feature added.

**Stephanie:** Yeah. And I think that's. Part of that is careful library design, right? Certainly, dependent types are our powerful tool that if, if you're not careful, you can put heavy requirements on your users where they could end up with error messages that are not very obvious about how to fix it or how do you use your library correctly. So just like anything else, thinking about what your interface is and how people will interact with the functionality that you provide is an important part of programming. And I think it's doubly so when you're working with the rich type systems of dependent type theory

**Adam:** I know, yeah. In Scala, like there is the shapeless library, which does a lot of dependently type looking things, if you look at it correctly and, it's quite complex to use. However, it's used all over the place in a number of libraries. And I think that what ends up happening is, it seems like every large Scala project has shapelessly included as some transitive dependency, right? So these features are being used just not just more by library creators than, the day to day users so I think that could be a vision for how this could work.

## **What Are You Working On?**

**Stephanie:** Yeah. I think I think that's completely appropriate, right? I mean, we kind of view programming as this monolithic thing, but it's not, we have many different types of users come into our languages and at many different levels and coming up with, you know, simple interfaces that newcomers can, can jump into to be able to do certain things quickly and easily is an important job that we have. But at the same time, we would need to make sure that we have, the. Powerful features that library designers need to be able to develop, expressive, and efficient libraries.

**Adam:** So we're running a little, we're running out of time. I wanted to ask you. What, what's new and exciting in the world of a programming language theory or type systems?

**Stephanie:** Oh, that's always a hard question.

**Adam:** What, what are you working on? What are you excited about?

**Stephanie:** Okay, so, one thing that I'm working on that's, that's new for me is, at  Penn we're collaborating with some other researchers at Princeton and Yale at MIT on a project that we call the science of deep specification. And the goal of this project is to bring verification that is provided by a system like the Coq Proof Assistant. To software systems at a very large scale, right? Not just proving individual little programs. Correct. But, actually verifying a large part of your system from the hardware to your operating system to the compilers, to the high-level languages that you use. So in my part of it, I am looking at how I can apply the Coq Proof Assistant to verify and reason about the implementation of Haskell itself, or GHC.

Can I use Coq to show that some of the optimizations and some of the transformations in the type system that GHC uses are correct? And we're just starting this out. So we're just starting to be able to model Haskell code inside of Coq so that we can, not just test the Haskell compiler to know that compilation is correct, but also have some much more formal guarantees,

**Adam:** As you were saying before, this may make it easier for future extensions because you'll have this proof to lean on.

**Stephanie:** Yeah. So hopefully this, so have a proof to lean on. And hopefully, this can also be a platform for being able to reason about the combination of the extensions. So not just an individual knowing that an individual extension is a sound with respect to a small core language, but if we have a large proof of the entire system, we can think about how that extension interacts with everything else.

**Adam:** Well. Thank you so much for your time, Stephanie. It's been great to talk to you.

**Stephanie:** Thank you. I've enjoyed it.
