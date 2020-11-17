---
title: "Unproven Tech with Sean Allen"
date: "2020-06-10"
---

#### **Choosing The Right Tool For the Job**

Choosing the right programming language or framework for a project can be key to the success of the project.

In today’s episode, Sean Allen shares a story of picking the right tool for a job. The tool he ends up picking will surprise you. 

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/14740817/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

His problem: make a distributed stream processing framework, something that can take a fire hose of events and perform customer's specific calculations on them but the latency needs to be less than a millisecond and the calculations might be CPU intensive. Who would need something like this? The initial use case was risk systems for Wall Street banks. 

“Basically programming languages are tools. It's not about ergonomics, it's not about developer experience, it's not about all the things that we normally talk about, it's about getting the job right. For whatever that means it's a means to an end.” - Sean Allen paraphrasing Sylvan Clebsch

### **Transcript**

**This is a machine-translated transcript. Podcast page for [this episode is here](https://corecursive.com/055-unproven-with-sean-allen-1)**

### Introduction

**Adam:** Why don't you like to state your name and what you do.

**Sean:** I'm Sean Allen, until a couple of months ago, I was the VP of engineering at Wallaroo Labs. There's a standing fan about seven feet away. I assume you're not hearing that?

**Adam:** I don't hear a standing fan. It does sound echoey.

**Sean:** I have no non-echoey rooms. It's basically a couple of large open spaces in Brooklyn required by the bridge. 

**Adam:** Sean held his laptop up to the window and showed me what I assume is the Brooklyn bridge. Sean is also recovering from COVID. 

**Sean:** I had all of the symptoms except for the smell thing but it was relatively mild. The highest my temperature ever got was 99.9. I felt like I had a bad case of the flu for the most part now I feel like I have a mild case of bronchitis.

**Adam:** Hello, and welcome to CoRecursive. I'm Adam Gordon Bell. Today, Sean shares a story of picking the right tool for a job. The tool he ends up picking will surprise you. 

What happened is Sean wrote a book about real-time data processing. 

The book is called Storm Applied, Strategies for Real-time Event Processing. The details of the storm don't really matter here, except to know it's an Apache big data project. It is written on closure and runs on the JVM. What happened is after he wrote the book, a company called Wallaroo labs hired him to build a system like a storm, but much faster. 

**Adam:** You started Wallaroo Labs and then what happened next?

**Sean:** We went through a couple of iterations of stuff with them and then decided that in order to meet the needs we were going to have to build something from scratch, and build a framework which was designed for these, low-latency type use cases whereas part of it as well, you want it to be as efficient as possible.

**Adam:** His problem: make a distributed stream processing framework, something that can take a fire hose of events and perform customer's specific calculations on them but the latency needs to be less than a millisecond and the calculations might be CPU intensive. Who would need something like this? The initial use case was risk systems for Wall Street banks. 

## **Building A Risk System**

**Sean:** A risk system could be one which runs alongside automated systems and analyzes the trading output coming out of the automated system to make sure it looks within some realm of reasonable and could then shut down trading, for example, there's a whole bunch of different types of risks things, perhaps like the most famous, are if you ever heard the Knight Capital story.

**Adam:** No.

**Sean:** So Knight Capital went out of business because, an automated system, started doing trades, that it wasn't supposed to do due to a, a configuration pushed to production that went wrong, in the space of 45 minutes, and put them out of business.

**Adam:** This stream processor needs to answer queries in a millisecond, 99.99% of the time. Median response time in the microseconds and it needs to be able to receive hundreds 0f thousands of requests per second. It needs to be fast enough to pull the plug on a high-frequency trading system that’s gone off the rails so what would you do? What language or framework would you think about using? Let’s play along and see if you end up where Sean and his team did.

**Sean:** We spent a good amount of time speaking out. This is what we think needs to be able to do. And looking at what is the language or libraries that we want to build this on top of I mean, the number one way to do low latency is to cut down on network hops that's like one of the first big things. So even though it's a distributed stream processor, we wanted to be able to do as much processing as possible on each machine and cut down on the number of network hops you'd have to have. 

**Adam:** Never calls are just slow compared to direct memory access or interprocess communication. You can't scale out to speed up latency as you're just adding more network hops. The more you can do on one machine. The faster year distributed processing system is going to be. Maybe this is the reason that storm isn't a fit here. 

## **Apache Storm**

**Adam:** How come Storm can't handle this?

**Sean:** Storm wasn't designed for these systems which basically had to be very efficient. In very low latency Storm and a lot of the other Apache big data projects are designed but particularly storm more as a parallelization engine. Then a low latency like data processing system, if you look at the early things are storing me, be like, here I have some algo, some commutate transformation I need to do and I need to be able to run it on like 50 machines because it won't run fast enough on my machine and in some ways being a bit of a realtime replacement or something like Hadoop, right? Which again is the same type of thing which you build that very differently when you're most concerned about it. I just want to paralyze this so I can get it done as compared to I need to get this done within a couple of milliseconds, right? Like a lot of the things we do for things like bank points and we're looking at 99.99% of requests that have to be processed in one millisecond or less. I mean you're talking about systems like that and that's just not something that a storm was built to do. Storm was built to do stuff where you're talking about, probably depending on your thing, your median latencies are going to be in tens of milliseconds probably if it's a small thing, it might be single-digit milliseconds, but you're not really looking at, Hey, we want to have, you know, like 15 microseconds, be our median latency for a lot of the stuff that we're doing. So it just wasn't designed for that kind of thing. But you know what I mean? If you were designing it for that type of low latency, you wouldn't use closure for example. 

Writing low latency stuff for the JVM, in general, is difficult, and if you write it like a normal Java program which is a lot of ways a Storm was written like a normal Java program. You're going to have a lot of object allocations. It's going to involve a lot of memory pressure.

You're going to involve a lot of garbage collection, closure for how it does stuff makes that worse and those are going to be problems for our ability. Something like what we built with Wallaroo and a variety of reasons. They didn't set out with the goal of building a system like that, so they made choices, which wouldn't result in a system like that.

## **High-Performance JVM Applications**

**Adam:** Yes, I guess, I don't know this area, but like a lot of these projects that are on the JVM, like they all end up kind of manually managing memory with some sort of off heat tricks. I understand.

**Sean:** If latency is a real concern, you're doing stuff like that. Yes. For a great project if people are interested in high-performance Java stuff and in a codebase, which is pretty easy to follow the era on the Aeron Project which is a message broker which does stuff over its own custom UDP that Martin Thompson is one of the big people behind.

That's, that's a great project to look at for doing that type of stuff on the JVM. But it's definitely not normal JVM programming at that point. 

**Adam:** Let me take the sample of like backend developers out there and I pull one out of the hat and I asked them to build this. I think, depending on the age probably a lot of people would go with C++ to build something like this? 

**Sean:** We definitely consider it C++.  I've done a lot of C++ programming in my life. I don't think I'm good enough to do it with C++. So when I was really learning and doing a lot of high-performance C++ stuff in the ‘90s and high-performance C++  stuff that is entirely different from what we were doing for hybrid, that we needed high performance with C++. Then you could just write it in plain old Java fashion now and be completely fine. The definition of high performance has definitely changed over the course of time, but doing this stuff in C++ it was all multithreaded and in order to go fast, you need to not copy memory which is also where you get into trouble because you can have data races, et cetera, where you need to be careful about how you're sharing memory and to make sure that you don't corrupt the memory to make sure that thread one over here doesn't free memory that thread too is still using. It is a variety of ways you go about doing this, usually with locks, et cetera, these types of things and still even with doing those, an awful lot of people like the number one way that you see bugs of this usually come about is segmentation faults is what happens from program crashes, segmentation faults and so like a lot of people developed different rules for how you can share a memory or what you can't. I had this all set of rules that were in my head but in the end, you can use tools like disposers and everything to try and find where you violated those rules but in the end, it's on you to carefully follow those rules. And if you don't and you built an awful lot of code and you're not regularly testing it with stuff where it's going to find the one little mistake that you made at some point you know, the further in the past that mistake was, the harder and harder it's probably going to be defined.

We didn't think that we could hire enough good C++ people to be able to do that and so while we still kept C++ around as an option, we really wanted to have something that had more memory safety like baked into it, where the compiler itself would say, “Hey, that's problematic.” That's something that Rust is definitely in part one particular approach to trying to solve that.

## **Considering Rust**

**Adam:** Yes, that's what I was going to say. I think when people start talking about data races, Rust, people talk about this all the time, right? This is a feature they bring to the table. 

Did you consider Rust? 

**Sean:** We did and Rust was a strong consideration. The issue there was that there was no high-performance runtime to do what we would, what we want to do, and we have to write that runtime, our estimate was, and this is an estimate where we spent probably a week to two weeks trying to spec out roughly in not even t-shirt size, bigger than t-shirt size, how long we thought it would take and we thought it would probably take anywhere from 12 to 18 months to have a really good, solid runtime. 

**Adam:** What's a runtime? like a scheduler?

## **What is Runtime?**

**Sean:** Every language has a runtime, they just don't necessarily know it, I mean, a runtime is a number of things: it's memory management, it's a scheduler. What your particular runtime provides might vary but yes, definitely scheduling and memory management are probably the two biggest ones.

If you're doing high-performance stuff, then you're probably going to be doing stuff asynchronously in some type of thing or some type of message passing type things so you can hand-off. Maybe you'll be using channels like Go does or something like that, but then, what's the communication mechanism between threads as well and having something for that.

**Adam:** Yes, because it seems like you need a runtime for handling concurrency. 

**Sean:** The thing that people don't think about usually when they're first starting out, with stuff until they've worked in an ecosystem for a language that doesn't have a set concurrency model that comes with it, is what you end up having different communities that develop where they have a concurrency model and there were libraries that work with that concurrency model. So like Rust has Tokyo now, which is a specific concurrent, there's a kind of currency model that's built into that, and libraries that might be written to use an entirely different concurrency model are not going to work with Tokyo probably and vice versa. You see this within C++ where there's a whole bunch of differences, like concurrency libraries, and they just, they don't work well together and if they do, they usually step on each other and that becomes a problem for high performance.

**Adam:** Yes. Like I think of like I'm a Scala developer day-to-day, mainly, and there's like Akka people who do kind of actor stuff and then there are other people who do other stuff, and there's, there's a number of communities, I guess. 

**Sean:** So like the JVM is a runtime and it provides a memory model for how memory works and it provides a basic concurrency model, which is you build on top of threads and then you use locking primitives in order to do this and Akka wants to in the end have a different model that they want to build on top of that.

So one of the things that comes up a lot is aware of this when you're doing all this stuff is make sure that you don't inadvertently capture values or references to objects and send them from one actor and Akka to another because now you can have, two actors that are both able to modify the same data and you now can have data races, et cetera, and everything, which is a problem.

And there's not a lot that Akka can do about this because, in the end, that is this single global memory space is something which the JVM allows, right? And if you want and you would need a special Akka compiler in order to prevent programs that do that inadvertently from compiling, which if you're building a library, you don't really want to have “here's my compiler for it” and so this is a thing where they're trying to overlay a somewhat different idea of concurrency and a runtime idea on top of different run time and, and running into some issues there, 

**Adam:** In other words, Akka runs on the JVM, which doesn't have first-class support for actors. You can make it work but the runtime is thread-based rather than actor-based. Rust on the other hand tries to have a very minimal runtime environment. But Sean feels that that means he needs to build these things himself, like a scheduler or error handling, or maybe even garbage collection. Which makes me want to ask about garbage collection itself.

## **Trash Day**

**Sean:** There's an awesome paper. I was thinking before this -- am I going to get through this without mentioning it? No, I can't get through anything that's on this topic without mentioning it. It's a paper, it's called Trash Day and I don't know if you're familiar with it, but folks who are listening might not be, which is really about how do you get the maximum performance out of a Hadoop cluster?

**Adam:** Why is it called Trash Day? 

**Sean:** Well, because it's about handling garbage, right? When you put out your garbage, that's trash. You know, like when you live in the suburbs and there's like three days a week when you have to put the garbage out trash day, and then it gets taken away.

**Adam:** In other words, in a distributed system on the JVM, a GC pause causes a slowdown, work piles up or work slows down. The paper makes the dupe faster by having everyone GC at the same time, that's your trash day so you get more throughput. 

But you still have latency issues when that GC happens, the point for us is the JVM and its runtime won't work for this use case even with the performance actors system, like Akka. 

All right so far we've crossed C++ off the list, Rust off the list and now it sounds like anything JVM off the list. Sean did bring us back though which gives me a clue about the direction he's thinking.

## **Considering Erlang and Beam**

**Adam: I assume your concurrency model is going to involve actors of some concurrency model.** 

**Sean**: What I really like is that you have something,  you start with how many CPUs? So you have and you have a single thread that does work per CPU you lock it to those CPS and you don't let anything else use the CPU. And if you want to go really fast you can use something like CSET to actually set those CPS apart so that Linux won't schedule anything on those at all.

They're purely for your program it can start up and it can have like 12 CPS that are all for itself, and you have one thread per CPU which will be responsible for running work, and you have something, and it could be actors, whatever your abstraction is over the top of it, but you give people some unit of parallelism of concurrency that they can program to and that's the model because I'm particularly interested in making things go fast but yes I happen to like actors. For me, it's a really good conceptual model, although I've seen lots of people definitely struggle with trying to figure out how to model things for actors, which in a lot of ways I think is because actors are really all about doing things asynchronously and the way most folks have been taught to do programming is in a very synchronous fashion and thinking about really thinking about concurrency, where things are happening asynchronously can be really difficult for a lot of folks.

**Adam:** All right that comment makes my mind go straight to this runtime that was built from the ground up to use actors for concurrency. 

I guess if you're going to embrace actors I mean it must've been a consideration?

**Sean:** Yes in his consideration, we didn't think that we could get the performance that we needed out of our mind early and was designed more for consistent latencies rather than consistently low latencies with lots of throughputs. Which is a slightly different one of the great things about Erlang is if you graph like what your latencies normally are they're just flat.

In a way that you don't get from like the JVM in general because of garbage collection strategies that are commonly used like the JVM. Whereas the garbage collection strategy on Erlang is very different, with the message passing and everything, it results in very consistent performance all the time.

It's just that, Erlang was not designed to be a high-performance language. The throughput isn't there but yes, Irvine was something that we definitely considered more than one person who was on the team had a prior in some cases, large amounts of Erlang experience 

**Adam:** It just won't hit you like one millisecond?

**Sean:** You can but it might not hit your thing where like we were doing one millisecond at the 99.9 percentile while processing 3 million messages a second, in a virtualized environment in AWS. We probably wouldn't be doing that amount of throughput with that late like that was, that wasn't going to happen like the per core amount of computation that you could do with Erlang is, in general, going to be less. Then what you would do with C or C++ because again it had different goals when it was, when it was, when it was designed.

**Adam:** So it seems like Erlang might not be a fit, but there is this company called Basho that makes a really fast distributed database, all using Erlang. 

**Sean:** For us when we were looking at doing stuff for a while, we really liked actors -- actors worked well for us for how we think about things and modeling them. And so Erlang was a natural, like a thing that we were interested in. So it was, let's go talk to the folks that we know in Basho, and go, “here's what we want to do.” Do you think that you think we'll be able to easily get early to do that?

And the answer that came back was, we love Erlang, but no, we don't think you're going to be able to make Erlang do that easily. 

## **Introduction to Pony**

**Adam:** So not C++, not Erlang, not Rust, not Java and Scala and the Akka. So I'm running out of guesses, let's just cut to the chase. 

**Sean:** Very little of interest has ever happened to me on LinkedIn, but Sylvan I've known Sylvan since he was 16, and I was 17 when we met and but we hadn't talked for a number of years, because Sylvan is very bad at email. I sent him an email and he never replied. So I assumed I had done something to irritate him and I didn't hear from him until he sent me a LinkedIn message and said, ”Hey, look what I built.” 

**Adam:** What have you built?” What Sylvan Clebsch had built was a Pony. The love child of Erlang and Rust, no data races, shared memory without copying and all based around first-class actors and something called reference capabilities. 

The first thing I think of is I've never heard of this language Pony. It cannot be a legit choice to bet accompaniment on, but Sean sees it differently. 

I'm imagining the story and I just imagine you're like, Erlang It's used in production, lots of people use it. The people who really know it say it doesn't fit, but you're like, actually, a guy I knew when I was 16, built something that I've never heard of. Let's use that.

**Sean:** If I hadn't known Sylvan right then, I wouldn't have heard of Pony and it wouldn't have been a consideration. But, I mean, like one of the other serious considerations was that we use C++ or we use Rust. And so in a lot of ways, I mean, we were very nervous about picking. We sort of dipped our toes but you know, it was that compared to Rust and writing our own one from scratch. And this is the big thing, the biggest consideration there. But Rust had a bigger community at the time, but Rust was still a very small community that’s really small.

It's picking up now but even though it's got a huge amount of mindshare on like, you know, things like hacker news or whatever, like the actual community itself is really small when you compare it to a lot of languages. I'm pretty sure that I know way more Scala programmers than I do hacker news programmers. I'm sorry, Rust program is at this point, 

**Adam:** Hacker news programmer that is for sure a Freudian slip but anyways, Sean chose Pony - language was written by his high school friend. Some might say that is a huge risk, especially since the whole company was this product. I think we need to learn a little bit about Pony to understand this choice, and then we'll come back around to -- “Did this work out for Sean in Wallaroo Labs?”

**Adam:** So what did you get out of Pony?

**Sean:** So we got a compiler which won't let you create data races, will allow you to share a memory in a concurrent system in a way that's safe so that you don't have to do copies, to allow you to go faster and we got a runtime which met our general idea of how we would want to go about writing both the runtime in terms of scheduling and basics for memory allocation so that we didn't have to spend that 12 to 18 months writing our own.

## **Embracing New Tech** 

**Adam:** So you mentioned fixing compiler bugs. I mean that that would frighten me from wanting to take on a language, I guess.

**Sean:** I think that is a thing that should frighten you. You should go into that with eyes wide open. Right? And all of us who worked on Wallaroo in the early days have a bit of scar tissue where even though none of us had hit a compiler bug in forever, we were still like “is that a bug in my code or is that a bug in the compiler?”

That thought would cross your mind all the time because he'd gotten in there at least part of the way I look at it is yes, Pony was definitely unproven technology and for whatever your definition of unproven is an awful lot of things are still unproven that a lot of people are comfortable with now.

I think one of the things that people don't think about when deciding like, “Oh, I don't want to use that thing because it's unproven, is that if their alternative is to build it yourself. Right?” Your thing that you're building is also unproven. Right? And it becomes a matter of certainly building it yourself.

You're going to probably understand the thing much better if you build it yourself. This is why when we took on building Pony we considered that the language, the compiler in the runtime were part of our project. This was code that we were starting from and we were looking at it as, “is this like, Imagine that we're starting our thing right here. Are we comfortable with this being part of our codebase?” Right. And the fact that it was such a really nice, clean C code base for like the core implementation of stuff,  with something that we were, you know, that made us comfortable. There are an awful lot of things that I've worked on in the codebases I've, over the years where I would not be able to make that statement, you know, where it's just like a jumbled mess. And it would be a bad idea to take that thing on a core part of your thing. That's really kind of there, but it's like if part of the choices is we're going to do this in Pony and we're going to potentially have compiler bugs verses we're going to build an entirely new runtime in Rust.

And who knows how many bugs we're going to have in our runtime, like if the compiler, likelihood and compiler bugs, you know, no longer become as much of an issue when you look at it as a trade-off between those things. yes.

**Adam:** It's interesting that you successfully embraced pony because I have to assume that there's limited packaging support. 

**Sean:** Yes. I mean, it's right there on the website, like “batteries not included.” You're writing almost everything, and if you're concerned with the performance, you're probably going to write almost everything 'anyway, and at least anything that's going to be on a hot path so that becomes much less of an issue but you know, if you just want to get your machine, if you just want your machine learning thing up and running, you know, it would be the wrong thing to use.

## **Beautiful Code**

**Adam:** One of the things Pony is famous for is this quote from Sylvan Clebsch - Sean's LinkedIn buddy. Let's paraphrase it. 

**Sean:** Basically programming languages are tools. It's not about ergonomics, it's not about developer experience, it's not about all the things that we normally talk about, it's about getting the job right. For whatever that means it's a means to an end.

**Adam:** Yes. It's an interesting perspective. Right? 

**Sean:** When we're designing Pony or anything, it's like, Oh, let's make it ugly for whatever we think ugly might be, but whatever it is that gets, I almost made fun of the developer like experience UX people from them, which is bad.

I would have fallen into making fun of it cause I just don't understand it. There is something that happens for those people when they're using a language that they love in this type of way like Ruby that I just don't understand. In the same way that I have a friend who's really who, like Ruby drives him up the wall and he just can't stand it.

He finds it horrifying to work with for a reason I also don't understand. To me, it's just like, well, I wish it had more things to tell me upfront that I was making an error, but you know, Yes. 

**Adam:** I get it though, like I do get the beauty perspective, right? Like there's like the Haskell, like the definition of it's like quicksort and it's really small and it just looks like a speck. Then they're like, well, this actually doesn't work, at the performance level.

So then there's an optimized version where they have to like, you know, do a bunch of stuff, and then it becomes much less, perceived as a human, right. I suspect when people talk about beauty, they're talking about something that very concisely reflects what I would like the machine to do.

**Sean:** Perhaps, yes, but that's certainly in the eye of the beholder right. Because one person is just, I want it to sort of list the other person is, I want this to be sorted in, is an efficient means possible. Therefore I know I have a pretty good idea that doing it like this, this, and this, rather than letting a compiler decide will result in better stuff.

And so, I mean, at that point, that could be beauty, you know? I mean It's a matter of context and where you are on a ladder of abstraction or whatever it is, for what you're really interested in. 

**Adam:** I think that there's even a bigger point of a wider than performance if you have a really hard problem, you have to optimize for solving that hard problem. Does that make any sense?

**Sean:** I believe I understand what you're saying. Yes, I mean, your hard problem is your primary thing. You want to solve the hard problem. Ergonomics is going to be somewhere down the line, right? Ergonomics is never the top thing for probably anyone there. There were other things that were first for me. Beautiful is I've written your work.

## **Who Should Use Pony?**

**Adam:** Who should use Pony? Like, so you're behind Pony now I believe you are, are you like invested in the language? Who should use it?

**Sean:** I mean, Pony particularly is good at doing things that are operating over TCP over a network. If you were in a bank and you needed to tap into anything, that card in order to like. Monitor stuff that's flowing by to make sure that there's not something unusual happening on your network. Pony is great for that if you're building like network servers that need to be high performance then Pony is excellent for that. 

The concurrency model and the fact that once you get over the hump that a lot of people have of having to do everything asynchronously. The performance is usually much easier to get in Pony than an awful lot of other languages that I've ever worked with. 

I do also think that from a not-trying-to-get-stuff-done-at-work standpoint, Pony is an excellent language for people who want to learn the language, runtime stuff, or just because. Anybody who comes into the Pony community right now and wants to contribute, we will happily accept them as long as they're not a prick.

We will help them and we will teach them and get them so that they're productive. I spend most of my time at this point not working on new features and stuff or everything but trying to figure out what I can do to make it easier for people to be able to contribute to politics. Like that's where I spend most of my Pony time these days, is what if I can eventually over the course of a year, make it so that five new people came in and they're contributing stuff eventually that's going to be better than my spending. All that time just being an individual contributor. 

**Adam:** In other words, Pony is great. Literally, if you want Sean himself mentoring you, I jumped on the Pony chat. Sean is just there answering people's questions, helping them out, along with several others. That's the beauty of a small community. 

It's also great if you want to work on a real, but understandable compiler or runtime. If you've built a toy language in the past, or played around with runtimes and are looking to continue that learning, it seems like honestly, a great fit. 

**Sean:** It is a really clean code base for implementing compiler features for implementing runtime features. And we have an RFC system where people can like, bring up ideas for changes they would want, and have them discuss. I don't expect, you know, that a lot of people would sit down and be like, Pony is the perfect thing for what I need to do for my job.

Because it's designed to do things, which the vast majority of programmers are not getting paid to do. They're not getting paid to write reasonably low down on the stack type stuff that needs to be handling a lot of stuff concurrently and do it safely, easily and in an efficient fashion.

That's just not what most people would pay to do. Like even when people were writing back end system stuff, right? If that's what people were being paid to do, then rails wouldn't have taken off.

**Adam:** Yes. But there are some fun problems down there. Low in the stack, I guess.

**Sean:** There are a lot of people who really enjoy working on it, but in the end, it is compared to the broader like some of what everybody's doing, it is a niche problem. They will never ever be a Pony community, that's as big as JavaScript, it just won't happen. 

**Adam:** Yes. That makes sense. Like, how do I know if something that seems unproven is worth the risk? 

## **Taking the Risk With An Unproven Language**

**Sean:** A lot of engineers that I know. I don't think that they follow a very good approach when they're picking tools in general.  I don't think they really stop and think about what their goals are and what they really need in order to accomplish those goals, right? This isn't just in picking tools but it's like I have a feature to implement, right?

Most people usually don't think through what really are the goals of this feature?

What are we trying to accomplish? What are we willing to trade-off? What is important to this? 

**Adam:** So we started with a problem of making something like an order of magnitude faster than the existing solution, then Apache storm. We chose our tech stack and it was built. There's one thing that we're missing to wrap up our case study. 

**Adam:** All right, back to Pony. 

**Sean:** Tangents, tangents, I like tangents.

**Adam:** So did it work? So you guys took Pony, you built, you were going to build a storm,  something better than Storm, right? Lower latencies. How did it go? 

**Sean:** I don't like to use the word better because we had different goals. Right? For everything I've said earlier about languages, I didn't say, That's a bad language or anything. The goals were different. Right? but for what we were trying to accomplish, it was a much better tool for those types of scenarios that we built it for then, then storm.

Yes. Going back, to what I find beautiful, right? About a year ago when we were at Wallaroo Labs, we put a system into production for PubMatic. They're an ad tech company. It was the first system to go into production that was going to be taking a ton of data, as lots of data for the system we built.

And we're all like we are all worried about what's our on-call thing going to be for this, et cetera and everything. Right, it's almost a year later, not a single issue. 

**Adam:** Oh wow.

**Sean:** There was one issue and that was when somebody went to upgrade something and didn't follow the upgrade instructions. But for the stuff that we built, that was processed at the peak, about 80 million calculations second handling hundreds of thousands of incoming requests a second with packed full of data, which would blow up into like 80 million calculations a second run in for a year. Not one teeny tiny little issue that to me that's beautiful. That's beauty to me. Right? 

**Adam:** So Sean focused on the features of his hard problem that led to a seemingly crazy solution using Pony. But it actually made sense and it worked out. He had to minimize latency and maximize throughput so he needed something very performant. He needed to minimize network hops and copying, and he had to do everything async. 

Maybe you have a use case for Pony?  Maybe not, but I bet you have to make technology decisions that are the right choice and could save or sink a project and that's what the story was all about choosing the right tool for the job. I hope you like this case study. If you have a case study about a project you worked on. Let me know adam@corecursive.com. 

I think we need more of these case studies so that we can all learn from them. 

Until next time. Thank you so much for listening.
