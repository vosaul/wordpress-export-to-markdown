---
title: "Scala Native with Denys Shabalin"
date: "2020-05-25"
---

#### Things Can Be Designed to Run Faster

In this episode, Denys Shabalin talks in-depth all about Scala Native and how the effort to bring the Scala compiler to LLVM sped things up.

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/6123766/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

"So the core Scala is really as close as we can make it, and be as same as in JVM" - Denys Shabalin

"But if you have native, we don’t really have to have this problem because the very first run is already optimized, so you can already run optimize code immediately." - Denys Shabalin

"Backend microservice kind of app. This is kind of the area of which we see Scala being used more in the future." - Denys Shabalin

### **Transcript**

**This is a machine-translated transcript. Podcast page for [this episode is here](https://corecursive.com/001-scala-native-with-denys-shabalin/)**

**Adam:** Welcome to CoRecursive, where we bring you discussions with thought leaders in the world of software development. I am Adam, your host.

Scala native takes the Scala language, which traditionally runs on the JVM and brings it to bare metal. It is an optimizing ahead of time compiler as well as a lightweight managed runtime design specifically for the Scala language. Denys Shabalin is a research assistant at the EPFL and the primary creator of Scala native.

In this episode, I talk to him about the motivations behind the project, how it was implemented, and future directions. One thing exciting that he mentions in this episode is an effort to bring the Scala compiler to a Scala native. And how doing so sped things up. Scala is a language built on the JVM. Could you give a brief overview of Scala the language before we get into a Scala Native?

## **Overview**

**Denys:** So Scala is a pretty cool language I originally designed for JVM. It really can be described as a mix of functional and object-oriented programming. It really doesn't bias towards one or another style. It really tries to blend both together because there is both good and bad on both ends.

Like for example, functional programming is basically considered as a better type of Scala and object-oriented to be more of a Java-style old school, less popular side, but still, language doesn't bias towards one side or another. You can perfectly do object-oriented, classical object-oriented programming, and fancy functional programming at the same time.

This is pretty unique because most languages are heavily on one side or another, which is often considered to be like a negative side of Scala because it's very open-ended. But anyway, that's where it is.

**Adam:** Yeah. Makes sense. So Scala lets you kinda, you can combine sort of a Java-style with an ML or Haskell style functional composition.

**Denys:** Absolutely. Yeah. That's it.

**Adam:** What is Scala native?

## **What is Scala Native**

**Denys:** So Scala traditionally has been a JVM centric language, so it used to compile only to JVM bytecode as the only target. And what it means is that it's really a plug and play on JVM. You just compile these codes then you can run it alongside your Java application.

That was the original backends platform for Scala, but since then, we got way more things. The first, major experiment Scala did outside JVM was the net backend. It didn't work so well because of the differences between how JVM and common language runtime handle generics.

So it was a bit difficult. I think the first successful alternative platform for Scala is Scala GS. By Sebastian, So basically, it's really a major difference in terms of how your Scala apps because it compiles them to JavaScript. A very elaborate advanced toolchain.

They have and Scala Native was very much a similar project to college. Yes. But instead of compiling to JavaScript is compiles to native code. And when I say native code, I mean more like a C, C++ standalone binaries that completely just don't require any virtual machine to run it. So just get x86 or ARM binaries that you can just copy, paste them to any machine with the same architecture, and just run.

Of course, it has good and bad of native style development, but it's really a kind of core idea of the project is very simple, is to compile Scala to native binaries.

**Adam:** Makes sense. So, you know, Scala GS gives you the ability to run in the browser. What problem does being able to run as a native application solve?

**Denys:** So why don't the issues with JVM, as I see it, is that JVM is a really heavy, heavy machinery. So it really requires quite a bit of a footprint just to run the VM. So you can see it in terms of memory used. You can see it in terms of application startup time. You can see it sometimes in terms of the overhead of the whole services, like just compilation behind the scenes.

## **JVM vs Scala Native**

**Denys:** And it's really because JVM is a very, very advanced, multistage, multi-tiered VM and it's really hard to support all this functionality because it was incurring some overhead. So Scala native is different in that we do most of the expensive parts, like compilation ahead of time so it means you already have a pre-compiled and pre-optimized binary. So when you'd started, it just runs your app. It doesn't do the whole multi-tier VM saying, so we don't have an interpreter. We don't have multiple-tiered of compilation and we just, whenever we emitted binary, that's it. There is no recompilation and runtimes, there are no tricks we do.

It's a simple binary, which means we have a way lower footprint and both in terms of memory, and in terms of startup time, this can be useful for a number of use cases of applications like common line tools. So for the common line, it's done, it's extremely important to start quickly, do your job and then die.

This is the area where JVM is really bad at right now because. Just start it as a VM is an extremely expensive operation. So you definitely see us kind of like initial slow down if your app is not in the long run.

**Adam:** So that is what people refer to as like the JVM warmup, is that right?

## **The JVM Warmup**

**Denys:** Yeah exactly. So it's like just warm-up and it also has to do with the fact that when you're on code and JVM, it actually goes through a number of stages. So first you go through an interpreter. The interpreter is really slow. It is not meant to be as is there for a long time. So it tries to go to compiled mode as soon as possible and are at least two compilers right now, which are used in production JVM C1 and C2.

C1 emits simple code to avoid the interpretation costs? And the C2 does a very advanced optimizer that only optimizes heavily used parts. So basically you have very elaborate machinery, which means that you don't get to optimize code only until your application is warmed up.

In native, we have basically the equivalent in between Ci and C2. So we already heavily pre optimize your code before you run it, but at the same time, it's not quite the same as the VM. So it draws some problems. Pros and cons.

**Adam:**  Yeah. So if you're, if you have a long-running Java app or a Scala app, I guess then the costs of this warmup maybe doesn't matter so much, but if something has to start up frequently, then you know, re-optimizing it is a lot of overhead.

**Denys:**  Absolutely. Yeah. That's it. And another area from the common line is different types of user-facing apps where you can observe and perceive the syrup time. Which often are like, you know, simple graphical apps, like for example, like start to an eclipse takes minutes, and I know it's just before it's like, and you never close it, right, because you're afraid to close it because once you close the eclipse, you'll have to go through the same thing again.

That's basically not eclipsing problem as far as I can tell, it's largely a JVM problem because for example, other IDs started much faster than eclipse.

**Adam:** Yeah I use IntelliJ, but I find the same thing. Yeah. I try to keep it running. In your talk, a Scala goes native, you were describing the JVM as a, as a golden cage. This is sort of what you mean by that, or could you describe this concept?

## **The Concept of the Golden Cage**

**Denys:** So this metaphor was basically tried to motivate why we don't try to artificially limit what you can do in Scala native-like JVM does. In particular with don't try to sandbox your code so that you can only write very safe code, which not never escapes the cage, basically, that's what I meant by the cage. We let you use low-level assistant level tools like broad access to memory rope pointers and stuff like that, which is potentially unsafe, but it's actually necessary for some domains like the systems programming where you want to have a very low level of control of your memory.

A benefit is that you get more controls to develop or you don't, you're not limited by the language, and the VM, because you can do whatever at C and C++, whatever you can do in C and C++ on the other hand, you do lose some of the safety you get on JVM. But this is kind of a trade-off. We take.

**Adam:** That makes sense. So is this strictly for memory management or how about interop?

**Denys:** So generally intro is basically, so it's called native exposes a number of language extensions aimed primarily at the intro with C code. And in a way it's a bit like writing C code in Scala. So we expose things like pointers, instruct. So you can do with familiar assist our programming but it also means it's extremely easy to call a C code. You don't need to go through a number of layers of bindings and gather. You can just do it all in Scala without any C and C++ code. But it also means that if you can call arbitrarily C code, you also can get arbitrarily. Issues that have, like, for example, different types of safety issues around buffer overflows and so on and so forth.

It's definitely a trade-off. It's not free like colon C is not free in terms of the safety guarantees you get, but again, this is kind of a trade-off we make. We don't try to be as safe as possible. We try to be as flexible as possible.

**Adam:** Makes sense. You want to give people that tool, even if they, you know, it could go wrong. So how about memory management on the JVM?

**Denys:** So JVM is basically a GC only platform. There are some very well hidden but extremely well-known areas like misconceived, which lets you do unmanaged memory and manage yourself. Like for example, you can allocate,  unmanaged memories to sound misconceived and then do roll memory accesses on it.

It's basically as in TAFE as pointers and only JVM people tried to hide it from you. Even though every major performance-centric framework actually used it. Like for example, Spark does have hip memory to manage this. Most of is data because they're just too expensive to allocate, ever seen on GC here.

But JVM people like you believe that you only have GC, which is the main paradigm and it's actually like CISI on JVM is really good. So very often it, it, it's a good idea just to just use that and not do any unsafe memory management. It's called native. We'd say both coexist and you have APS for both, and they're involved in doing use.

So definitely unmanaged memory is a dangerous thing. You can definitely shoot a wrestler, but for example, if you want to do some,  you know, domain-specific seeking to optimize the memory layout and so on, and so forth, you can do that without. Jump into the hook as like JVM

**Adam:** Makes sense. So, you know, the JVM complaint, it purports to be memory managed, but if you look at these high-performance apps, they're using backdoors to sort of actually do manual memory management.

**Denys:** Yeah. And it's like most of them really go far away to try to say, saves a cage to find a small door outside to get more freedom, but it's on JVM. It's really hard to do those kinds of things.

**Adam:** That's where the cage metaphor comes in. Yeah. Okay. So now that we understand some of the motivations for, you know, getting Scala run natively, not on the JVM, maybe let's discuss,  some of the implementations.

So could you describe the compilation steps that it takes to get from, you know, Scala source to a native application?

## **Compilation Steps from Scala Source to a Native Application**

**Denys:** Oh, sure. So it's actually a bit involved. And there is a good reason we have every single step on the line, but it's actually a really multi, multi-step process. So the first thing you do when you go from a Scala source, so you always start with Scala sources, which is a source of truth and in case this calls an idea if you end up with native binary, but it's not the one-step saying like from Scala source native binary is the first thing you do is you do parse and type check and basically do the pipeline from the main Scala compiler from JVM. And this, uh. It contains a number of things, but the most important one, I guess its type checking because they have checked Scala very involved with don't reimplement type checking or the language? We keep the same core, the same language Scala, JVM, and later, once the Scala compiler is almost done, we branch off and we emit something called NIR. NIR is short for Native IR, which is our own intermediate presentation.

So this NIR is the four-month we worked within our toolchain. And when I say our toolchain, I mean linker optimizer and is the old speaks this language as if it was like. Or were your language? So to get from NIR to binary, now we have one step closer because NIR is already quite low, quite more low-level since Scala, for example, many things are gone and I like, there's the illness of classes are no generics type system is much simpler and it's actually very close to Java by, it's called and it's Scala language.

And the main difference from Java code is that it's an SSA form, which makes it very easy to admit LLVM later, is this forum for coder presentation, which is very nice to optimize and compilers. So from NIR, we need to get native binary and do major steps on three major steps in this way. Its first linking is linking loads and a minimal subset of your class pass to satisfy your application requirements. Like, for example, an app that doesn't use regular expressions, should not come pre-compiled regular expressions in the binary, and so on and so forth. So we've tried to really limit the amount of code we put in the final binary not to include every single class on the class pass, because sometimes class passes and get quite bloated, even though we don't use some of those things. Sometimes people depend on the library even though they use a single function from it. So we do something called the whole program that coordination at link time.

And then after that step, you get a minimal subsistence across the past, which we optimize our own optimizer, which removes common patterns, which LLVM doesn't know how to optimize. Well. And then, in the end, we admit LLVMIR, which is another. But now for LLVM LLVM is this project for reusable compilers, basically, so it's a core for C lang compiler. And it's also used by many, many other open source languages and it's actually very well documented and very nice to work with. And from there on, basically, LLVM’s jobs to grant from LLVM to native code.

**Adam:** You have your Scala code, you're using them, you're using the front end Scala compiler to get some intermediate representation and then doing some transformations and then passing that through to LLVM. Is that the. Yeah that's a true,

**Denys:** That's pretty much the gist of it.

**Adam:** And then,  because everything, cause there's, there could be a lot in your classpath. You're making sure that you only include things in that binary that are actually part of that are actually called within the program.

**Denys:** We don't always are going to be called, but we try to analyze it and kind of do our best guess and what's going to be called. Yeah.

**Adam:** Okay. Yeah. Makes sense. So one of your frustrations with the JVM was that it's garbage collector doesn't fit every use case. So many listeners may know that there are different types of garbage collection strategies. I was wondering if you could describe a couple of strategies for performing garbage collection.

## **Strategies for Performing Garbage Collection**

**Denys:** So on JVM, you should have a number of built-in garbage. As far as understanding as the fault one is called G1. And G1 the latest collector from Oracle, which is optimized for latency? Sandra workloads? So typically GCs are often kind of put in ISER latency-sensitive or super tentative buckets. So what latency-sensitive means is that the just use optimized for the shortest pause that GC can take to collect garbage but this pause can be extremely frequent, but every single pause is small and stripped with centric collectors care about now that length, so a single, but rather the total time of time spent in the system, for example, sort of what tantric collector can take fewer pauses but makes them much longer.

And basically on JVM right now is the official ones is G1 for latency-sensitive and parallel and GC for stripped sensitive workflows. As far as I understand. And CMS, which was previously as a default, is deprecated as of Java 9, which is a bit sad because on some of our workloads scala compiler.

I think CMS is still the best one, but otherwise, it's basically, it's three main collectors we have right now with CMS being duplicated, the general seems for all of those collectors, it's that they're typically generational. It typically directional at least parallel often concurrent. So what concurrent means is that collector, runs alongside your application and try not to stop your application as much as possible. This is the basic way it does garbage collection, not just in parallel as in doing multiple strides of garbage collection, but also. Concurrently to your application. So compared to all of this, so we're just calling native stent right now.

We have a rather simple garbage lecture called MX, which is inspired by a paper. You can see our more information on our website if you're interested, but the general idea is it's a single generation collector, which is right now optimized for the predictability. It's not concurrent today. It's still in the works and we currently optimize mostly for throughput and latency. Sensitive is our next big milestone, which we haven't reached yet.

**Adam:** Okay. That makes sense.  you also have,  like,  as I understand that you have more than one GC available in Scala native. Maybe you could describe what they there.

**Denys:** It's a default one. It's actually not MX, it's called BOYM GC is this super easy to use, plug and play garbage collector, which was designed originally for C and C++. And the reason why it's even possible at all to make it work in this environment is that garbage collection is conservative. So what does it mean?

It means that garbage collector doesn't really require your app to declare ahead of time, objects. It will conservatively guess what objects are based on their size and layout. Just for example, if a field-specific offset looks like a pointer. It can consider the pointer, even if it's not, as long as it satisfies a bunch of properties that just he wants to see from pointers.

This is more expensive than precise garbage collection. So precise garbage perspective knows exactly where at which offsets you have pointers and which offsets it. Just data needs to do less work as the main reason why our current collector called MX  is because it's precise. So we do use information about the call object many hours, and it's way easier to collect the garbage.

It's still conservative in one small aspect, but it typically doesn't matter much. It's,  the techs are conservative, but. Typically it's not a problem. And another cool thing about MX compared to BOYM  is that it actually uses us a very smart data structure for allocation and collection, which lets it bump a cage most of the time, which is really important because bump allocation is the fastest way to allocate, and while still use a free list from time to time, purely to start, typically quite expensive in our own experience.

And apart from these two,  we have another collector called,  no GC or settings called native GC colon equals none. So that is, that one lets you completely disabled the garbage collector. And his idea behind that one is to kind of have a rough understanding of how much time was spent in garbage collection and what's the baseline performance.

What's basically is it a perfect garbage collector? Because essentially allocating and never freeing is actually extremely close to perfect garbage collection. It's not perfect because it will spill arcade objects far apart if objects were not like at the same time. So it can still cause problems with memory locality, but most of the time it's basically spent zero time in garbage collection.

So it means it's. As low overhead most of the time,  for most applications. And we use it as a baseline to benchmark our, our GC. So it's basically the main purpose is benchmarking. And apart from that, there are some use cases, like extremely short leaf applications, which really don't need to manage memory because they like to run for less than a second, and they don't locate gigabytes of memory, but maybe hundreds.

So if for those kinds of apps, it's actually beneficial to be able to disable garbage collectors because it means they will run the best performance possible.

**Adam:** Makes sense. So, none exists as sort of a, for performance testing, but in actual fact, it can be used,  for like a command line up. So you have none.

So you can test what you're calling like a, you know, a perfect GC, against the two that you have. When you do this type of testing,  like how, how do they perform compared to a perfect standard?

**Denys:** So compared to our reference, so typically the MX is somewhere around 20% overhead. So it just means if you add MX, your app will run 20% slower in comparison to BOYM. It is somewhere around a hundred percent. So basically enabled GC slows down your application by a factor of 2x, which is pretty bad. And it mostly has to do with the conservative nature of the collector. So MX is 20%. It's actually still higher than we want it to be. I think we can get to 10, or maybe even less, without changing the design of the collector too much.

**Adam:** Interesting. Do you, do you happen to know like 20% away from absolutely perfect. Doesn't it doesn't sound too bad?

**Denys:** Yeah.

**Adam:** Do you know, like where the JVMs generational garbage collector would fit on, on such a measure

**Denys:** It hard to compare with such CMS G1, or do you want, because they're on can practically, so it's typically under 5% and I would probably say even probably even less than that.

Because for a concurrent garbage collector, you never performed the garbage collection on the actual application thread, you have a separate thread, which only points application to do simple things like scans a stack or wait for this condition to halt. It's typically short pauses, so five milliseconds or less.

It can be frequent, but. I typically ask for incentives, like under 5% so basically this, this is our like gold performance to be on par with JVM right now. We don't guarantee a priority was JVM in terms of performance.  so is there still quite a bit of work to be done there.

**Adam:** Makes sense. So, you know, some people's complaint with the JVM is sort of the stop the world garbage collection, but you shouldn't go to Scala Native to get away from that because. That's all you have at this point.

**Denys:** Yeah. So at the moment, I want to be done to solve the stop the world problem. So we're looking, we're like researching ways to refine our GC further, but right now, like as a released version, I'll need, no GC has no stop the world problems because it doesn't GC.

**Adam:** Yeah makes sense. So now I think a, I understand how the GC works. I'd like to look a little bit at Scala native usage. So is Scala native the same language? Is it Scala or is it something like a

## **Scala Language Features**

**Denys:** Superset? So Scala native, his score is one to one Scala. So there are very few differences in terms of how we treat normal Scala language features and they mostly are around age cases. Like what happens when you call a message on a novel or what happens when you do a cust, which doesn't make sense. So on JVM. Those cases are defined just for exceptions. Some of those are just undefined behavior on native, so it means anything can happen. If you do this typically it means that if it just crashes with the sec fault, which is basically a bit worse than JVM but still easily the debugger bowls through native tools like that will show you a stack trace and we'll effectively show you as much as an L pointer exception. We've kindly guaranteed you one to one parity in each case and it's likely we will never have this because it's typically been a non-issue for us. It's a bit more known to do a ton of this, but essentially it simplifies our implementation quite a bit. And apart from the core language, which is almost exactly the same, like 99% the same. We have a bunch of extensions for intro, intro extensions, and are very different from Scala and JVM.

You don't have any similar, we do have parole unmatched pointers. And things that go with them, like memory, layout types, like structure, so you can have structs and they test means which is the same as in C. we also function upon insurers and a bunch of other things to basically make it easy to call a C code.

Generally don't have to use this kind of extension at all. They're actually, they're only for the intro. Pointers are also extremely useful. Kind of having a lower level, just you free subset of the language that you can use for extremely performance application. But again, you don't have to use any of this.

So the core Scala is really as close as we can make it, and be as same as in JVM

**Adam:** May makes sense. And I guess with the pointers, then you can kind of approach that perfect GC we were talking about, so, if you've added a concept like structs. Like structured types of functional pointers, like doesn't that make it the language, like a superset, like are these new keywords in the language. So new syntax?

**Denys:** We don't add any new syntax whatsoever. So our role is to type check without any problems. But by normal compile rate, it might not make sense. But essentially all of our extensions are tied to like magical intrinsics meshes or magical annotations, which. Modify how we compile things, but at the same time, it's still type-check 1:1 Scala compiler without changes from a text point of view, it's the same language from a runtime point of view is quite different. But,  types are still the same example.

**Adam:** That makes sense. Yeah I think that's a nice way to do it. So I mean. Because you're using annotations, does that mean that you can actually cross-compile?

So the same source can be a. A native binary and, you know, a jar.

\[**Denys:** Absolutely. So we do support for cross-compilation. So cross-compilation is done through this as SBT cross-project plugin. It's an aesthetic plugin that lets you cross-compile against three major targets, which is JVM and Native. These targets are basically treated as separate set projects of one megaproject, which is called a cross-project from SBT. The point of view is kind of like separate projects with separate jars, but we tried to streamline and do the experience so that truly it feels more like. One single project, which you really just manage this,  the corresponding API, but overall ZDF or across completion is you can create a cross-project with one or more platforms, and then when you compile and publish, you publish one jar per every platform you want to support.

**Adam:** How about libraries? Like the Scala standard library, I think it is kind of very important and kind of gives the language a lot, it's a lot of its fields. So do you have the standard libraries available natively?

## **Scala Standard Library**

**Denys:** So it turns out every story is a bit involved, but generally the idea is its call center rep, sound library. And you can use it unchanged. Things like collections and type servers and they just work. And the how it works Scala implemented in terms of Java API very often and instead of trying to rewrite the whole library and have like a compatible but different library, we do a bit more which gives us better compatibility to the story is we implement subsets of JDK API, which are used by Scala, science library and popular third party projects to be able to have the same code on both JVM and native, completely unchanged. Like for example, projects like Utest and fast pers. To the cross-composite idea of they had zero changes in the source. He only had to change the build to support across projects in the city.

**Adam:** So what about the JDK, like, I assume that's underpinning a lot of this Scala standard libraries, JDK calls.

**Denys:** Yeah. So basically those are the Java libraries that we care about. So in typical, typically what means is that we have our own Scala implementation of Java Lang, Java I/O, and a bunch of other things, which are essentially core API, which people rely on in open source projects and Scala library.

We try to implement those as faithfully as possible to their reference limitation on,  under reference JVM. We don't look at the source of the reference, but JVM, because we tried to kind of stay away from the GPL code as much as we can. And essentially Scala is a BSD license, and our implementation is licensed.

And one of the only inspirations for some of the parts of APS we implemented was the Apache Harmony project, which is an early implementation of Oracle APIs,  without the GPL. But under. Apache license.  so we send time to use it for some cases where it's hard to reverse engineers' behavior of the JVM. I know we need some help there.

**Adam:** Interesting. I hadn't heard of that project. So if you're recreating the,  I'm just thinking there could be the case where an implementation detail of some aspect of the JDK actually becomes something that becomes dependent on, and then when you have a new. You know, native implementation and somehow that varies and things break. Have you, have you come across any cases like this?

**Denys:** We already experienced some of those. Technically, every time we see some of us it's a bug and native and we fix it as soon as we can. There are differences that we know of.  some of them seemingly minor, but they can still cause accidental breakage. Like for example, our float to strain, like gentle and float and box-type just train as slightly different output format. It was the same number but has sometimes more trend. Zero is one JVM and it has caused some open-source test projects which rely on two string output to be exactly the same as in JVM to fail.

We tried to fix those as fast as possible. The first time I was in, it's a bit hard, but I go, our philosophy is if you're going to observe the difference from the reference foundation is a bug.

**Adam:** Well that's a that's a hard standard to hold yourselves to. I mean, to me it almost seems like, you know, their tests shouldn't be dependent on the number of zeros that a two-string implementation does.

I'm interested to hear if any,  like of the large Scala frameworks can run on native. I'm thinking like a Spark or ACA. I don't even know what the play framework has any large project been taken over.

**Denys:** So as far as now. Nothing major has happened yet. Probably the biggest codebase that headed across compile this Colise which has been done as part of our recent experiments.

## **Satisfying all the Java Dependencies**

**Denys:** Technically it's not hard to compile the source to NIR like the first step. What's hard is to satisfy all of the Java dependencies, all of the Java library assumptions, which are expected by this project. Like for example. You need like  IO support, like from boat complete socket support. Some of these parts are still working on progress. Like for example, it has been just merged in and initial support for Southwest has been just merged in the previous release. We're still working there. So,  it's a bit, a bit early for like. Major frameworks to just happen out of the box, but to be constantly looking at basically what's blocking people in terms of several library coverages and in terms of API specific support.

And these to me are often implementing things just based on reports of people trying to port libraries. Typically, right now it's a smaller scale, open-source projects like you test and fast bars. And, but for those, even for those cross compilers and test them, it often likes all of these small differences in library semantics are important.

**Adam:** So you mentioned a Scala. The compiler has been, has been ported over. Could you describe why and how that went?

**Denys:** So it had this like still private kind of mostly private experiment or the Scala compiler to, to the Scala native. Right now on JVM because of the startup issues, you kind of have to have an SBT always in the background because otherwise compiler just it's only usable after it's warmed up after a few completions. But if you have native, we don’t really have to have this problem because the very first run is already optimized, so you can already run optimize code immediately. And what have you observed in our very early experiments right now is that we offer. Significantly faster performance and called calculations. And simple projects like an understanding line of code can be that time faster. So basically. Called build.  ms Colossian JVM can be like two to three times slower than,  called built on native.

**Adam:** Wow. That's, that's amazing. I mean, one of my frustrations with Scala is,  Yeah the cold compilation time can be longer than any other language that I can think of. So what were some of the challenges of, this? Moving it to native.

**Denys:** So probably the major challenge was to have enough IO. So we had the long story, of doing a file IO in different types of file IO because Scala sees like uses almost every single type of file. Your JVM has a, don't ask me why, I don't know, but it's basically, this is IO uses Java IO and a bunch of other things.

So also things like jar. So most of those kids have been contributed by Martin Durham from the Scala Center.  and it's been extremely helpful to make this even possible because essentially without. Its libraries and project depend on, it's hard to run it on native. So basically those are probably the hardest parts.

We also had a have a work in progress support of Scala ASM. So is a work of ASM library, which is a Java byte code generation tool kit, which basically lets you programmatically admit job bicycles. What's policy does all the time? So we have a limited,  it's up to the library part. It's native,  to have enough APIs to compile and to clause files but otherwise, those basically were the only challenging parts. So we only kind of, the library problems, we haven't really discovered any major bugs in Scala. It's this way. So as soon as we had a library drown, basically, that's basically typical story of port and stuff native.

**Adam:** Once those libraries are in place, then it works great. So if I have a, if I'm in Scala native and I have access to see as well as to, you know, Scala and JDK libraries, like what is a string? When I create a string, is that a native string? Is that a set of Java string? Is it

**Denys:** Immutable? So let's call a string is an instance of type string. Which is immutable, a string baked by Scala array, which is also garbage collector, which is quite different from what he has for C has for arrays, Right? So she has just a, basically, a sequence of bytes in memory, which, and was traveling zero. It's really this number. It can be really anywhere because it's C and it's untyped.

So when you call an API, which expects the C string, you need to convert Scala string to C strings. In some cases where, you know, you have the same data presented in both Scala and C side, you can share data structures, but often you have to,  copies data over if they're completely different formats.

Like, for example, for file IO, when you read or write a bias, we can just share a memory with  Scala native arrays without copying.  so it does not authenticate that you have to copy data over.

**Adam:** So you can, you can use either and you get to choose and there are some helpers for going back and forth.

**Denys:** Absolutely.

**Adam:** Yeah. I can see why that would be very useful. What hardware architectures, what platforms can Scala native-run on.

## **What Platforms Scala Native Run On** 

**Denys:** So technically we have very little requirements, but right now we only test on 64-bit architectures. Mac and Linux, a 64 bit Intel people have reported and it seems to work on the 64-bit arm unchanged. Also, we don't officially support our amens moment as we don't have for it, but generally just about any 64-bit architecture so it just worked out as a box.  we only had reports about arm and Intel, but. Maybe more obscure things like PARP is you would work too, but be done now for sure, because we don't have this kind of hardware, so basically anything was a 64 bit  I should just work.

**Adam:** I think now I kind of understand a lot of the usage around Scala native. What interesting projects have you seen making use of this project?

**Denys:** So there have been a number of experiments going around. So one of the more interesting ones there is this experimental framework and development code. Denver, and it's actually very, very early stages, but it tries to be like native first fhat framework, which currently is built on simple stuff like CGI. Is it all sort of. Experimented with a faster GI now and it seems like it's an interesting place to be because happened to the point we have a stable that from our, it's basically the first framework to market will be the main framework for Scala native probably, it seems like it didn't, is our, has the biggest lead,  to market so far and is there's already quite a bit of code working and quite a bit of experiment and you can check one of the blog posts.

I think we had some of them. Who retweeted from his Twitter.  but basically it's sick days to do a native first bad prime Mark, which is pretty cool. I've always seen people do different types of a comma, line tools, and this is basically the area where we excel. And this is the area where JVM is often word land unusable performance-wise.

**Adam:** Just because of the warmup time. Yeah. If you, if you write a command-line tool, it's just this slow.

**Denys:** Yeah.

**Adam:** So because of that quick startup time, I'm interested if anybody has thought of, or if you think it'd be a good idea to use Scala native for things like an Amazon Lambda, like serverless computing.

**Denys:** It's probably an interesting idea. I've never seen anyone try it on to be interesting to see how it works out.

**Adam:** I saw, I think I saw some talk on your website about,  compiling down to,  iOS-like to make an iPhone app. Is that a real thing or

**Denys:** Its people try to compile it to iOS and it seems to work in principle, the main challenge was iOS and is interrupt with objective C. Right now, we don't support objective C. Basically, you're a bit in an uncomfortable place right now, as far as I know, nobody's actively trying that, so it's a plus in principle, but it's not directly on our shortlist in terms of things we want to do now.

**Adam:** I think that you mentioned earlier that you were inspired by Swift with the LLVM intermediate language. Is that right? Yeah.  so how, how did it inspire the implementation of Scala native?

## **Major Scala Influences**

**Denys:** So Swift is called, and I recently, but the major inspiration for Scala was Scala GS. because before it's Scala GS, it was basically considered,  like general truth, too hard to implement Scala outside JVM. So, essentially, major, major inspiration from Scala is Scala GS and not Swift. The swift influence is mostly in terms of,  compiler,  technology in terms of what we do under the hood. So, so it has this, an intermediate language called SIL which is short for Swift Intermediate Language and it's kind of like a higher level,  LOVMIR and it's basically the area we also aiming for was NIR. Like a higher level, LVMIR likes saying the main difference between a SIL and NIR is that seal is reference content and a NIR is a garbage collected. And basically this probe is a main major difference between the two.

But otherwise, they're trying to solve a similar problem, both sort of presentation for high level optimizing. A compiler for high-level language and they both try to optimize parts, which LVM cannot do well because LOVM is actually a very low-level API and very low-level representation. Because, for example, some things are just simply gone by the time you and its LOVM are one of her longstanding issues is the promise of virtual dispatch.

We already did a lot to make it pretty fast, but still,  an LVM,  when you compile a virtual, this past typically ends up with. Calls to function pointers. Basically, this is what you compiled down to, and when you're at that low level of obstruction, you, it's really hard to optimize this away. So LVM typically does very little close to nothing to optimize virtual dispatch ao this is what we do ourselves. So a cell also solves similar problems, and basically it's a. A format for pre-optimization before the LOVM condition happens. So you tried to make the LVM job as easy as possible and to meet high-quality coding.

**Adam:** Were there any challenges with having a language that has two paradigms like Scala and kind of having this compile to LLVM.

**Denys:** Actually, I don't think this two nature thing was a big problem.  probably is the main reason is that essentially Scala already does a functional object-oriented part of combination essentially.  all of the high-level features are all high-level functional features that are placed by equivalent object-oriented features.

Typically what you end up by the end of the Scala compiler is a very object-oriented code. And essentially most of our challenges to make functional code work well are the same estimate object code. Well, because at the end of the day, for example, at closures are just object to this virtual message, just the same as any other object-oriented so basically it's all compiled down to this same representation where it has. The same for a much for both object-oriented and functional features.

**Adam:** That makes sense. Yeah. So that kind of part is taken care of for you. What features are up and coming in 

## **Up and Coming Features for Scala Native**

**Denys:** So right now,  we are pretty much complete in terms of language support.

So we don't know any major semantic difference, which will be a breaking change as we would like to fix it as soon as possible. So, and most of the innovation right now is happening in libraries. So we are slowly working towards bigger and bigger coverage of our implementation of Java API APIs.

I was a major thing, which we are trying right now are multi-strategy in API, like from Google, it seems like locks, concurrent primitives, and so on and so forth. And apart from that, it's also networking and its things like that. So basically those are typical API. So you would need for backend microservice kind of app. This is kind of the area of which we see Scala being used more in the future.  so apart from library innovation, we do lots of, lots of work on the compiler code quality, and there's around 10 code quality. So basically those are small iterative changes patterns we see basically to improve performance, to reduce overhead, to reduce footprint,  to make it even more lightweight and so on, so forth. I guess that's pretty much what it is. Why do the areas where we always see the biggest changes, which are like non-iterative, incremental, slow, a convergence towards better performance are changes and garbage collectors are probably the area where we could? 

Do things significantly better than what we do now.

**Adam:** So if people would like to learn more about Scala Native, where should they go?

**Denys:** Started places. Our website, scala-native.org, and our Twitter, twitter.com/scala\_native. Those are the two central places for announcements, our latest releases. And so as a forth,  you can also go to get her as a Gitter is a second nice cozy chatroom for.

If you just tried Scala, if something doesn't work or you have a problem, it's basically a place where you go to to ask questions. And of course, for all of the active development where you can get help and type issues, like the discussion on what's going on is happening over there. It's basically if you're subscribed to Twitter and Gitter and get help, it's pretty much, you will see everything that's going on.

**Adam:** And, I understand since you first announced this project, you've had a lot of contributors. Is there a lot of contributions coming in?

**Denys:** There's actually quite a bit of contribution right now. We have a bit more than 60 contributors. Overall, it's really nice because people often contribute sometimes small things, sometimes bigger things, but it's really, really nice to see people interested in the project and trying to help as much as, again.

**Adam:** Yeah. That's great. That's great to have community involvement. It's not just a, you know, a couple of people working a way on it. Well, thank you so much for your time, Dennis. It's been great to learn about Scala Native.

**Denys:** Thank you for having me.
