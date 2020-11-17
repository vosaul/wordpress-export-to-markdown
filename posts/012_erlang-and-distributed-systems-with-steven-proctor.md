---
title: "Erlang and Distributed Systems With Steven Proctor"
date: "2020-07-21"
---

Erlang evolved to support distributed computing.   It became functional because of the need to limit side effects.  In this episode, Steven Proctor discusses what he’s learned about functional programming and applying FP principles to various non-FP contexts.

"So there's, some management around that as well that allows me to essentially do my database migration on the fly because my database is just the state that the process holds and not an outside database." - Steven Proctor

"If you're in a team where a bunch of people may or may not be familiar with the functional programming ideas, you start introducing immutability everywhere. That might be a harder push. As opposed to just saying, "Okay, well let's think about how we're changing the data."  - Steven Proctor

"Essentially Erlang was a language that they evolved and what sounds like a very agile way of sitting with the people who are actually going to be writing the software and building a tool for them that solves their problems. And so early on it became out of the necessity of the problems they were solving." - Steven Proctor

### **Transcript**

_This is a machine-translated transcript. Podcast page for [this episode is here](https://corecursive.com/012-erlang-and-distributed-systems-with-steven-proctor/)_

### **Introduction:**

**Stephen:** Let's do this. Let's do the object-oriented idea, which is a good idea. And we're just gonna turn it up to 11.

**Adam:** Hey, today's interview, we talk about distributed systems and functional programming, specifically a lot about Erlang. And also we touch a little bit on my favorite topic, which is building your own mechanical keyboard. Proctor is the host of the functional geekery podcast, and also runs an Erlang meetup. Proctor, welcome to the podcast.

**Stephen:** Thanks for having me.

**Adam:** So I'm a longtime fan of your podcast and I have some questions for you. What is functional programming?

### **Functional Programming**

**Stephen:** What is functional programming? I'm not really sure, that's one of those things that I've heard a bunch of other people get frightened, say their definitions, and I've heard the quote, I think you ask a thousand people what functional programming is. You'll get at least 1,001 different answers. So I think at this point, the basis for what appeals to me at least of functional programming is limiting side effects, and by limiting those side effects, you drive towards what people commonly think of as functional programming solutions. It comes down to limiting, in my view, where the side effects in your system happen.

**Adam:** So you try to limit the proportion of your codebase that does side effects to the minimum part that you can. So what's the advantage of that?

**Stephen:** So for me, that gets back down to having worked on an app at one point for 10 years, there were a lot of innocuous decisions or decisions that seemed innocuous at the time that five, seven, ten years later, it was like, “Oh, this is real pain”. And so I started feeling these pain points and it was trying to figure out what these things are and some of that came from the test-driven design side and making contracts and kind of sending me the hint of pure functions. It's easier to test if the data coming out is dependent on data coming in and doing and getting rid of mocks.

So if you have to mock it, you realize it's harder and these ideas were kind of setting the foundation that when I saw functional programming, I was like, “Oh, okay. I see where this, like this thing, is going even further, a single responsibility principle and object-oriented says it has one reason to change.

Well, if you take that to the extreme, at a certain point, that's just an interface with one method on it, and that method is really almost a function because you don't change the data underneath it, you just change the behavior or you have interface segregation principle and object-oriented side, which are things that don't change together, get separated out.

And so if you take that to the extreme, well, every interface is just one function. “Can I push something? I have something that's pushable”. I can push something onto a stack. But I can push something onto a list, or I can push something on to do this. And so the interface is really pushable, which is just a push method, things like mappable, or I have things that are poppable, or I have things that are innumerate where I just iterate over the next and I can just call “next” and that becomes like a string. So some of these ideas, we're kind of setting that thing. And I saw functional programming and realized that some of these things are functions.

And I kind of realized that if I want to limit these changes, I can start doing this. And that's kind of where the appeal for functional programming came from me, was all these principles that yet are object-oriented or procedural, they're the same principles on functional programming -- they're just looked at from a different side and almost taken to the extreme because data is one reason you need to behave another reason to change. So maybe your data and your behavior don't necessarily belong together. And so it was a lot to know all these things that kind of pushed me down that track and seeing what are those things that go and what are the common principles, whether or not it's from functional or from OO and so there were a lot of these ideas that formed that I think functional programming to me is just a lot of these ideas about, how do we control what goes on in our system? And by pushing to these bounds, you wind up in a more functional programming oriented mindset.

**Adam:** So you're saying functional programming is sort of best practices from the OO world, you know, taken to a more extreme stance. So do you find OO and an FPE like in conflict with each other or do they sit well together?

**Stephen:** I think they sit well because there are points at which you need to actually modify stuff. And I think in that case of modifying stuff, the object-oriented side can fit together. And some of this object-oriented side is more of the Allen case, Smalltalk vision of message passing between things.

So this is where people who are familiar with Erlang, say Erlang is actually both functional programming and it's object-oriented and it's probably one of the more object-oriented languages besides Smalltalk that you actually find, maybe Eiffel's up there as well. But I think there's a lot of the sense that they live well together to a certain extent, now again, I haven't gotten into monads and free monads and a lot of these other side effects capturing concepts. So I'm not quite sure how well that fits in, but I've heard other people, Michael Feathers, I believe Gary Bernhardt, I believe in a couple of other people talking about functional core, imperative shell and some of this stuff is Allister Coburn's architecture. The outside of your system, you push everything that does side effects as far out of your system as you can. And you keep the pure stuff and you keep the center, you keep the core domain stuff as pure as you can. So I think there is a place where both of these fit in because eventually, as a lot of people, that if you didn't have side effects, you wouldn't be doing anything.

Because even at the purest level, running this computation is going to eventually make your fan run hot. So there are some side effects there. On our current architecture, it's controlling those and pushing to the outer bounds of the system. So in a lot of cases, for anybody who's doing object-oriented programming, people talk about checking your data at the perimeter and assuming once it gets inside your system, all the data's good.

So do all your null checks at the very edge of your system. Assume once you're in your domain logic, you'd never have any nulls if they take that idea and you just treat that with side effects as well. Put all the side effects at the outer boundaries of your system, and then anything that needs to happen already has its data, and then you can just do data transformations and modifications through the rest of your system, and it starts being easy, and then you build immutability on top of that as another way of limiting your side effects and the way you interact with things and change things.

Then you know that, okay, this thing is this. It's always that. And in other languages like Erlang and Haskell and certain other languages you only have binding. So you can only set up once in that scope too. So you know, if X is Y, X is always Y for that scope, and it's never going to change, and all of a sudden X becomes Z so that's the view that I found and suddenly I don't get to do functional programming day-to-day. As a lot of people would say, Oh, you're working in a Haskell, or you're working in an Erlang or Elm or CuraScript or Scala, or pick your closure or pick the functional language of your choice.

A lot of this is still, okay, I'm in JavaScript, or I'm in Ruby, or I'm in Bash programming, or I'm in whatever it is that requires me to do it. How can I essentially bring the most sanity to what I'm doing?

**Adam:** So that's a good question. So you're saying day to day you're working in Bash, in Ruby, in JavaScript, so how do these principles influence what you do in those languages?

### **Principles that Influence Languages**

**Stephen:** Some of that is like all good answers. It depends if there are certain areas I try and think of data transformations first, which becomes easier in certain languages. Potentially, JavaScript might be a little bit easier to pull that off if you fold in underscore or low dash or potentially you can sneak in some Miranda because people understand underscore, and you can just kind of say, well, here's underscore, like improved and evolved. So pretty much everything you know about underscore, here's a few things and you can use it pretty much the same, but if you need to and you can do this other stuff. 

If you're doing Ruby's, sometimes you can find off the place that, okay, well what if we copied this? Or what if we just took this object and returned a new object can, didn't really modify this or at least what if we think of a transformation, even if we are modifying it because of the constraints wonder, but think of this as, as a series of maps and reduce and folds in any other operations, and we can kind of just chain these things and think of it as that pipeline operator that certain functional programming languages have where you can say, here's the series of transformations instead of, okay, well it's a series of a bunch of these other calls.

**Adam:** And when you say, to make sure I understand this when you say a data transformation, you're saying immutability is like a functional programming principle, and so in Ruby or wherever I am, rather than, you know, changing the value of the user, my function can create a new user with that value change. So what do you mean by transformation?

### **Data Transformation**

**Stephen:** Sometimes, if I can get away with that. Sometimes in Ruby, sometimes in JavaScript or in these other languages to do that becomes hard or it becomes hard,  A - because that's not how that language is necessarily shaped. So sometimes there are things where you're like, okay, let's just take the hit, we can take this hit. At other times you're on an existing codebase you can't all of a sudden just go make this object immutable. That's going to break too many other things. So at least with data transformation, maybe we can outline it as a series of steps that this data goes through. So this thing happens, and then this thing happens and then this thing happens.

So yes, I may modify it again in place, which is kind of cringe-worthy, but at least. I outlined the discrete steps of how this data gets transformed and thinking about it in a pipeline or composition of these things together. Even if it is mutating the state, I can at least start to shift that mindset of it's a series of steps that we're going to do.

This is, we're thinking in an algorithm, so let's actually think in the steps and outline those steps that the data goes through, even if it is being transformed on the same objects.

**Adam:** Yeah, because there is a cost to immutability, especially depending on the language, right, of actually making copies of things.

**Stephen:** And it's not just that cost. It's the cost of the introduction to teammates potentially. If you're in a team where a bunch of people may or may not be familiar with the functional programming ideas, you start introducing immutability everywhere. That might be a harder push. As opposed to just saying, okay, well let's think about how we're changing the data.

And then maybe once we get that, we can show that, Oh, do we need to change the data? Or can we create a copy? And it's that slow evolution of some of these ideas.

**Adam:** So it's a culture war within your workplace where you have to convince them that you're not crazy, that there's, that there's some idea behind what you're doing.

**Stephen:** Well, it's not that it's a culture war, it's just like anything when you introduce new ideas. A - if people aren't bought in, to begin with, just to essentially make it a sink or swim idea in something that is an existing context becomes something you want to watch out for because then you don't want to start that culture war. Right? 

If you're going into, if you're taking Ruby in saying, rewriting high Haskell, then you're thinking in hassle. If you're saying Ruby and think in terms of more functional styles in a more object-oriented language, then it may just be how do we start to think about these things? Because even then these are still potential object-oriented things.

We think of workflows. We think of pipelines, we think of potentially state machines. Even if that state machine or the pipeline is modifying the same data, can you take these ideas and introduce them? So it's not one of those things that's completely unfamiliar and you lose the battle. You lose the war before the first battle is even finished in the fact of just trying to get exposure to these things. Right? 

So there's a thing, there's the idea that more of a pragmatist that says, yes, I love functional programming. Yes. I wish I could write every code functionally, even though I'm bad at that and nonfunctional languages that don't keep me strict. So how can I, knowing my limitations, how can I make this easier for someone instead of making them swallow everything at the same time and slowly expose these ideas and build upon ideas little by little and exposure by exposure and saying, okay what if we did it this way? How do we think about this? Like instead of redoing and re-introducing someone and making them feel like they don't know anything about coding.

Or challenging and saying, “you don't know anything about coding. Here's how you do this and this is the much better way. Even though what you're doing has worked for you and you've been successful with it and your career, I'm going to completely invalidate it”. It's more about how we approach these things? How do we make this more familiar instead of, and therefore easier to grasp onto because that familiarity is there, instead of saying no now for something completely different, and I expect you to learn this in response to my will, even if the language is not even wanting to cater to my will?

**Adam:** Yeah. I can understand that. That battle can be hard to fight. But a pragmatic approach, I think always makes sense. You mentioned Erlang so for anyone who's not familiar,  what is Erlang?

### **Erlang as a Solution**

**Stephen:** So Erlang was the solution to the software crisis that Ericsson was identifying in the 80s they had Joe Armstrong, Robert Rooney, and Mike Williams as part of this lab that was, their goal was to, people are expensive software, expensive to write how do we do this? We need to solve this problem of making our telephones switches and doing the software for this and making it reasonable to write can you go off and solve this problem, cause we need constraints of high availability because we get fined if the phone lines are down. You don't want the phone lines cut out when you have to make a 911 call.

You don't want phone lines to go down because my call with you is ruining someone else's call because our call goes bad. So they had a bunch of these constraints, and so Joe, Mike, and Robert went off and started looking at a bunch of different solutions and essentially Erlang was a language that they evolved and what sounds like a very agile way of sitting with the people who are actually going to be writing the software and building a tool for them that solves their problems. And so early on it became out of the necessity of the problems they were solving. It became functional because they need to limit their side effects. It became functional because they kind of enhance your estate. So if things are running on five switches. If one switch goes down, you can't share that state, it's gotta be isolated. So you kind of start being functional in that way. It became a message-passing because of the way that they were dealing with concurrency. And these things can happen in whatever order they can happen, and a lot of these constraints kind of led them to invent, reinventing an actor-model, as they say. They didn't know they were doing an actor-model with message passing. They didn't realize that they had functional programming experience, but a lot of that functional programming stuff became implicit because of the problem they were trying to solve.

If we take down one computer, we take down one switch in the network. We can't crash the whole network. We need to be able to move things around. And so Erlang became this functional message passing system that was designed for high throughput, high availability, had things to schedule, so it was near real-time requirements, not absolute real-time, but very near real-time. So they couldn't start any piece of work for too long. 

There were all these other constraints that made them wind up with Erlang as it is, and it became a very interesting language and it made me, one of the things that I appreciated about Erlang was it made me rethink how some of these systems work. There's a lot of distributed systems stuff that gets tied into the Erlang ecosystem.

**Adam:** Like they were doing distributed cloud programming. I mean, it wasn't called that but it was definitely distributed programming like way before everybody else.

**Stephen:** Yeah. Because all these switches were everywhere. And one of the things that Erlang did was because it was isolated because they had the code across the switches.

If a switch crashed, they needed to be able to recover from that crash. And some of that is their way of supervisors and management of applications of what they call applications, which are like micro apps,  with supervisors and workers. And then they, because of the distributed sense, and if this thing happens, we don't know where which switch it's going to be on. And so they had an idea of location transparency. They have this process identifier and that is encoded where this is running, which no, this is running on, but for all intents and purposes, you as the client don't really know and can't really be involved about which node this is running other than a few constraints about, -- you can't manage as you can't supervise something that's on the other note on another node.

But if you're just sending a message to something, you don't care if that's your local machine, you don't care if that's a different machine. So all these things that they were doing were this simply distributed cloud in the sense because if we're going to put this on however many switches, we don't know at any given point, which switch is going to be running, which piece of code and it could be running on a bunch of different stuff. It can be running in one place and we don't know, and we add a certain point, don't care. And so yeah, in the case it was essentially a managed cloud in away. These switches were servers that were managed by this, but when it came down to running it, which piece of code is running on which server?

Well, who knows? Maybe this code, just something else from down in. Then we start up another instance on this thing because we can't communicate that. So we've got a process that just spins up a new application here and starts managing that life cycle here, and we can broadcast that, “Hey, we've got the service running”, and so there was some stuff around that are very much the problems that we're hitting today with my understanding of Kubernetes and some of these Docker orchestration levels and microservices and all this other stuff about making what's running where invisible and not really caring about it, and having these small things that if they crash, how do we monitor that crash? How do we restart it back up? “Okay, good. We got it. Did we start-up in this area? Maybe not.”

**Adam:** I never thought of this Kubernetes connection, but yeah, I guess for anyone who's not familiar, like my understanding may be wrong, so just jump in there. But like the message passing actor system in an airline is like each, each function has a mailbox, right?

Which is basically a queue. So messages are considered in front of it and pile up and, and it runs within a cluster. So it could be running on one machine or another. Right? And I guess, yeah, I can see what you're saying. This is very similar to sort of a microservices architecture except for a lot more lightweight. Right? Because you talked about today, like, you know, I have a Docker container with a JVM instance running in it, and that's being distributed by Kubernetes and there's a whole bunch of other things. But in Erlang this is just actually a function, right? Like it's a much, much smaller unit of distribution.

### **Distinction Between Function and Processes**

**Stephen:** Yeah. And there's a little bit of a distinction, just to be clear is between functions and processes. So processes, run functions, so you can actually call a function without having to go across that mailbox boundary. And depending on how you define it, I know I've done early days where it's like, okay, well everything is concurrent, so let's round up a whole bunch of these things and like every module is now its own process. 

Well, sometimes I get you a bottleneck. If you've got a hot code path, now you're going through a mailbox. When that could just be I can invoke it as a function or I can start it up as a process. And that was one of the questions that I kind of was talking to, with Martin Logan on one of the early podcasts, is how do you define that boundary of what's the function, what's just the function in the module, and what's the process that you spawn up to handle something.

And so that's kind of the same in the microservices world of at what point do I start-up service and on focused service to do something versus at what point do I just call a function and even Lambda on AWS, another function as service things are more than just a function, right? Those are still super small services because if you need to calculate a min and max value, you're not calling up a Lambda to invoke max to give 2 numbers. Right? So there are certain things you start to think about. This is a functional unit, but maybe there's still functions here. But when I need to do side effects or I need to go to outside stuff, that's when I start to figure out where those boundaries are, when it gets elevated from a function to a process.

And the confusion, I think where I've seen people get confused about the process and function. And I think where I started was to start a process you just essentially give it a function. So if you just have one function that runs, that can be a process. You can start up a process that just invokes this function and if it just does something and immediately returns, that process spawns up quickly, does its work, and dies. And sometimes when you're first learning this, I mean. I know I fell into it. A couple of other people I know have stolen into it like cause everything, and that is one of those things that you have to figure out where does it make sense to have a process that's the equivalent of a max function or a streamlined function? Or do I just call that as a function with a module namespace?

**Adam:** How do you decide where to draw these lines?

### **Process Boundaries**

**Stephen:** One of the good ideas was after I asked Martin Logan, I asked that question on that when I was still trying to process it myself, his answer was “what are the concurrent operations?”

So that was one of the things that informed it. He gave an example, I think it was Lambda Dam up in Chicago a number of years ago that was talking about this, and he outlined a vending machine. And he said, here are the parts that are concurring, like if this thing goes down, what parts of the vending machine could still operate?

What parts of the things are concurrent in isolated factors? So some of that is what's concurrent, what can be run whenever and in whatever order. Some of that is back to supervision. The supervisor has a restart strategy, so it can monitor the work of processes. And some of those can be other supervisors, but it can know when that process terminates.

Some of that boundary is if this thing terminates, what goes along with it? What has to, if I have to terminate and restart this, what kind of failures cascade, and how do they cascade? Well, I think one of his examples of the vending machine was if my money, the part that takes in the coins, takes in dollars and dispenses change in accumulates change fails, when that dies and when that error is out, does that fuel the cooling system that keeps the drinks cold? Well, if the refrigeration of the cans and the vending machine die when the coins become inoperable, or there's a jam or it's out of money and you can't take money. Well, that there's a resiliency boundary there. So maybe those are different processes.

**Adam:** Isn't it true that the cooling system doesn't even interact with the change system? 

**Stephen:**  Yeah. And so, therefore, if the change system dies, why do you take down the cooling system, Right? So those become two different domains in your system that become obvious process boundaries.

**Adam:** Because just because things interact doesn't mean they have to be in the same process, I'm assuming.

**Stephen:** Correct, and some of that's the concur. So the first thing was what are the concurrent pieces of the system? Right? So the cooling thing can operate independently of the change. So once you start to realize that, you start to see, Oh yeah, maybe it is taking a step back, “do I really want to kill my cooling when my change goes or vice versa?” Okay. There's a boundary of some processes. The other part is some of that state management and which processes hold which parts of the state. So once you get the dividing line of some of those concurrent activities and failure modes in which things are actually related to each other, you say, “Do I have an individual processor each rack of drinks potentially in that vending machine? Maybe I have something there and if I'm empty in one, do I or if that one, huh? Spinner or release or whatever dispenser is broken for that spot in the vending machine. And that has the state of its own sodas or its own beers, whatever you put whatever you're stocking in that vending machine. So if A3 breaks, does that break A2? Does that break A6?” So that one can break so that that has its own state. It has its own level of how full that thing is. So the full row of maybe the same drink, cause that's a very popular drink. What if one of those lots in that row, do I want to have everything else right? So if that state gets messed up, if that thing's empty, can I not dispense any other things? So there's a little bit of isolation there. And the fact that it's got its own state, it's state mirrors other states.

**Adam:** I think one of the important things about the data is that, because each process is single-threaded, it's a good way to prevent concurrency issues with data, right? If you're like this very small process, this very small instance of whatever, of a thing that's running is the only thing that can touch this state and it has a message queue. So, like work, it needs to compile up, but only ever one, you know, the mutation will happen at a time.

**Stephen:** Yeah, absolutely and in that process, that process is single-threaded, but you extract the concurrency out and that gets one of those things back to the object-oriented side is decided concurrency side effects. Well, now I'm single-threaded. I don't have to worry about concurrency at this small level.

I've pushed that out and there is concurrency. Well, the concurrency is different things being concurrent, not, I have three different things modifying the same state at the same time.

**Adam:** Yeah. The way I think about the actor, you know, the model of concurrency is like an actor, as a person, right? It's like the concurrency model is like, you have like a guy or like a gal, like a process that's sitting there and only it can manage this data that's it's in charge of, so like there can be as many things in parallel telling it to make various updates, but they just get put in its mailbox and it processes them one at a time and that's kind of, that's the way that they kind of cut that, not have concurrent data.

**Stephen:** That was one of the metaphors, I think Alan Kay said as long as cells were isolated. But if you take it out and it's an actor, yeah, “you, I send you a message. If I'm going to, I might send you an email and someone else might send you an email and someone else might send you an email” and you're only ever going to work one of those emails at a time.

We don't communicate, we're all locked in rooms and all we have is that little Dropbox of an inbox and an outbox that we can communicate through. So whenever I do, you don't know.

**Adam:** Yeah. And I mean, that's quite functional, right? I'll use your only inputs are,  the smell box and your only outputs are. Also the mailbox, and it ties back to your, single responsibility principle, I guess, right? Because you're like, this process is in charge of the, A1 row of this vending machine and that's it.

**Stephen:** Yeah, exactly. And my responsibility is either to supervise things that are doing jobs or do a job. 

**Adam:** So what does the supervisor do? I know you, you've mentioned supervisor a couple of times, but,  what is the role?

### **Role of Supervisor**

**Stephen:** So a supervisor essentially as a process that monitors other processes. So it has children processes in the supervisor, and you can either have workers or can have other supervisors. So you can get this nice nested hierarchy of supervision.

You can think of it like, the company you're in, right? Hopefully, it's the same company and you're not reporting to multiple supervisors, but you've got a supervisor at the top level, so maybe you've got the CEO, CEO has its own set of supervisors that’s the CIO, the CTO, the CEO, all of these other whatever levels that organization has, they have their supervisors, but they also have people who don't supervise and do stuff. So they may have administrative assistants, they may have some other people who do research for them gathering data, go to meetings for them, but they don't report, they may have consulted, uh. Not consultants as in contractors, but people that they go through and say, okay, you're my sounding board, so I'm going to bounce ideas off of you. You're a domain expert, so you've got this thing, you've got these, you might have this whole hierarchy of an organization and you have a hierarchy of an organization in your code.

You have a web server that handles multiple web requests. So every time you get a web request coming in. And a lot of applications, you have something that says how many, what requests can I have at a time? Okay, this web request goes off and does some work. It may have its own set of the hierarchy of things to do.

And so all these processes are isolated and you get down to the things that are actually doing the work. And so when this thing does work, It does his job. Supervisor, you can have long-lived workers or you can have just dynamic workers, but when a supervisor detects that the workers are not working, so the supervisor thinks it died, it's not responding to any messages.

It gets a message that this process is terminated. It can take that and it can act on that and say, okay, well, this process has died. What do I need to do? Can I restart that? How do I restart that? And how many restarts can I do in a given period of time? So the supervisor has different, they call supervision strategies and thresholds.

So if this thing keeps crashing and crashing and crashing, well maybe it's time for me to just die myself and let someone else higher handle this error. So it's part of an error propagation strategy too. Dave, Joe, and Mike and Robert have joked about this, have you tried turning it off and on again, that's applied to processes via the supervision strategy.

If you've used Word or Excel or Outlook and something's acting up, sometimes you might have multiple Word documents and this thing is acting up. Okay, well let me close that one Word document. Reopen it, restart it, reopen it. See if it's still acting. If that's acting up, maybe I close out all my instances of all my work documents that I have open because I have 10 different word documents that I'm working on now.

Okay, well, does that work? Okay, cool. Now I'm back and I'm in a known good state, If not, okay. Well, now I close every office program because there's some shared library code and office and maybe something and some sort of shared state got affected. So maybe I close all of the offices down, close my PowerPoints, close outlook, close Excel, and reopen it and restart Word.

Okay, cool. Now that's working. If that didn't, well maybe it's time to go nuclear and restart the whole computer. Right. So you've got the supervision strategy, which kind of is levels of escalation of, can I handle this air? Yes. okay, let me try, okay, cool, or if I keep getting repeated failures, it's like, I can't handle this. Let's escalate it to the supervisor above me.

**Adam:** It definitely mirrors the way that, like debugging works. I think that also, isn't there an Erlang phrase about to fail fast or I don't know. If you don't know what you're doing, kill yourself. I'm not sure.

**Stephen:**  they talk about failing fast. Let it crash.

Okay. So. Some of that is, again, back to the separation of concerns and do one thing and do one thing well. If your code crashes, there are some things that you might know about like, Oh, okay, I got a file. That file is not there. I expect it to be there, so if I'm writing, I just typed that file and reopened it.

But if there are things that I don't know how to handle, don't litter your stuff with the try-catch in error handling clauses and if checks and all this stuff essentially code for the half your path. And then if you, there's something that you can't do, your code is not responsible. Your process, your code is not responsible for handling that.

Escalate that up. Let the parent, let the supervisor know how to try and handle these failures because then you isolate your error handling from your work and a lot of cases you get some of these languages. Where are some of these, some of this code where? You've got all these guard conditions and you're like, what part is the error handling and error checking and making sure that the contract's good and what part is the actual work?

“And I know I've been in places where I've even written code that was probably 75% error handling and 25% work. And maybe that's a good ratio for that piece of code. Now it's like, okay, how can I actually understand what this is trying to do? And I can look at the error handling as a separate concern, this is okay, here's the case when it crashes, how do I handle that? And so I'm going to let it crash and I'm going to restart from a clean state cause maybe I'm assuming that something got corrupted again.” Okay. The joke of “have you tried turning it on and off again? It goes to your processes.”

### **Restart from a Known-Good State**

**Adam:** So do you still have the 75% of the code that's air handling, it's in a different place or, or is it not needed anymore or

**Stephen:** You still have some of it?

It gets moved to a different place. So then it gets condensed because now you're handling a set of classes of errors. Instead of every potential different permutation of it. And then the other side is maybe it just goes away in some cases because it gets reduced because you're like, “I don't really care about that class of error. Let me just retry this process. Let me turn it off and turn it back on again. I got into a bad state.” I don't, now I'm like at a certain point, and some of those things are like, well, if I've got my state. And it's not necessarily for your function because I've got an internal state. Let me just retry this and just restart from a clean known state.

That's well, and maybe something because these processes hold their own state. Maybe some message came in that eventually caused it to corrupt its own state and get into a bad state. So you just say, instead of me trying to figure out all those error conditions. How can they get into a bad state? We just say like, “kill and restart it with with a fresh state”

**Adam:** So it can be simplifying. That's good. One thing about Erlang and I guess maybe about the actor model in general like it doesn't seem to work terribly well with types. Like, I mean Erlang itself is a dynamical type language, to my understanding. And then like there are other implementations of actors like I know ACA on the JVM, but also it tends to be untyped as well, just because these messages coming into these mailboxes can be anything I guess.

**Stephen:** Erlang is a weird mix because it’s typed. I think it's got eight or 10 types that it can be, and then you just build out more complex types, in a sense that everything is either a tuple, a list, or hash kind of thing, or an atom, which is just something that refers to itself.

So the types of error, the ways more dynamically leading, at least for Erlang and some of this is, I don't think it's impossible to do because they have dialyzer which you can give type specs and document this stuff and it's for outside. Some of the catch is you can be running these systems and running these nodes and the messages might change and evolve.

So the message becomes a little bit more dynamic because you could be dealing with different versions of the code writing because this thing got upgraded and this, this node got upgraded, this node didn't, this process is still running version one of the API where this version is running node three the API, and it tries to send a node, one to node three messages.

So you might have a little bit more dynamic side there with that because you don't necessarily know which code is running and there are upgrade paths that it can go through so you can do some matching and pattern matching, all this stuff. But my understanding was there was more about the dynamic and long lift code because one thing we didn't touch on earlier is it's got code upgrades, which means you can keep your app running and it can hold two versions of your code in memory at the same time. And once it crosses a fully qualified function call, it will upgrade you in the new version of the code. And so sometimes if you say, this function takes this type of a, and now it's type of a prime, well some of that could be due to “How do you compile that when you can be running multiple versions of your code at the same time, and how do you manage those types?” And so I think some of those were just kind of,

**Adam:** It's a constraint

**Stephen:** That's a little bit of constraint and pragmatic solution that says, sure, I can compile all this and again, it's like if you think of microservices right. I can determine a contract, but that contract is an HDP request or a message and a message to you or something else. If I'm going to communicate across these boundaries, I don't know who, I may not know who is calling me, so I just have to essentially match on these things, handle those messages I can, because it could be any one of these messages and how do I do what type system like that when the types can evolve in the code can evolve and I can have three different versions of my services running at the same time, the kind of thing in which services are going to hit.

**Adam:** So how does it work with the hot code reloading? Like, okay, if I update this, this, a receiver of this, of this, a queue of this message, a mailbox, that's the word I'm looking for, so I update it but now it's expecting like a new field. but then, you know, the old messages are still in the mailbox,  too. So do I explicitly handle that case?

**Stephen:** So each process has its own state and its own message. So when you get different versions of the messages. You can, you have to be responsible for how to match on those different versions of the messages you get in. But you also have versions of your state. So maybe I have a user and instead of having an email address associated with that user in this process manages the state for a user. The state now went from a record or a map of name to string an email to string two and that's version one and version two. It might be the name of string, and Emails instead of email, which is a list of strings. So now you have to say, this state that this process holds onto while it's running, how do I upgrade that internal state of what this user represents?

And so there's a code change callback that gets invoked when it says, “Oh, I see you've got a new piece of code here. We're loading a new piece of code. We're going to take that state. I'm going to give you that old state. Here's the version, and go from version one to version two, and then your code and say, okay, well from version wants to version two I have an email that needs to go to the emails and I put that single email in a list and now I have other things I can do by appending in my new code.”

So there's, some management around that as well that allows me to essentially do my database migration on the fly because my database is just the state that the process holds and not an outside database. It has its own private variable. That's its internal state. That is Database non-persistent holds in memory that it holds onto, but how do I do migrations of that data? That state between version is the code while keeping that code where the

**Adam:** Migrations are per actor and that makes sense. I think you helped to help me to understand that. I have a kind of a general question for you.so how, how do you learn. It seems to me you've used a lot of languages in your time.

### **Learning Process**

**Adam:** You've played around with a lot of new technologies, so how did you learn about Erlang and other things? What's your learning process?

**Stephen:** Yes. Reading a bunch of technical books, trying to find things just across a bunch of different topics, and eventually got me into picking up SSEP, picking up closure, closure evolved into hearing some podcasts about .Net Rocks! with Brian Hunter. Talking about Erlang hearing some other people talk about the Facebook messenger and Erlang and rabbit and Q and Erlang and couple of these things that were kind of getting popular at the time somewhere around the 2010 areas are putting me on my radar, more moved into a job where they had somewhere Lang as well.

So work to pick that up and start putting it on the user group. So the user group became one of those tools for forcing me to learn because now I have to explain to other people. So essentially, I don't have to run the bear. I just have to run. becomes I have to ask you your question. I can answer it. I don't know at this meeting, but now it's something on my list. You understand well enough to explain the answer back at the next meeting in the early days. So essentially the best place to teach from is the person who just learned it. So putting myself in that route, and then the podcast, I find these languages and I hear something else and that works in an interest.

It's like, well, okay. A lot of these podcasts episodes that I do become curious about, okay, let me ask questions. Let me see what kind of high-level concepts I can start to put together and get a very high level, but a very incomplete picture and see how some of these things fit together. What are the common patterns across languages?

What are the common patterns across paradigms as well, as I mentioned, where there seems to be a lot of ideas and functional programming seem to be? Let's do the functional programming idea, which is a good idea. Or let's do the object-oriented idea, which is a good idea. And we're just gonna turn it up to 11 and then what's common between Haskell? What's common between Erlang in what’s common between Elm or Closure and the dynamic versus static languages in the strongly typed languages and what are these things? And like if you listen to me talking to Edwin Braidy about interest is like, I've just heard about this. I still really don't understand this.

Help me explain it. Then eventually I get enough people where I can start to ask more and more intelligent questions, but I also go in knowing that, well, if I'm asking this, I'm sure I'm not the only one, so maybe someone else who doesn't know this can be able to piggyback off my learning.

**Adam:** I interviewed Edwin Brady too and I have an interesting book and I've been working my way through it, and I found him to be super modest like I was kind of blown away by all the things that this language presented and he was kind of like, go, yeah. This is what it does. A lot of these ideas just came from other places and I'm just polishing them up and presenting them for programmers to use, and he was so modest.

It was a bit surprising. I guess I'm used to people kind of wanting to push their technology. So, speaking of technology and your learnings, what are you excited about right now with all your interviews and your reading? What technologies are on your radar?

**Stephen:** Idris is still one. I want to get deeper in understanding dependent types. Haskell is still a bit on my radar and trying to take some peeks in trying to understand some of the concepts better than enforced purity and say, okay, well I know I get impure. The lists are interesting because of all the meta-programming stuff and creating that codeless data and macros and how do you actually design a real DSL and essentially designed from the outside in and say, well, this is what I want this to be, let me write this and then I'll figure out how to transform this either via macros into something that's actually usable then you get things like reason, which is appealing from a different perspective of how do I take this? This is OCaml made friendly to JavaScript, so it's not quite okay. OCaml syntax, but maybe I could do Ocaml and use their compiler or buckle script, compile OCaml down to JavaScript. But even shorter is if this is designed by the intent that we want to make this bring all these ideas from functional programming and OCaml and make them more easily accessible to the JavaScript community and make it more familiar instead of being looked at and saying like, “this feels like a far stretch because now I've got to learn A a syntax that's completely different along with completely different ideas. Ocaml seems appealing and our Reason seems appealing in the fact that we're taking this and will this be coming up soon enough that it might actually be reasonable that where people talk about coffee-script or TypeScript.

Now probably TypeScript more than coffee-script, but coffee-script a number of years ago or any of these babbles and taking some of these other JavaScript, even if it's future JavaScripts, are finding these functionalities of is Reason close to being something that could be more mainstream, more and more introduced into a workplace environment with people who aren't necessarily the functional mindset co converts, but be able to start introducing this and say, look,” here's the way to do this. You've seen coffee-script, you've seen TypeScript, you've seen some of these other things. How much of this stuff, they thought that far of a leap and now we can start taking advantage of some of these ideas. Elm interesting for the react to stuff.

**Adam:** I think ahead JavaScript is really an interesting space now, isn't it? With all, I mean it's just become the assembly language for a bunch of other languages.

**Stephen:** Yeah, and the closures again, closure script is appealing on a personal level. Elm and pure script are appealing on a personal level. I think. Reason why might have a chance of being one of those nice introductions to getting more functional JavaScript without feeling like the burden of having to learn a new syntax with Elm or pure script or going full-on closure script of parentheses everywhere.  Again, I like Elm. It actually pointed to a couple of coworkers to Elm when we were doing a react project using Redux.

I said “play with this. Look through the Elm architecture. That's an interesting idea that we've had back and forth between these things. So some of that stuff is looking at what are the concepts and what's appealing. That means I can bring that back easier. So in the Elm perspective is how I can understand Elm and the Elm architecture play with that a little bit.

And then bring it back in. Now when we start doing React and Redux, I've got a head start because I've understood the Elm architecture, which is what Redux was kind of ripped off of and exchanged their ideas from. So that's kind of the perspective I take in a lot of this stuff of learning. What are those principles that can come out and what can I learn from the principles that I can then apply, even if I don't get to do them?

Functional programming directly in this thing. I understand those principles and practices that can help make some of the stuff I'm doing more sane than if I were to just go off and not even think about some of the stuff.

**Adam:** I can understand that, and it's interesting to see these concepts move around from language to language or framework to framework.

Totally unrelated question.  I was kind of stocking you, looking at your blog and I saw that yeah. Are you into, like custom keyboards? Is that true?

### **Building Your Own Mechanical Keyboard**

**Stephen:** Yeah. I got into mechanical keyboards a number of years ago, and then. I haven't gotten in via another co- coworker. I got hooked on mechanical keyboards. He reinforced the ability to do custom keyboards.

**Adam:** Very cool. I have a plank keyboard here and I have my customized firmware. I think it's pretty cool stuff. I actually have a couple of commits and the QMK a keyboard firmware?

**Stephen:** Yeah, my coworker got me hooked on some of this stuff. So I had found Steve washes a modern space next to the keyboard. Post a couple of years ago, and I started following his advice. So I kind of mud on my laptops like, I use them and we'll get them, we'll get the Holy Wars going on a little bit, but because then we use the escape key, and I never used the caps lock key.

I turned the caps lock into control on escape, and then that software was carabiner or it stopped working with high Sierra. So based on my coworker who. Created essentially mini dongles. I went off that route and started doing me USB adapters, so I could actually put the firmware as essentially a keylogger slash translator from what's the song, will keyboard key into what I want, and it kind of just went down the rabbit hole and did a couple of adapters for a coding keyboard that I had, a Doss keyboard that I had.

And then found an old Apple and 0110 from 1984 and 1985 that takes the phone Jack connector and actually created an end adapter. That's a phone Jack connector on one side and RJ 22 and USB on the other side. I started going down that path and within the past year, or actually, within the couple months, I just finished an ergo dose and then started to love them.

So kind of went down a little bit of the hardware hacking route as well. So that's one of the other things that sounded interesting as far as upcoming topics. There's some flex about functional languages running on hardware.

**Adam:** Yeah. The one I've been interested in is because like the QMK firmware that my keyboard runs, and I think ergo docs can run it as well. I have an old ergo doc somewhere like it, it appears to be mainly composed of C macros. It seems hard to understand. So I want to look like a rust version.  because you know, Rust is supposed to compile down to, you know, a very small runtime and C equivalent. So I'd love to see some of these more modern languages. Taking a stab at keywords, keyboard firmware, it will be awesome.

**Stephen:** Yeah. And I've seen some, again, closure with a macro system or some of the Haskell with the types. Do you know that? Yeah, when you did this, you didn't screw up this thing. Some of that stuff, and being able to put that on some of these smaller windows or change other microcontroller boards is something I'm anxiously looking forward to.

**Adam:** Well, I think we went over. But,  thanks so much for your time. Proctor, it's been great talking to you.

**Stephen:** Thank you for your time. Thanks for having me.
