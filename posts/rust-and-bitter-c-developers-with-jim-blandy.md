---
title: "Rust And Bitter C++ Developers With Jim Blandy"
date: "2020-04-05"
---

Writing secure, performant, multi-threaded code is very difficult. In this episode, I talked to Jim Blandy,  a free software hacker and coauthor of Programming Rust. Rust is a programming language that is used to make multi-threaded coding a lot easier. 

We talk about what problems rust is trying to solve, the unique language features and type system of rust and why it is so hard to write secure code.

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/6580284/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

“it's targeting all those bitter C++ programmers who are sick and tired of writing security holes.  ... You are writing the code, which is going to go out in front of ... millions of people.  If you're the reviewer, you're sort of like the last line of defense. This is the last chance for a bug to get caught before it becomes an exploit.” - Jim Blandy

“You want to make them say ... I can handle it. I can get things done. Even though Rust is restrictive,  I can overcome these things. I can take this limited, buttons downed system and make great things.” - Jim Blandy

“Rust is just a really good, productive language to work in. It will make you worry about a bunch of things that maybe you thought you shouldn't have to think about.”  - Jim Blandy

### **Transcript**

**This is a machine-translated transcript. Podcast page for [this episode is here](https://corecursive.com/013-rust-and-bitter-c-developers-with-jim-blandy/)**

## **Welcoming Our Guest, Jim Blandy**

**Adam:** Welcome to CoRecursive, where we bring you discussions with thought leaders in the world of software development. I am Adam, your host.

**Jim:** So it's, so it is sort of asking them to give things up. But the thing is what you get in return is exactly this guaranteed memory safety. And this guaranteed freedom from data races and it's just this huge win.

**Adam:** Writing secure, performant, multi-threaded code is very difficult. Today I talked to Jim Blandy about Rust, a programming language that is trying to make this a lot easier. We also talk about why it's so hard to write secure code to Merck's on Firefox and his insights into the difficulty of writing secure code are super interesting.

I also asked Jim about Red Bean software, a software company that refuses to sell software at all. Jim Blandy is the co-author of Programming Rust among many other things, Jim, welcome to the show.

**Jim:** Hi. Thanks for having me.

**Adam:** It's great to have you. I have your book and I really hoped I made it a long way through it before I talked to you but I could see the bookmark.

It's about a quarter of the way through.

**Jim:** It ended up a lot longer than we wanted it to be.

**Adam:** I don't think it's your fault that I haven't made it.

**Jim:** What we had in mind originally, we wanted to do something more like K&R. This slim volume just covers exactly what you need.

But basically Rust is a big language that is trying to address the things that people need and we took a little while to cover that.

**Adam:** Yes, it's not a small language, I wouldn't say.

**Jim:** Yes.

**Adam:** So what is Rust for? What is it targeting?

## **How Rust Is Targeting Bitter C++ Programmers**

**Jim:** Well, I mean the funny answer is that it's targeting all those bitter C++ programmers who are sick and tired of writing security holes. My coauthor Jason and I, we both have worked on Mozilla SpiderMonkey JavaScript engine and that is a big pile of C++ code. It's got a compiler front end and it's got a byte code interpreter. It's got two jits and it's got a garbage collector, which is compacting and incremental and generational. Working on SpiderMonkey is kind of hair-raising. Because Firefox, it's not the leap browser. We still have hundreds of millions of users, and that means that when we make a mistake in the code we can expose a huge number of people. I mean, of course, when you're working in this field and I think of all the browsers you get to see these things get published, you find out about exploits and so it really is very humbling.

And so whether you are writing the code, which is going to go out in front of all these millions of people, or whether you are reviewing the code, somebody has finished their patch and they flag you for review. If you're the reviewer, you're sort of like the last line of defense, 

This is the last chance for a bug to get caught before it becomes an exploit and you sort of getting used to it. You sort of accepting this is the way things are done. And then you start working in Rust or I just was curious about Rust because the original creator of the language, great and Graydon Hoare is a personal friend of mine.

We worked together at Red Hat. Modern Rust has gone far beyond what Graydon started with. So I wouldn't say that it's his language anymore but I was curious, I've been following its development since the beginning, so I was curious about it. And once I really started getting into it I realized that this is systems programming, where I the programmer and in control of exactly how much memory I use. I have full control over how things are laid out in memory. The basic operations of the language correspond closely to the basic operations of the processor. So as a systems programmer, I have all the controls that I need.

### **How Rust Is Helping a Program Compile**

**Jim:** But I don't have to worry about memory errors and memory safety. Just like I said, when you're working on a security-critical C++ codebase as I said, I have been, you sort of getting used to it,  And you sort of internalizing that. Like there's these, this is just the standards that you're being held to is actually perfection.

Right because that's what it is, right. The smallest mistake and these people when you read about the exploits and people show off at black hat, it's just amazing. Just the ingenuity and work and just blood, sweat and tears that people put into breaking things are really impressive.

You've internalized that and then suddenly you work in Rust and that weight is lifted off your shoulders. And it is like getting out of a bad relationship. You just sort of gotten used to being like, just treat it badly and then suddenly somebody is reasonable to you and you're like, holy cow.

I am never going to do that ever, right. And then the next thing is that, when you get to work on, concurrent code in Rust. Actually trying to use, trying to take problems distributed across multiple cores, Rust is constructed so that once your program compiles it is free of data races by construction.

So make sure not using unsafe code and in C++ everybody thinks that their multi-threaded code is fine. Everybody understands what a new text is and how it works so the criminals are not difficult to understand at all.

But then you end up getting surprised by what's actually going on in your code when you have to work on it. One of the engineers here at Mozilla. Firefox is a heavily multithreaded program. I think when you start off, there's like 40 or 50 threads that get going.

And there's the garbage collector does the stuff off thread; the JavaScript compiler will push compilation work off to a separate thread. We do IO, like for example, when a tab is trying to write something to local storage, that IO is often pushed off to a worker thread.

And it's sort of handled asynchronously on the main thread. So it's a very heavily multithreaded program. So, anyway, so we had an engineer, here at Mozilla who decided that he was going to use Chief Sam, the thread sanitizer tool to look for data races to actually look at our code and observe how well we were doing in keeping data properly so that we keep data properly synchronized. And what he found was that in every case where Firefox uses threats, we had databases.

## **What is Data Race?**

**Jim:** Not most, every single case.

**Adam:** Yes, that's kind of astounding. So let's back up. Well, so what's a data race?

**Jim:** So, a data race is when you have one thread write to a memory location, and then another thread reads it, but there is no synchronization operation that occurs between those two, that it's not like that. Nobody releases a new text when the person acquires new texts or the write isn't atomic, or there isn't like a sort of message sent right there.

There is a number of primitives the language provides that ensure memory synchronization. This is an issue for two reasons. One is that, whenever you have any kind of non-trivial data structure, the way. They're always implemented if you have a method or a function, just any operation on that data structure. And the method will temporarily relax the invariance that data structure is built on, do the work, and then put the invariance back into place. 

For example, if you're just trying to push an element on the end of a vector. Usually, it will write the new elements to the end of the vector, and then it will increment the vector’s lengths. Well, at that midpoint between those two operations, the vectors got this extra element that it's supposed to own, but the length doesn't reflect that. So there's this momentary relaxation of the invariance of the type that the length actually is accurate, or even more so if you are appending an element to a vector and the vector has to re-allocate its buffer.

So first it's going to allocate a larger buffer in memory. Next, it's going to copy over the existing elements to that new buffer. At which point there are actually two copies of every element. Which is kind of strange, which one is the owning copy, which one is live? 

### **Problem With Unsynchronized Access**

**Jim:** And then it frees the old buffer, and then it sets the vector pointer to point to the new buffer. So that's a more complicated operation wherein the midst of this operation, the vector is actually in this wildly incoherent state.  But by the time the method returns, the vectors guaranteed to be back, in shape and ready to use again, right.

And so when you have data races, getting back to data races, the problem with unsynchronized access is that it means that you can have one thread observing the states of your vector, or really of any nontrivial type while it is in the midst of being modified by some other thread. 

And so whatever invariance, the vectors methods are counting on holding. In order to function correctly, may not hold. And so, that's sort of the language level view of things. but then modern processors of course, add even further complication to the mix where each processor will have its own cache.

And, although they do have, cache coherency protocols, trying to keep everything synchronized. It turns out that even Intel processors, which try to make fairly strong promises about memory coherence, it's still visible. That each processor will queue up writes to the main memory. That is, if you are one core on a multi-core machine and you're doing a whole bunch of writes to memory, those writes actually get queued up and, reads on that same core will actually, if you try to read a location that you just wrote to, it'll say, “Oh! wait, I see in my store queue that I just wrote to this.”

And so I'm going to give you the value that I just wrote. Even though the other cores will not have seen those writes yet. And so the other thing that synchronization ensures is that at the processor level, the memory that you are about to read is guaranteed to see the values that were written by the processor that wrote them.

Assuming that both have executed the proper synchronization. So data race is a write to a location. I'll buy one processor if I want a thread and a read from that location from another thread without proper synchronization. And it can cause a variance to be evaluated and it can cause you to encounter memory coherence errors.

### **Intel Processors**

**Adam:** The, the hardware thing you mentioned is interesting and maybe it's a bit of divergence, but, so how does that work? So if there's writes queued up to like a certain sector or something and you are reading from it as it does it block until those writes go through? Is that what you're saying?

**Jim:** Okay. So this is something, the processors change over time and the different processors have different details about exactly how they do this. And so I'm not sure that I am going to be able to accurately describe as the current Intel processors, but this is as I remember it, what you've got at the basic level, you've got the cache that is communicating with each other about what they have cached locally.

Like, for example, if nobody has read a particular block of memory, then that's fine.  But when one core brings a particular block of memory into its cache, it'll actually mark that and say, okay, I've got this, but I haven't written to it yet. And it's okay for other cores to read that memory.

And so maybe all the cores, maybe it's a big block of read-only memory. Maybe it's, I don't know. Maybe it's. Strings, static strings or something like that. And so all the cores can bring copies of that memory into their caches and then use it. However, before a core is able to write to a block of memory it says, I need exclusive access to that. It actually broadcasts out on this local bus for the purpose of this kind of communication and says, okay, all you other cores, I'm about to write to this block of memory, please evict it from your caches and market as exclusive mine. 

And so all the other cores, they, they kick out that block from their caches. They say we don't, we don't know what's in this block of memory anymore. Only that guy knows what's in it. So then that processor that's obtained exclusive access to that block of memory can do it, will do as it pleases.

And then in order for the other course to actually even read from that memory. Now they have to go and get a copy of it back from, force the core that was writing to it to flush. It's what it had back to me and memory and so then it goes back into the shared state. and so they call it the MESI protocol.

### **What is MESI Protocol**

**Jim:** It's MESI which is like, I can't remember what it is. But like, E stands for Exclusive are four letters are the names of the four states that a particular block can be in. And E has exclusive access, which is when you're writing something, S is for Shared access. when you're, when it's actually just everybody has the same copies and everybody's just reading from it.

And I think I is Invalid where like somebody else's writing to it. So your copy is its focus. So that's just keeping the caches coherent. But then the other thing is that writes are a lot slower than reads. And so each core has a queue of the writes to memory that it is made, that it is waiting to write out to main memory.

Right. And so if you do a whole bunch of stores, your store queue will get filled up with the list of these things going out. And if the core, which has done the writes tries to read, then certainly it. It knows what the current values of things are. But the other cores can't see it yet.

It can't see those writes yet. And so it is the way that you can get incoherence, the way that you can end up with different cores having a different idea of what order things happened in is when one core gets a result out of its store queue, and then the other core gets the results out of main memory.

And so you can end up with different cores. Seeing write to memories seem to happen in a different order. And the history, this is actually really interesting for a long time, see, Intel would have sections of their processor manuals where they tried to explain how this worked, and they would make these very friendly promises like, Oh yes, everything's coherent.

Don't worry. You just do the writes you want to, and everybody sees them. And then there was this group, I could look up the reference later if you're curious. But there was this group, in either Cambridge, I think, or Oxford. Anyway, a very theoretically inclined group who basically said, we're going to actually make a formal model. If you know the memory, going to formalize the memory model that Intel has.

### **Running Tests on Intel and Apple Processors**

**Adam:** Like formalize it?

**Jim:** They get a little logic that says which executions are acceptable and which executions are committed by this and which executions are not permitted by this.

Now again, the specification doesn't say exactly what happens. It just says what the rules are. So it says this could never happen. This might happen. So it identifies a set of acceptable executions, not a specific, it doesn't tell you exactly which one the processor's going to do,  It just specifies a set of acceptable executions or a predicate that you could run our execution to say, this was real or this is not acceptable.

So anyway, so what this research group did is they said, well, let's take them at their word and we're going to write tests. We're going to use this, formal if we're gonna use this specification that we've written. I mean, made up,  Because all we got us English to work with, and we're going to generate a ton of tests that we will run on the Apple processor to see if the processes actually behave the way their claims to behave in the manual. 

And I mean, you can tell obviously, yes or no. That Intel themselves in their own documentation did not directly describe the behavior of their own processors. This group and the great thing about it, what was really powerful was that their techniques allowed them to just generate lots of tests and then find ones that failed. 

And then, they were able to reduce them. So when they published, they had very short examples. If you run this sequence of instructions on one core and this sequence of instructions on another core, you will observe these results, which are forbidden vibes back, 

So it was really nice. It was really just like, here's your book, you know? And basically what they found was that in general, yes. The MESI protocols do work as advertised. but the thing that you really have to add, the thing that you have to put it, you add to the picture to make it accurate is the store queues, the right queues. 

## **Rust Takes Control of Aliasing** 

**Adam:** Because if you have a write that hasn't done, then you're going to have this.

**Jim:** If you have a write that you've done, if you've just done a write, you will see that write before other cores will see it. Yes. So anyway, this is the kind of thing, 

Just to bring this back to Rust. This is the kind of thing where. It sort of raises, I think the programmer or sort of macho hackles,  You say, well, that seems pretty tough for those people but I can handle it. Everybody says that I think I catch myself thinking that It's not true. You are not up to the task of being perfect. And so to have a language where you can start, pushing your algorithm out across multiple cores, pushing your code out to run, in multiple threads and just know that you may have bugs, but they're not going to be these bugs that, it depends on exactly the order in which memory writes happened in the exact instructions that the compiler selected and things like that. It's just a huge win.

**Jim:** So, data races are out.

**Adam:** Yes, data races are out.

**Jim:** So how?

**Adam:** Well so, the key idea of Rust, which is something, and this is, I think really the thing that most programmers get hung up on when they learn it, is that Rust takes control of aliasing. And by aliasing, I mean, the ability to reach the same piece of memory under two different sorts of names under two different expressions.

### **How Rust Handles Aliasing**

**Jim:** The example that I give in the book is, I actually give a C++ example and I say okay, he's got this a C++ mind you, this is not Rust. So you got int x,  And it's variable, it's not constant facts.

It's just int x,  And then you take a const pointer to it. So I say const int \* x or \* p. const int \* p and I say = & x. So I've got a constant pointer to a non-const x. Now the way C++ works, you cannot assign now to \* p. 

If you try to assign a variable to \* p or use the increments operated on it or something like that, then that's a type error. You're forbidden from using a p to modify the reference to the pointer. But you can assign to x, no problem. And so you can go ahead and change the value of x anytime you want.

And so it's not the case that just because p is a pointer to a const is that the integer it points to is constant.  How, how privileged is that? I mean like what does constant mean? If it can change. Okay. But the thing is, I want to make clear that there are uses for this kind of thing, 

It is pretty useful to say, well, through this point, or I'm not going to change this value,  So in some, I'm not saying it's useless, but, but it is kind of, not what you expect. And so, but if you think about what it would take to fix that, To say, well, if I'm going to say that this pointer to this thing that this point, this is a really a pointer to a constant thing that would mean that for as long as that pointer p exists, appointed to a constant that all other access or that all of their modification of the thing that it points to has to be from it.  You have to, basically, as long as P is pointing to x, you have to make sure that x can't be modified.

And so that's what I mean by aliasing, that \* p that is the referencing the point p and x are both things that you can write in your program that refer to the same location and this kind of aliasing kind of rise under pretty much any circumstance,  Anytime you have two paths through the heap.

### **Shared and Mutable Reference**

**Jim:**  That all arrive at the same object,  And you come, you have a shared object right in the graph of objects. That's two ways to get to the same location. And there will generally be two different expressions that you could write to refer to the same object, So JavaScript lets you do this job.

Java lets you do this basically every language lets you create aliases. And what Rust does is it actually restricts your ability to use pointers, such that it can tell when something is aliased and they can say, okay, for this period, for this portion of the program. These objects are reachable by basically there are two kinds of pointers.

They are shared pointers, and then there are shared references and there are musical references. So it'll say these objects are reachable by shared references, and thus they must not be changeable. And so you know, not just that you can't change those values through those shared pointers, but you know that nobody else can change that either.

So it's really powerful when you have in Rust. If you have a shared reference to an int, you know it will never change and if you have a shared reference to a string that string will never change.

If you have a shared reference to a hash table you know that no entry in that hash table will ever change. While you have that shirt just as long as you have that shirt.

**Jim:** Right. So once that goes out of scope, then changes could happen. 

**Adam:** Exactly, and then the other kind of reference is a mutable reference, where what it says is you have the right to not modify this, but nobody else does.

Nobody else has the right to even see it. And so a mutable reference, like it's basically, it's a very exclusive kind of pointer. So when you have a mutable reference to a hash table. Nobody else can touch that hash table while you have it. And that's statically guaranteed. It's part of the type rules.

### **Segregation Between Sharing**

**Jim:** It's guaranteed by the type rules around mutable references. And so you can imagine that, any type of system which can guarantee this thing about like, Oh, this, there's nothing else. There's no other live way in the system to even refer to the reference of this people pointer. That's a pretty powerful type system.

And, we're working through the implications of that, I think is where most people stumble learning Rust, that there is strict segregation between shared references where you have shared immutable access, and where you have mutable references, where it is exclusive access.

So there's this strict segregation between sharing. The mutation and the way that Rust accomplishes that is I think is really novel. It's something people aren't used to. And honestly, when you tell I was having lunch with a very accomplished programmer who just sort of old friends.

We haven't talked in years. And we're talking about Rust, and he says, Yes, and I can't create cycles. I mean I'm a programmer and I know exactly what I want to do with those cycles. I want to have data structures that are arbitrary graphs and I need those data structures and Rust which let me make them.

And so I'm not interested. And so I think he's, I think he's wrong, but I think he's making a poor choice. But he is correct in his assessment that basically Rust really is asking you to give up something that is just such a fundamental tool that most programmers have to have, just internalized and they've learned to think in those terms. So it's, so it is sort of asking them to give things up.

But, the thing is, what you get in return is exactly this guaranteed memory safety and this guaranteed freedom from data races. And it's just this huge win. So the way Rust works when it does work is when you can take that, I think I mentioned the programmer machismo I want a gender-neutral term for that, but like based on the programmer's pride.

### **Concurrency to Cover Every Possible Execution**

**Jim:** The programmers like that, the little bit of confidence that you've got, you want to flip that from people saying, oh, I can handle data races, I can handle unsynchronized memory access. No problem. You want to flip them from thinking that to thinking, oh, I can write my code in this restricted type system.

You want to make them say, I can feel I can handle it. I can get things done. Even though Rust is restrictive,  I can overcome these things. I can take this, this limited, buttons down the system and make it.

**Adam:** Maybe people just shouldn't be so invested in their own pride. I don't know.

But one thing is, it sounds like what you're talking about is a, it's like changing the relationship you have with the compiler. I mean, I think some people view a compiler as a teacher with like a ruler that hits on your hands, like don't do that. But there's an alternative way where maybe it's more like an assistant.

**Jim:** Yes. And, what's going on a lot with Rust is that your debugging time is getting moved from runtime to compile time. That is the time that you would spend chasing down pointers or problems in C++, you instead spend in negotiation with compiler about your borrows and about your lifetimes.

And the thing about it is, the difference is that tests only cover a selected set of executions. My tests cause the programs to do this. It runs it through its phases in this specific way, whereas types cover every possible execution.

**Jim:** And so that's the property that really makes it wonderful for concurrency, which is with concurrency, you have to just give up on your tests really exercising all possible executions.

Because the rate at which different cores run the code and how the threads get scheduled and what else happened to be competing for your cache at the time. None of that stuff is really, something that you can get a grip on. And so having a type system that says all possible executions are okay, is exactly what the doctor ordered

## **RustBelt Project**

**Adam:** So are we at risk of there just being a problem with the type system?

**Jim:** Yes, sure. I mean, the type system isn't sound then you lose or we lose. In fact, so one nice thing is that the people who are sort of the lead designers of the type system right now, as I understand it are Aaron Turon and Niko Matsakis.

And in particular, Niko is the one who had this insight about. Hey, we have the possibility of really separating, sharing and mutation. Keeping those two things completely segregated. That's what I think is really the defining characteristic of Rust. or rather the defining novelty of Rust.

And so they work. When they talk about type systems, they're playing with, with PLT redox, which is the system from the, from the PLT group that made a racket and all that stuff. For playing with formal systems and looking at derivations informal systems, but they're not proving things about it.

There is then a project, called Rust Belt. I mean there's also a conference called Rust Belt, but Rust Belt is a project. At a German University where they're actually trying to formalize Rust, it's a research program where they say, okay, we are a group of people, and we're going to work on finding a formal model of the Rust type system and Rust semantics.

And in particular, there's a guy, Ralph Young, who is really taking this on and he is working on machine verified proof of the soundness of Rust type system. Now it turns out that there are aspects of Rust that make this very interesting and challenging and turn into something that just has never been done before.

In particular, all of Rust is built on a foundation of unsafe code and unsafe code is code where it uses primitive operations whose safety the compiler cannot check.  These operations, they still have, they still can be used safely. They just have additional rules in order to be used safely that you as the programmer can know.

## **Is Rust Safe to Use?**

**Adam:** So what do you mean to say that it's built on a foundation of unsafe code?

**Jim:** Well, the Rust vector type, for example, is the vector type itself is safe to use. If you are writing Rust code and you use the vector type, it's a fundamental type in the standard library.

It's like, analog of Haskell's list or something like that. Just, you can't get away with it. You can't use it. And so basically if you are using vector, then you are at no risk. Any mistakes that you make using vectors will be caught by the type checker and the borrow checker at compile time. 

So Rust is a vector that is safe to use. Vec is safe to use, but the implementation of vec uses operations whose correctness the compiler itself cannot be sure of. In particular, when you want to push a value onto the end of the vector, what that's doing is taking this section of memory.

You got to imagine the vector has a big buffer. And it's got some spare space at the end of the buffer, and you're gonna push a new value, so you're gonna push a string onto the end of that vector. You're transferring ownership of the vector, you're transferring ownership of the string from, whoever's calling the push method, to the vector itself.

And so there's a bit of uninitialized memory at the end of the vector's buffer or towards the end of the vector buffer, which is now having a string moved into it. And in order for that to be correct in order to make sure that you don't end up with two strings thinking they are both on the same amount of memory in order to make sure that you don't leak the memory it has to be guaranteed.

It has to be the case that to be true, that the memory that you're moving the string into is uninitialized. And whether or not the location that something gets pushed onto is initialized or not depends on the vector being correct. That is the vector knows the address of its buffer.

### **Unsafe Code in Rust**

**Jim:** It knows its length and it knows its capacity, the actual in-memory size of the buffer. And so the vector has to have checks that there is spare capacity, that the length is less than the capacity. And that link has to have been accurately maintained through all the other operations on the vector.

If there is a bug in the vector code and the length ends up being wrong, then this push operation, which transfers ownership can end up overriding some existing elements of the vector. And then that could be a memory flaw, a memory problem. But the nice thing is that vec is a pretty simple type.

It's built on some modules which have a very simple job to do. And so that is a small piece of code that we can audit to ensure that the vector is using its memory correctly. And once we have verified by hand, by inspection, that the vector is using its memory correctly.

Then we can trust the types of vectors, methods to ensure that the users will always use it correctly. So the users have no concern it's only we who implement the vector, who are responsible for this extra level of vigilance and making sure that we're getting the memory right.

**Adam:** So the type system can be and is being formally verified, but the libraries need to be hand audited. What's the vector written in? Is it written in Rust?

**Jim:** Vector is written in Rust and that's the key, is that unsafe code in Rust is sort of this escape hatch that lets you do things that you know as the programmer is correct, but that the type system can't recognize as correct.

So, for example, my main vector is one of the write of the vector itself is written in Rust uses a selected unsafe code and so this is exactly what the Rust Belt project is tackling. In order to really make meaningful statements about Rust, you're going to have to actually be able to handle unsafe code.

Because of the primitive operations of Rust, like the synchronization operations, the stuff that implements new taxes, the stuff that inter-thread communication channels or the basic memory management of things. 

### **Trust the System to Do the Audit**

**Jim:** That gets memory that obtains memory, free memory for a vectors’ buffer or that free vectors buffer when the vector is disposed of. Or, the IO operations and say, look, we're gonna read memory. We're going to read the contents of a file or data from a socket into this memory and without wiping out random other stuff around it.

All of those things are sort of their code that no type system can really. Yes, I think you say that they're, primitive operations and so no type system and really say what they do. But you can use unsafe code and make sure that you use them correctly. Assuming that you're unsafe code is right, you can build well-typed things on top of those that are safe to use. 

And so this two-level structure of having unsaved code at the bottom and then having time to code on the top is what allows people to have some confidence in the system. And so, the Rust Belt people actually want to.

Understand the semantics of unsafe code and actually spell out, what the requirements are in order to use these features safely. And then they want to verify that Rust standard library doesn't indeed use them correctly. So they're really going for the whole enchilada. They want to really put all of Rust on a firm theoretical foundation and it's really exciting.

**Adam:** And the trade-off, like as a user of the language, it seems to make sense to me. So you're saying like, rather than needing to audit my code to make sure these issues don't exist, I can trust that the system has been formally verified except for these unsafe primitives, which have been audited themselves.

**Jim:** Yes. Well basically if you don't use unsafe code. Then the compiler prevents all undefined behavior, prevents all data race and memory errors if you don't use unsafe code, you are safe. If you do use unsafe code, you are on say features. You are responsible for making sure that you meet the additional requirements that they impose above and beyond the type system.

### **Implementing Under an Unsafe Code**

**Jim:** And so, Yes, I mean, either you can figure out how to fit your problem into the safe type system. And the nice thing about Rust is that the same type system is actually really good and quite usable, and most programs do not need to resort to unsafe code. So you can either work in that world, which is what I almost always try to do.

Or if you really need, if there's something that's a primitive that you really know is correct, but that Rust that the type system can't handle, then you can drop down to unsafe code and you can implement that. 

And one of the things we, one of the strategies that we emphasize in the unsaved chapter of the book, it's the very last chapter after we presented everything else, is one of the strategies that we encourage people to use is to make sure that or to try to design interfaces such that once the types check that you know that all of your unsafe code. 

It is ok and then that means that you've exported a safe interface to your users. And so if you have an unsafe trick, would you want to use you isolate that unsafe trick in one module. That has a safe interface to the outside world, and then you can go ahead and use that technique, and not worry about its safety anymore.

You use the module. And then the module types ensure that it's okay.

**Adam:** The unsafe code doesn't escape.

**Adam:** It sounds similar to the idea of like people be writing some Haskell function that claims to do no side effects, but for performance reasons, maybe it's actually doing some sort of generating a random number. Maybe that's a bad example, but it's totally hidden from the user. It acts purely from the outside, whatever may happen.

**Jim:** Yes, that's, that's a good example. That's a good example because the question comes, the question arises, is it really pure from the outside? If they did it right, if they really actually kept all of the state fullness local and isolate this, but you can't tell from the outside, then everything's fine.

## **Rust Performance**

**Jim:** The people that in the rest of that, whoever's using that. Oh, from the outside can use it and not worry about it. And they get the performance and they don't have to worry about the details. But then inside, the people who wrote that code are, they have extra responsibilities. And the normal Haskell guarantees of statelessness don't apply to them because they've broken the rules or they've stepped outside the rules and they're now responsible.

**Adam:** And you mentioned, the type of system Rust is and actually it has a lot of features that I guess you wouldn't expect from something that maybe I didn't expect. It has a lot of functional, filling features.

**Jim:** Oh Yes. I'm really glad that you brought that out because I've talked about safety and I think I've talked about performance.

But Rust, the really nice thing about Rust is that it is not by any means a hair shirt. It is actually really comfortable to use. It has a very powerful, generic type system. The trait system is a lot like type classes in Haskell if you use tech classes in high school.

I mean, everybody uses hypothesis and Haskell, but they know it or not.  and, Yes, so Rust has traded. The whole standard library is designed around those generics and those traits, and it puts them to full use and it's actually a super comfortable system to use.

I did a tutorial at AusCon in Austin last May, where we went through to the extent that you can, three hours, writing a networked video game. And that involves 3D graphics and involved a little bit of networking and it involves some game logic.

Obviously I had to up the game ready for the talk and I put it off. And so I had to do the last stages of development in a rush, and it was fantastic. It was like I had wings or something because once I'd gotten something written down.

### **Utilizing Serializer Deserializer**

**Jim:** Once I'd really gotten the types right, it was done. It was done. if I had been working in C++, I would have had to randomly take three hours out of the schedule to, to fix, to track something down, and debug it. Because it was Rust, I just gotta keep going forward.

And so it was just like really great progress and Rust has all of these sorts of batteries included kind of things. Like there's a crate out there called SerDe which is for serializing or utilizing serializer deserializer. And it is a very nice collection of formats like this JSON, there's a binary format, there's XML, there's a bunch of other stuff right.

And then a set of Rust types that can be serialized. String hash, table vector what have you. And SerDe is very carefully constructed which it knows how to serialize or deserialize. Then you can use that with any format that it knows how to read or write.

So you're just like, pick something off of this list and then pick something off of that list and you're immediately ready to go for sending something across the network. You can actually, and that naturally, if you've defined your own types, you can specify how they should be serialized or deserialized.

You'll define your own custom struct and say, well, but the thing is, that's real boilerplate stuff so there is actually this magic thing that you can say you can slap on the top of your own type of dish. You can say derived serialized and deserialized and what that does.

I guess the Haskell has something like this too that automatically generates the methods. It looks at the type and automatically generates to serialize and deserialize that type and so it is super easy to get your stuff ready to communicate across the network and so for communicating people's moves and communicating the state of the board.

that was, it was just a blast because there was all of this sort of boilerplate stuff that I didn't have to worry about and those are just the kind of power. 

## **Is Rust for Non-C++ Developers?**

**Adam:** So, and I think just for a callback, I think that's like generic derivation and I did have miles on the show earlier who wrote something similar for Scala and yes, Haskell has it. I think it was originally called scrap your boilerplate. But yes, a very cool feature.  A lot of boilerplate can be removed by things like that.

**Jim:** Scrap your boilerplate is done within the Haskell type system. If I remember that paper right and SerDe is doing a little bit of procedural macro kind of, I'm actually gonna exactly look at your type definition and decide what to do with it.

And I wonder if that stuff could be done in the scrap your boilerplates style. I don’t understand scrap your boilerplate well enough to say. But yes, it's that stylistic and yes, those are just wonderful tools.

**Adam:** I think you're making a good argument. So Rust apparently is hard to learn. This is what I've heard. However, once you learn that there's a superpower. So is this superpower applicable to non-C++ devs? Is this a useful skill for somebody who's like throwing up web services?

**Jim:** I think so. So you had Edwin on talking about interest and Edwin made a comment that I want to push back on. He said I don't think that types really helped people eliminate bugs that much because unit tests are still useful. So I work in the developer tools part of Mozilla, and we have a JavaScript front end.

The user interfaces for the developer tools in Firefox is written. They're written themselves in JavaScript, and it's a react-redux app basically, that talks over a JSON-based protocol to a server that runs in the debug key and it looks at the webpage for you. I'm proud to say that my colleagues are enthusiastic about the potential for types and they really see the value of static typing.

And we are bringing, we're using a flow-type in Javascript. We're bringing flow types into our codebase but it's not done. We haven't pushed them all the way through. There's plenty of untapped coats still because of full Javascript flow types. Let you type one file and leave the rest of the file.

### **How Errors Are Missed**

**Jim:** Left just the system untyped. Leave the rest of the system untyped. And so you can gradually introduce types to more and more of your code as you go. So we're in that process and of the bugs that I end up tracking down. I don't want to put a number to it because I know I haven't been keeping statistics, but it feels like, at least half of them, would have been caught immediately by static.

**Adam:** I've heard people say this when moving to typescript, which is similar. Often they found a yes. Like, not a super obscure bug, but like a little corner where things would go wrong. That the type system was like, what are you doing here?

**Jim:** The thing is I think people like the people who work in Haskell or, certainly somebody who works on the address, I don't think they really know what the JavaScript world is like. It's just insane what people do. 

In JavaScript, if you typo the name of a property on an object, it's just a typo, you capitalize it wrong or something. That's not an error. JavaScript just gives you undefined as the value and then undefined just show up at some random point in your program. And so until you have like complete unit test coverage of every single line.

You don't even know whether you've got typos. That's crazy. That is just not what humans are good at and it's exactly what computers are good at. And so to put that on the human programmer's shoulders doesn't make any sense.

**Adam:** To be fair to Edwin, he does have t-shirts, but say if it compiles, ship it.

**Jim:** Oh no, I thought that was a really good podcast. And like I said, we're all really curious about the address. So, I think that we don't want to undersell the benefits of static typing and so back to your question. For people who aren't doing systems programming, why would they be interested in Rust?

### **Value of Rust for Single-Threaded Code**

**Jim:** Rust is just a really good, productive language to work in. It will make you worry about a bunch of things that maybe you thought you shouldn't have to think about. But in retrospect, I kind of feel like I'm happy to have those things brought to my attention. Like for example the at the very beginning I talked about how data structures the method of a data structure will sort of bringing it out of a coherent state and put it back into a coherent state.

You don't want to make sure that you don't observe it in the midst of that process. Well, you can get those kinds of books even in single-threaded code. You can have one function which is working on something and modifying something that it caused something else because something else goes through a callback.

And you have several call frames and then suddenly you have something that tries to use the very new instruction that you were operating on at the beginning but you weren't aware of it. And so nobody knows that they're trying to read from the data structure that they're in the middle of modifying and that's something that's called the iterator validation in C++ its undefined behavior. 

In Java, you get a concurrent modification exception. Like I just mentioned this to a Java program and he's like, Oh, yes, see, he says though, if they'd had a name for him, they knew. and that's also, that's a totally a single-threaded programming error. 

And that's also prevented by the Rust type system. So I feel like Rust types actually have a lot of value even for single-threaded code, which is not performance sensitive, but it's just really nice to house. It's really got your back in terms of letting you think or making sure that your program works the way you think it does.

So, yes, I think it has a lot of applicability as a general-purpose programming language.

**Adam:** Hey, the one thing we didn't talk about, but I think that you touched on briefly at the beginning was to do with security. So we talked about data races, but you also mentioned security.

### **What Happens When There Are Security Holes**

**Jim:** Yes, there are lots of different kinds of security holes. And according to the collected data, there are a few people who collect statistics on the published security vulnerabilities and sort of what category they fall into, is it SQL injection? Is it cross-site scripting?

They sort of categorizing them. And the category that I'm interested in. In this particular case is memory. Memory corruption, memory errors, and those have been consistent, 10, 15% of all the security vulnerabilities being published altogether.

And so there's still a very big issue, and most of the time, almost all the time, what's happening there is you've got a buffer overrun, or you've got a use after free, or you gotta have some other kinds of dynamic memory management error, which normally would result in the crash. But in the hands of a skilled, exploit author can be used to take control of the machine because after you have seen enough of these attacks, you start to feel like pretty much any book could be exploited with enough ingenuity.

So like, I can't find this post anymore, but the Chrome security team, Google's Chrome browser security team had a blog post about just about security errors caused by integer overflows. The intro, integer overflow sounds so innocent.

I mean, but it turns out that integer is the size of something you are 90% of the way to perdition.  Because basically you can make it think that something is much bigger than it actually is in memory. And then you've got access to all kinds of stuff you should have access to and you've broken out of jail.

And, so having a type system which prevents major mayhem in which basically makes sure statically that you're not going to your program doesn't behave in an undefined way, really does close off a very significant opportunity for security holes.

One of the quotes we open up was a tweet by Andy Wingo, who is a great JavaScript hacker and a great free software hacker and basically there was a bug and a true type parser, a font parser and that was one of the bugs that were used to break into the machines that were controlling the Iranian nuclear purification facilities.

## **Red Bean as a Consulting Company**

**Adam:** Oh, I didn't know that. What's that at Stuxnet?

**Jim:** He was built around a flaw and true type. So true type is a font parser. The true type is security-sensitive code. So basically all code. It's a security sense. There's no longer, you can no longer say, Oh good, no, it's just graphics code.

If you're writing C++ code and you've got control of memory and it's doing point or arithmetic, you've got to be on your toes and the standard is perfection.

**Adam:** And so Rust, like the same as a data race, it takes a certain class of these vulnerabilities off the table?

**Jim:** Yes. In a Rust without unsafe code, if you have a program type, then we are saying it will not exhibit defined behavior.

**Adam:** And undefined behavior is like?

**Jim:** Is often the root of the security hole.

**Adam:** So we're reaching the end of our time here. One thing, I was Googling you, what I found is your Red Bean software site. I actually ended up forwarding this to a couple of my friends. It says on it, to all intents and purposes: it appears you have a consulting company that does not sell software. Is that correct?

**Jim:** Well, first of all, it's really, really old. My friend Karl Fogel and I ran a little company called [**Cyclics Software**](http://www.cyclic.com/) and we were selling CVS support. We were the first group to distribute network, transparent CVS. We didn't, we didn't write it, but somebody else wrote it and they said they didn't want responsibility for it.

And so we were the ones who were distributing it. And so I'm kind of proud of that because it was network transparent CVS. That was really the first version control system that open source used to collaborate on a large scale and then got replaced by subversion and gets material.

Network transparent CVS was, was really how things got started. So yes, so we had cyclic software and then we, we decided we didn't want to run it anymore. We couldn't run it anymore. And so we sold it to a friend and we realized we had to change our email addresses. We had to tell everybody, don't email us, gimpy at sick like anymore.

And that's kind of a bummer. We realized that we were going to be changing our email addresses every time we changed jobs. So we resolved to create a company whose sole purpose was never to have any monetary value.

**Jim:** So we would never have to sell it. And so he could keep a staple email address for the rest of our lives.

Is it, I mean, it's a vanity domain and lots and lots of people have vanity domain. But our joke is that it's a company whose purpose is never to have any value.

**Adam:** Yes. I found on the front page it says, let me read this. By buying our products, you'll receive nothing of value. But on the other hand, we will not claim that you have received anything of value in this.

We differ from other software companies who insist in the face of abundant evidence. On the contrary that they've sold you a usable and beneficial item.

Well, it's been a lot of fun. Jim, thank you so much for your time.
