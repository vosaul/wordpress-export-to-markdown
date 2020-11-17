---
title: "The Birth of UNIX with Brian Kernighan"
date: "2020-11-01"
---

When you work on your computer, there are so many things you take for granted: operating systems, programming languages, they all have to come from somewhere.

In the late 1960s and 1970s, that somewhere was Bell Labs, and the operating system they were building was UNIX.

They were building more than just an operating system though. They were building a way to work with computers that had never existed before. 

In today's episode I talk to Brian Kernighan about the history of Unix.

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/16624724/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

“If you wanted, you could go sit in your office and think deep thoughts or program, or write on your own blackboard or whatever, but then come back to the common space when you wanted to.“ - Brian Kernighan

“I found it easier to program when I was trying to figure out the logic for myself rather than trying to figure out where in the infinite stack of documentation was the function I needed. So for me, programming is more like creating something rather than looking it up, and too much of today's programming is more like looking it up.” - Brian Kernighan

“If what I find challenging or hard or whatever is also something that other people find hard or challenging or whatever, then if I do something that will improve my lot, I'm perhaps improving their lot at the same time.” - Brian Kernighan

### **Transcript**

_Note:  This podcast is designed to be heard. If you are able, we strongly encourage you to listen to the audio, which includes emphasis that's not on the page.  The podcast page for_ [_this episode is here_](https://corecursive.com/brian-kernighan-unix-bell-labs/)

**Adam:** 

When you work on your computer, there are so many things you take for granted: operating systems, programming languages, they all have to come from somewhere. In the 1960s, that somewhere was Bell Labs, and the operating system they were building was Unix. They were building more than just an operating system though. They were building a way to work with computers that had never existed before. To find out more, I reached out to this guy.

**Brian:** 

I'm Brian Kernighan, and at the moment, I teach computer science at Princeton University.

**Adam:** 

Brian coins from Unix. He's the K in K&R, the famous book about C that still tops most recommended book lists. He was part of this computer science research group at Bell Labs for 30 years. He's going to share the story of the creation of Unix, and hopefully, I'm going to try to figure out some of their secrets to being so impactful. Along the way, we're going to have to learn about the Unix philosophy and printing patent applications, but we're also going to have to learn about 10-kilo chocolate bars and fake demos to the CIA, and of course, British satirical magazines.

**Adam:**

The story of Unix is a story about Bell Labs, so let's start at the beginning when Brian is a grad student and he gets an internship to work there for the summer.

# **My First Day at Bell Labs**

**Brian:**

Bell Labs is a very big building, a sequence of connected buildings, and probably 3,000 people working over these long multi-story buildings. The thing that I remember most clearly about the first day, and I think it was the first day of the first internship, so call it the summer of 1967, and I got an office, and if I recall correctly, I had an office to myself. So this is something that's unheard of in the modern era.

**Brian:**

But I had an office to myself, and I was sitting there in my office at probably 11:00 or something like that in my first morning, I wondered, "What the heck do I do? I have no idea what's going on." And this older gentleman came past my office and he said, "Hi, I'm Dick... Let's go to lunch." I thought, "Well, okay." I went off to lunch with Dick..., whose name I hadn't caught. We had a good lunch, he was an interesting kind of curmudgeonly, but intriguing guy. Then after lunch, he went off somewhere else.

**Brian:**

I snuck past my office to his office on the same corridor to see who the heck he was because everybody had name tags on the doors. It turns out it was Dick Hamming, the inventor of error-correcting codes.

**Adam:**

Dick Hamming is aka Richard Hamming. His Wikipedia page is huge. He worked on the Manhattan project programming computers to calculate the equations needed to develop nuclear weapons. One year after this lunch with Brian, he would win the Turing Award, the so-called Nobel Prize of Computing for his work on error-correcting codes. Hamming is also famous for this talk he gave on the secret to having impact in your professional life.

# **Thinking Great Thoughts with Richard Hamming**

**Brian:**

The talk was called You and Your Research, and it was basically a retrospective on his career, thinking whether there were general lessons that would help other people in some way to have a better career. He was very, very interesting, and I think a good example of somebody with clearly lots of talent, but not a super genius type, who made the most of what he had. Who in every way, amplified so that he compounded his effect on the world. The other thing that's maybe is appropriate for today, he used to say that he would reserve Friday afternoons for thinking great thoughts.

**Brian:**

He would sit in his office, he would put his feet on the desk, and he would think great thoughts, whatever that might be. It was usually introspection on himself or on where was the field going, or what might happen in the future? What might you do to take advantage of that or deal with it in some way or other? This is Friday morning when we're talking, and I don't get that luxury on Friday afternoons very often, but it's a useful way to think of it. You say, "I'm going to stop and do it regularly to take stock of what's going on, and in some way, think about, 'What could I be doing that in some way would be better, that would be more useful for me or my family or the world or whatever?'"

**Brian:**

He did that quite religiously, you went in after lunch on Friday, you'd find him sitting in his office thinking great thoughts. So he's fun.

**Adam:**

I love this advice, it presupposes that if I just had my Fridays free, and I wrote thinking great thoughts on my calendar, I would upgrade thoughts. I mean, maybe that's the case, I'll give it a try. There's one concept though that Hamming is most famous for, and that is about how you choose what to work on.

**Brian:**

The way he told it to me and probably lots of others was that he used to eat with some group of people like chemists, I think the specific thing was, and he would eat at their table at lunchtime, big cafeteria setting. He would sit down with chemists and talk to them and he would ask them what they were working on, and whether what they're working on could possibly lead to a Nobel Prize. The answer was often no, not a chance, and that was the point where he'd say, "Well, then why are you working on it? Because if it couldn't at least potentially lead to a Nobel Prize, it isn't important. Why are you wasting your time on something that isn't important?"

**Adam:**

Whether intentionally or not, Brian followed this advice. When he returned to Princeton to work on his thesis, he was working on graph partitioning, which we now know is in some sense, equivalent to the traveling salesman problem. You have to find an optimum route that the salesman would travel from city to city minimizing travel distance. To complete his thesis, Brian had to work on the computers of Princeton at the time. Computers today are a lot different than they were in 1967 and '68 at Princeton. At the time, computers were all about Fortran and punch cards.

# **Fortran and Punch Cards**

**Brian:**

Fortran was designed in a card environment very definitely, and I assume the cards came before Fortran, but in my mind, they're very strongly linked. And so yes, it was basically one statement per line, which was, therefore, one physical card. And so, when you wrote a program, you had to punch it on these punch cards, and then make sure you kept them in order and things like that and then you handed them to somebody who operated a very big, expensive machine. And a while later, back would come to your results, very often where it's just something like there was a syntax error somewhere, and you had to find the cards that were wrong, replace them with new cards that were right and repeat the process, but with a very, very long latency that could be often measured in hours or sometimes even days.

**Brian:**

It's not exactly like an instant compilation. And Fortran itself is a kind of clunky language as well in part reflecting those early days in computing, and partly just the fact that we didn't understand a lot, and the computers themselves were not particularly sophisticated. Then finally, Fortran was intended for scientific computing. It was not intended for, let's say, general-purpose system programming or anything like that. All of those things meant that although the program was a lot of fun, it's not the same as it became five or 10 years later, and it has continued to evolve.

**Adam:**

I had to watch a couple of YouTube videos to get a sense of this punch card world. A punch card is like an index card, but it's wider because it has 80 columns. And each of these columns corresponds to a single character. You punch holes in that column to indicate what letters should go there, and so each punch card represents one line of Fortran code. People build the programs this way, punching these cards, putting them into big boxes in order that they would carry around, then you take someplace to give them to a computer operator who would give them to the computer that would read all this in and run the program.

**Adam:**

So if you had a 1,000-line program, you would have 1,000 cards. There were no screens, no interactive output. You gave your cards to the computer operator and waited for your printout that was the result of your program. Computers were expensive and giant, so they wanted to maximize the throughput. Your program might be doing expensive mathematical calculations, but you could also just be doing word processing. One card might say, "In bold, print my thesis," and the next would say, "Print, by Brian Kernighan," and so on. It's like a verbose way of using a typewriter, except the advantage is you could change the cards around and have it reprinted.

# **Time Sharing and Text Formatting**

**Brian:**

There was a lot of interest in text formatting at that time. When I was at MIT in '66, I used a program called RUNOFF, which was written by Jerry Saltzer. I learned only very recently that Jerry actually wrote that for doing his Ph.D. thesis, which is kind of neat, but I didn't have that, so I was at a position of having to get my thesis into printed form. I decided, what the heck? And so I wrote a very, very cheesy little formatting program, it was about 1,000 lines of Fortran that did straightforward stuff like make sure the lines were all the same length and even justified the right margin, which I think in retrospect was dumb.

**Brian:**

And the one other thing it did... punch cards were unfortunately only upper case. I mean, you five finger salutes that you could do that would get a lowercase, but nobody ever did them. So it was uppercase. So part of my little format or was just thing that did automatic capitalization. So it would find the beginning of the sentence and make sure that was uppercase, convert everything else to lowercase, and so on. I could in that way print something that looked like a thesis.

**Brian:**

And of course, you needed escape characters to defeat the automatic capitalization in the places where it wasn't appropriate. Fortran didn't handle characters very well at all, so there was a lot of faking to make that part work, but it was fine. And so thesis was basically three boxes of cards, 6,000 cards in each box, probably weighed 10, 12 pounds, five kilograms. And so you'd take these three boxes, 1,000 cards of which the first half of the first box was the program and then the remaining 5,000 cards was the thesis. And you would take those three boxes and you'd hand them to the operator. And an hour or two or three later back would come a printed version of thesis again. And you'd just keep iterating until it was good enough.

**Adam:**

I think this is a foreshadowing or something. Part of your thesis was writing a program to do your thesis. So the front part of your cards for your thesis where the implementation for a small language that would let you format your thesis, and then the thesis.

**Brian:**

Yeah, it's exactly right. It's entirely accidental, but in a sense, yeah. It's building tools that let you do things, and the tools that are often some kind of specialized language.

**Adam:**

While Brian was working on his thesis, back at Bell Labs, Ken Thompson and Dennis Ritchie were working on a project to bring more interactive computing to the world. The project was called Multics. Multics was a time-sharing operating system. The insight of time was that although a single person couldn't effectively use up the clock time of a computer if you could hook up a number of people to the computer, that maybe they could. And you could do this via time-sharing, basically giving each person a slice of each second so that it felt like they had full access to the computer while really the computer was switching around among them.

**Adam:**

If you had full access to a computer during your time slice, you didn't need a punch card system, you could use a teletype terminal. Teletype terminals looked like large typewriters combined with printers and maybe a phone line, and they were originally used for sending telegraphs, I think. You could type in commands and send it directly to the computer using the telephone line and then have the results printed out right away right above you. And with a timeshare system, you could hook up a number of these to a single computer and split time between them.

**Adam:**

Teletype terminals communicated over telnet, a protocol that's still in use to this day, although I guess SSH has largely replaced it. The ASCII format of text documents was created for these teletype machines, and that's why it has weird control characters like the end of the transmission. This was such an interesting time. It was the birth of these interactive computers. Anyways, back to the Multics project

# **The Multics Project**

**Brian:**

Multics system was that joint venture of MIT and Bell Labs and actually General Electric, which made the hardware. And so the people doing the software were at MIT and at Bell Labs, and that got people used to a very nice computing environment, not a batch environment with cards, but an interactive environment, which is of course today.

**Adam:**

Multics was not a success. Bell Labs pulled out of the project, no more operating system work at Bell Labs. It was a waste of time, that became the sentiment of management. Ken in particular thought the system was too complex, but it was interactive and it was far ahead of this batch processing punch card world.

**Brian:**

And so that left the people, Ken in particular, but also Dennis Ritchie and a handful of others, with a taste for real nice computing environments, but not having one. And so they did a variety of things. They lobbied management to get a high-end machine so they could build their own operating system, and that went nowhere. And they spent a lot of time thinking about design, what would go into a time-sharing system, sort of like Multics but presumably not so complicated, but certainly stealing good ideas from Multics. Multics had many good ideas. I mean, that's the place where in parallel, I guess Ken was exploring this PDP-7 environment.

**Adam:**

A PDP-7 was mini computer produced by Digital Equipment Corporation in 1964. Sounds like a misnomer to me because when I Google it, it looks like a series of giant cabinets with a small desk attached to it and some computery looking parts. Anyhow, this PDP-7 at Bell Labs, it was obsolete, it had been produced in the early '60s and nobody was using it, but it did have a graphics display, basically a very early computer monitor. Computer monitors didn't exist much at that time. So Brian is awarded his PhD, and he starts working at Bell Labs full time. He has some early memories of this graphics display.

# **Early Video Gaming**

**Brian:**

The graphical display was then used for some of the games that Ken, and not long after Dennis Richie, did, which were things like Space Travel, where you had a complete, accurate model of the solar system and you could navigate your little rocket around the solar system and land on various things, so you can land on one of the moons of Jupiter or something like that. And there was also this Space War game, which was you and me shooting each other up, like the two-person version of the asteroid games that you sometimes see. And I wasted a lot of time on that. I think that game may have come from MIT and just been transplanted, but I don't actually know. It was a lot of fun. And what little I know about orbital dynamics comes from playing that because he learned how to deal with gravity.

**Adam:**

The other interesting thing about the PDP-7 was the secondary storage. It basically had this giant disc drive, and Ken was interested in the best way to use it

**Brian:**

He had been working on file system, experimenting with file system stuff on this PDP-7, just experiments to see how you could manage information on some giant secondary storage device. They had physically giant, not very much capacity. And so you had, I think, the rudiments of file system in mind if not actually implemented.

**Adam:**

So Ken has these ideas of a better, simpler Multics in mind. And coincidentally, around this time, his wife went off on vacation, leaving Ken with more spare time than he was generally used to.

**Brian:**

Bonnie went off to California bearing their son who at the time, I think was a year old or something like that. And was there for three weeks. And so Ken figured that he was close and so he built himself basically a working operating system in three weeks. And I think you could argue that's serious soccer productivity in some sense.

**Adam:**

I think that's serious productivity by any measure. So that was the first version of Unix. They had an old computer, often a room to the side, with a teletype terminal. And from there, no more punch cards. Things started to pick up speed. This first operating system was written in PDP-7 assembly, but this is the bones of the Unix-like operating systems that are now everywhere. I mean, that's crazy. Maybe that was the secret of this computer science research group, just have a Ken Thompson. I mean, how good of a programmer was he?

# **Ken Thompson is Good**

**Brian:**

It's one of those realizations that it probably dawned on me at some point just how astonishing he is as a programmer. We were interested in a document preparation software, going back to the text formatting for my thesis, and so on, and there are other people there as well. And so we had bought a typesetter that is a device... think of it as like a laser printer, but before laser printers were around, so it printed on photographic paper which you then had to develop, but it was the thing for doing high quality printed material. And we got it from a company and it turned out that the machine itself came with software that the software was just so buggered and it was completely useless. And so the question is, can we figure out, reverse engineer this machine so that we can create our own software to run it. And the device, in addition to its physical things for manipulating photographic film or paper had a mini-computer in it, it was called Computer Automation Naked Mini, something like that. It was basically another one of these wimpy, little 16 bit computers at this point. And all we had for that was a manual and that we knew the fact that the typesetter had one of these things in it. So it was the controller inside the typesetter.

**Brian:**

And what are you going to do with that? Well, what you need to do is you've got a bit of code that comes from the manufacturer, but it's binary, what do you do with that? And so we're sitting there late afternoon thinking, "Well, something's got to be done." And we as Ken Thompson, Joe Condon and myself.

**Adam:**

Yeah, well, so if you just have ones and zeros, somehow you have to get like the instruction set or something, right?

**Brian:**

Yeah. Well, you had a manual for it, so you knew normally if their assembler corresponded to what bit patterns for the instructions. But we didn't have any of the software itself for the Naked Mini, we just had some code that had been written in assembly language and then compiled down to bits, so we only had the bits. So you have to make some assumptions about what's going on there. Part of that was that a lot of this stuff was stored in basically EPROM, things that are the equivalent of today's flash memory, and so you had to figure out what was going on there as well. And that means extracting the bit patterns and then mutating them, is it big-endian or little-endian and things like that to figure out what is the code there that's in those things.

**Brian:**

I said, "Geez, I don't know," and I went home for dinner, but this was interesting stuff. So I came back after dinner and in the interval, Ken had written the disassembler for this thing so that he could now see what the code was in the Naked Mini. And then at that point, he could write an assembler for it and then start writing his own code for it. And then over the next day, or so, he also wrote a version of an interpreter for the B language, which we then put on the typesetter as well.

**Brian:**

All of this is measuring hours to a day or two to get all this stuff up and running on a totally unfamiliar machine. It's kind of the thing that you could do, I could do, but we wouldn't be very fast at it probably. And for Ken, it was just like breathing. Oh, okay, done. Next.

**Adam:**

When Brian says he, or I could do this given enough time, I think he's giving me far too much credit. This is astounding. I wouldn't know where to start from having like a pamphlet on a CPU and some binary software and go to a working high level language interpreter, I wouldn't even know how to get things onto this machine. What was your reaction? You come back from having dinner with your wife, and he's like, "Oh, I've just assembled this."

# **The Patent Application Gambit**

**Brian:**

Yeah. I was just like, "Okay." It was really fun. With typesetter was I think that the time that I worked closest with Ken, and work with is too strong, I was just mostly standing there watching him do it, but just seeing how effective he was as a programmer in there and figuring out how things had to work.

**Adam:**

You're a professor now, you work with a lot of young students, I assume. How would you build a new Ken? Is that a thing where you could...

**Brian:**

Geez, it'd be nice to know. That'd be quite a growth industry. I don't know whether they are grown or whether they're just born that way and the ones who are lucky or were lucky find the outlet for it early on in something that then pays off for everybody. I suspect it's more the latter.

**Adam:**

So we can't create a Ken, but I guess if you get a chance to work with Ken or somebody like Ken, you should do it. Did you notice also how much Brian downplayed his own contribution? I think this is going to be an ongoing trend. Brian is very modest. I don't know if that's just because he's Canadian or what, but I think probably he had a larger role than he would ever let on. But back to Unix V1. So this PDP-7 is working well, but the computer is obsolete. How can get a proper machine to run this on?

**Brian:**

So Bell Labs, a scientific research place produced lots and lots of patent applications, typically one or two a day at that point. And those had to be formatted in a very specific way for the patent office, weird stuff, including things like numbering the lines. And at the time there was no commercial word processing systems that could handle numbering the lines, and so people in the Unix group at this point promised that they could deliver such a system so that the patent office could develop their prepare patent applications in the appropriate format, and that this would be delivered well before any commercial operation could provide the same thing.

**Brian:**

And the quid pro quo was that some part of the company, related to parts, I guess, would provide some of the money for acquiring the machine. And so this all came to pass. And so development went on at night when the patent typists were at home, and then in the daytime, just no software development because the typist for typing patent applications.

**Adam:**

That's awesome. Yeah, that's truly time-sharing. So the computer science research group at Bell Labs, it's a pretty elite group, agrees to build a patent application system for the patent typists. This is strange. I've actually played similar games myself before where you know the company wants X and I want to use technology Y. And so I say, "Hey, Y is the perfect thing for X?" And you can sort get some legs for your side project if you try to tie it to something important. I'm not totally sure how ethical it is, but in this case, it worked for the Unix group. I think for them, it meant that the operating system had real users and very practical use cases to hit. And this constraint of being this patent document rendering machine was actually very helpful for the early development.

**Brian:**

You notice there's this text formatting thread that goes through all of this stuff?

**Adam:**

Yeah, totally.

**Brian:**

It's kind of weird, but it was in some ways a focus and something that kept things together in a way.

# **The Unix Room**

**Adam:**

Once they had their PDP-11 and they ported Unix to it, they needed somewhere to put it. And that place became The Unix room.

**Brian:**

There's a classic picture, it may be the one in Wikipedia or something, that shows Ken Thompson and Dennis Ritchie at presumably age late 20s, early 30s, or something like that in a room. And there's a PDP-11 behind them. It was on the sixth floor of Bell Labs. That was the top floor, and that's one of those things like if you live in a garret you have these sloping walls and you store old stuff that gets dusty. And so this was the sixth floor of Building Two where this was going on. It was a big plain room and nothing there. And the corridor wasn't well lit and there was old junky equipment from World War II left alone behind a chain-link fence which was just not very nice.

**Brian:**

But the room itself was perfectly fine. You had a PDP-11 in there and some of these model 33, and maybe I guess ultimately 37 teletypes, and a few tables and chairs, and people would hang out there and do things. And some of it would be working on the operating system or some of the supporting software, or some of it was just drop in and it was kind of a social center as well. So it was there for a while and then it moved into slightly nicer quarters, one floor down. And so it was more a place where people could hang out and work and also have a coffee machine rather than going to the horrible vending machines down the hall.

**Brian:**

But in all cases, it was a place where people could hang out, socialize. So it was like the open work environment that you see in many places today, except... It's probably just as noisy, but it was people all working on the same thing, or very strongly related. And I think that made it work out.

# **Building The Hierarchical File System**

**Adam:**

Eventually, the teletype terminals were replaced by computer terminals with proper monitors, and these computer terminals start spreading all over Bell Labs, everyone's got one. But The Unix room remains important. Several important innovations came out of that room. One of these is the hierarchical file system.

**Brian:**

Early computers, like if you used big IBM computers in roughly 1960 or something like that, they didn't really have a file system. There were ways to store information, but they were incredibly clunky and they were very device-specific. When you talked about accessing information from secondary storage, you had to know all the weird properties like the number of cylinders on the disc to be able to do it. And so the idea that, gee, you could have directories within directories, kind of obvious in retrospect, but doing it that was, if I recall correctly, absolutely part of Multics or it was variations. And what Ken did in Unix was to make that very clean and simple.

**Brian:**

So the actual interface to the file system was remarkably small, half a dozen system calls gives you pretty much everything you need to manipulate the information. And the actual implementation itself, once you've seen the system call interface, you think, "I could actually build that." And so it's neat in that respect. And now you look at it and you say, "Well, of course, that's obvious. What else would you do?" Because what you want is the file system to provide some abstraction hierarchy as a nice abstraction, you want it to be independent of the specific kinds of devices down there, and it certainly does that. It hides things like how many blocks there are, or whatever else.

**Adam:**

Maybe it's because I don't have any experience of computers from this era, but I didn't know the insulating computer programs from the specifics of various hard-drive layouts was an innovation. Another thing that was innovative about the Unix system was the interactive shell, the command line that we all know and love.

**Brian:**

I think, again, that was Multics idea, and then it was cleanly implemented in Unix. Again, the original shells were not super good for programming, but that got better as people realized, Jake, it's just another program you could write programs in it. And that had the good points, if you didn't like the show, you could replace it. And it had bad points that meant there were a lot of shelves and there still are. And I just discovered one of my new Macs has switched to Zsh. I'm sure it's an absolutely fine shell, it was actually done by an undergrad at Princeton long ago, but I've never used it.

**Brian:**

And so now, my startup reverts to Bash, not because it's necessarily better, but because they know it.

**Adam:**

I think it's backwards compatible.

**Brian:**

It may be, and it probably is, but it's one of these things where I don't care enough at this point. So I temporarily at least stick my head in the sand and go with the one I know.

# **Shells and Pipes**

**Adam:**

This has come up quite a few times, I guess, like texts and text formatting. One of the things about the shell, I guess, is input and output streams of text, where did that idea come from? Why is it powerful?

**Brian:**

The original idea of the standard input and the standard output that you could redirect those to files? I think that was fairly early on. That was probably in almost the first version that let's say, the first version that had a manual. Oh, that was probably there at that point. And so that's pretty neat, the idea that I can run the program and, oh, rather than seeing it could come out on paper, I can stick it in a file easily, and the program itself doesn't know that has happened because the service of redirection is done by the shell, the program just knows that you're writing someplace.

**Brian:**

That's probably quite early the idea of pipes, where you could take the output of one program and run it into the input of another program without an intermediate file, that appeared almost out of nowhere, somewhere, and I will guess, call it 1973 or something like that. The idea had been in the air for a while, Doug McIlroy was particularly very interested in being able to connect programs together like garden hose, connect another couple of programs in to get some job done. And he'd been talking up then for a long time.

**Adam:**

Doug had wanted annotation for being able to describe entire graphs of computations and then execute them. I'm not even sure we have an easy way to do that now.

**Brian:**

And that's a nice idea in theory, but it's much harder to figure out how to do that in practice. And so I think, and I don't know where that was, can, or what's the saying, wait a minute, linear is good enough, let's see what we can do with that, and not worry about the other stuff. But nobody figured out quite how to do it nor a sensible syntax. And then at some point, I'm pretty sure it was Ken, figured out how to do it, it wasn't very hard. And there was very, very briefly a bad notation for it. And that probably didn't last more than a few days. And then somebody, and I don't know whether it was Ken or Doug, came up with the vertical bar, the pipe symbol these days.

**Brian:**

And that happened, and that was one of those things that just clicked instantly. Everybody looked at it and said, "Oh, wow, of course." And then there was this frenzy of going in and fixing up programs so that they would work properly in pipelines. So that error messages didn't clutter up a pipeline, programs didn't put out or hid files that they would if there were no file names, they would read from the standard input and they would write to the standard output no matter what. And a lot of programs worked that way anyway, so it wasn't a problem, but there were others where it wasn't so obvious.

**Brian:**

Think about sort, you can produce any output from asserting program until you've seen all the input. So putting a sort in the middle of a pipeline is a fraud in a sense, because it's a dead stop and all this stuff piles up until it's sorted and then it goes out again, but it didn't matter. So sort was repackaged so that it read from its standard input and wrote to its standard output so that you could stick a sort in a pipeline. And of course, that's something, I don't know about you, but I do that almost every day in some way or others, I'm fiddling around with something.

**Brian:**

And so that's the kind of unification and that happened in an incredibly short period of time. Literally, it measured probably days where people start to realize, "Wow, you can do things like that." And then, of course, that led to these lots of ideas of screwball connections.

**Adam:**

Yeah. It seems obvious in retrospect, but I guess there are lots of ways where it could go wrong. You could have come up with a system where each program had to have some parameter where it took the next thing to call or something, you could have conceivably pushed it down into the individual programs to handle this composition, that probably wouldn't have been as compositional or something, I don't know.

**Brian:**

There's an early example of that. When MS-DOS came along, it had file named Wildcards, stars for file names, and so on, but that was implemented not at a shell level, but at each individual program implemented that. And that meant that some programs had it and some didn't and the ones that had it, who might be irregular. And so that was a right idea, but totally botched implementation. So putting it all in the Schellman, it was unified,

**Adam:**

It's hard to overstate pipes, I get why they lead to a Cambrian explosion of little programs being developed and glued together in this Unix room because they give you a composition. No matter how you write your program, you can glue it together with other programs and you can use shell scripts as first-class programs. To me, this makes me think of like early functional programming. It's just inputs and outputs and composing things together, gluing them together. 

# **The Unix Room Culture**

**Adam:**

Part of what made all this innovation happen was the community and the culture that was born out of this Unix room.

**Brian:**

If you wanted, you could go sit in your office and think deep thoughts or program, or write on your own blackboard or whatever, but then come back to the common space when you wanted to. And some people just lived in the common space, Ken did, for example, he was rarely in this office. I was mostly in my office, but I would go get coffee every hour or two and talk to people and sit down in a chair and read whatever random thing had come by and so on. This was all of course, before laptop computers, so you were pretty much wired to some particular place if you wanted to talk to a computer,

**Adam:**

You could be in your office working on something and then once it's working, you head in for coffee and you're like, "Check out this it's... "

**Brian:**

Yeah. That kind of thing. It was very much. And the whole building was, I think, geared up rather well for people to interact with each other. There was very, very long corridors within a long corridor, but then things sticking off the sides. And so the people in the computing science research operation were fundamentally in two of those little side corridors, and you'd go like this to go back and forth. And the Unix room was back on one end of the main corridor, at least at one point, or it was up on the sixth floor, between the two little side corridors. So it was relatively compact, but the whole operation did seem to encourage people to run into each other in the hall.

**Adam:**

I work from my home office, I guess now many people do, but it's interesting to hear Brian talk about this community that was built around a physical space around this Unix room. I wonder how much of what they built relates to the fact that they were just sharing a single machine, they were also sharing a common room, and a common table, and a common espresso machine.

**Brian:**

I just remember it as being a nice place that you could sit and listen to the ambient conversation, which was often interesting or people would bring in things.

# **The 10-Kilo Chocolate Bars**

**Adam:**

One thing they would bring in is 10-kilo chocolate bars, a 10-kilogram chocolate bar is massive. If it was shaped like a Hershey bar, it would be roughly the size of a coffee table.

**Brian:**

they would put a 10-kilogram chocolate bar in the middle of this table, and of course, it wasn't long before you had little chocolate fragments all over the place. It was just an unbelievable mess, but it was good chocolate. So people would come in and they would go take a knife and go pump and carve off an ounce or two of chocolate and leave a lot of fragments. And I'm sure that whoever hit that terrible job of cleaning up this place must've been really irritated. So I remember that kind of thing.

**Brian:**

And another thing that I remember, a rather odd thing, Dennis Ritchie, who sometimes was there, but I think more often in his office, his sister who had lived in England gave him a subscription to this English satire publication called Private Eye. And so Dennis would bring that in and stick it on the table, presumably beside the chocolate bar. And I found it funny to read this stuff. They had interesting cartoons, but it was very British. And I think if you weren't in the UK, a lot of this stuff would just go right over your head.

**Brian:**

And I'm sure an enormous amount of it went over my head, but Dennis would bring it in and I'd go in and I'd pick up Private Eye and I would read it for 10, 20 minutes and get some chuckle out of it or something like that. So fairly trivial memory, but there was just lots of little things like that that were fun.

**Adam:**

Unix doesn't stay limited to the Unix room in the computer science research group in the patent typists, it starts spreading around Bell Labs. People would hear about it and they'd want to find out more.

**Brian:**

Occasionally, you would come into the unit room and you would discover that one of the places off to the side of it, because there was a bigger room and a couple of smaller rooms this side, you would discover some august who was being shown the wonders of Unix or whatever else we were doing. And so you would see people that were in some way, well known, coming through, "Oh, who's that" Whatever. Carly Fiorina is one I remember distantly, she was at that time working at AT&T and then she went on to a variety of things, including HP. And I have no idea where she is now, but people like that well-known people.

**Adam:**

Oh, nice.

# **Demo Engineering The CIA**

**Brian:**

There was also a period when we did demos of Unix, and this was probably a little earlier, the maybe mid to late '70s. We would do demos for distinguished visitors who were coming through and they would be accompanied by distinguished upper management from Bell Labs and dog and pony shows. And so I met a number of interesting people that way. Perhaps the most interesting was William Colby, who at the time was head of the CIA.

**Adam:**

What did you show him?

**Brian:**

This is one of these things, an interesting story, I guess. The idea of Unix and I don't know whether this ever resonated with people who weren't programmers, but the idea was that you could build things very quickly by combining stuff that already existed. And so you could do shell pipelines, for example, so you could take two or three or four programs that did interesting independent things, and then glue them together into some sequence that did a specific task. And it was easier to do that, at least to prove feasibility or explore it of read and write a special program.

**Brian:**

And the specific one that we often used was a spellchecker, one that would basically take a document, split it up into words, canonicalize it in lower case or something. And then compare that to a dictionary and spit out the words that were in the document, but not in the dictionary. So those are plausible contenders for spelling detection. And you could write that pipeline practically, just type it because it wasn't very complicated. And so you would demonstrate that, for example, because this is a time when word processing didn't really exist in any sense. And so, "Gee, computers can check your spelling, what a neat idea." And so we were choosing-

**Adam:**

It's like even putting line numbers on pages was a bridge too far, right?

**Brian:**

Yeah, exactly. Whereas of course, that's a one-liner etc. So I would demonstrate that. The problem was that that pipeline and these were days when the machines were exceptionally slow, that pipeline took too long to check the spelling of a reasonable document. Well, it might take 30, 40 seconds to check the spelling of a document, and you don't want to keep a distinguished visitor waiting 30 or 40 seconds while this thing runs. So knowing that Colby was going to show up, what I did of course, was run the program the day before, collect the output in a file. And then what I showed Colby was actually something that basically said sleep for two seconds, and then print the result I had done the day before. And so this is a classic example of demo engineering.

**Adam:**

That's hilarious. Yeah. And he went back to the CIA and he's like, "These computers they have are super fast at Bell Labs." I'm thinking of computing today, we each have our own computers. You guys there, you were all on the same machine in the same like the hierarchical file system. So I don't know, I'm wondering, was that part of the magic that you could write something and then somebody else could use it?

**Brian:**

Yeah, I think it was. Having everybody in the same file system made it actually quite easy to share whatever you were doing, probably in retrospect, too easy to share because most people didn't bother with permission. So everything was written by everybody, and that could lead to potential issues. I could read your email or I could fiddle your program or whatever. But since it was a small group of very definitely cooperating people, that wasn't an issue at the time. But just the fact that all of the, for example, the source code of everything was there, and so you could look at something, anything from the operating system through to any of the programs that ran on it and see what they did.

**Brian:**

And then if you had an idea, you could make a new version of it that improved it in some way or other. And in fact, the only real rule there was, you changed it last, it's yours. At one point, I had an idea for improving the text editor, ed at the time. And so I went in and added some things to ed, very small stuff, but in that sense. And I was just perfectly fine, but I guess technically at least for a brief period, I owned ed. That encouraged you to be somewhat careful. But I think that having everything on the same computer was contributed to a sense of community as well. And part of the community was the shared information, but the other part of it was simply knowing that other people were logged in at the same time. So the command called Who, which just told you who was logged in. That just by itself was definitely a community builder because it would, when you run Who, it would tell you who was logged in, but also when they had last done something. And if you sent them a message saying help or whatever, you might get a response. So I think that living on the same computer, both the shared information, but also the shared we're all listed right here and we can talk to each other easily was an improvement.

**Brian:**

Google, for example, keeps a lot of their source code in one single giant tree at this point. And that's definitely good for code discovery and so on, but it doesn't address the problem of whether your teammates are all sitting there online at the same time and easily accessible.

# **Development Today**

**Adam:**

This development model of sharing a tree of source code, sharing a bin directory, it's interesting how in some ways, it mirrors how I work today. I ping teammates on Slack, we review PRs together, we're all making improvements to the same software. It's like in the 1970s, they've figured this out and we're just learning to recreate it.

**Brian:**

I don't want to sound cynical, but I think in a lot of cases, that's absolutely true, that there was a perfectly good mechanism that was appropriate 40, 50 years ago. And then it falls out of use and then people rediscover it, modified by whatever the current issues are or something like that. So, yeah, there's an awful lot of reinvention in that sense. That's absolutely fine because the circumstances are somewhat different.

**Adam:**

Yeah. The Unix room is now like a Slack channel somewhere.

**Brian:**

Yeah, exactly.

**Adam:**

Unix spread outside of Bell Labs, Bell wasn't allowed to make any money on it. So they distributed it pretty freely, including source code. People started adding contributions to it and it had a snowball effect. It wasn't open source, but it was close to it. It had a very permissive license.

# **Programming is Harder now**

**Adam:**

In my mind, these guys like Brian, like Ken Thompson, like Dennis Ritchie, these guys were like elite programmers. And part of my goal in this interview was to figure out what some of their secrets are. But Brian said programming is a lot different today.

**Brian:**

I found it easier to program when I was trying to figure out the logic for myself rather than trying to figure out where in the infinite stack of documentation was the function I needed. So for me, programming is more like creating something rather than looking it up, and too much of today's programming is more like looking it up.

**Adam:**

That makes sense. And yeah, I can see magical, I guess, if you're just pulling something in to do something. And I do have a sense though, how like... So you guys, you're in the Unix room, you were building all these little tools and the tools were starting to accrete and like no JS, is just a world that is accreted all of the things, or Python. So it's just that the end state of this process or something.

**Brian:**

Yeah, it probably is. Accretion is probably the right world, and I don't know how that ends if it ever does.

**Adam:**

There's a book, A Deepness in the Sky, the science fiction book, takes place like thousands of years in the future on a spaceship or something like that. One of the main characters is a programmer archeologist because that's the job at that point is like, everything has been accreted and his job is mainly running various VMs of old systems and hooking them back together. And these archeologist, because he have to dig and try to find the thing-

**Brian:**

This is thousands of years in the future or just today?

**Adam:**

Yeah. Well, science fiction is always about the time it's written, I think more than the future. But he makes reference in the book, like the system he's using uses Unix timestamps. So the vision is some future where he's still running something based on what you guys created back then, which is, I don't know, if it's a scary or a beautiful vision or a scary vision.

**Brian:**

That's mind boggling. I assume that the time, \_t went to 64 bits in there somewhere.

**Adam:**

Yeah. I don't know. That's funny.

# **We didn't know it was important at the time**

At the beginning, you were talking about Richard Hamming and his work on important problems and you were working on trying to find this problem that's equivalent to the traveling salesman problem. And Ken was trying to port a video game onto an old machine. It seems like the advice was not well-placed there, you couldn't tell from the beginning which... Like yours seems like the more important problem, I guess.

**Brian:**

Yeah. That's interesting. Do as I say, not as I do, because you're right, it's hard to think that working on a better video game or whatever was in some sense, working on an important problem. I think underneath it, maybe let's say, Ken was working on an important problem which was, how do you create a programming environment in which programmers can be more productive? And then Dennis added to that, the observation, how do you make it into a community, so the people who are doing it are working in some sense together?

**Brian:**

And I think those are important problems, seeing whether what you're doing on a day-to-day basis in some vague way is related to that. But all of that time sight, it's certainly at the time, I didn't think that any of that stuff was important in that sense

**Adam:**

This is interesting, the important work that these guys did, it didn't seem like important work at the time. So how do you choose something important to work on?

**Brian:**

I think the closest you get to important is thinking, "It's hard to write programs, what can we do to make it easier to write programs?" And that's partly something that I've felt myself, Gm, writing Fortran, Fortran is really hard to write with, can I do something better on that? And if what I find challenging or hard or whatever is also something that other people find hard or challenging or whatever, then if I do something that will improve my lot, I'm perhaps improving their lot at the same time.

**Adam:**

Yeah. I think that you've done a great job at that. I think you're too modest about your programming skills. I somehow suspect that you're better than you're letting on.

**Brian:**

Don't do a code review on me, please. Thank you.

**Adam:**

But this has been great. So thanks for your time.

**Brian:**

And it was great pleasure, fun talking to you. Well, talk to you again sometime.

# Closing Thoughts

**Adam:**

I think my takeaway is forget about Richard Hamming's advice, do what's interesting, help, smooth out problems, find the community that you can collaborate with. And if you find a community you really gel with, treasure it. And who knows, maybe what you did a couple of decades later will turn out to be really important. What's your takeaway listener? If you like this episode, do me a huge favor and tell someone else to try out the show. Maybe you could text somebody you know and let them know, "Hey, check out The CoRecursive Podcast." The main thing I'm trying to do right now is just grow my listenership. So if you have any ideas for how to do that, let me know, but I think the key is just word of mouth. So think about who you know who might like the podcast. Until next time, thank you so much for listening.
