---
title: "Portal Abstractions with Sam Ritchie"
date: "2020-04-17"
---

## **How abstract algebra solves data engineering**

Today the story of how twitter engineers came up with a unique solution to data engineering.

Adam interviews Sam about how the abstract algebra and probabilistic data structures help solve fast versus big data issues that many are struggling with.

Adam talks to Sam Ritchie, a machine learning researcher.  Stop in to hear their conversation about portal abstractions that let you leverage work from other fields. 

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/14012333/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

"You want to go mine the literature of what other people have done. You know you want to be able to plug these things into your work and really just benefit from this incredible community that's been cranking, for again, maybe hundreds of years." - Sam Ritchie

"So I think to go forward like there's always going to be new discoveries to be made, but one very, very fruitful thing to do is to turn around, look back and find these things and say, well, is there an interface I could discover that someone's already found that would let me just plug into this incredible, almost battery of human creativity that just exists waiting for the taking.  It is in maybe dusty old papers and books, but it's there. No one's hiding it." - Sam Ritchie

"I'm aiming to implement these interfaces and pass these tests and then being able to immediately turn around and have like an approximate sliding window counter that would just work with stripes ... entire machine learning feature generation interface." - Sam Ritchie

### **Transcript**

**This is a machine-translated transcript. Podcast page for [this episode is here](https://corecursive.com/050-sam-ritchie-portal-abstractions-2)**

**Adam:** Several years ago, Twitter had this problem that may sound familiar. The problem is big data versus fast data or batch processing versus real-time string processing. Probably because of the scale that they operate at and the realtime nature of the Twitter feed they hit this problem earlier than the rest of us.

Batch is very efficient. You can calculate things on years of data, but doing the calculation might take a day. Real-time is much faster, but you can sort of only work forward in time. Really, you need both these things. If I want to look at my most liked tweet, I need to look at all the old batch data, but also any real-time tweets that I'm doing 

So it's 2013 Sam Ritchie is a mechanical engineer by training is uncle is Dennis Richie, and he's working at Twitter, and his job is just translating from one system to the other from real-time to a batch job.

**Sam:** And there's just so many jobs that looked like that, and it kind of looked like that was going to be my life, like just coding these things. 

You just said enough is enough. Like we need to figure out how to write one piece of code that will run in a real-time world and also in batch world.

**Adam:** I guess I've come up with the problem from that side where it's like, “oh, I can calculate this thing, but I just started calculating it and like, the world existed before.”

**Sam:** Yeah, the backfill problem's hard and it's hard. Like it just consumes your life writing, you know, backfill jobs and you kinda, you, you stick to really simple things because you know, you're gonna have to write them twice. You're going to have to maintain them twice. I mean, it's really not a nice way to live. 

## **Backstory**

**Adam:** Hello and welcome to co recursive. I'm Adam Gordon bell. How did Sam get away from these one-off jobs? How did they solve this fast versus big data issue? An issue many are still struggling with, the answer isn't some new data processing system that he's here to show. 

Well, the answer is actually abstract Algebra and probabilistic data structures.  If you don't know what those are, don't worry. We're going to walk through it. We're also going to talk about what Sam calls portal abstractions. That’s finding abstractions that let you leverage work from other fields, But we'll do that at the ending. Let's start at the beginning. When Sam was working away at Twitter.

**Sam:** I was on the revenue team.  I had a colleague named Oscar Boykin who I didn't know that well. We both maintained one of these like libraries I mentioned before that lived on top of a dupe. He had the scala version. I had this closure version and I'm kind of yet again, I had a task for work that was like building one of these dashboards.

You're trying to count something like, you know, tweets per user per day. You're just basically grouping on some key and then adding numbers to a database. And there are just so many jobs that looked like that, and it kind of looked like that was going to be my life, like just coding these things. 

Through, you know, this or that, Oscar and I teamed up to work on some shared piece of machinery for serialization between the code we both maintained and we realized that like we both were doing this sort of thing and he's got a lower tolerance for BS. You just said enough is enough. 

Like we need to figure out how to write one piece of code that will run in the real-time world and also in the batch world.   Like this is, this happens with compilers, like this is a compiler problem. Let's just back off and solve it. 

**Adam:** So they solve it. They built version one of this open-source analytics system could do a batch, it could do real-time. Some of the results together. They called it a Summingbird. It sums things, and it's from Twitter, so it's a bird. But then they had some interesting revelations about what they had created.

## **Stitching Things Together**

**Sam:** You know, if you really simplify what we're dealing with here,  you're writing code that is generating for some key, tweets per user, per hour, something that happens. It might just tweet per user, it might be how many users we have. 

And then you have some value, you have some counter that you're ticking, so you're just incrementing this thing up. And so many machines learning features and dashboards and everything is just like ticking counters. It's kind of like and that's like the secret of analytics work is you're just adding ones. That seems suspicious too. Like that's something you could maybe break out of like a really, is that all we can do? Like how would you do more complicated things? But so this, this software package, Summingbird was a library that lets you write a logical declaration of what you wanted to happen. And then, the second component of it would take, that data structure that you've built and go run it on any number of these different, underlying platforms. 

## **The God of Counting**

**Sam: ** So I can power a dashboard. I can do backfills. I have this boundary that's maintained transparently to me, that behind the scenes we'll give a hard line between the, you know, massive, multi-year database. And then the last couple of hours that are stored in some much harder to manage, much more fragile, but very, very fast, you know, online processing system.

And you know, phase one was just write something that can do, you know logically you're doing the same thing. You've been rewriting the same code. Just have the machine write it for you. but it does open this door and this is the topic I wanted to get to.

It opens the door and you start to look at this thing and think you know, you have these two buckets. One is like all, all-time before a couple of hours ago, and then you have a bucket for each of the recent hours. So you're doing this addition of some of the numbers, Uh, but you're sort of putting parentheses in one case around like years and years of data, and then another set of parentheses around like each of the previous few hours, and then you take this final step of adding them together.

**Adam:** If you're calculating how many times I've tweeted, like Hadoop gets like everything up to yesterday, and then I'm adding that to something that's actually getting the real-time data and just

**Sam:** That's right.

## **Abstract Algebra**

**Sam:**  Those are nice ideas, but they're not that they're sort of obvious and not that powerful. But this idea of adding things and putting parentheses wherever you want, It also seems kind of innocuous. It's like this little lamp you pick up, right? It looks kind of, you know, you rub the lamp, you and what you find is like, this idea is not, it's not your new idea.

It's very simple, but it actually exists in this field of abstract algebra.

**Adam:** Alright. Abstract algebra, if you're not familiar with it, it's a subfield of math. Stick with me here. I'll explain it a little bit. A lot of concepts from abstract algebra can be implemented in a programming language. A semigroup is one of these. It's an interface. It has one method. That method is add or sum. If we want to stick with the summingbird pun. It also has a rule that things have to be associative. You might remember associativity from a high school math class.

What happened here is Sam had the system where to calculate analytics. The calculation had to implement a certain interface and then the system could run it in both worlds. The interface had an add method, which meant it was a semigroup, which meant this subfield of math with people talking about seemingly obscure constructs could suddenly enable him to answer interesting questions in his real-time analytics dashboard thing at Twitter.

**Sam:** So yeah, you can start slimming things back, and when you slimmed it back almost to nothing, you're left with this object called a semigroup, which is an idea of: okay I need some set of things. So numbers in what we've been doing, which is just counting, some way to quote, add two of them together and get something out that's like still the same type and then a test that goes along with that. So the test is that I have to be able to do that associatively. 

So this is kind of, it sort of sounds like a pedantic Mathy thing. Like there's this impulse that I'm sure we can get into in the functional programming world to like, like see ideas that seemed mathy and like slap math names on them and just tweet about it and to like spraying that and that, that sucks.

But I think it's, the, the thing you get when you do that when you identify this like mathematical concept is. It's not yours, because it wasn't your core idea. People have been thinking about this. It turns out for a long time you have potentially hundreds of years of work that has gone into answering questions of what can I do with types that are able to implement a plus method and then a single test of associatively calling plus, that is a very, very tiny interface to satisfy. But there's a huge amount of work on all the things you can, one, all the things you can do just relying on these two properties and two like a zoo of data structures that all hold those properties. And yeah. So by backing out what we built and making it not just about numbers, but about this thing in schola, you might say, I want to type where I can implement a type class called semigroup for that type.

You know, if you just make that one change, suddenly you've kind of opened this portal into. You know, again, this whole zoo of data structures, anything that matches this tiny contract will fit into your model. And that's true of any abstraction. But this one was special because when you turn and look at the computer science literature, you find, you know, things I never would have thought about or never expected to work in the context of like, you know, an add dashboard job.

Suddenly we were able to plug into this thing. So the work became less about how do we go manage, you know, real-time and batch and this kind of boring suit and tie stuff too like we've gone into Narnia and suddenly there's these like approximate, sketching data structures where I can feed items into it and it'll give me a count for the unique number of items seen.

And can do that up to billions and billions and trillions of items and it just won't get any bigger. Like it doesn't actually have to store them. How does that work? That's like a different question. All you know is that you can take two of these things, add them together, it works associatively and so they suddenly become candidates for running on years and years of tweet data or Twitter data or any, you know, large scale data set and the results, you know, will make sense, will not have any errors and will be real-time updatable.

## **Why Adding Things is the Key**

**Adam:** So you went out to solve this problem of, of like realtime analytics. And your solution is, uh, is a semigroup. It doesn't seem obvious to me. I guess that that's a solution to the problem of analytics.

**Sam:** Yeah. That's a semigroup. And then the Monoid, I mean, it doesn't stop at the semigroup. Yeah. It doesn't seem obvious that that's the problem too. Uh, the, that’s the solution to analytics, but, it is, 

What, what started to happen as you start to realize that, okay, well it's not the solution to analytics per se. What it is though is, you know, adding things together associatively this seems to be the key that unlocks being able to store data in multiple places and merge together you know your results when you want.

So being able to distribute in space or time is tied somehow intimately to the associative property that we know from elementary school. Like that's kind of odd.

Why do I say it's like intimately tied? Just because if you ask what you need to go do that like it's really just this one simple property.

**Adam:** Let's do a tiny recap. So if we want to run calculations in real-time and batch, we need a common interface. That interface turns out to be  semigroup from abstract algebra. That interface is important whenever you need to distribute calculations.

 

**Adam:** All right, next up in solving analytics is how you deal with data that may be missing. We're going to change our interface to handle that, which will bring us to another interesting concept. 

**Sam:** There's other properties, like the idea of missing value, like if you're querying multiple databases and data might be missing, like, how do you deal with that?

Well, okay, you probably need some notion of like a zero. So if I'm adding numbers, like adding zero doesn't do anything, that's fine. If I have like lists of tweets, I'm merging together, I can have all these nil checks or check for none or have optional types, or I can know that for a list if I can concatenate an empty list, nothing happens.

So my code becomes simpler now because I've got this idea of like, you know, an empty data, an empty element of the type. So you can, you can start to see that like a lot of data types have this idea like a set has this idea, uh, numbers, of course, have this idea, for multiplication, you kind of have this idea or you do it just once instead of zero.

So that's kind of odd. But you know, in fact, there's another thing called the Monoid, which again has like this in your face name. , but it's just the same as the semigroup, but added on is this extra method you implement called identity. We're just getting back a thing that if I pass it into plus to something else, you just won't do anything.

So again, a very simple idea. But what you get out of it is suddenly the ability to handle missing data. And that comes up all the time. And like dashboards, like how do you represent, data is not there yet. 

## **A Restrictive Interface Can Make You Creative**

**Adam:** All right. So we have semigroups so that we can distribute work. We had one more method to our interface and we get Monoids so that we can handle the absence of data. This is still a very small interface to enable distributed computing.

**Sam:** It's a very well defined interface, but it's, it's I really think of it like, Portal. It is like a portal into some like an interdimensional transport system.

I used to think when I was thinking about how do I become creative? Like what do I want to do in software? And you want to make like original things that no one's done before, right? You want to make these things like crack the door open on something no one's thought about, but. I think more lately that that, I mean, that's kind of lonely. Like if you do that, if you actually succeed and make some like 2001 obelisk, and that's exciting, but it's the contrast that with. If I managed to build like a transporter gateway from like Star Trek, right? And you look through and like you weren't creative at all.

Like you just made a thing that like million, you know, millions of other galactic civilizations and made before, like that's good. Now you get to plug into the network, like coming up with abstractions like. You know, figuring out some, like, I don’t know, an endpoint to a website or like the packet format required to talk to the web.

Like that's what picking an interface out of some, like an incredibly well-trodden field, as abstract algebra does for you. 

**Adam:** Okay. This metaphor is great. I think it needs a little explanation. The monolith is from the 2001 Space Odyssey. I don't think anyone understands it, but it's powerful. This is like coming up with your own unique solution to a problem, a solution that no one has thought of. But the transporter gateway from star Trek, an HTTP interface is less creative. Perhaps you're implementing something that someone else already built. It's not really a new discovery, but you get to draw on all the existing solutions that exist for that interface. You transform your unique problem into a known type of problem where known solutions exist. This is what Sam is calling a portal interface.

**Adam:** What was on the other side of this portal behind your, your ad function?

**Sam:**  I mean, we, what, what we got, we built a library of all the things we found. The library is called Algebird. You know, very concretely we got, I mean, the thing I'd never seen before, it was this whole zoo of data structures that the core idea is that if you don't really care about the exact value that you're accumulating wo for numbers, maybe I want a counter, but I don't really care that it's like exact. Like I'm happy with 0.1% error, maybe a hundred or a thousandth of a percent. It turns out there's this whole field of research on data structures like this where if you can give up a little bit error or a little bit accuracy, you can get often, you know, two orders of magnitude, you get a hundred X space savings on this thing and that just, that's so outrageous.

That, I mean, that took me a while to even understand like what the hell was going on.

**Adam:** Like, why so why does the amount of space matter? I can make a Monoid that just adds every Twitter user together.

## **The Amount of Space**

**Sam:** Okay. This is a great point. It's not even that it doesn’t, have anything to say about what you can add. It's that you can plug things in. It will just shatter the system. So this example you gave, if I'm trying to go say, I just want to keep lists of everybody's tweets. I decide to group on a user and every time a tweet comes in, I make a list with the single tweet in it. That's my thing. How do you add lists? You just concatenate them together. No problem. So what you find is that most of your database is empty cause most people don't tweet. The tweets that are putting out anyway. And then some people just have these huge amounts of tweets that are pumping out. I mean, some, some are bots that are just hammering out tweets every couple minutes.

And so you get these incredibly skewed, keys in your database. Some of the values are just getting bigger and bigger and bigger. And there's nothing in your system that has a limit to this from happening. So when you're running some system that sometimes is fetching nothing, the default value, and sometimes it's fetching like dozens of megabytes of, you know, tweets and then filtering on them.

Like, this is. In some sense orthogonal from your original problem, like that's totally logically fine to do. Totally fits the interface and it'll fit the database for awhile. But it's not everything you meant. There's some problem there. And the problem is that you know, in almost all these systems, definitely at Twitter, there are just skewed keys everywhere.

Like somebody has got the most followers. And so when you, when they tweet, you've got to fan it out to everybody. And that just like hammers the system. Whereas maybe when I tweet, no big deal, like the system wouldn’t notice. Okay, so why would you accept like an accuracy loss? Like, Yeah, I want, I want the total result.

Like I want the full thing. I want to know how many followers I have. I don't want to know how many followers I have, like plus or minus 1%. Maybe not though. So it turns out, if you can, well, the problem you're trying to solve is like, how can I track counters and deaden the effect of these massive explosions of a particular key-value pair?

You get it for free with something like a counter. Because people had done a lot of work to make sure that, okay, all our numbers, add up to some massive amount are gonna use the same amount of bits.

**Adam:** Yeah. If it's a long or something, it can only get so big. 

**Sam:** And if you want to double its size, like just that a bit. No problem. Why do we just count numbers like it's easy? Well, why is it easy like, well, a lot of problems are solved for you just because of the architecture you're inheriting about how numbers are represented.

Like if numbers actually took a ton more bits, if we hadn't figured out like how to write things in binary, 

**Adam:** Counting would be harder. Yea, 

**Sam:** So counting lists, like adding lists is pretty hard or sets let's have that example.

If I want the set of how many followers I have, how many unique people have seen my tweet today? well, what's one, how would you implement that? 

**Adam:** I just add them to the set and then I can combine sets by just getting rid of them, like doing a distinct.

## **Hyperloglog**

**Sam:** Yup. Exactly.  you know, if everybody had roughly the same number, and it was small of people that saw their tweets, but sometimes, you know, there's just huge amounts. So the distinct set of people that have seen you’re,  the tweet is just massively larger than, than the average.

So you get this massive set in memory, and you're serializing a deserializing it every time. And there are two ways you can go. One is you can. You start to build any special cases in your system where the abstraction starts to leak and you say, well, you know, I can't really tolerate this. So like it's not just a type with a semigroup, it's like this other thing and there are more constraints. That's fine. If you can accept a little bit of error, like if I don't really care if my account if people that have seen my tweet is off by 10 which honestly I don't like. I mean in that example like data gets dropped all the time. Like if you see, if you hit like on my tweet and then your phone's offline like there's already air just built into the universe.

So if I accept that and I just live with it, I can reach for a data structure. Like here's the buzzword, there's this thing, all the hyperloglog where. If you allocate this thing, some very small amount of memory, you can get something like 99.9% accuracy on account of how many unique things you've dumped into this.

So it's an approximate set. You add things to it, or you sort of put things into the set and then you can ask the question, how many unique things have I seen before? And it'll tell you and it'll be almost right and it won't get any bigger. 

**Adam:** It doesn't seem like it should be possible.

**Sam:** It doesn't seem like it should be possible. And if you try, if you thought of that idea when you were working on your analytics system and you said, yeah, it'd be really nice if I could just like count this thing and like not have the set grow at all, like you're not going to go take a few months and go off and figure that out.

**Adam:** Yeah.

**Sam:** It just sounds impossible. But somebody figured it out and then somebody, maybe the same person, but somebody figured out that, Oh, if I have two of these things, I can add it together so I can track, you know, I can track like users for a few hours. I can track my distinct counts. And then if I have another set that represents like stuff I've seen before, you know, I can merge or at a later time I can merge those two together. And the result of the merge set will also satisfy the properties that I had with either of the two side ones.

**Adam:** And then we can distribute it. 

**Sam:** Yes. Then you can stop and you can save, you can save your state, and then you can load it up again later and keep going. And that's really all we want to do. Like we want things where you can pause and wait a while and then load it back out and keep going.

And yeah, these approximate data structures get you that ability. If they have that ability, then you can plug them into a system. You know, Summingbird just running these massive analytics jobs and things will just work and you'll solve again, your system’s problem of heavily skewed key distributions that will just go away the same way it does when you use counts.

## **Functional Programming Metaphors**

**Adam:** All right, so we have our simple interface for real and batch, and it turned out that it already existed in Abstract Algebra. It was the Monoid or semigroup. We found this portal abstraction. We rated the research papers and found probabilistic data structures like the hyperloglog or Monoids that run in a fixed space, but I wanted to ask Sam about this pet topic of mine: Do names for math help or hinder adoption and in software?

**Adam:** I just imagine you, you know, standing up and being like hyperloglog is semigroup and everybody, nobody knows what the hell you're talking about, but you're like, no, this is important.

**Sam:** I absolutely have the reaction that you're saying. Like at first I was kinda like, I had to write this job. Fine, we can do it this way. But then it just started to get like. More and more clear that we'd gone down some rabbit hole that was actually like, not just abstraction for abstraction sake, I  had a few experiences of going out and finding papers that, you know, again, implemented like these, there was an approximate sort of sliding window counter.

Would I have found the paper? No. Would I have taken the time to implement it? No. Absolutely not. But  I'm aiming to implement these interfaces and pass these tests and then being able to immediately turn around and have like an approximate sliding window counter that would just work with stripes, like entire machine learning feature generation interface.

Like I could take this thing, put it in the cupboard, write a nice docstring for it, like write a little pitch for why you might want to use it and it would just work. There's no sort of. That doesn't look like it would work in an analytics system. Like that just goes out the window. It just will, you know, we've got the test to prove it and you know, pull it off, see what you can think of.

**Adam:** Yeah, like it seems so non-obvious to me and I don't, I don't really live in this world, so maybe it's not non-obvious. I don't know. I hear people talk about fast data and big data and pipelines. I never hear anybody say like, “Hey, if you can make something a Monoid then you can like calculate it either in batch or in real-time and you can combine it and all you need to do is meet this interface and that's it.”

**Sam:** Yeah. Well, you heard it here.

**Sam:**  No, I look, I'm, I'm with you. And I think, so I listened to your podcast with a DHH and he was talking about Ruby and you know when he first picked up, you know, Ruby-like this, this emotional sense he had and that really got me thinking about like, why is it that this idea is not more out there?

I mean, it's not a tough idea in that if you didn't need it to If you just write the test down and you encountered it, you wouldn't find it to be you. You could do that code, would you? No problem. But there's this like aesthetic sense with certain abstractions and there's something about like pulling abstractions from math that sounds I don't know. I mean, I'd love to hear your, you're in the functional programming world. Like functional programming has this bad rap of just, you know, like, it's all about category theory. We need to show a funk, DARS, and monoids, and monads and, and you know, if you don't get it like here's this category theory textbook, you go figure it out.

What we were trying to advertise was, here are the names of these things and the names themselves are important because they, you're going to find these names when you go on the hunt for stuff, you can plug it, right?

## **Naming in Functional Programming**

**Sam:** If you call it addable you have this problem of, okay, what do, what do you solve? You make it more comfortable. And if I have a preexisting library of things. That I can plugin, like this is great. This, I can look at the name addable the function slot, the parameter type. I can go look at the library and I know what can fit into what.

But what you lose is this sense that you're plugging into this larger, you know, this mine like that you can go down and find new things. And so for someone who's actually looking to like expand the range, you know, I think it would be not wise to change the name to something more comfortable because what you might do, and here's something that happens, you know, I might pick a, or Adam, you might pick up like this thing and you might go, well, okay, I'm going to make a new data type. Like I have addable that looks pretty easy. It's got a plus method on it. And I can implement my thing. I don't pass the associative test, but like, that doesn't really matter. That's just, I'm still an addable, you know, I can still have a minute plus, so I'll make my thing work and like, I'm just going to ignore the test. No problem. I just won't implement that test for me. Um, but like, now you're in dangerous territory. It was so tight. It was such a poetic little interface. When you ditch one of the two lines like you're totally off the map now. 

but I, it really is tied, I think, to this idea of like the aesthetics of abstraction. Like there's an aesthetic response you have to, some people have an aesthetic response to these mathematical abstractions and go like, Holy shit, like this, I’m plugging into something big, and this is a, I'm so happy this post was here.

I have no intimidation at all. Well, some people go, I kind of remember getting my ass kicked in eighth grade, like in Algebra, you know? Uh, like is it really that again, 

**Adam:** I think, yeah, there are cases where people are maybe like overly extraneously using terminology, but here it's actually the key to running things. It is paying weight, I guess, in actual business use cases.

**Sam:** That's right. That's it is, I mean, a thing I'm really passionate about and the reason this stuff's important is. You want to go mine the literature of what other people have done. You know you want to go be able to plug these things into your work and really just benefit from this incredible community that's been cranking for, you know, again, maybe hundreds of years, but then you're turning around and you're presenting this aesthetic thing and.

Yes, it matters like what the references are to the past, but it also needs to kind of present itself, you know, as its own thing to use. Like you should ideally like a good design is about giving people an on-ramp at every level of engagement they want. You know, like “experts only” is like, fine, but if you're trying to build something that's accessible across the, you know, the entire range of experience and like, you find yourself confused about why.

Monoid and semigroup and field are not like doing it for people. I think there's, there's more we need to learn there about how to go use these like incredible minds of abstraction resources in modern code.

## **Finding Abstractions**

**Adam:** I think this makes sense. These concepts are super valuable and these concepts already have names. Maybe the names aren't the problem here. Now I know how semigroups can model distributed calculations, how hyperloglog can give me fixed overhead, but how do I find these abstractions on my own? Like how do I repeat this trick and find my own portal as Sam calls it? 

**Adam:** Like if I, if I go through and I extract some interface, for everything that has a name, like, you know, a dog has a name, a car has a name,  like, how do I know if that's a valuable thing or just me wasting time?

**Sam:** Yeah. It's hard. It's, ‘s like the that's the thing we all deal with is programmers. Like, how do you know? I had this, I was thinking this the other day on a walk that like, I wonder if conspiracy theorists would be like, great software developers would just be so sensitive to like, abstraction. You know, you've seen patterns everywhere.

Like there's probably some dial in, in our brains that crank up or down and it's hard. I don't think an abstraction can like, tell you, like, you know what you just described, like extracting names for everything, like maybe it's good, maybe not. You need a thousand examples that you look at and go like, I think I've got something really powerful here, and if that gets you excited, you should do that.

But if you simply, if you want to make your search process faster, then there are these other fields where people have been thinking that way for a while. 

**Adam:** So there's, um, this great talk about, ah, like Richard Feynman.

**Sam:** Oh yeah. Totally. Tell the story though. Tell the story I think. I think I know what you're going.

**Adam:** So Richard Feynman collected all these problems over the course of his life. And he said like, that was the secret to him being so successful is like, he had all these problems.

And then whenever somebody mentions some new solution as he would just go through his list of problems and see, like if it solved them all. Which I guess is kind of what you're talking about, right? It's like, we'll Monoid solve this, and you try it on. Maybe it's a horrible fit.

**Sam:** Wow. I love that. That's great. Yeah. That's a brilliant Feynman story. It's like, yeah. He says he'll get a click sometimes and go, ah, here's the connection. People go, how did he do that? Well, most, you just don't tell anyone when, when you don't get a hit. Yeah, I love that. Yeah, absolutely. You have this, you have a solution, you have some interface. If you learn about some abstraction that seems powerful in another field, like go backward.

Say, does this apply to what I'm doing? Is there, you know, I forget if it seems natural or obvious, but like what would it mean if I forced it in? 

## **What does the future hold for Software Development?**

**Adam:** What is, what does this all say about the future of software development? How should we think about this idea of importing these portal concepts?

**Sam:** Yeah. I think that the clue I get from this is that, you, I mean, you're trying to solve interesting problems. You're trying to go expand the range of what is possible for you to build. You know, if you buy this idea that these things just kind of lead toward greater complexity and interest there's always more to learn, there's always more to do than one way to make progress is to go make new like artifacts, new examples, new kinds of works of art almost. We're trying to build these, these things like spun out of our thought and. You know, that is, that's really powerful. That's really like what it's all about.

But in fact, there are other fields that have been obsessed with this idea of, you know, structure and relationships between things. And, you know, Physics is one, Math is another.

I think that all of these are just these incredible cupboards we can raid of ideas that most of which were invented before, like the modern software era. 

You know, one way to move forward is to really use the hundreds and hundreds of years of work that have already been done to give ourselves hints about, you know we effectively have like an alien civilization that we can raid. And that's like our own work before the 60’s when structured programming just became a thing.

So I think to go forward like there's always going to be new discoveries to be made, but one very, very fruitful thing to do. Is to turn around, look back and find these things and say, well, is there an interface I could discover that someone's already found that would let me just plug into this incredible, almost battery of human creativity that, you know, that just exists waiting for the, taking in maybe dusty old papers and books, but it's there. No one's hiding it.

**Adam:** We started with fast data versus big data, we hit Abstract Algebra and probabilistic data structures, but these are all just examples of Sam's idea of finding another field that has already solved your problem and pulling in those ideas. Sam is actually working on this right now and his latest side project, he's looking for more of these portal interfaces into Math.

## **What's next?**

 **Sam: S**o I'm, I've got a, like a project that I'm about to, I spent like three or four months in this before my current job and I'm, I'm about to restart it like but it's this like reimplementation of a lot of the core reinforcement learning algorithms, but using like totally hardcore functional programming style.

**Adam:** So it's like you're pulling the same trick or you're attempting

**Sam:** Trying. Yea, to see, see if I can be like a one-trick pony. But from a, you know, like with my math trick. 

**Adam:** I don't mean that in a dismissive way. 

 **Sam:** No, I'm, I'm, I'm on purpose doing it to test this theory we're talking about, about like if you're a one-trick pony, but like your trick is like opening the portal. Like, yeah, just keep doing that. 

**Adam:** Very cool, sir. Well, um, good luck surviving the pandemic 

**Sam:** Yeah. This is all assuming we survive. Yeah, you too, Adam. Good luck with this man

So that was the show. If you have an interesting story of a solution to a problem, like Sam's, let me know. It doesn't have to involve Math. Adam@corecursive.com or you'll find me on Twitter or the website or wherever. If you liked this episode, like really enjoyed it, then tell your coworkers about it. I've been trying to improve the quality of the episodes and hopefully, it shows.

Thank you for listening!
