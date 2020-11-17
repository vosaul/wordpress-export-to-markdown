---
title: "Scala at Duolingo with Andre Kenji Horie"
date: "2020-06-07"
---

#### **The Process of Rewriting A Complex System**

To produce a faster and reliable system with fewer bugs and a cleaner codebase, time efficiency may be the biggest factor to consider. Rewriting code can be a necessary process to achieve this.

In this episode, Andre Kenji Horie discusses their motivation, experiences, pain points of rewriting a Duolingo’s engine in Scala.

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/6124029/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

“So I was actually more fascinated that Scala is like a modern language. It has so many nice things that we don't have in Python and Java that kind of outweighs the pain points. “ - Andre Kenji Horie 

“I mean, it's that sort of thing that after working with a Python a lot of time you just become so used to that, that whenever you have something nice, you're like, “Oh, that's nice.” - Andre Kenji Horie 

“There are caveats, it's slower to write a piece of code, but then the amount of effort you have to maintain that code in your test code is a lot lower in Scala, so for me, in the long run, Scala is just a faster language than Python.” - Andre Kenji Horie 

### **Transcript**

**This is a machine-translated transcript. Podcast page for [this episode is here](https://corecursive.com/003-scala-at-duolingo-with-andre-kenji-horie-1/)**

**Adam:** Welcome to CoRecursive, where we bring you discussions with thought leaders in the world of software development. I am Adam, your host.

Duolingo is a language learning platform with over 200 million users. On a daily basis, millions of users receive customized language lessons targeted specifically to them. These lessons are generated by a system called this session generator. Andre Kenji Horie is a senior engineer at Duolingo. He wrote about the process of rewriting the session generator as well as moving from Python to Scala and changing the architecture all at the same time.

In this episode, I talk with him about the reasons for the rewrite, what drove them to move to Scala, and the experience of moving from one technology stack to another. It's a great interview and I think you'll enjoy it. Andrea Kenji Horie is a senior software engineer at Duolingo.

**Andre:** Hello. Welcome for inviting me.

**Adam:** You have great case study about the rewrite work that's been done at Duolingo's book. Before we get into that, I was wondering if you could explain what Duolingo is.

## **Duolingo as a Language** **Learning** **App**

**Andre:** Duolingo is a language learning app.  We have around 200 million users as of today. In the app, people can learn a new language,  by doing exercises and translating sentences from their language, their native form to the language they want you to learn.

And then we have other exercises that practice listening skills and some reading skills and grammar skills.

**Adam:** It tries to make it sort of a game to learn a new language. Is that correct?

**Andre:** Yes, that's correct. And we have all of the gamification mechanisms, such as levels, experience, all of that to make the language learning experience more engaging because when you're learning a language, that's the sort of process that takes people like several years to become fluent in that language, right? So by gamifying it we make it easier for users to, keep learning and keep engaged. So that they can achieve this very long term goal.

**Adam:** How big is the engineering team at Duolingo?

**Andre:** Engineering teams should be around 40 to 50 people.

**Adam:** And how is that organized?

**Andre:** So we have several teams, we have some product teams, which we call product teams. For example, we have the learning team, which is the team that focuses on improving our learning metrics and improving the learning experience to users. We have our growth team, which is concerned with expanding our user base and keeping people engaged and we also have some more for the foundational teams, like for example, a Q&A or operations.

**Adam:** Which team are you on?

**Andre:** I am in a team called the architecture team. So it's basically, guaranteeing that we have a healthy code base, or a  healthy system in terms of -- at the application level.

**Adam:** So would your tasks be around sort of setting standards around what languages are used or what frameworks or things like that?

**Andre:** Maintaining like common frameworks and libraries for the rest of the company to use, making sure that the architecture as a whole is healthy and each of microservices is doing correct things and not abusing infrastructure.

**Adam:** You were involved in a rewrite of the session generator? Could you explain what the session generator is?

## **System Redesign with Session Generator**

**Andre:** Yes, absolutely. So, well, when a user is learning Duolingo, they will need to, we give the users exercises and we have a pool of exercises which is pretty large.

So, actually let me take two steps back. We have a product called the incubator and in that product, we have volunteers making the courses, the courses that you'll see. So it's like a crowdsource called approach where they volunteer, you input all of the data and we'll make the course structure and the write, all of the course content and then the session generator is responsible for pulling all of that data and picking the exercises that will be the most interesting for the user at that point and give a session that is bite-size and small for the user to do, let's say in a bus or wherever they are. 

**Adam:** A session is like a unit of learning and that the session generator creates that, that unit?

**Andre:** Yes, that's correct. A session on these, simply speaking is a collection of exercises.

**Adam:** Is this session generated on the fly or is it created ahead of time?

**Andre:** Part of it is on the fly. We have a lot of pre-processing going on because there's so much dating involved in each session that if we do every single step on the fly, and that's very time-consuming.

**Adam:** Why couldn't all, say Spanish sessions be created ahead of time? Is there info?

**Andre:** Yes. We also want the sessions to be adaptive for each user, right? So for example,  let's say our user knows 10 words that some or the user knows 50 words. So the sessions for these 2 users will be different and also with the consideration, how likely they are to remember a word and other things like that. So it's very important for these sessions to have these online components.

**Adam:** How do you figure out when somebody's going to remember a word?

**Andre:** So we have a model for that, there is this thing called the forgetting curve for a word and it's, basically the probability that a user will forget or will remember a word after a period of time after they've learned, let's say that one day later, they have a probability of remembering that X, 2 days later, the probability will decrease. And so we model that, as in a curve. And then we do some sort of regression to estimate how well the user knows each of the words.

**Adam:** If I learned that today, then you’ll figure out based on certain probability, as I'll probably know it tomorrow, but not next week. And then you reintroduce

**Andre:** Yes, that's correct.

**Adam:** So why did you decide that a rewrite was required? So you have this session generator, it takes into account these kinds of forgetting curves and builds the lesson on the fly, I guess. So why did you decide you needed to rewrite it?

## **Move Fast, Ship Quickly Mindset**

**Andre:** Yes. It all starts with the monolith, I guess, and all of the nightmarish stuff started with a monolith. If so, we have the monolith and it's written by them. And the thing is that in the first years of a startup, we are all thinking of, let's move fast, let's ship quickly. And after some years,  we ended up adding a lot of dependencies like data stores and other services and whatnot.

And in the end, the entire system becomes very, well, the performance is not so great anymore. And also, the site's not as stable so one of the reasons it's true is to re-architect the whole system, so that the system is more robust and the, well, the second reason is that we have the code in Python. Well, Python is a great language for, you know, writing things quickly and having like prototypes ready very fast. But far systems that are very large that have very, complex data structures and complex algorithms, then Python is not so great, because you know, let's give it examples, so something as simple as dynamic typing becomes a nightmare because then you don't have all of the niceties that you have in a, in a strongly typed language because the compiler won't do as many checks, for example. And then the developers lose confidence in writing code and then they have just spent a lot of time testing and testing to see if all of the possible corner cases are being caught and nothing's going to break in production.

**Adam:** So let's see if I understand it. So we have this giant, Python monoliths. So as you add new features, it keeps on growing and you're saying the problem. The problem with Python is when you want to add, when you want to add something new, like your level of confidence is low because of dynamic typing. Do you have an example to explain? 

**Andre:** Sure. Okay. I'll give a very simple example, which is, let's say we want to,   rename a function. And I mean, you could grab your, your entire code base and start changing stuff, right? But it's also possible that in some part of the code, you pass that function as a Lambda and it has a different name somewhere and then your code breaks into production are, for example, if you want to add another arguments or function, then you have to guarantee that also nothing's going to break. But then it's also very hard to find out that the occurrences are for example even simple things as you don't know what data type you're getting into function. You can assume you're getting something, but the end, you're getting something else and these are all things that a simple compiler check could figure out and say that you're doing it wrong. But since it doesn't have that, then it's very easy to break stuff.

**Adam:** Did, unit tests help with this process at all, or were there tests?

## **Testing**

**Andre:** Unit tests definitely help, but in the starting years of a startup, I guess people are more concerned about shipping things than writing unit tests, and it gets just data. Even parts of our codebase are very difficult to mock with a unit test and are part of the monolith because, after a while, we learn from our mistakes and realize that, “Oh, we can architect things in a different way that makes tests easier.” But in the monolith, there are still many places where it's very hard to write unit tests, very hard to mock things.

**Adam:** Especially, yes. If you didn't have unit testing in mind, sometimes you make decisions that make it hard to add them after the fact.

**Andre:** Yes, that's very true.

**Adam:** So when you decided to do this rewrite, what made you choose Scala?

**Andre:** There are some reasons. The first is that our infrastructure is built on top of AWS. We needed to think of the languages that are natively supported by Amazon. Right? And they are, well, Python, Javascript in no-js, a JVM based languages such as Java, closure, and Scala. And I think Go, which is also, one of the supported languages as well.

JavaScript has the same problem, as Python is weakly typed.  we're in and this is something that we wanted to avoid for the particular case of the session generator. And then Java is, well, it's well known and it's a bit slow and verbose so it's slow to develop and it's very verbose.

So we wanted a more modern programming language, which is why we thought that Scala was good,  a good might be a good choice. And also because Scala is also very mature in the backend, and it's used by many applications in the big data domain. So, big data is kind of similar to what we're dealing with in the session generator, right? Because it's like, there's also a lot of data,  complex data structures, complex algorithms, it seemed to be a very good fit.

**Adam:** Is there any concerns about the learning curve of a language like Scala. I mean, it has a reputation for being somewhat complex?

**Andre:** Yes. So we had concerns. Right now, since our entire engineering team is small, and the number of people dealing with Scala is also small. So, my population of people who learned Scala here in the company is also very small. So I don't know how good we can talk about like how, how easy it is, but,  up to now, I personally thought it would be harder for me and for other engineers to learn Scala and to get going, well, it was a lot easier than we anticipated.

**Adam:** Let's discuss some of the features of Scala that you found useful in your rewrite. So could you describe referential transparency?

## **The Method of Referential Transparency**

**Andre:** When we have referential transparency, we have a method that the only thing it does is calculate the output and doesn't change any state anywhere. So it's very easy to unit test and to also to just logically debug what's going on because you know that once you will have that once it has some input, the output will always be what you're expecting.

It makes things very easy to test, to reason about, and that's one thing that's very good once you have very complex infrastructures.

**Adam:** So an example, just it's helpful for me if I am probably the listeners if I can tie it, tie it back to an example. So referential transparency means you have a function with some amount of inputs. So let's say like the words that I know in Spanish, and then the output is -- or do you have an example of where that could be used.

**Andre:** So let's say, in some part of the algorithm we are thinking if we should choose an exercise A or an exercise B and we put both into the function. And so what happens with referential transparency is that first there are not going to be any side effects. So, we won't, you know, write things to the database for example, because that will be adding a side effect. We won't be changing something inside one of the objects, because that doesn't contribute to the output. Right. And then, the idea is that we will just do some calculation and that calculation will be yours only for the output. So let's say if we wanted to pick between two exercises, we will do well, the output is simple. This is one of them, but we can guarantee that nothing else is going on,

**Adam:** Which is what makes it easy to reason about.

**Andre:** Yes, you're correct.

**Adam:** You also mentioned, and I think it ties into that example, about immutability. So how does immutability tie into this?

**Andre:** When data is immutable. You have some nice properties like you don't need to think about. You don't need to think if something is changing your data from somewhere else. And I think many people have seen, you'll call a function and then you'll pass an object to a function that function calls and that function call another function. And somewhere along the way, someone changes one of the properties. And then you don't know who changed it, what it changed to and you just need to add print statements all over the place to figure out what is going on because something changed part of your data and you don't know why. So when you have immutability, you're guaranteed that things won't change. So all of you, in each step of your algorithm, the state will be very clear to you.

What this means in the context of Scala, for example, is that in each step of your algorithm, what happens is only data changes. Let's say you have a list and you'll change the elements of a list by let's say adding one to a property, and then you'll know that in your next step that the, your new list will have all of the elements with plus one, and you'll know that you're guaranteed that that's going to be that for so if you use that variable for something else, that value, it will always stay the same.

**Adam:** But you did say the list, we're adding an element to it. So how, how can something be immutable?

**Andre:** Yes, that's a good question. What we do is we actually copy the list. We have the original list. We have the new list with plus one in all the elements. And then we keep just transforming data as we go and that's a way functional programming happens is that you will always, generate new stuff but you won't be changing what you had because if you changed what you had done, it's, it becomes hard to, to understand what's going on once you have a giant system.

**Adam:** So this is like Scala’s immutable collections, and you're saying the immutable, immutable control structures means when you write your session generator, nothing's changed. If a number of lessons come into the input and we need to select one, then that one comes out the other side?

**Andre:** Yes or another example would be, let's say, if you pass, for example, you have a set of exercises. And in one part of the algorithm, you want your filter and consider, let's say half of these exercises because they're better in that context. So you'll filter your pool to half, and then you'll do whatever you have to process. But then in your next step, you wanted to use the actual like full set of exercises and the data is there because you have not touched it, you created a new smaller set in the previous step which if you want you can use it or not, but the idea is that your variables always stay the same so if you want the entire pool for the next step you're guaranteed that nobody changed it, nobody removed things, without you realizing

**Adam:** To make this rewrite work. It's quite a different model of operations. So did you have to change the architecture of the session generator so that it could work more as, transforming inputs rather than mutating them?

## **Transforming vs Mutating Inputs**

**Andre:** Yes. So we did change, so many of the algorithms as we had to just rewrite them in an immutable way. Sometimes when the algorithm was way too hard to rewrite and it was risky to introduce errors in those cases, so Scala has this nice thing that it's, I don't know if it's nice or not, people might disagree, but you can port Java code into Scala, and just run Java libraries in Scala because both of them run on top of the JVM. And what this means is that Scala also supports things from the Java world. So like mutable types and some, for loops, while loops that are not very functional -- functional programming. So. If you're rewriting something and then you realize that, Oh, this will be very hard to rewrite without adding complexity or making risky changes, then you can write in Java, like an EDM of Scala.

**Adam:** What percentage would you say, is more of, you know, Java is written in Scala, and what percentage is, did you kind of go with this functional transformation style?

**Andre:** So in our codebase, I'd say that more than 99% is functional because we try to do those things in a more -- so when you're using immutable, collections and we are using referential transparency, things are much easier to debug, much easier to maintain. So we try to make things immutable and, or referential transparent and, you know, functional in general, in most of our codebase, most of our code basis, maybe one or two algorithms, we thought it would be better to just use the nonfunctional version.

**Adam:** Well 99% is very functional. 

**Andre:** Yes. When you're writing a code based on scratch, you can also do unit tests that you couldn't do in your monolith. Things are much easier to just test that your algorithms are working as expected.

**Adam:** How is unit testing in Scala?

**Andre:** We use, in Scala, should I say in our whole framework we use Sinatra as our HTTP server. Sinatra is an HTTP server written by Twitter. And we, and they use a Guice, which is the Google library. So unit testing in this context, we have like all dependents out of the box, we have mocking out of the box and it's very easy to do everything.

And I'd say that it's, well, it was just easy to write unit tests and we ended up writing a lot of them and I think our coverage right now is somewhere along. 70% maybe. 

**Adam:** Nice. In the session generator, you mentioned microservices. Is it something that calls out to a bunch of services and combines them together, or how does it interact with the rest of Duolingo's infrastructure?

**Andre:** So we have to pull data from a lot of places, and we have a data pipeline for that. So the pipeline is just a task that runs offline so that we don't, you know so that we don't make real online traffic depend on our data stores, right? So we have these tasks that run daily and hit all of these services and whatnot that we need to hit in order to fetch the data. And then this task pre-processes everything and then serializes all of the data into the S3  file server by Amazon -- AWS. And then, when we are online, we are serving actual requests for users. What we do is we just fetch from the file server and catch it in memory and serve it and when we do that, we get, we have an architecture or a system that's very robust to faders because the only, your only real dependency is your file server and network of course. It's also very fast because everything is caching memory.

**Adam:** So the only real, external dependency you have is S3 and then even that is kind of insulated by your cache?

**Andre:** Yes.

**Adam:** With all this functional idiomatic code you're writing. Does that mean the session generator is sort of like, it takes as an input, like a user and then all of the possible lessons ever, and then it spits out what they should learn next?

**Andre:** A little bit, it actually takes as input, the online part of the session generator takes as input the lesson the user wants to learn and some other user settings and outputs the session to the user -- the collection of exercises. 

**Adam:** There's an idea that statically typed languages are more verbose and dynamic languages are more succinct. So I've actually found, in my experience  that Scala is a very succinct language, maybe even more so than Python in some cases. What did you find in terms of verbosity moving from one language to the other?

## **The Verbosity of a Language**

**Andre:** Yes. So I think verbosity depends a lot on the language itself. And so if you're familiar with Python or JavaScript as your go-to dynamically type language and Java is your statically typed language, then I would agree that yes, Java is super verbose. We have that Scala is a language that is concerned about a lot of typing. Scala tries to infer types whenever it can.  Sometimes it can't and makes some errors here and there, but usually it's able to infer your types and sometimes infer other things that the decompiler can infer. 

Like Python you can do a list comprehension and write one-liners, instead of writing like in Java, you need to write three or five lines of code just to do a for loop. And Scala is very succinct, and there's not as much typing as a language like Java, and compared to Python I’d say in some cases a Scala it's fewer variables. When you're defining a class, you don't actually need to write, if you don't need a body, you don't need to write a body for a Scala.

**Adam:** Are you using implicit within your codebase?

**Andre:** In Scala, there are two kinds of implicit. Implicit parameters and implicit conversions. Implicit parameters basically define some of the parameters of your method as implicit. As long as we think about the scope of the color, a variable of that type that is also an implicit variable. It's declared as implicit then you're able to just not write the code to pass that value into the function. So it's basically to avoid typing and so for those, we do use implicit. We don't use implicit conversions because we usually find that a little bit scary cause you know, you won't see when things are being converted. So generally,  no implicit conversions, but we do use implicit parameters.

**Adam:** What's an implicit conversion?

**Andre:** Implicit conversion is when you have an object of type a, and then let's say that you'll want to convert it to an object of type b. There is a mechanism in Scala that you can define your conversion from type A to type B, and if you put that conversion in your scope, you're able to convert it from it for A to B without writing code to convert.

**Adam:** So it could be very handy and save on typing, but also maybe you don't know. What's changing to what?

**Andre:** Yes.

**Adam:** In my experience, Scala can be less prone to runtime bugs. I think you mentioned you had some issues with runtime bugs getting to production in Python. So how did this change now that you've rewritten?

**Andre:** Yes, so in Scala, we do have a lot fewer runtime bugs, part of it is because your compiler would just get most of the errors. So as long as compilation passes, well, you don't have any programming errors you have like application logic bugs here in there, but that's another problem, right? And so, the compiler does a lot of stuff for you, and the unit testing framework is also very user friendly. So we can write a lot of tests that make sure that your code doesn't have the most common application logic errors that you'll know about. So, in the end, it's very hard to have these runtime bugs going on these Scala

**Adam:** What, what did you find to be the pain points, of moving to Scala as a language?

## **Pain Points of Moving to Scala**

**Andre:** So I was actually more fascinated that Scala is like a modern language. It has so many nice things that we don't have in Python and Java that kind of outweighs the pain points. There are some pain points, but I would say that they're not actually the language itself. There are some small things here and there in the language, but those are not a big deal. Most of our pain points where let's say we have a library in Scala that it's like undocumented or we have a function that's available in Python by default are in one of the common libraries and it's not in Scala. So they're like some small things but I guess that that's true. Whenever you change,  a codebase from one language to the other.

**Adam:** Nice. You mentioned there are some things about the language that fascinated you?

**Andre:** Okay, let me see -- What are the things?  So yes, I think one of the things is a well functioning, functional programming in general, how readable it makes it your code. Since the language is not too verbose the end result is that a, your code is very explicit on the application logic instead of having like a boilerplate of just like controlling your loops or things like that. I find coding in Scala very readable and that's nice, it's also very easy to just look at the code and see if there is a problem because, you know, it's all immutable and it's just easy to debug even without running any code.

I originally started my life as a programmer in Java and then you know when you're in Java and you move to Python, the first thing you think to yourself is that “Oh, I love lesser codes. It's much faster to write stuff. And then there's also that difference.”

Scala is very fast to write code. So in the end, I spend my time not only writing code but all of that extra time that I would either spend you know just typing in Java or testing things in Python. I use that time to write a unit test in Scala and in the end, it's a confidence thing you can write code and be confident that things will work as you expect.

**Adam:** So you're back on the JVM, so you got tired of the JVM and you left, and now you're back. But the language, the language is more fun. 

**Andre:** Yes, exactly

**Adam:** Is it faster to write Scala slower but worth the trade-offs or compared to Python compared to Java?

**Andre:** I'd say that far it's a bit slower than Python, but there, there are caveats, it's slower to write a piece of code, but then the amount of effort you have to maintain that code in your test code is a lot lower in Scala, so for me, in the long run, Scala is just a faster language than Python.

**Adam:** So, not faster to initially develop, but faster, like the all-in time.

**Andre:** Yes.

**Adam:** So how about maintenance? So maybe you don't know, maybe this is so new that you haven't had to do much maintenance of it?

**Andre:** We haven't done that much maintenance because the system is very new but whenever we have to like refactor or something it's very easy to, cause, you know, your IDE does, does it fire you basically. So you don't even need to think about it. We just click two buttons and that's it. 

**Adam:** The compiler gives you confidence, I would imagine too, or around these, these refactorings because you know, you get some sort of error checking?

**Andre:** Yes, exactly. So, I remembered the first time I had to refactor some stuff in Scala. I was just surprised that in fact, it would take me like, I don't know, an hour, maybe not an hour, but you know, a lot of types and in Scala I finished in like less than one minute and I was just so surprised. I mean, it's that sort of thing that after working with a Python a lot of time you just become so used to that, that whenever you have something nice, you're like, “Oh, that's nice.”

**Adam:** Scala being on the JVM should, in a lot of cases, be much faster than Python.  do, did you have any sort of numbers about that?

**Andre:** I wouldn't say like, so we haven't actually done any benchmarks that you would be able to trust that compares the exact same code in one environment, R and D out there the one thing that we have going on is that we, well we have rewritten the whole system. The whole session generator in Scala.  we've, we have also rearchitected things and some of the performance gains that we saw were, so from rearchitecting and using the memory cache and, and using a street, we decreased latency from it was maybe 700 - 800 milliseconds to tenths of milliseconds. So it was like more than 10 times. That was very good at the number. Also, the number of servers that we need to show. Just to use to serve the same amount of traffic decreased by -- how much was it? It was like maybe 10 times or so.

**Adam:** Well. So that's a big savings cost bottom line, I guess.

## **Scala and Savings Cost**

**Andre:** Yes, and also just the fact that you know, Scala and the JVM general do better in both multithreaded,  environment, and multiprocessing and it's able to, to just run a lot of stuff at the same time. It's nice, so one thing that's color has the Python does, for example, is a, it's called futures.

So what a future does is basically it's a unit of an asynchronous computation. So whenever you make a request,  you'll get the response in the future, but the value is not there. The value is you're waiting for the value in another thread. So what happens is that you don't block your original thread. And because of that, you're able to do a better job in concurrency, for example. And that's one thing that we see in Scala that our servers are able to handle a lot more concurrent requests than Python? Because in Python whenever you have a request and then you're waiting for I/O, that thread is completely blocked. And if you have, I don't know, let's say 20 threads in your server, then you have one less to serve traffic.

**Adam:** Is there, is there a Python way to deal with this? Like, or there's just none?

**Andre:** Not that I know of well, not out of the box. Maybe there might be some libraries that do, for example, the actor model, which is something,  it's, it's the thing that languages like Elixir and Erlang out of the box too, so it just handles concurrency better.

I think there is something for Python as well, there's Akka, it's a library for our Scala. And if I think if you use that, you might be better off, but not out of the box, not if you're using Pascal’s pyramid.

**Adam:** Are you using the actor model in your session generator?

**Andre:** I'm not in the session generator. No, because we wanted to. The interactions with I/O are very simple in our session generator and there's also the overhead, to get it set up first because you know, nobody in the company had that kind of knowhow. So we chose to first do the more common approach but it's something that after you start reading, you become interested in it.

**Adam:** Are you using actors at all? I'm just curious because you mentioned it.

**Andre:** So we're thinking of implementing that for the offline part of the session generator because we have a lot of data. And in that situation it wouldn't make more sense to have a data pipeline that uses actors, for now, we still haven't had the opportunity to do it because, you know, we're still working on some other things, and that's not the highest priority yet.

**Adam:** Makes sense. So now that your rewrite is over.  What were the business benefits of the rewrite? Like was it a success?

## **The Business Benefit of the Rewrite**

**Andre:** Yes. So far now I think it's a success, it's not completely over yet because we have some, it's just some features to port, but it's mostly done. I would say it's a success because we were able to have like those cost benefits, it's just a lot cheaper to run or to serve traffic with the rewritten code and the rewritten architecture than the original one. Also, in terms of developer productivity, it's also very good because definitely. It's a little bit weird if I say it, but the feedback from the other developers is that it's just less painful and I think it's painful. It was the word they actually used.

**Adam:** So what makes it weird?

**Andre:** Well I started the whole process of moving to a Scala so I might be very biased towards the new system.

**Adam:** So you don't find it weird, but other, other people do? Is that what you're saying?

**Andre:** No, it would be weird for me to say cause I'm biased, but other people, I also got feedback from other people that it's less painful. It's that thing that I talked about we've like, you can write code, and I think that's very important.

**Adam:** Okay. I understand. Would the rewrite have been successful or as successful if you had made the architectural changes, but not the language change?

**Andre:** I think partially, with the architectural change, we would see improvements in latency. I think in Python they wouldn't be as large one reason is that Python is a bit slower than Scala. The other reason is that having a threat-safe caching Python is not as trivial as it should be. So I think that's, that that would be one problem. But also generally, we would lose all of the benefits of developer confidence of not pushing breaking changes,  because you know, it's all dynamically typed and the, it would be much harder to make, like larger changes are just, you know, what the data structures are.

## **Language Learning Perspective**

**Adam:** What is it like working at a company with such a focus on learning?  Are you a language learner yourself? Does the company have a learning perspective based on what it does?

**Andre:** Yeah. So I think it's very interesting to work here. So I am a language learner so my native language is actually Portuguese. I was born in Brazil. I'm a Japanese-Brazilian, so my native language is Portuguese second language is English. I've learned Japanese and kind of know Spanish. It's very fun to be surrounded by people who have the same interests in learning. There are some people who are learning like a ton of languages and they know a lot of languages. And even,  with our community.  Sometimes when we meet some members of our community, it's like very interesting because they have all these, a view of worlds that you don't usually see in your daily life and know people who want you to learn new cultures and learn new languages and have a very broad horizon I’d say.

**Adam:** Yes I could see why that would be refreshing, people, Talking to people who have a global perspective. Well, it's been great to talk to you about this rewrite. I'm glad it's been a success. Thank you so much for your time.

**Andre:** Yes, thank you for, thank you for inviting me. It was great at talking to you.