---
title: "Loving Legacy Code with Jonathan Boccara"
date: "2020-04-03"
---

Legacy code is everywhere. I don't think I've met anyone who doesn't have to deal with legacy code in the substantial portion of his work.

Our guest, Jonathan Boccara is a French C++ developer and the author of The Legacy Code Programmer's Toolbox. In this episode, Jonathan will help us understand and build the correct mindset to effectively work with legacy code by using his approach and processes.

Listen in and learn how you can be good at working with large existing codebases and how legacy code works.

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/13797818/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

"An important message I'm trying to get across is that you should not complain if you don't, in turn, intend to improve the code." - Jonathan Boccara

"That would be any critique that's technical. One thing that comes up very often is levels of abstraction. If I had to sum up best practices in, in three words, that would be those levels of abstraction." - Jonathan Boccara

"The point of code is to make a piece of software run and to make it run in a way that will make customers happy. " - Jonathan Boccara

### **Transcript**

**This is a machine-translated transcript. Podcast page for [this episode is here](https://corecursive.com/loving-legacy-code-with-jonathan-boccara/)**

## **Meet Our Guest, Jonathan Boccara**

**Adam**: So I get to talk with quite a few people and what I learned from that is that legacy code is everywhere. I don't think I've met anyone who doesn't have to deal with legacy code in the substantial portion of his work, at least

**Adam:** Hello and welcome to CoRecursive. I'm Adam.

**Don:** I'm Don. That was Jonathan Boccara.

**Adam:** He's a French C++ developer, and he's on a mission to teach people how to work more effectively with legacy code. So much so that he's written a book all about it.

**Jonathan:** I hope this book will change how people will see that everyday life with working with existing code.

**Don:** To write the book, Jonathan needed to define what legacy code was.

**Jonathan:** It's essentially, existing code that's hard to work with.

I had to come up with a more precise definition, so my definition would be threefold. First, it's code. That's hard to understand for you. Second, it's code that you're not comfortable changing. And, three, it's code that you're somehow concerned with.

**Adam:** So today we want to answer this question. How do you get good at working with large existing codebases? How do you work with legacy code? Basically.

**Don:** And how do you enjoy working with legacy codebases?

## **The Reason Why Legacy Code Is Hard to Work With**

**Adam:** We're going to talk about what legacy code is, how to work with it, how to improve it when you shouldn't improve it, and as you said, you know why you should want to, you know, be comfortable working with it, enjoy working with it.

**Don:** Yeah, legacy code is, after all, just code and reading code and understanding it, is what our job is all about.

**Adam:** Yeah. There's this quote from Joel Spolsky about legacy code. The reason that developers think that old code is a mess is because of a cardinal fundamental law of programming. It's harder to read code than it is to write it. Nobody talks about that. Right? It's totally true. Like writing code is easier than reading it. That's weird, right? Like, it's the opposite of what you would expect.

**Don:** It's very counterintuitive. 

**Adam:** Yeah. So today we're going to explain how to live with and love the legacy code that you have to work with. And how to think about code you're not familiar with in general. How to get comfortable with it. And to do that, I took my various questions about legacy code to Jonathan.

**Don:** Yeah. His process is to accept the code, critique it, own it, document it, and improve it.

**Adam:** And we're going to take you through all the stages. Let's start at the beginning.

## **Accepting the Code and Having to Work With It**

**Jonathan:** I've been a software developer for a couple of years now, like eight years. I noticed that people around me, like the people I met, like meetup or on the internet or whatever, they were sad about the code they were working with. And I think it's a terrible thing. Because most of us, we choose our job out of passion. You know, quite a few developers have been programming before they were actually working as a developer. It really saddens me when I see people's motivation or whether overtime because it's not worth what they were expecting and that they don't really know what to do with it. And they feel like they're a victim of code and that ended up in the worst place on earth.

When you think about it when you get into a new job. It's like your first job or something, you're probably going to get into an existing project. And perhaps this project or company has been there for years and some other people have worked on it. Perhaps quite a lot of other people.

And so on your first day, you're going to be thrown into that huge sea of code written by perhaps dozens or more of people over the years. So you have to be able to work with that somehow.

When you enter a company, chances are you're going to have to face some code that's not as easy to work with as you would wish it were. So yeah, that's an essential thing because that's what is out there and you have to do something with it.

**Don:** So I would call this acceptance. Accept that as a professional, you need to deal with old, possibly crappy code.

**Adam:** Google has tons of old C++ code. Facebook has tons of old PHP code. Somebody is maintaining old versions of Windows, and just being old or not being in your favorite language doesn't mean that it's not valuable code.

**Don:**  I feel like this is honestly the hardest part, accepting old, crappy code and having to work with it.

**Adam:** Definitely agree. All right. Next up in Johnathan's steps is critiquing.

## **How to Critique a Code**

**Jonathan:**  Where you look at a piece of codes, that you have written a while ago or that someone else has written. Something that's not fresh for you.

It happens that it doesn't look quite right to you. It feels like it's badly written. And when you see that you have two choices, I think one of them is saying, this is bad code and move on. And the second choice is to try to express why this is bad code.

Because it happens that, you know this piece of code is not well designed, but you can't quite place a finger about what exactly is wrong with it. And sometimes it takes a bit of time of reflection and analysis to exactly pinpoint what's wrong with that piece of code and being able to critique this code in depth.  Being able to voice exactly in excruciating details why he didn't like it. Once you find out when you identify what's wrong with it, you can, you know what to pay attention to. You know that specific aspect of design and you know it's important because it made you feel uncomfortable in the first place. Next time you're going to write your own code, then you will know, need to pay attention to that.

By doing this kind of analysis, you get better as a programmer. I often compare that with the vaccine, where you get short of a disease, but that's not dangerous and your body has time to do its stuff for the immune system with antibodies or whatever.

And then your body remembers it. It remembers exactly what's wrong with that molecule or whatever. If you happen to actually encounter the actual disease, then your body is going to recognize it. And, and smash it apart in no time.

**Don:** I really like this metaphor. Don't just say, Oh, this code is horrible. I understand why it is bad.

**Adam:** Yeah.

**Adam:** If you want to be a great developer, you should actually work on some legacy code. There is one caveat with this critiquing approach, though.

## **The Purpose of Critiquing the Code**

**Jonathan:** Yeah, I was going to say it's also a dangerous thing to do to critique or rather to criticize code.  As a natural reaction, people would like the existing code that's done. The theory is badly designed and sometimes it's badly designed. Sometimes that's not badly designed and it's more difficult than it looks, but it's not really the point.

An important message I'm trying to get across is that you should not complain if you don't, in turn, intend to improve the code. So you don't criticize just for the sake of it because it's a natural thing to do. And if you start by saying, Oh, this code is terrible, Oh, I would have done such a better job, and you do that all day, then you're going to get depressed and you're going to depress everyone who sits around you.

So I think you've, yeah, you need to be careful to criticize only for learning purposes or improving the code.

**Adam:** That's kind of the tricky part. it's really easy to complain about the code that you have to work with. Like it just comes naturally, right? When you see some codes, you're like, this is a mess . And it can actually be hurtful because the person who wrote it might be sitting nearby.

**Don:** And also like you don't understand the original constraints like maybe this code made sense at some point. Maybe it still does. And it's just so complicated that you don't know how it's supposed to work. I think that what Jonathan is trying to say is if you can try and move past that and maybe accept it, then you can better yourself.

## **Taking Ownership of the Code Can Be Empowering**

**Jonathan:** If you have to work with codes, be it good, be it bad, be it the one you wrote or be it that someone else wrote. Think about it as your code.

If you're working on it, this is your code. You have to take ownership, and if even if you don't think it, it's good. Even if you didn't write it yourself, this is your code. And when you get into that mindset, you have the position as a leader you feel empowered, do things with this code because this is your code.

So it doesn't matter that it's bad. You have to make the most of it. And you, when you take the ownership over the code you're working on, you leave this victim attitude, for doing that. That's one thing that's particularly frustrating with legacy code is when you feel like you are bearing the consequences of someone who made a poor design in the past.

And it's not true because in the first place, maybe that person didn't make a poor design. Maybe just not seeing the big picture and maybe even in the same situation, you wouldn't have them touch a better job.

**Adam:** This is such a great attitude, like, I've been, you know, accidentally on the receiving end of like what moron wrote this code and it's not fun.

**Don:** Yeah, I mean like ownership is a great attitude. And also I think what you're talking about is empathy. Like, have some empathy for the person that wrote it.

**Adam:** Okay. So far, we have accepted our code. We've learned how to critique our code and, and take ownership of the code.

**Don:** And don't be a dick.

**Adam:** You mean develop empathy?

**Don:** Yes and develop empathy until you get it.

## **Considerations for a Valid Code Critique**

**Adam:** All right. Before we leave a critiquing, Jonathan has a rule for what type of code critiques he considers valid.

**Jonathan:** That would be any critique that's technical. One thing that comes up very often is levels of abstraction. If I had to sum up best practices in, in three words, that would be those levels of abstraction.

That's something that's sometimes not respected and that makes the code look bad and complicated.

**Adam:** Do you have, an example of that?.

**Jonathan:** Yes, when you have to choose the name of a parameter or anything else really, but let's stick to the parameters example. That's a tricky thing to do. That's like naming is a difficult thing to get right in programming surprisingly. I think that to get the right name, you have to choose a name that's at the right level of abstraction.

And to do that in practice, you have to think about what this object you are trying to name represents. It may sound a bit trivial, but this question, what is this object representing? I think it's the crux of how to get to do good naming for an easy example of the parameter. If you name your parameter with a name that reflects how it participates to the inside of the function, then you know you're too low in terms of levels of abstraction because the parameter represents something that's at the same level as the name of the function.

If it looks like something that's logical to implement the function on that, then it's too low. And on the other hand, if you're too high in terms of the level of abstraction for a parameter, that would be that your parameter is bound to the context that uses that function. Does this make sense?

**Adam:** I think I understand. If I have some function that is called, let's say, format email and it takes in a string and it goes through and it removes any like double line breaks and I call it that because I use it for my email. So that is kind of a violation of these levels, right?

Because it doesn't actually format an email. I'm giving it too specific of a name, what it's actually should be called to something like remove extra line breaks.

**Jonathan:** Exactly. And your parameter should be called email but should be called. text. For example, as a great example because it shows immediately. 

**Don:** If you're keeping track, we have now covered accepting, critiquing.

**Adam:** And also, you know, using that critique to improve your code.

## **Why Fixing the Code Right Away is Not the Way**

**Don:** And speaking of fixing the code, should I just fix these right away when I find them?

**Jonathan:** Oh no. Absolutely not. I don't think so. The thing is it would be great in theory. If you could fix the world, that would be awesome. But the thing is, legacy codebase tends to be vast. One thing that makes codes go into legacy codes is age. You know, like you have old code, it has more chances to be legacy than like brand new code you just ship

But I'm sure that all the code is not equal and that really shows at any scale. Even if you're like at function, you're going to see that all lines don't matter, but just a handful of lines that really contain some meaningful action. And I think that's true for like larger scales, like code-based. Some places where you go everywhere all the time, everyone goes there all the time. That's the places that are hot, if I may say, in terms of like of cash, cash for Cadbury. It's the places that people change. They make fixes because our bugs will be called that. Interesting. And the clients want more features in them. And those parts, they represent a portion of your codebase.

And this is the portion that matter.  The point of code is to make a piece of software run and to make it run in a way that will make customers happy.

And that's a very harsh business view, but I think that's what code is for in, I mean, in a professional context of course. So making code good has to somehow improve your business. So if you make code better, it can be because better code tends to have less bugs. Right? Or because it's easier to add features to better code than it is to code that you can't make any sense of.  Like for example, you shouldn't do a refactoring project just because it's easy to do or just because it doesn't cost a lot. Like I hear people sometimes say, Oh, I'm gonna go in that code and improve, I don't know, like the names or make the code cleaner. And that's an easy thing to do. And if no one goes through that code, that doesn't matter. It's the same thing as fixing some other's company codes, you know, that won't make you better. That won't make your business better.

**Adam:** You're saying the cost is low, but the value is zero?

**Jonathan:** Absolutely. That's exactly my point. No, I'm not saying that naming is a bad thing, that naming is tremendously important, but that matters more in code that matters

**Adam:** So my biggest concern is not what Jonathan just described, like fixing code that doesn't need to be fixed. It's actually just making code worse by, trying to improve it. So I asked Jonathan how to deal with that situation.

## **Making Code Worse By Avoiding Nesting**

**Jonathan:** I think it can do the same kind of analysis like when you did choose to fix a piece of code, like to improve its quality by making a refactoring task. After it I think it's a great thing not to move on immediately, but rather to think about why it's better. And once again, it's not something that's obvious to do sometimes.

Like for example, I remember one time where we had a slightly complicated if statements like something that was an if involving several Booleans and a bit of nesting, you know, nothing monstrous, but you know the thing that takes you a few minutes to figure out. And we were thinking, well, this if we see it often, maybe we should do something about it.

So we went about and, and refactor it. And we moved it around and somehow it was looking much better, much easier to understand. And then we stopped and thought, why is that? Why is it better? You know, it looks better. I feel I can understand it better. And that's the point of code really. But why is that?

After I view, I know, like minutes apps or perhaps, even more, I don't remember, maybe an hour of analysis or perhaps like when you think about when you sleep on it really. We realized it was better because sticking to the specification like the business had explained this. If such and such condition is met within this context and without this other then we should do that thing, you know? And, and after the refactoring our if statements were looking exactly like that. And surprisingly it was more nested. By nested, I mean when there is an if statement inside of an if statement and you can measure nesting with indentation, which is the distance from the left margin of your screen.

And you know there's a general guideline about if statements that's a classical thing in programming, which is avoid nesting. Like, refactor your if statement so that there are as little nested as possible, it can be not nested at all. And in this particular case the if statements became more nested but clearer. Because it fits better with the specifications.

So we came up with that go line that we try to use every time we have to do something that's related to conditional, try to stick to the specification to what the business side more than about nesting 

**Adam:** I liked this example. The structural indenting. So following the rule very clearly about reducing indent actually would lead you to a solution that was less good than what you ended up with.

So the rules, it's not, it's not totally rule-based, but you should be able to explain it somehow.

**Jonathan:** Yeah, absolutely. You have to know the rules. Like you have to know that nesting is something that can be dangerous. That's a smell. But performing your analysis on your codes allows you to go further. Expound beyond the rules, and that's like, you know, another level of skills.

## **Create Understanding with Documentation**

**Don:** Learn the rules for improving code, but learn the exceptions

All right, we have hit except it, critique it and improve it.

**Adam:** And there is one more key left to legacy code and this one I have to admit is not my favorite. That is documentation. To Jonathan. The magic of documentation is

**Jonathan:** You can create understanding out of nowhere with documentation. That's a very surprising thing to know to do because it's, it sounds like magic, but the very fact of explaining what you already understood helps you understand more.

You probably know that if you have made a talk or written a blog post or written a book or written actually a piece of documentation. If you explain anything to anyone in any form, and I'm sure we'll ever listen to data at some point, you know, that this makes you this made you realize things.

And. If, if anything else, it helped you realize that there were things you didn't know. There were holes in your understanding, and that gives you more questions to answer to make a consistent whole. So that's just one aspect of how documenting helps understanding now.

**Adam:** That's a great example cause you're, you're saying that the actual act of explaining it to somebody via documentation actually deepens your understanding. It's a way for you to understand it better.

**Jonathan:** Yeah. And of course, it goes without saying that it helps the other people. Oh, it's going are going to read your documentation. Now I think. When you're a software developer doing documentation is not hype. That's not the thing that motivates people becoming developers, or at least most people that I've met.

That's why I think it's important to realize how important it is and that it's not a terrible thing today. And one. Way to this to see things that I've realized over time by actually managing people and making them write documentation is documentation. Just like improving good quality. You don't do it because it's a good thing.

You know you don't do it because you're a good person. You do it because it helps the business.

And knowing that. You, you're going to quit this horrible. It's horrible for everyone. An attitude where you write documentation and then we do homework. You know, like, my manager asked me to do that. I don't have a choice.

I'm going to crank it out and, and be done with it. And that's the worst documentation you can make for you if for everyone, for you, because it's going to be pain and for everyone, because it shows really when you read a piece of documentation that's been written that that's someone that didn't want to write it, that just cranked it out. It shows and you're doing, really understand that it's not helpful. And, and if it's not helpful, then you wasted your time,

## **How Your Future Self Will Benefit From Documentation**

**Adam:** Yeah. That's a great attitude.

**Jonathan:** Yeah. So one simple tip I was going to say when you write documentation is to write it not because you have to because your, because you're, you've been asked to or because you feel guilty not to, but write it to explain something you had a hard time understanding. Explain it to your past self.  Because you know how it feels not to understand that thing. You know what's easy to understand. You know what's. Like they're tricky parts and sound as if you are speaking to your past self because other people are like your past self. They don't know about it.

And actually, your future self has a high chance to be like your past self at some point, regarding this particular topic.

**Don:** In other words, document things because you're going to forget them and you're going to need to explain to your future self when you come back to this code, inevitably what it does.

**Adam:** Yeah. You're going to be the person reading this documentation, so if you don't write it, you're just hurting yourself.

So we understand now how to work with legacy code. We have accepted it, critique it,

**Don:** Critique nicely,

**Adam:** Improve it.

**Don:** But don't make it worse.

**Adam:** And document it.

There's one item from the beginning we haven't covered though, and that's how to enjoy working with existing code bases.

The key to loving maintenance programming is understanding how valuable a skill you're developing. Get good at it, master it, enjoy it. Or as Jonathan says.

**Adam:** It's a fascinating thing to be programming. We love that.

But more importantly, yes, it empowers you to do great things and you can do fantastic things with legacy code.

**Don:** You can find out more about Jonathan and his book at [CoRecursive.com](http://www.corecursive.com)

**Adam:** This interview with Jonathan originally aired on SE Radio, a software engineering radio. It's a great podcast. I'm one of the hosts.

Let us know what you think of this show.
