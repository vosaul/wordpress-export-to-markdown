---
title: "Building Subversion"
date: "2020-07-01"
---

Software is just the tool and it should get out of your way. In this episode, Jim discusses how to build a great developer tool.  It all started with: “What's the worst software that you use every day?” 

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/15020282/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

### **Transcript**

_This is a machine-translated transcript. Podcast page for [this episode is here](https://corecursive.com/software-that-doesnt-suck-with-jim-blandy/)_

### **Introduction**

**Jim:** Basically, there was a coworker of mine who said, CVS’s repositories indexed backward. **CVS is the software equivalent of a telephone book sorted by telephone number.** And that's a funny lunch comment, right? And basically I was just thinking about it myself, you know, doing the dishes every night but the thing is you can't just accept something like that. You have to say, well, wait a second. **If CVS is backward, what would it look like if it were right?** 

**Adam:** Welcome to the CoRecursive, I'm Adam Gordon Bell. Today, our topic is what would it look like if CVS was not backward? CVS is a source control management tool. Think of the early 90’s - Git.

Jim Blandy is my guest and he brings us the story of making CVS better. 

I would guess that a number of features of your current source control tools that you probably use every day we're influenced by Jim's work. I also think he has some interesting insights on how you build great developer tools and also how to recognize when some improvements to the existing tools will topple the current market leader are something that he's done twice.

We started the story of the year in 1993. It's the year the Mosaic web browser came out. You know, email has been around for some time, but the web was fairly young and CVS was the most popular open-source source control system. 

## **Network Transparent CVS & The Commune**

**Jim:** So I went on this trip that I was going to go on in Europe and Japan, and I came back to the US and I had no job. And no apartment. And my friend had gotten a job. My friend Carl Fogel had gotten a job working at the University of Illinois, Urbana Champaign on a gene-editing mode for Emacs. And this is an Emacs, you visit a file that's full of genetic data and Emacs will bring it up and it'll apply colors to it, and you can like select, you know, rectangles and stuff like that.

But he was living in Illinois at this lab at UIUC, and I was living in Indiana and so we were collaborating across the net and this was 1993. And so the way you collaborated across the net was you shipped people patches, you emailed people patches, you FTP, do your sources,  network, transparent version control was not a thing. But, I had an old friend from college who had gone to work for a Silicon Valley startup, except he didn't want to live in Silicon Valley. He wants to live on a commune in the Hills of Virginia. And so they ran a frame relay line, out to the commune because, you know rural telephone access, right? And there he was on this commune, you and everybody else was making hammocks and nut butter, and he was hacking on code for Silicon Valley and so his income was probably a significant portion of the whole communes income, but, there he was, and he realized that it was kind of lousy doing this collaboration at a distance, his name is Jim Kingdon and he was just an amazing hacker and he sort of disappeared from the world after this and I don't know why, because he is amazingly talented. What he did is he took the CVS version control system, this was like I said, this is ‘90, ‘93.

It was designed for a situation where you have lots of people using the same computer, right? And so you have your CVS repository in one part of the file system that's shared by all the users. And then people are checking out copies of the tree into their own home directories, making local changes, doing updates, doing commits, right?

And so they're doing all of this activity but it's all on one machine. It's all one local file system because people would share their computers back then because that was what you have to do.  So what Jim Kingdon did is he took this CVS version control system that was designed to work locally only and basically, by I sheer force of intellectual will, he ripped it apart into a client and server and he invented a protocol to go with it that like and the protocol even like, you know, minimize round trip times to keep latency down and all this just amazing stuff, right? It's a program that wasn't designed to be a network program at all, and he turned it into a network program and then he used Kerberos for authentication and it was real network security back in 1993. He used it for collaboration with his startup that he was working for, which was, Signus Solutions in Silicon Valley. And so, you know, it was this amazing thing but he didn't publish it, he just used it.

He wrote it for himself and for maybe other people in his company. And then he just used it and so I had heard that he had done this and here I am trying to collaborate with my friend Carl in Illinois and so I wrote him and I said, Hey, you know, do you think I could get a copy of this code?

And he says, “Oh yeah, sure. But on one condition, you can't ask me any questions.” because basically he doesn't want to get into the support thing. I think this is probably why he didn't publish it in the first place.

**Adam:** That makes sense. Yeah.

**Jim:** So I said, “Oh yeah, sure, fine.” You know, give me a copy. And so he sends me a tarball of it and other sources and so immediately I asked him a question and he's like, I told you not to ask me any questions.

Carl and I started using it like, this is amazing! Right? Because you set up a server on some machine somewhere and you do a checkout and you get the sources and then you work locally and nobody gets in your way, and then you just commit and poof! it's there for everybody else to see.

Right? It's just a whole new world. And so, you know, we were just blown away,  at how much better it was to collaborate. Over the net using the network transparent CVS. 

**Adam:** So since CVS is GPL, Jim takes these improvements and he releases them to the world like a fork.

## **Waiting Tables & Drug testing**

**Jim:** At first, the official CVS, the mainstream CVS distribution was like, Oh yeah, interesting work. But you know, we have our own ideas about how we're going to do things because everybody -- nobody likes existing code. Everybody likes imaginary code because imaginary code is always perfect. 

**Adam:** Yeah. And you're like, we already have this. It's done, you can use it.

**Jim:** Yeah, you could use it and then but they didn't want it because they wanted to do their own thing. But you know, after a few months it becomes clear that they don't have network transparency and we do have network transparency and basically everybody is switching over to cyclic CVS, which is what we called it and they capitulate and say, “okay, I guess we'll merge your changes”. And that is how network transparent CVS came to be. And, you know, within a year, all of the open-source worlds were using this. Because when you think about the kind of collaboration that has to happen with open source, you know, it's all distributed teams.

It's people from everywhere you get volunteers, you have no idea where they're coming from. There's no physical locality to it at all and it took over the open-source world by storm and within a few years, pretty much CVS was the standard.

**Adam:** This network transparent CVS became such the standard both in open source and in the corporate world. Jim got some interest in contracting work, just helping people understand how to use it. 

**Jim:** One of the biggest thrills I ever got was when I was just going around to different companies and government groups and teaching them how to use CVS.

And I got an invitation to teach for a few days. I think it was a three-day course at the Goddard space flight center, out on the East coast and so here I was teaching these folks who were doing satellite development and doing weather analysis. And I remember one day over lunch,

one of them said, you know, we've been having this bug with CVS I wonder if you could help us out with it and so I said, sure. And so we walked down to his cubicle and AEs says, well, okay, here, let's, let's, and so we just check something out. It just checks out a tree with CVS. And I say, well, what is it?

And he says, Oh, this is the stuff that analyzes satellite data, satellite images,  to analyze,  hurricanes and predict where they're going to go. And there was just something like just seeing that checkout, right? CVS lists each file as it downloads it from the server and checks it out. It's like, Whoa! I'm actually helping people do stuff, you know? Right. Here's this person who is just trying to, you know, track hurricanes. And because we made this thing, they were able to do that  is a really exciting feeling. That they're not really interested in your software they’re just using it to get something done and that because you were there, they were able to do it.

## **Cyclic Software**

**Adam:** Jim and his buddy Carl didn't let this good opportunity go to waste. So they start a business cyclic software that offers support for cyclic CVS for network-transparent source control. 

**Jim:** Our little business failed to die in the first four horrible ways that businesses always die.  We've paid ourselves a salary, we earned back our initial investment and actually made a little bit of money beyond that and we had customers. One of our clients was Goldman Sachs. It turned out the Goldman Sachs was using CVS internally and they really liked network transparent CVS. And so Goldman Sachs wanted us to port it. I think they wanted reserved checkouts or something like that.

And so here we are, two guys basically we're grad student age and we're like, okay, we're going to write a contract with Goldman Sachs and so we'd go consult a lawyer and stuff like that and we send Goldman Sachs our little contract. You know their full legal department comes to bear on this thing and everything that we wrote them becomes exhibit A and then they have this big, whatever is 15 pages of boilerplate that we have to 

**Adam:** They faxed it to your lawyer?

**Jim:** Well they faxed, I think they emailed it to us, or maybe they, snail-mailed it. They snail-mailed it to us. I think those are the days. But the fax would be reasonable, we might've had a fax machine.

So I'm reading through this contract and then I get to paragraph 15. And it says “contractors agreed to submit at Goldman Sachs, his request to drug testing.” I don't know where this comes from. So Carl and I are about as square as you could possibly get.

I mean, we don't, we don't even drink, right? Not because of any moral issue, we just don't. That's just not our style and so we would have completely passed any tests that they'd ever, they could ever get us to take,  but also that's just obnoxious, right?

What do they care? I go back to Carl, like back into the other room carrying the contract and say, Carl, they want us to take drug tests and Carl says, “Oh, we won't sign that; we can wait for tables” I'm like, “you're the best” and so we write Goldman Sachs and email back and say, this looks great. We're ready to sign it. However, paragraph 15 has got to go. So without any comments at all, we just get back another copy of the contract from Goldman Sachs with that paragraph gone and we sign it and we do the work. And that was that. But we did hear from the hackers at Goldman Sachs later, the people that we ended up doing the work with they said, told us later, it's like, nobody's ever done that before. Nobody ever complained about that. That was cool. So, yeah, that was kinda nice. And that's the kind of thing that you can do when it's just the two of you, right? I mean, if I had had a family at that time or if we'd had employees, then you start to have to worry about other people.

And it's like, it's not just your choice to do something or walk away, but when it's just the two of you, it's really nice. You can really just do whatever you please and don't have to do anything you don't want. 

**Adam:** So let's fast forward. The company was a success, but eventually, they move on to other things. And Jim joined Sigma Solutions where he was using CVS every day and he starts to notice certain things about the tool that he does not like. 

**Jim:** So this is actually interesting. When you think about it, a repository, like a get repository or something like that, you think about it as a database, right? It's a database where you put in,  you know, commits, right? And you check out trees, right?

And one of the most common things you're going to want to do in the version control system is you're gonna say, Hey, I have this version of the code and I want to pull all the changes that have happened since then. So please send me the diffs between this prior date and this current date.

Ideally, if only three files have been touched between this old date and the new date, you should only get data about those three files. And the backing database should be organized in a way,  that makes that efficient because these are very common things. This is a diff query, a diff between two revisions.

This is a checkout, this is a merge, right? This is a common operation, the way CVS stored its data was as a gigantic directory tree shaped the same way as the sources that you are managing except fit each individual file was an RCS file that held all the different revisions in it, and there was no connection between. The set of revisions stored in one file and the set of revisions stored in another file. If you did a commit that touched two files, there was no indication anywhere in that data that those two files that those two commits had anything to do with it might have the same log message and the dates on them would be about the same.

But there was no indication that that was a single atomic commit. 

**Adam:** That is something that we take for granted right now. Atomic commits without atomic commits, you can introduce inconsistency issues. Especially if somebody is doing a slow operation, like creating a branch, which is going file by file and somebody else is pushing changes at the same time. You're not guaranteed that the branch will get all the files from the commit since they're happening in parallel interleaved. Also, in this case, the lack of being structured as an atomic commit actually made the implementation slower. 

**Jim:** And so when you did a CVS update, the way CVS decided which changes to shipping to you was it would scan the entire directory tree. It would open up every single file in the directory tree to see whether this might have been changed since the date that you asked.

And actually, what you had to do when you did an update, you had to ship to the server, the current versions of all of your files. And then it would actually check to see whether any of those files that do versions and then it would ship you the diffs back. 

So that's terrible, right? It supposes you've got 10,000 files, but only three of them have changed.

Do you have to check every one of those 10,000 file when somebody does a poll because the data is organized in a way that doesn't give you any sort of centralized indication of like, you know, what changed. The performance was so bad that when Sigma solutions when they want to cut a branch, they would announce it ahead of time. They would schedule the branching. Because you didn't want anybody else committing while you were branching, because that would totally screw things up, right? And it was okay, Friday at 2:00 PM, we're going to cut the branch and then all activity would stop, access to the server would be cut off.

They would start the branch. Now, remember, this branch requires walking through, however, you know, a hundred thousand files. You've got, you know, this, we sickness did GCC, GDB,  canoe assembler, canoe linker, basically the entire new toolchain work and so they had you know, hundreds, thousands of files.

And so they would walk across these hundreds of thousand files and make a branch and every single one of them, and it would take like, you know, 45 minutes to cut this branch and then you'd say, okay, we've opened up the branch. Everybody can start working again. That's crazy. 

**Adam:** That does seem a bit crazy, right? Jim is talking about how in CVS, the performance degraded based on the size of the repository, not based on the size of the changeset. 

This is something we kind of take for granted today but now source control. The performance is related to the size of the changeset. Change one file, that should be cheap, change all of the files that should be expensive and branches you're changing no files. That should be free. 

## **Enter The Rewrite**

**Adam:** Jim had been thinking about this design for a better system and his buddy Carl, he got approached by a company looking to shake up corporate development by introducing ideas from open source software development. 

**Jim:** This was around the time that the cathedral and the bizarre essay was being written there were a lot of companies that were saying, “Wait for a second, why isn't our internal software development as dynamic as what we see going on there? What is it about that dynamic that makes it work so well out there? And how can we bring that into our own in house development?”

**Jim:** But CollabNet was interested in doing, they saw CVS and they knew that it sucked and they were willing to fund writing a replacement for it.

And so they approached Carl or Carl approached them - I don't know exactly how that happened, but anyway, they ended up working with Carl and we started. Carl and I had already started drafting ideas for a replacement for CVS because, there's something that a friend of mine said to me once, “CVS is the worst piece of software I use every day.” That's a very interesting sentence because it's got the word worst in it, right? This is the “worst” piece of software and it's got the word every day in it,  right? It's like if it's so bad, why are you using it every day? The answer is, I need this so badly that I'm willing to put up with the crap when somebody says that about a piece of software that's a good target for a rewrite.

**Adam:** This mythical rewrite that Jim started planning. He called it subversion and he started talking about it with everyone. This whole thing predates Git and Mercurial by five or six years, by the way.

**Jim:** So when I told the sickness people, Oh yeah, I think the person's going to be able to cut branches pretty much instantaneously and constant time. They didn't believe me.

They said, “we’ll believe that when we see it.” Cutting a branch is nothing. It's just creating a name for a particular revision, it's a free operation and so that was big, it was a big deal. 

So, yeah, so we, we had already started working on this new design for subversion, and then CollabNet said, “this is great, we'll fund you and we'll get other people to do the network stuff for you.”

**Adam:** There's a step missing or something like when did you have come up with this design and did you like what email Carl and say, I have this idea..

**Jim:** Yeah, it was the design for the repository. Basically, there was a coworker of mine who said, yeah, CVS has repositories indexed backward. It's the CVS that has a repository. Is the software equivalent of a telephone book sorted by telephone number? It's just exactly the wrong thing. and so that's funny, that's a funny lunch comment, right?

It was, somebody says it and you're like, Oh, that's funny. That's really true and then, but the thing is you can't just accept something like that. You have to say, well, wait a second, if CVS is backward, what would it look like if it were right? What's the proper organization for a version control repository and basically I was just thinking about it myself, you know, doing the dishes every night and I ended up coming up with a design that's actually other people have come up with. It's not original to me. I hadn't read about the other things but it turns out that, I think Perforce actually has a very similar, repository structure to subversion but basically the idea is that you want to share, whenever you have a commit, right? And the commit changes, say one or two files. You want to recognize that the directory tree before the commit and the directory tree after the commit are almost identical. The only difference between them is that there are these two files that have changed, and so what you actually want to do is you want to share as much of the structure between those two trees as possible. Go ahead and represent both trees, but have them share as much structure as possible. 

**Adam:** It sounds the same as like a persistent data structure?

**Jim:** Yeah. You mean persistence in like the way functional people use that word? This is a persistent, persistent data structure, right. Because 

**Adam:** The terminology is very confusing, I think.

**Jim:** It's persistent in the sense that it's saved to disk. And it's not going to go away when you exit the program, but it's also persistent in the functional programming sense. 

**Adam:** Yeah. If you have like an immutable tree in your, whatever programming language of choice. When you make changes to it cause it's immutable, it will just like, it will make a copy, but only of the elements that you need to change and kind of update the pointers.

**Jim:** Exactly. Have you ever heard of Chris's book, Functional Data Structures?

**Adam:** I've seen the picture of it and one of my friends bought it and said he couldn't understand it.

**Jim:** That's too bad. Because Chris goes into all this stuff and it is hard to understand. But, once you get it, it's, it’s kinda minded blowing., I think it's a good, worthwhile investment because a lot of those algorithms play well with incremental contexts, right? That is, if you're making a series of small incremental changes to a large data structure, then the way that the persistent data structures are trying really hard to share as much data as possible really works in your favor. 

## **Building Subversion**

**Adam:** So, you have this idea, and what happens next?

**Jim:** Well, so I had this idea, and Carl and I had started working on it, and then Carl gets this funding from CollabNet. And that's fantastic, suddenly we have a guy who's a web dev expert to do the protocol for us. We ended up getting an office in Chicago, so I'm traveling up from Indiana up to Chicago to meet with Brian Fitzpatrick and Ben Collin Sussman.

And we agreed early on that we wanted to break it up into a nice reusable set of libraries, right? So there's going to be, if you want to work with subversion working directories, here is the working directory.

Library that accesses all of our metadata. If you want to speak the protocol, here's a library that does the protocol. If you want to, you know, have different backends for storage --here's the interface to the back ends. 

**Adam:** So you had your design and then what, there were a couple of you working on it and..

**Jim:** Yeah. There were about five of us, I think.

**Adam:** Did you split it up into modules and you're like, “I'll work on the working directory part and..”?

**Jim:** Yeah. I was working on the server part so other people took sort of the command line part.  There's somebody who took the working directory library and things like that and so I think, I think that you know, for another kind of project, you have to be much more careful because there's drift between one person's understanding of the design and another person's understanding of the design. Because the thing that you're building doesn't exist yet. But in the case of subversion, we had this very clear goal, which was to become a properly designed, modern CVS. 

Net transparent CVS and that the fact that we were imitating or replacing something that already existed, I think created a lot of clarity in people's minds and so I think it actually was a project that could be undertaken with a lot less coordination than you would normally need for something that size

**Adam:** Yeah. That makes sense. So you like not only did you have an existence proof of something like this existing as you knew it well, you were using it I assume you were using it for subversion

**Jim:** Yeah we had to use CVS at first but then there was the day when, when we started being able to dog food, and that was a really great day. Right?

## **Celebrating Success**

**Adam:** How did, how did you guys like to celebrate? Like if you were all distributed?

**Jim:** Oh, we would go up to Chicago. We had this great office in, I think it was called printers row in Chicago. It's a whole bunch of old buildings that all used to be full of printing presses for newspapers and stuff and they had this cage elevator, whether you could see the elevator shaft through the iron bars of the cage and if you looked down, you could see these gigantic relays that controlled the elevator. And it was a relay driven elevator and yeah, oh, we partied, I would drive up to, I would drive up to Chicago quite frequently and,  we had a bet that whoever wrote the first security hole had to buy everybody else dinner. And so that was, I don't know whether you want to call that a celebration or you know, losing a bet or something like that. 

So I worked on it for a year but then I actually found it kind of exhausting and so after a year I really wanted to go back to working on GDB I think the subversion started self-hosting within the next year after that.

**Adam:** So Jim's designed for a new version control system succeeds. It takes over the world Subversion, atomic commits, free branching, performance proportional to change size. These were all great changes. It quickly replaces CVS. 

## **Becoming the leader**

**Jim:** And then it rose to its heights over the next, like within three or four years, I think. But it was really nice. We got a recommendation by these consulting newsletters, like the gardener group, gave us,  you know, listed us as an essential tool or the best of the breed or something like that, which was really funny because it's like, you know, we didn't do.

Marketing research, we don't have any idea. We just know what we want as hackers. And then you have these, you know, very serious businessy industry,  newsletters recommending you, and it's kind of ridiculous.

**Adam:** the Gardner quadrant or something? They probably had a graphic that showed..

**Jim:** Yeah. It was exactly that, we were in the good quadrant, it was crazy. 

**Adam**: There was probably somewhere there was a meeting of people in suits, figuring out like how far to the left you should be and how far to the right. 

**Jim:** Yeah. And it's very silly to have those people's attention, you know? but that's the way it works. 

**Adam:** But within five or so years, it started being replaced by other version control systems by Git by the Mercurial. And although probably some people are still using subversion right now, Jim really doesn't think they should.

**Jim:** Yeah. They shouldn't be. I actually had somebody come and try to talk me into consulting about subversion for him because he had this great idea about how, but in the end, I tried to really talk about it that I said, it's not, people aren't developing it anymore. It's not actively supported. When you bring in developers, when you want to hire developers to work on your project, they're not gonna know it, but everybody will know Git.  I was in a funny position of trying to talk somebody out of using something that I was one of the original designers of, but yeah. I don't think anybody should be using it anymore.

**Adam:** I mean, are you sad?

**Jim:** I have Git, I have mercurial. How can I be sad? I don't know. Yeah. I mean, the nice thing was that it set a standard of usability.

I think subversion at the time that it became popular, it set a standard of usability below which people just weren't willing to put up with, got started out with a terrible CLI, and now it's only a mildly horrible CLI, right? That the options are the only sort of ferociously confusing and not overwhelmingly confusing. You know, and I think that's our response to pressure from well-designed interfaces, like a mercurial, which has a beautiful CLI and, and subversion, which has a very fine CLI.

So I think that you know, you, you could have your influence in a lot of different ways, and that influence outlasts the use of the actual code. 

**Adam:** So subversion is 20 years old this year. And Jim, he doesn't want us to use it, but its influence is still out there. A question I wanted to ask Jim was if subversion was addressing shortcomings in CVS, what were the shortcomings in subversion that Git helped address? 

## **Subversion Problems**

**Jim:** You know, how to Git uses, content hashes to identify file contents, and to identify directory contents.

And it's a very beautiful model and those hashes are really essential to the distributed nature of Git because it means that basically if you've got data, it doesn't matter how you got that data, everybody can tell that you've got this branch and you don't need to be sent that data anymore. Somebody suggested that subversion does this. What we were actually doing is we were just assigning fresh numbers to the nodes as we created them and so somebody basically said, well, you know, we should be using content hashes. And this is the worst decision I've ever made. I think in terms of impact. I said, no, we shouldn't do that because if you do a rename if you modify a file and do a rename, there's no way to tell that the old version of the file and the new version of the file are related at all. The only kind of vindication that I can cite for this is that even now Git doesn't really know about it. It just sorts of looks at the file and says, yeah, they're, they look close. It seems to be right. And it basically, you give it some cheesy parameter that says how hard it will try to look for them.

And it's such a kluge and it just reconstructs them post facto. So like, you know, it doesn't, it doesn't even know anything about what happened. It just sorts of guesses that this must be a rename of that, even if it's not. It's a total kluge. 

## **The Merge**

**Adam:** You know, when I started using Git, people were talking about this distributed case and I guess it does happen but the big thing that seemed different to me was just like merging was like free all of a sudden like merging and branching and like. So you're the guy to answer this, I think like, like why is that right?

It doesn't seem like there's some reason that distributed mixed merging better, except you have to do

**Jim:** No this is kind of a sad story, the great thing about merging in Git, and I'll just pick that as an example, Mercurial is the same. The great thing about merging and Git is that it's just like what does it merge? Merge is what I say it is, right? I say, I have this parent and I have that parent, and now here's a new chainset that's got both of them as its parents, right?

There's no restriction on what a merge means. The mistake that we made in subversion, is that we thought merges should actually mean something textually, right? That actually there should be a way to say, here is the reconciliation of these changes with that change,  and I think we really just over-thought it a lot. 

All you need to do is have some good textual merge tools that use whatever heuristics they want, whatever heuristics work well for your project. We'll have some off the shelf mergers that do a great job in most cases. But if you want to have a specialized tool, you just drop yours in and you can do whatever you want and then what you say, it's okay. That's the end of the story. 

**Adam:** It's interesting, like almost what problems you decide not to take on, can kind of define things where he just gets just punted on this. They're like, let's not worry about it. 

**Jim:** Absolutely. 

## **Building a Tool to Do Its Job**

**Adam:** So better merging of branches; Git was distributed, it had content hashes, but better merging was really the big difference. Subversion was huge and it's time though. I imagine being the developer behind the tool that most of their developers are using many times a day must be like being a celebrity. Jim said it wasn't like that at all, though.

**Jim:** Although I do remember one time that I had moved on to another company and we were using subversion to hold a copy of, the entire neutral chain, GCC GDB, BFD, the linker, assembler on it, so on and so forth. And I think that is also a copy of the C library. So it was a very large repository. And then we used it every day and it was fine. And the founder of the company said to me one day you know, so you know, “Jim subversion doesn't suck. And he said I hope you understand the way I mean that.” And I said, “Oh no, definitely get what you mean. Thank you very much. I'm proud”

**Adam:** The greatest of compliments. 

**Jim:** It really was though. What more do you want that to have somebody say, I used your stuff every day and it's okay. That's like.

**Adam:** I want more. I want more than that. 

**Jim:** Oh, I don't know. Everybody wants to get five stars, everything like that. I mean, when does anything actually five stars, right?  Like if I go to a bike shop and I'm trading in my bike and they treat me decently, right? I gave them five stars because that was what I wanted from the transaction. But it's not like I'm skipping home, right?

It's just a transaction. Right? And I think a lot of software, right? It's there to get help. You get your work done. It's heritage. You're here to help you get through the day. 

**Adam:** Especially developer tools. Right? A tool like just by definition, a tool, like you don't want your hammer to do something crazy. You want it to hammer.

**Jim:** You don't want to maximize engagement with your hammer. Right. That's stupid. You don't want to maximize engagement with your version control system. You just want it to do its job and get out of the way. And so basically if somebody says, you know, this doesn't suck. That's actually pretty much exactly the right thing.

**Adam:** All right. That was Jim -- the first three-time guest writer of software that doesn't suck. The thing about Jim's story that will stick with me beside the guy at the commune, you know, making nut butter, but also building distributed software. The thing that will stick with me as Jim's question, “what's the worst software that you use every day?” 

Also this idea, that software is just the tool and it should get out of your way. That's interesting. Nobody ever says that right. Everybody wants to change the world. He's like, “I just try to build things that don't suck.” 

If you liked this episode, if you like the podcast, you know, tell your coworkers, I don't really know how podcasts spread people say word of mouth. So, you know, tell your friends. Tell them to open up their podcast app search for CoRecursive or search for Adam Gordon Bell and hit subscribe. Until next time. Thank you so much for listening.
