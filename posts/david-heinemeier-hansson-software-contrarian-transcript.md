---
title: "David Heinemeier Hansson, Software Contrarian - Transcript"
date: "2020-02-01"
---

David Heinemeier Hansson talks to Adam about being avoiding a software monoculture. He explains why we should find a programming language that speaks to us, why ergonomics matter and why single page apps and microservices are not for him.

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/12943403/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

"That is the pleasure and privilege of working with the web. No one knows what you built it. It, you could build an in basic, you can build it a Ocaml, you can build in the Haskell, you can build it in whatever Ruby. No one is going to be none the wiser you get to choose. You want to write for the web. I mean, literally every programming language that's ever been invented and known to humankind is serving a webpage somewhere."

"The crimes against programming humanities that have been done in the service of single page applications are far worse than the ones that have been done in the service of microservices.

But then of course, as it is, lots of people combine the two. So it's a fleet of microservices serving a single page application, and that's just where it bam, my head explodes with like, yeah, I would rather retire and fucking, I don't know, make weaved baskets than deal with that shit."

### Transcript

**This is a machine translated transcript. Podcast page for [this episode is here](https://corecursive.com/045-david-heinemeier-hansson-software-contrarian/)**

**Adam:** David, thanks for joining me. So I think that like Ruby on rails, it kind of, it changes the world in some ways, at least by a very small world of, of software development. I recall like years ago going through some tutorial, that I think was like build a blog and Ruby on rails, and I was a, a C sharp developer at the time. it was kind of mind blowing, like just how quickly you could build things. Why did rails succeed?

**DHH:** that's a good question. I think a lot of it was just the right time. there were just a bunch of things that had gone before the stuff that I'd made that essentially provided the foundation, but that I felt was just trapped.

So I drew my main experience and influence for rails from two camps. One was Java and the other was PHP. And I thought that Java was simply chock full of clever people who have clever ideas working in an absolutely terrible. Development environment.

So if you could take those clever ideas and as I like to call it, liberate them from the environment, you'd be left with some really clever ideas and they would be much more appealing.

They would be much. Broader distributed, they were just very inaccessible for people who weren't already deeply enmeshed in that world. So that was where I drew the other inspiration, which was from PHP, where you literally could do a one line thing that said,

print hello world. And it would show a web page. It would show hello world on a webpage. You just drop that file into the correct folder and you're on the web. I mean, just such an incredible, I think to this day, still unsurpassed ease of hello world. So I thought, Hey, if we could take the great ideas around frameworks and how to structure larger software applications, and we could infuse them with that ease from PHP, there'd be a really interesting combo here.

And that was really what I did. Right. And then the conduit for that was, Ruby. That was the sort of third missing element. The third secret spice to the, to the dish here was that Ruby is simply an incredible programming language that enables you to have the best of both worlds. That immediacy.

Then ease of, of introduction, that ease of use, like the, uh, the print hello world is almost as easy, not quite because sort of it's not targeted just at the web. yet it's a language that's also capable of carrying the ideas from something like Java.

So that's really all I did, I took those three elements, put them in a pot and started real good. I was building base camp at the time, and I needed practical things. Right. And I think that that approach to it, that I'm the builder was also the tool maker.

Gave it a unique feel that wasn't true in all other environments, especially in the Java world. There were, at the time, a lot of this architecture thinking that people would be architects and all they'd be doing, they'd be doing frameworks and they'd be doing deep thoughts about how you should build applications.

They wouldn't actually necessarily be building those applications. Right. And the outcome was often sort of, uh, what Spolsky used to call 'em architect Austrian odds. That they would get so high up in the stratosphere that you essentially lose all oxygen and lose your mind. Um, so my way of tethering myself to earth was to actually build with what I was constructing.

So Ruby on rails turned out to be this really practical thing that was using influences from these three different environments. And then I had the blessing and the gift of being a newbie. I was new to Ruby when I started on rails. Rails was basically my first real sort of project. so I didn't know what you couldn't do.

And that went both for building something in Ruby. For making open source software. It went for a lot of things that I simply just didn't know what it entailed or what the challenges were or what I was supposed to do and not to do. So I just felt like, well, this is the thing you can do. Of course, you can release a framework that does everything in his full stack and like 2000 lines of codes and, and, and you should show it off to the world.

So I was influenced certainly by the open source community at large, but I was also repelled by it in some instances. . It was very intellectual when you were pitching your software, but like, well, here are the tradeoffs here is sort of the, um, objective measures for, for why we've done it that way, where I try to convey an emotion.

What does it feel like to program in this environment? What does it look like? What does it taste like? What does it smell like? Invoke all the senses, not just like you're a prefrontal cortex, right? Like, go wider, dig deeper into, um, uh, all the elements of being a human. Because I think if anything, Ruby's greatest insight was the programmers aren't just programmers.

They're also human.

And I tried to follow in Ruby's footsteps of appealing to the whole person, um, to sort of a deeper humanity in, in, in programmers and for reasons greater just then let's make software, right? Like, let's make software that we really enjoy making. Where the art of creating the software is a pleasurable experience in and of itself that can supersede and be more important than all these other attributes we keep talking about.

Whether that's execution, speed, or memory usage or all these sort of objective terms that feel like very concrete and very real. Uh, Ruby was incredibly daring, I think by going out and say no. The most important thing, the most important design criteria for our. Programming language is going to be programmer happiness.

I mean, what a hippie concept. I showed up here and it felt like. Ruby hurt me. Ruby saw me. Ruby was sort of speaking to a deeper aspect of my being almost sort of, uh, communicating with my soul. Um, now it's really getting hippy. And then Ruby sort of took my hand and showed me just how deep the rabbit hole could go. And by the end of it, I came out on the other side.

Loving programming, loving, uh, the creation, loving the dance with the syntax and the subtleties of the language and going like, this is what I want to do with the rest of my life.

**Adam:** out of your three components, Ruby definitely seems like the most unusual. I had never heard of it before rails and I don't know if I would have heard of it, if not for rails, like how did you come across it?

**DHH:** yes. So when I first got introduced to Ruby and was absolutely this esoteric. Very lightly used programming language, at least in the West.

And I think it was 2003 I picked up, um, a couple of these programming magazines. I think it was one from Tripoli and maybe one from ACM or something else like that. And in one of them had an article by Martin Fowler where he was explaining some pattern, and he picked Ruby to explain this programming.

And he said something in the intro, akin to, Hey, I don't usually get to programming Ruby, sort of professionally. Yeah. But I'm just explaining a concept here. Ruby is very close to pseudo code, so even if you don't know Ruby, you'll be able to follow along. And I, and then he showed his his idea and I thought like, wow, this is wow.

What a beautiful language. What an interesting, this looked very different from what I've done before. And then, um. I think it was Dave Thomas who had another article in the other magazine where he was also talking about some programming concept or another, but he also picked to use Ruby and.

 I just got inspired by the fact that here are two of the great heroes of the programming world. When they are free to pick, they pick Ruby.

So I thought to myself, when I had an opportunity to pick whatever program willing to try, I wanted to use it. I should probably listen to these two. These guys, they sound pretty smart,

So I think that the initial. Interest, or that initial exposure just sparked something in me. And I, I quickly tried to learn everything I could about Ruby. And shortly thereafter, I think maybe 2004, I went to the third, it was called the third international Ruby conference, I think, which was essentially an American Ruby conference.

And I think there were about like 42 people there. And I was giving a talk on a rail to that point. I had worked on it for, for a bit and I was giving a preview of it. And, um. At one point I asked, so how many people in this room get to work with Ruby professionally? And I raised my hand because I was actually getting paid to work on Ruby.

And I think there was one on the person who raises her hands. So this was like 2004. The main Ruby conference in the West has like 42 people there. And like two people get to raise their hands. Um, how many you work with it commercially? Um.

And I think just a few years later, we'd be like 2,500 people at the rails conference, um, in whatever city that was. So it was kind of a wild ride. Um, and that was fun.

And like I look back at now, I've worked with, uh, with, uh, with Ruby for, what is it like 17 years now. Um, and I'm, I'm as excited as I was when I discovered Ruby 17 years ago. It is just truly a uniquely beautiful, engaging, rewarding programming language. And I feel just utterly blessed to be able to still work with it.

It's just a, it's just a treat.

**Adam:** so you went to this conference and these people were interested in the language but weren't using it professionally, um, but were excited about it. do you think that that like the, that there's a broader lesson there? Like if I pick a language today. Um, the people are very excited about, um, but aren't using in their work that that's like a sign that there's something there?

**DHH:** Yeah. I think it's, it's always a great, uh, signal when you have people who are so enthralled by. A technique or a tool or language or whatever, that they were willing to sort of just do it for the fun of it. That was really what the other 40 people in that room did. They did it for the fun of it. For the intellectual stimulation, for the excitement of getting to work and programming with Ruby like that's a very strong signal that there's something there. Now that doesn't mean that that's going to be the next big thing.

There are countless tons of both frameworks and programming language and whatever that over time I've had a very passionate, small core group of people like you can speak to Haskell programmers or Ocaml programmers or whatever, who were like, this is the best, greatest thing ever, and it is for them. It doesn't mean that it's going to be a mass movement in the way the Ruby on rails is because truly, very few things become a mass movement, right? It doesn't necessarily matter. I mean, I'd be doing Ruby and rail still if we were, I mean, maybe not 42, but 200 people. Well, maybe not 200 but 2000 or 10,000 people, right?

Not, it doesn't have to be a million person movement for it to be a place where you can live and breathe and work. Um, I mean, I created. Base camp when Ruby had nothing, right? In terms of the tooling that I wanted and I needed to create web applications. I just created all that stuff for myself. By hand. I mean, it's totally doable, right?

That is the pleasure and privilege of working with the web. No one knows what you built it. It, you could build an in basic, you can build it a no camel, you can build in the Haskell, you can build it in whatever Ruby. No one is going to be none the wiser you get to choose, which is really unique.

Advantage of the web as a distribution platform that is very seldomly cherished enough in my opinion. You look at all of these other platforms, you look at a, you want to write a, um, um, uh, Android Android application and it's going to be Java. Well, maybe you can read it in Kotlin, but like, it's going to compile down to Java bytecode, right?

You want to write a thing for a iOS? Well, I'm you, you're going to ride in Swift, right? Like it's just such a mono language approach it, there are a few people who do something on the edges, but not sort of in the broad sense, right? You want to write for the web. I mean, literally every programming language that's ever been invented and known to humankind is serving a webpage somewhere.

I'm sure there's all sorts of, uh, uh, applications out there that those programming languages don't have good access to other programming platforms, but they have access to the web.

**Adam:** Yeah. Yeah. That's an interesting kind of meta point. Like if I, if I find the language that's my Ruby, I might not be able to build rails and have it such be such a big success, but I can, I could still make a framework. I can still build my stuff in it. I could still live in that world.

**DHH:** And you really don't need that many people for that to happen. I mean, I think when we look at the modern web. Tool chain. It's very easy to get overwhelmed and think, Oh my God, I got, we could never build that. Like you could just look at rails, look at the number of lines of code that's in rails, and like you stare at that today and you think, Oh, let me rebuild that no camel, and you're going to go like, yeah, that's just not going to happen.

There's like tens, I don't know, maybe there's hundreds of programming years into that, but remember Rails didn't start like that. Rails was serving real business traffic, unlike 2000 lines of code. That's what base camp launched on. Ruby on rails, I think was 2000. Maybe it was only a thousand lines of code.

Actually, I should know this, but it was a very small package created by one person in their spare time. Um, and that was enough to get on the web. Right? You don't need to recreate the entire tool chain. In fact, in many ways, it's better to start from scratch. Because this is your opportunity to jettison all the preconceived wisdom of what you're supposed to have, what you need to have.

No, you don't. You can you can you print a HTML tech? Can you send back a 200 okay. There you go. Off to the races.

**Adam:** Yeah, yeah. And you said business value, which is interesting as well, right? Because if I, I guess if I build my, my thing, you know, Ocaml, um, if it has business value and people end up using it, um, there's going to be some longevity there,

**DHH:** yes. And I think that that's sort of the magic of programming, right? Like we get to build these things out of sort of basically the spirit of our imagination. And, um, and again, with the web, it's just, you can do it in anything and like, no one is going to. Judge you in terms of at least uses using it as long as it's a good application, right?

Like it, it, it really can be done in anything. And then you get to have that longevity, at least if you're the ones working on it, right? I mean, Ruby had this, uh, argument used against it in the early days, which there's some validity to, but for example, let's say you build a launch application and let's say a ocaml right.

Perhaps your sort of talent pool for just hiring someone who could plop into that project and be productive right away is, is a little smaller than has been.

Um, but it's certainly doable. And I think. You should do it. Right. I love this idea that like the web is being served by hundreds of different programming languages that I could be using this web app I really like, and it's actually a written in Ocaml or

**Adam:** Hmm.

**DHH:** or algo 64 or whatever esoteric language.

It could be like, that's, um, there's just something heartwarming in that, that this idea of the monoculture that like this is all just a battle to the death and there's going to be one framework and there's going to be one programming language that lifts. Is left standing. Programmers are really drawn into that right into that horse race.

So much of their technology choices seem to be predicated on like, is this popular? Is this going to be popular next year? Do you know what I mean? Fuck that.

Not all, not in all places, but plenty of them who have the freedom to just pick something because like they want to do it. And, and I say to them, please, do I want to see what that ocaml next framework is going to be?

Right. I think actually one example of that, um, that I love sort of following from afar is elixir

that here you have this sort of obscure, for a lot of programmers, at least programming language in Erlang. But, and then along comes Jose and says like, Oh, this is actually great technology. There's some core idea here, ideas here that are really important.

Let me try to sort of shape those a little bit and make them more appealing to a wider audience. And here we go. Now there's a great programming platform and language , I look at that and just go like, man, that's amazing. I love that.

**Adam:** Yeah. I agree there is though there is a certain weight like to popularity, right? Like there is a certain like fullness of of libraries or or whatever. That is an advantage when you're,

**DHH:** It is. It is. But I find that that advantage is often overstated. And the reason I say that is because that was literally the number one argument that kept hearing when I created rails back in the day. Oh, Whoa. I mean, there's only like, there's so few programmers and yeah, everything starts from a seed.

If you expect that every new thing is going to be this thousand year old. Redwood, nothing new is ever going to happen. You have to have the seas, you have to have the people who are willing to nurture those seeds and accept the fact that, yeah, they're not standing with a Redwood right now. You can't drive through it. It's a, it's a small little thing and you have to protect it and you have to nurture it, and that's also really satisfying. There are people who really get a kick out of that. Me included that. Seeing my life's work in terms of Ruby on rails grow from this tiny little seed that I planted in the ground, the fertile ground of Ruby, but ground nonetheless, and seed nonetheless grow into, if not a Redwood, at least a very strong solid tree.

It's just magic. And there are people who are attracted to that and they're not all at the same people. Some people just want, yeah, I just want to use the thing that's popular because like I w I w I maybe don't care as much or I'm not an infant as much, or my boss is yelling at me, or like, whatever it is.

Right? There's all these practical, reasonable reasons for why someone would just go like, just give me the most popular thing. Right. Like that. That's got to be the best thing and that's fine. It's great. It's, it's okay. Like Ruby and rails is in some ways a beneficiary of that same thinking that once we tipped over and became this mass phenomenon, there were a lot of people who suddenly had permission to use it.

And that was a long time and a driving force for me working on rails was to make rails Poplar enough that it gave people who didn't have otherwise a choice to permission to use Ruby. That felt like just like a gift to the world. Um, and a gift that I essentially owed the world, given the fact that I had found Ruby as a gift to me in my programming journey.

So to return that favor to a broader audience was incredibly rewarding. And I think still one of the crowning achievements of all the work I've done in rails, it's not just the rails, it's the fact that so many people got to work with Ruby and. Perhaps they otherwise wouldn't have had. Like maybe they would have, maybe someone else would've come along six months later and they created bales or whatever, something else.

Um, and then would've gone on to be just as popular. But there's certainly plenty of examples where that didn't happen. Right? Like programming languages that that had something to it where people saw a sparkle in it. It didn't go on to be a mass non non for a variety of reasons of either timing or fit or whatever else.

Have you. So the fact that Ruby. Did and ended up being this, um, mass language like this mainstream language actually, in many ways, right? Like, it's being used. You set, uh, sort of all these internet companies that everyone's heard of, right? Like, let's run skid hub and runs Shopify. No runs square. It was the foundation of Twitter.

It was like all of these things, like people go like, Oh yeah, I know that. Right? And all these companies are now, many of them, big billion dollar companies that hired tons of programmers all the time, and those programmers get to use Ruby. And then there's this entire ecosystem What a wonderful thing. Okay?

**Adam:** It's true, but I, I'm going to give you the negative spin on it, which is when you created rails, there were people who were forced to do Java who didn't want to. There's people who, who are doing rails now who don't want to.

**DHH:** Yes. And I think that is a real thing, but I also think there's, that's a sort of subjective truth that I absolutely recognize. And then at the same time, if you were to do it on the grand scale of like the number of people or the percentage of people forced to use Ruby who actively hate it, I. I'm certain just in my soul that like that is a far smaller number than the number or the percentage of people who are forced to use Java who hate it.

Right? Again, certainly there are people who will be exposed to Ruben, go like, what the hell? Right? Like I F one of the things, for example, is that Ruby is loosely and dynamically typed, and some people simply have their brain wired in such a way that that is an offense to their sensibilities.

Right. And I respect that because I feel the same way about sort of, statically type languages. I, I, I just don't like it.

And I find that a lot of those people have been sort of forced into a bad situation from the start. Like they joined some company that had a truly terrifying code base because some people just wrote some bad code, right? And they associate that with Ruby on rails, and they go like, this is where I, I hate Ruby on rails because I have to work in this shitty code base every day and it's killing me.

Okay.

**Adam:** I think that's right. yeah, oftentimes it's actually just dealing with a horrible code base where everything might fall over and yeah, there's just no fun there.

Um, I definitely, uh, I definitely find, uh, types really useful, but, uh, I do like, I do like Ruby as well, you know, when I first encountered it, um, it has some, some things that, uh. The aesthetics of it are, are unusual, right? Or maybe less unusual now, but certainly at the time it seemed like a lot of things seemed like sort of the inverse as I would expect.

You know, like you have a, instead of like, you know, looping over an array, you do like array.select or, um, you know, what was your, how is that kind of, um, I'm trying to think of how to word this question. What did you think of it when you encountered it? Did it, did it look strange to you or was that

**DHH:** for whatever reason, Rubin was the program programming language had been searching for my whole life. And when I saw it and I saw the,

just the layout of the statements and how it all fit together, it was just one of those Eureka moments where, uh, how my brain thought about programming was expressed in this programming language.

And I know that that's sort of.

That a people have that about all sorts of programming language. They go like, yes, I can. We use this example over and over again, and the funny reason, or the funny thing is like, I actually don't even know what Ocaml looks like. Like I don't even have a mental picture of it.

Right? But there are, I'm sure there's some people who come to a camel and just think like, yes. This is me, right? Like this fits my brain. And then there are other people who sort of acquire a taste for something, um, that they didn't like Ruby in the beginning, and then they work with it for awhile and then they do, or they didn't like John in the beginning, and then they worked with it for a while and then they do, for me, it was just this romantic moment of love at almost first sight.

And then just is, um, just faction right from the get go. It was just like, this is how I think. Like it is, is like if you were to do sort of the source map off my brain, it would map to Ruby

**Adam:** Nice. That's interesting. Uh. Yeah. It's funny. I was just, you just made me look, look up some OCamll examples. I think that, I think that you might like it because it is strongly typed, but it's a, it's like inferred types, so there's not actually any types and it kind of a please stand by.

**DHH:** I see your screen. Um,

**Adam:** lots of lets.

**DHH:** yeah, that's, it's, it's funny because I don't know, for whatever reason, I had a sort of a lisp look in my head when I said, okay, ammo. Um, this obviously does not look anything like list.

It doesn't. Like it doesn't speak to my sort of heart right away, but at this point, I'm perhaps also beyond the point of no return with my love affair with Ruby. I will absolutely accept that. That's a possibility. Um, yeah, this is actually not bad like that. That looks, uh, that looks pretty cool. But yeah.

Then I look at this, although this is sort of a, this is one of the reasons why for a long time I thought I wasn't going to be a programmer. Like the code we're looking at now is sort of very mathematical. Right? Like it's, it's about math problems and I was never interested in math problems.

**Adam:** listeners, I've pulled up the end Queen's problem, which I think is, yeah, a very mathy type problem.

**DHH:** Yeah. And this is exactly why I literally thought I wasn't going to be a programmer because I just didn't have any interest in math problems. I don't have any interest in algorithms beyond their utility. Um. What I do have an deep, deep affection for is sort of domain modeling. I'm sort of in the, uh, Eric Evans sense of the word domain, uh, driven design.

Uh, I love noodling with a business domain. I love finding just the right words. I love sort of breaking that, the main model apart and, and all that stuff, which is all sort of. logicals sort of semantical approaches to it. It is not algorithmic. It is not scientific. It is not. Um, math.

**Adam:** Yeah.

**DHH:** and I think that this was one for the longest time why I thought like programming is not for me, because I knew quite a few programmers and they all did the math type programming.

Like they were demo coders or game programmers or whatever and everything was vector this and vector that. And I would look at the code and I'd just go like, yup. No interest. Absolutely zero interest in that. And then I started working with the web and I started to working with business applications and sort of it in the literal sense of information technology and so on.

And I thought, Oh, Oh Oh. Can programming be this too? This is what I like, like programming, uh, of this sort. That's what speaks to me. That's what I'm interested in. Um, and then I kind of just went like, let me double down on that. And then Ruby just felt like that was a perfect fit for that. Right? We looked at that piece of piece of math, the code, and like camera looked more clean somehow, right?

Like it didn't feel like Ruby is the natural language for doing math. Like programming.

**Adam:** That makes sense. Yeah. So I had somebody on as a guest, and he was talking about how, like some people really think about coding as math, but he thinks of it as, as like literature. Uh, what do you, what's your take on that?

**DHH:** Yeah. I'm, I'm in that camp. I had a. Keynote at a rails comp. I think about five years ago where I framed all of the sort of approach, how we think about programming rather than thinking of about like construction projects or thinking about math properties. I think about it as writing problems like it's, it's about being a good writer.

How can you be clear? How can you be succinct? How can you structure your paragraphs into cohesive arguments that makes sense to a human reader? That's the part I enjoy. The writing part and the rewriting part, like sort of the draft and the edits and I'm boiling things down into sort of logically clearer components, fitting those things together. And then, um.

It's just like there's some division of labor here is that I have no interest in the zeros of the one or the assembler language above it, or the C code above that. Right. I, I joined the stage by the time we get to the high level programming language of Ruby and then someone else with interests different than mine can, can do sort of the work beneath it.

**Adam:** makes me think of like, I think at the same time I became familiar with rails. Um, there was a lot of excitement about it, but also, I mean, people who really didn't like it, and. I mean, maybe that's kind of where the division was. There was people who, you know, maybe, I don't know what they were doing, building databases or distributed systems where they thought they were.

Um, and they were like, this isn't real coding, or I'm not sure. Did you, this is my impression was there was, did that kind of pushback happen? Um, or imagining it.

**DHH:** Oh, hugely, hugely. No, absolutely happening today. I've still literally listened to people say, well, what did they call it? Ruby is a scripting language, and they say it into sort of the rice of tone, right? Like it's not a real programming language. And like people like, well, you can make prototypes. This is what I hear all the time.

You can make your prototype in Ruby on rails, but once you make a real application, you're going to have to rewrite and something else, and you just go like. Dude, where have you been for 20 years? Like, look at the internet. You stooge like a lot of it is running off Ruby on rails. What you think, uh, you think Shopify is not a real application and get hub is not a real application.

Um, it's just the, the blinders of sort of ideology. And, and I can see where they're coming from, right? Because I'm actually, I'm a fan of ideology in many ways. I'm a fan about having values and practices and beliefs that underpin your paths for life. But you gotta recognize the fact that when you adopt an ideology, uh, the trap is that it puts blinders on your head, right?

And you start thinking that the values that you hold dear are these universal truths. That are true for everyone rather than just your personal truths. I'm very comfortable accepting just the personal truths of Ruby for me. I don't need everyone in the world to believe those same truth. They're true for me.

Ruby is the perfect programming language for the kind of work that I do using the brain that I have. Right? Like that's about as, as personal of a statement as as as they come. But there are a lot of people who sort of adopt an ideology and then they just. They can't square other people having a different one.

Right. And then the cognitive dissonance of sort of other people being successful with a different ideology or a different toolkit like just blows their minds. Like they literally can't hold that truth in their head without going crazy. So they just sort of dismiss it.

**Adam:** I guess their complaints have to do with tradeoffs the rails and Ruby have. Right?

**DHH:** I think the vast majority of this is not based in sort of some logical empirical, objective evaluation of different languages. I think it's absolutely a contrast of ideology, and if you're a kind of person who goes like, you cannot, right. Sort of high quality software without static typing like your head will simply not accept the fact that people are writing high quality software using a dynamic view type language like Ruby, right?

And then you need to cotort your arguments to support that conclusion, right? Like, then you come up with all this other stuff. There's a bunch of good books about how, um, sort of, the logical mind is actually not the one in charge, right? Like, it's, it's our, it's our sort of primal. Mind the one that operates on emotions and so forth that's in charge.

And that mind will come to a conclusion and then it will enlist your logical mind to come up with the justifications that support that conclusion. And I'm as susceptible to that as anyone. But I tried to sort of, um, limit dose justifications just to underpin my own personal truths. And I mean. It doesn't always succeed.

but yeah.

**Adam:** you think the enterprise Java guy looks at Ruby and rails and he's just like primarily angry about it and then backwards he works and says like, well, it's not as fast as what I've written

**DHH:** Right? Or is it that speed matters for that application I'm working on? I mean, that is the biggest joke of all when back in the day when sort of the enterprise was the bar, right? Like, is it, is this language enterprise ready? We don't talk about these terms anymore because they've been ridiculed to death because the enterprise usually means like nothing of significance, right?

Like these days it's. It's a web scale, right? Like there's no enterprise application that runs in what a fortune 500 company that there's more traffic than say, Facebook pushes through PHP, or that Shopify pushes through Ruby or that any of these mega companies, uh, on the web deal with like the enterprise is just small potatoes and what it didn't use to be right.

Like, it used to be that there was some sort of unique scaling challenges that the enterprise was fail facing. But, um, that's not been true for.

**Adam:** So then you I guess you're saying performance is not a trade off that's being made like because it doesn't

**DHH:** I mean, not, not categoric you're right. Like there, there are these cases like, um, there are cases where you truly hit a hotspot or a bottleneck and you want to replace that with something. It's just that for the vast, vast, vast majority of applications that point is so far out into the future or so imagined as it might as well be a fairy tale.

It isn't a fairy tale, right? Like there, there literally are people who deal with Webscale. Um, and, and when you're dealing with, um, I dunno, a million requests per second, like, yeah, you need to do different things. You can't use off the stock software. But that was always true. Even in the Java days, right?

Like, you can't use standardized tools to deal with extraordinary, um, circumstances. You need extraordinary tools. Like, this is why if you look at everyone from Facebook to Google to whatever, they've built their entire tool chain internally, right? Like pro Google build it, got them programming language, right?

Like Facebook build a new interpreter for PHP, and like all of these web scale companies eventually end up in a place where they built their own tooling because they need to. They're at the, literally at the Vanguard of sort of pushing things to the maximum. I mean, they're building their own damn hardware for Christ's sake, right?

Like facebook even is doing hardware design because like that just makes sense when you have, I don't know, 200 data centers that have millions of computers and shit in them, right? These are not the problems that we, you and I face and that like 99.9999999% of everyone else making software today face.

I'm interested in making software for the 99% and do you know what the 1% they can go off and make their own software. They always have

**Adam:** Uh, one thing, one thing that I think is unique to the software industry, right, is, is like that, that 1%, I mean, they're really held in, in some reverence, like, so we're all watching what they do and trying to learn

**DHH:** to our detriment.

**Adam:** Yeah. Like I guess if I watch somebody build a skyscraper and then I. I tried to build my house using like I-Beams or something.

**DHH:** Perfect example. Yes, there is a reverence, I think, thankfully. Um, it is fading. Uh, I think both in society at large and also in programming circles where everything that comes out of, say, Facebook or Google is not. Automatically just thought to be the greatest thing ever, or in service of the Nopal list aims a goal ever.

I think finally. Um, but also just on the practical sense, trying to learn from the people who have the 1% problems and apply those to your 99% concerns is often exactly the opposite of what you should be doing. The constraints and challenges that Google face at Webscale are just utterly irrelevant. To what the 99% are dealing with.

Not only are there irrelevant, like the, the solutions are literally the opposite, right? Like you simply, you almost couldn't go worse if you tried by looking at, Oh, so, so how has the Google search engine implemented? Right? Like, what kind of setup does it have? What kind of distribution does it have? And then you apply, try to apply those lessons to like how to run your little web app, like base camp and, and, and I mean, you die.

Before you even made it to hello world, because just to sort of construction of that whole rigamarole would kill you as a business. Right. Um, so I, that reverends is. Is better thought of as like sort of a distant appreciation, not actually as a fucking guidebook, right? Like it's, it's, it's actually the opposite.

Um, and then worry about the 1% problems when you're in the 1%. Right? And then it has all these sort of embarrassed millionaires that are wondering about like, how to outfit their yacht while they have like 30 bucks in their checking account. That I just think like, do you know what? Maybe you have more pressing concerns than what a marble to use on the fourth floor of your yacht.

Then I'm. Uh, then than worrying about that, right? Like you shouldn't be worrying about like, well, how can I make something happen that people like and now we're going to get a hundred people to like it. I'm going to get about a thousand people to like it, right? Worrying about what will happen once you have a billion users and do you know what?

I think you're wasting your time here.

**Adam:** Yeah, but it's hard to find where the line is, I guess. I don't know. So let me, let me give you some examples. Um, so a company called, uh, Amazon. I think kind of pioneered, um, microservices and, you know, my experiences with it have been that it can be a pretty useful way to, uh, to do things.

What, what do you think?

**DHH:** Is this a trap? Do you know? I have like a 15 minute rant of micro services, so I'm always at the re the in my gun holster.

Yeah. I think microservices and the hype around it is probably one of the most damaging, uh, trends that has hit. Web development in the last 10 years. Um, I think very few things have done more damage to sort of the integrity and the productivity of software development teams.

Then the premature application of microservices. I am a stound. Stout and proud supporter of the majestic monolith. This idea that you have a single application that a single person can fully grasp, comprehend, understand, deploy, operate, and then as far, far preferable to this. Idea of having a fleet of microservices, a building, a hundred different toolkits and languages that no one knows how to sort of operate in and go on.

Microservices is a great

example of an organizational tech pattern. It's not actually a programming tech pattern. Microservices is what you do when you have teams so large that they essentially need. Dominion over their own domain. Right. They need to sort of control their own boundaries and so on. And when you have 50,000 programmers, yeah, it's a completely reasonable pattern and it makes total sense trying to apply it while you have two, five 2050 programmers.

Jesus, no, just no.

**Adam:** So I would agree

at five, I don't know, 50 50 is a lot of people, like it can be helpful to break people up into teams. Right. Um, and then it can be helpful if those teams have a, a clear, you know, area that they own with clear interfaces.

**DHH:** Yeah. I think that just that the boundaries are much higher, right? Like, I don't think it happens. It's 50. Um, I think I think it happens a, a much later in the equation. And that the benefits of having a single application that everyone sort of, uh, operates on are vastly underrated. And that this, uh, appeal of the microservices, um, approach neglects all the tremendous.

Downsides to that approach. Um, including the whole idea that a method call is now a network call. Right. And just the complications that come with trying to orchestrate different applications together. And I don't say that just out of sort of a high minded, um, theoretical concern. I say it out as a practical concern of someone who did microservices back in like 2006.

Um. Base camp actually had a number of microservices when I kind of, uh, before microservices we called it service oriented architectures. And it's sort of the same thing depending on how coarsely you, you grain things, right? But we broke base camp up into a number of sort of sub-services right. And I just, I learned on my own body just how different a method call is from a network service call.

And it's funny because in some ways we're, we're traveling back in time here. Um, when I got started with Ruby on rails, the big thing in Java was EJBs, um, and J2E, which had sort of these remote and local services and which was essentially doing the same thing, right? Turning method calls into network service calls, and it was a shit show then too.

And I think it is exactly as we talked about, people looking at. The big shops. Oh, Netflix has 126 services to run their thing. Of course we should have 23 right, and you just go like, no, you shouldn't. You should have one.

**Adam:** Yeah. That's funny. What about another example I can think of, I guess is. Like single page applications or or react like, I think rails is in the, in the world primarily of like emitting HTML, but a lot of things are moving towards maybe a more free standing front end

**DHH:** Um, first, I think tons of rails applications are feeding Jason into react applications and . And, and all peace be with that. That's not how I want to build applications. Um, that is a, another instance of distributed applications where you end up having one application on the front end that talks over an API to an application on the backend.

Um, and you end up with a lot of reimplementation back and forth and a lot of contortions to make that happen. And I'm not a fan at all. And at base camp, we try to not do that. And all of our approaches to, uh, dealing with the front end is in, in, in essence, um, ways to get out of that while delivering the same high quality user experience.

And there are not surprising we tons of other alternative techniques that people can use. But I will absolutely say that react has been an astounding popularity success. I mean, it's really quite something to watch. Just how. Sufficiently it's swept the world. I think it's more of a tragedy or a comedy than it is a documentary of how to do things well.

Uh, especially once you mix it and not so much just react in its core, beautiful form of sort of blow away the world. And rerender I actually kind of like that. Um, it's more, once you get into all the contortions needed to make to make a complete application, right. And a Redux and all these other things.

When I look at, uh, a fair amount of that code, I look at some redox routing code and you'll go like, do you know what J2E was simpler than this, even at its height of complexity, even at the height of the Ws. Deathstar for an, it was simpler than this. Like, how did we end up here? Holy shit. Um, so.

Even if I think that the single page application front end is a horrifically overuse pattern, far more so than than even microservices. And I think, so the crimes, against programming humanities that have been done in the service of single page applications are far worse than the ones that have been done in the service of microservices.

But then of course, as it is, lots of people combine the two. So it's a fleet of microservices serving a single page application, and that's just where it go. Like. Co plan, my head explodes with like, yeah, I would rather retire and fucking, I don't know, make weaved baskets than deal with that shit.

If I had to work in assembler or, or even C, I'd go like, do you know what? I could do something else with my life. It doesn't have to be programming. And if someone told me, do you know what? You have to build a fleet of microservices and the has to work with a single page application, front end.

I could go like, do you know what a farming sounds nice. Give me a rake. Um, but so we are different, right? Like, it doesn't mean that, that's just my personal truth as we were talking about, right? Like, it doesn't mean that that's right for everyone and community. There are people who, who like this thing and to each ther own in some regard.

Like, I will continue to advocate for the fact that I think that this is , but, um. That's just my efficacy. Right? And you have to discount that from with my biases and so on and so forth. But you can use that as a counter melody to play in your head for reconsideration. When you think, Oh, let me just go with what's popular on the industry norm.

Like, let me start up with my Ragnar services. Let me go for my react Redux monstrosity. And like, that's best practices, right? You'll have me sitting as a little Canary singing, no, it's not. right. Or like. That's a dead end, like a Canary in the coal mine lane with my tongue out, just going like, don't go so deep.

You're going to die

**Adam:** like you think we make things too complicated, like just in general, is that true?

**DHH:** I would even go stronger than, than think in that statement. I would say people make things too complicated, period. And it's tragic period. And I wish they wouldn't pay re it. And I'm trying to focus most of my advocacy on . Helping them unlearn the things that they have learned that have let them down this, uh, tragic path.

Um, so yes, I think that programmers in particular are susceptible to the siren song of complexity and they get this kick. Out of being able to master that complexity and out to wield that complexity, whether it's appropriate or not. It feels just like a, a sense of intellectual accomplishment that you can figure out the most gnarly shit on the universe.

Like a multi microservices backed application serving a single page, front end application. You can go like, I am victorious. I beat the computer and you can feel good about that and I just go like. Oh, Kay. I mean, we all have our kicks. That's not my kick. Um, and let me tell you that there is a different way here.

**Adam:** how about unit testing and test driven development.

**DHH:** Um, you hitting all the, all the highlight and hot buttons here. Um, yeah, I gave a talk. It was actually that same talk that the one we just talked about with, uh, about software development being writing 2014 you can look it up on YouTube. Um.

Where I call TDD the greatest diet fad that the software development world has ever seen.

And I kind of labeled in that it, that from perspective of sort of this approach of pseudoscience, right? TDD presenting itself as the scientific method of creating better software. And, um. I just thought it was bullshit and I lived under it for a long time where I thought, yes, the gospel is true to teach truly better, and I'm a bad program and a bad person because I don't get it right.

I, I wrote TDD, I wrote a lot of TDD, right? Test driven development. I wrote a lot of tests first and then I wrote my code and I didn't like it. I thought it was not a way to fit with my flow of my brain. Like most of the time what I will do is I will explore my programming first, just sort of exploratory.

I'll figure out how it works, and then I'll write my tests afterwards. I'm a huge believer in automated testing. I mean, I can't even comprehend how you can make a modern application without automated testing and have it. Any confidence that the thing is It often serves the proponents of TDD to conflate those two things. Like, Oh, you're against TDD, therefore you're against automated testing.

No, you're not. What the fuck you talking about? I love automated testing. Um, what I don't love is to drive my development through my tests. I don't love writing my tests first and then writing my code afterwards. I don't love having my tests dictate the inner workings off my. Classes and in my methods to serve some sort of testability purpose.

There's TDD proponents who simply believes that like. If you write code, it's easy to test. It means it's better code bullshit.

No, it's not. I did a whole series together with Martin Fowler and, um, Kent Beck on this topic. When back from that 2014 talk, when I sort of provocatively pronounced TDD to be dead and I promoted it to be dead and sort of that niche, a sense of the word that God is dead, right?

Like it's not that God doesn't exist, it's that that doesn't. He doesn't hold the central focal point in our universe anymore, right? And that's how I felt about TDD, the TDD for wild health, that central focus point and in a programming universe. And, and. And I want it to kill that. Right? Or I wanted to see that die.

I just got fucking tired of listening to people telling me like I just didn't get it. No, I get it. I just don't agree. Like those are two separate things. Right.

**Adam:** the TDD advocates or whatever, they're, they always seem a bit too. A bit too keyed up or something like it's the, it'll, it solves everything. Um, what about just like, just like unit tests? I believe I watched something, uh, where you were saying, I dunno, unit test not as valuable as people think.

**DHH:** We usually have about half as much test code as we have production code, and that's been a ratio that has been surprisingly stable across all the applications that we've done at base camp. Not because we designed it that way, but that seemed to just be a heuristic that for us, for our application, turned out to be.

That's the level of tests that we sort of. Like to, to have the confidence for, um, for our code and unit test is one part of it. But I think that oftentimes, actually I've stopped calling it unit test, what we call it now. We call it model tests cause some purists took offence to the fact that when we do unit tests in rails in particular, we often end up talking to the database, right?

Which is a big no note when it comes to unit tests that you're supposed to isolate all your sort of dependencies and, um, Test only in isolation, both for speed and for repeatability and blah, blah, blah. And I just went like, do you know what? I'm not interested in that. Those kinds of tests do not reveal anything interesting for me.

Uh, I want to be able to test all the way down to the database layer when I test my models, because that's where I often find the bugs or the issues or whatever. Uh, and I don't really like mock or stub data. I find that it often introduces all sorts of bugs, and then I need to deal with those and da da da da da.

We write some model tests and I think model tests are great. And then we also write some sort of control of tests which happened at the layer above.

And those controls also do not stop anything out. They actually called the real models and those real models called real database calls and so on. And then above that we write call system tests that flex the system for active of, um. The job and driving a browser and so on and so forth. Sometimes you have the same thing tested in your model tests as you do in your controller test and as you're doing your system test, and other times you just go like, do you know what the system test covered tier is fine. The controller of test coverage here is fine.

I don't need to replicate everything down to a unit test level because I have to level of confidence than I need or want in my code. So we're done.

**Adam:** There you go. Your, your book had some interesting things that were kind of like more organizational, but, but that I found equally shocking, like in my work, we meet daily, um, kind of, we have a standup meeting where we kind of all say how things have been going.

If anything's in the way. Mmm. Do you think that's a good use of time?

**DHH:** in the broad sense. No, I think the requirement for standup, which often. Have these connotations of in-person that they're better when they happen, sort of face to face, um, are not worth their price. And the price, especially for in-person standups, are synchronization of time that everyone shows up at the same time synchronization of space, that they're all in the same location at the same time, these are.

Dramatic compromises and costs that I could never subject our organization to. And the value you get out of that synchronized, uh, linkup to me seems very small in comparison, right? The advantages of remote working, uh, we have 56 people at base camp, and I think the city that has the most people, um, in one cities like Chicago and there's like 10, um, we could not operate our business like that.

If it was for an in-person standup. Now people do these stand ups, they do it in over sort of video chat or whatever. Um, I also find that just to a lot of time, be a waste of time. Like I don't need, we don't need a SyncroNis meeting that's sort of under calendar every day to give status reports. In fact, writing status down as.

Far better use of time so people can show up when they show up. They can read it at their leisure when it fits into their schedule of the day, and then you can have this asynchronously communication back and forth if there's blockers. The need to to happen. Now that does not mean that there was never a time where you should sync up synchronously and talk things through when you hit real deep blockers where you need to do collaborative design work together, by all means, jump on a video chat.

I do that all the time. It just doesn't happen like every day. Barely happens every week. Maybe it happens every few weeks. Then we have a thing where we go like, Oh, this is a real hard problem. We don't want to wait for, the asynchrony is back and forth. Like most of our design problems we solve through pull requests and comments, and someone will chime in on that pull request when they're ready.

And someone will read those comments when they're ready and it's plenty good enough and you don't need these synchronized gears that kind of grind the whole organization to a halt unless they line up perfectly.

**Adam:** so I work remotely from, from here. Uh, I have for some time, um, and my team. So we all kind of do our stand up on zoom as we're talking now. Um, you know, one thing that I get from seeing people's face, like maybe not everybody's as vocal as you are. So like if I'm saying like, Oh, we need this new calendar thing, so I'm going to rebuild the section using like react in a single page app.

Like maybe I'll see somebody wince and then they can explain.

**DHH:** I agree it's important. Humans are important. Looking at humans move and picking up the subtle cues. Important, everyday important. No. We do these synchronizations at base camp every six to eight weeks. So we run these six to eight week cycles, which also comes into a whole critique. I don't know if we have time for that too, but I think sprints and the whole sprint language is absolutely a travesty and a harm to the software development community at large.

Um, this idea that you should be constantly sprinting and that sprint should only be like a couple of weeks long, I think is has caused immense damage and harm to software development. Now it came as a reaction to something that I totally understood why that reaction came, right? Like if you're used to sort of projects that run on for years and years, you go like, Holy shit, this feedback loop is totally broken.

Let's do the counter to that and let's just do it every two weeks. I just found that like doing that every two weeks is, is, is, um, is its own kind of harm. And where we ended up at base camp was, um, with this methodology we called shape up. We just. Published a, a web book around that is base camp.com/shapeup the details, our full methodology and how we approach it, the software development process.

And that process includes that every six to eight weeks you have essentially sort of some cool downtime where you consider what you do next. And it is in that time when we sync up and we have a chat face to face. Well. Zoom to zoom or video chat to video chat, um, where you go over what you should build next.

If you are in the middle of developing things and you just come up with, Hey, we should build a calendar in react, you're software decision making processes broken, right? Like if you can just on any given Wednesday, come up with a whole new branch of feature, um, something's wrong.

**Adam:** Yeah. I guess my example is bad, but sometimes people thrash, right? Like they just start working on something and they get stuck and I don't know. Yeah.

**DHH:** Totally, and you should follow up on that. Um, and you, you can write, like if you have someone observing the work and following along and doing pull requests, you can see when people get stuck and then you can do an intervention when that happens. But over sort of prescribing that intervention to be something that has to be applied every single day for every single one is to me, a complete misapplication and miss intervention and actually disruption and, uh, one that comes at great cost

**Adam:** how about just like a, I use Slack and you know, often pinging people on my team. Uh, to ask them questions

**DHH:** my condolences.

**Adam:** not useful.

**DHH:** Harmful.

 I think actually the introduction of chat as a main source of company communication has probably been the most hurtful introduction in the history of sort of interactive communication tools. And I say that as someone who built a, essentially a chat tool just like Slack in 2006 called campfire and for many years essentially ran a company on that philosophy it's a terrible way of working and you don't realize it until you take a step back and look at how your day is spent and how it's broken up and the cognitive harm that happens through interruptions, that if you can't seem to get two, three, four hours of uninterrupted time without someone pinging you, interrupting you.

It's, it's, it's not good. We have a whole big a write up on this, uh, that Jason, my business partner, just recently finished called group chat stress.

Again, not the chat is always bad, but the chat as a main mode of communication is a horrible interruption and intrusion on people's . Productivity, cohesion and sanity. So you have this partial attention syndrome going on all the time because of chat versus sort of the reaction that chap came to, which was email, right? Email has in its sort of most naive implication, a lot of all of these issues, right?

Like it's, it's, I'm not saying that email is sort of in its base form is wonderful, but you know what is wonderful asynchronous. Write-ups of cohesive, full thoughts, people using actual goddamn fucking paragraphs to describe ideas and proposals, and they put those paragraphs together into form entire, cohesive thoughts.

And then letting someone take that in, read those several paragraphs, sit back for more than fucking five minutes. Ponder that. And then respond. 

That is all lost. Once you move your collaboration to chat, every person now thinks on a line by line staccato basis and you don't want the quality of that thinking is low.

It is poor and it has all sorts of cognitive consequences to interrupt people constantly during the day to get them to reply to this or reply to that. Um, I think chat has really done tremendous harm in that regards and in some ways, um. We're still healing our organization from the harm the chat has influenced,

because once you pick up the habit of chat, once you pick up the habit of pinging someone, it is so fucking addictive. Like you have to slide as issue. You're, you're stuck for 30 seconds. Oh, let me pick the Sam because Sam knows the answer, right? With no consideration about whether Sam is in the zone trying to solve a real hard problem. Right? You just ping Sam. Hey Sam, what's up with it? Can you solve it for me? You have no consideration about whether what you're, what the cost of that interruption is, and often the cost of that interruption is incredibly dear, right?

Because Sam wasn't just pinged by you. He was also pinged by, I mean Susan and Jack and a bunch of other people, right? That you didn't even know. And before you know it, Sam has spent his entire day just answering other people's questions, trying to get into his groove, into his loop, and he has nothing to show for it.

Absolute travesty, absolutely. A contributor to burnout and all these other things.

Chat is not the sort of devil in all regards. And I think especially with the social components of chat, chat can be quite

Helpful and useful to create cohesion in a remote team and they're good and you should do some of them. You just shouldn't drip it throughout the whole day and require everyone to pay attention through the whole day and require them to be immediately responsive to someone pinging you on chat.

We have a concept, for example, called office hours. That's, let's say you have someone like Sam who's the expert in some domain, and a lot of people have questions they want to post up. Sam Sam decides the Thursdays from 10 to noon, you can reserve time with Sam.

To ask him questions about his expertise and you don't pepper those questions over the whole week, you simply hold them until it's fucking thursday Right? And do you know what? Most of the time you'll solve your own problems sooner and you'll learn more and you'll be better. You'll, you have taught yourself how to fish before it's Thursday and it's not relevant or it gets to be Thursday and you get some real dedicated time where you're not in position where everyone has agreed upon that this is now a good time to do it.

And Sam has set time aside to be available for you and that works well.

**Adam:** it's, it makes sense. Um, but at the same time, because of the way that I feel like I'm working. Currently, it sounds insane like that. I would wait until Thursday to talk to Sam. .

**DHH:** Yeah, totally. Because we've all gotten addicted to right here, right now is ASAP and that is a terrible addiction. That is very hard to break once you've become addicted to ASAP. Uh, almost anything else seems insane. I could totally see that. Right. But, um, actually the insanity is the water that we're in.

Um, I, I love this, uh, commencement speak by David Foster Wallace that goes, uh, this is water. Uh, you can look it up on YouTube, which basically goes to say that like, you become blind to your insane environment very quickly. If, to me, it's an absolute insanity that anyone can interrupt anyone else in entire company at their leisure with no warning, no consent, uh, and just like, Hey, because I want to fuck that.

It is such a selfish, um, view of the world, right? And I think it's counterproductive. And when it happens back to you in return, you don't like it. Right? Like, people get it. People like helping other people. So this is why they always say, yeah, yes, right? Um, this is why you never get like, Hey, can you help me with this?

And people say, no. Come back on Thursday, right? Like you need to set up procedures and protocols for this to be effective. Um, and if you don't, you just get this selfish imposition of people stealing other people's attention in sort of the slight inconveniences, just because it's good for me. It's good.

This is what I want right now. I want someone to help me this second. It can't wait 10 minutes. It can't wait an hour. I can't write it up. As opposed to for Sam to ponder later. I just need this right now. No, no, that's, that's insanity. But I totally, I mean, I, your reaction is, is a perfect reflection of, of how most people respond to a lot of the ideas we have about how to work.

Right? You go like, well, this is not how it works like this. That seems crazy. Like, right. Which is, I mean, that's literally the title of our latest book. It doesn't have to be crazy at work.

**Adam:** Yeah. So we're running out of time, but yeah, I've really liked the book. It's, it's very, I think it's short and pithy and the, I guess the big takeaway I got Was something like that, like, Hey, we're all really busy. Um, but we're not getting anything done. Maybe. Maybe we should stop that.

**DHH:** Isn't that insane? Right. The fact that people can't go work done at work that so many people think like I have to show up early in the morning, stay late at night or work weekends cause that's the only time I can get my actual work done if I'm just there. In the office from nine to five. Well, what happened to my time is I had to spend half of it paying attention to some rolling conveyor belt of chat.

Then I have to spend the other half with people pinging me and then another half, and now we're up to three halves. That's intentional being pulled into all sorts of meetings for status reports. Holy shit. Just shoot me now.

**Adam:** so I recommend everybody check out the book. Uh, thank you so much for your time. This has been a lot of fun.

**DHH:** Absolutely. Thank you for having me on and and pushing all my red buttons.

**Adam:** that's what I'm here for.

**DHH:** Awesome. Thanks man.

Picture from [Faces of Open Source / Peter Adams](http://www.facesofopensource.com/david-heinemeier-hansson/)

**Links:**

- - [The Majestic Monolith](https://m.signalvnoise.com/the-majestic-monolith/)
    - [TDD is Dead](https://dhh.dk/2014/tdd-is-dead-long-live-testing.html)
    - [RailsConf Keynotes](https://m.signalvnoise.com/all-my-railsconf-keynotes/)
