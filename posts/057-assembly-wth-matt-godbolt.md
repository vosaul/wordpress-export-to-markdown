---
title: "To The Assembly"
date: "2020-10-01"
---

How do CPUs work? How do compilers work? How does high-level code get translated into machine code? Today's guest is Matt Godbolt and he knows the answers to these questions.

How he became an expert in bare metal programming is an interesting story. Matt shares his origin story and the creation of compiler explorer in today's interview.

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/16214276/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

"I want to engender, hopefully, excitement in other people that I feel when I start taking the lid off  of the computer and pulling out bits further and further down the stack until you get to the CPU and then go like, Oh my gosh, I've got all the way to the bottom. And then someone taps you on the shoulder, says, no, you can go deeper than this.  And you are like like deeper, this is amazing and keep on going. ." - Matt Godbolt

"I think it does inform the way that you write software. Just knowing how the ground works. I think there are some things that, that there's nothing that can save you from yourself if you don't do it. If you don't know a few things about how everything's working at the bottom" \- Matt Godbolt

### **Transcript**

_Note:  This podcast is designed to be heard. If you are able, we strongly encourage you to listen to the audio, which includes emphasis that's not on the page. This is a machine-translated transcript and may have errors, [you can help correct them](mailto:adam@corecursive.com).  The podcast page for [this episode is here](https://corecursive.com/to-the-assembly/)_

**Matt:** I think that's probably the thing that I want to get out of this conversation with you, is that I want to engender hopefully the excitement in other people that I feel when I start taking the lid off and pulling out bits further and further down the stack until you get to the CPU and then go "Oh my gosh, I've got all the way to the bottom" and then someone taps you on the shoulder and says, "No you can go deeper than this," and you're like, "Deeper? This is amazing," and keep on going.

**Adam:** That's Matt Godbolt. He's an expert in low level computing, he's going to teach us some lessons about why it's important to understand what happens between your high level language and when things get executed down at the level of the CPU. For instance, what does a for-loop in your high level language actually turn into when it's executed by the CPU and does that have performance implications?

**Adam:** Matt's an important speaker because he has all this knowledge and how he came by it is a pretty interesting story.

**Matt:** It all came out of a lucky break, where an afternoon's work with a friend and a bit of JavaScript and a memorable last name, and here I am.

**Matt:** I carry a certain amount of guilt for that, but that's also just being British.

# Welcome to Corecursive

**Adam:** Hello and welcome to Corecursive, where I bring you interesting stories about software development. Before we get into the episode with Matt, I have a brief plug, I started a new job, I now work at Earthly, we're building an open source build tool. You can find it on GitHub, search for Earthly. Builds are always a big mess and we're trying to make that situation a bit nicer.

**Adam:** Back to Matt. Matt's fame is not all luck as he describes it, we're going to walk though his story a little bit and I think you'll see that he's been on a trajectory to be the expert in what happens when you get down to the metal, for some time.

**Matt:** I was about seven and I went round to a friend's house and they had a very, very, very primitive flight simulator that he was flying around, and I was apparently uninterested in that, but when he then showed that you could type in stuff and make stuff scroll up the screen, apparently that was what enthralled me, and so I was very, very lucky to get one of them for myself for my eighth birthday.

**Matt:** That was yeah, 1984, so I've been hacking on computers for a long time now, 36 years.

**Adam:** That computer as the ZX-Spectrum an 8-bit computer with 48K memory and a 16K ROM. Also it had a tape drive, because we were in the era before discs were very common. What did this computer look like? Did it look like computers as we picture them today, or?

**Matt:** If you have any kind of reference point, maybe in the US in particular, things like the Apple II, IIE, that kind of era, that kind of thing. The Spectrum was relatively small, so the keyboard was probably smaller than an average laptop keyboard area, and the keyboard was the computer.

**Matt:** The keys themselves were like rubber, they were like a rubbery mat with indentations in them, which underneath there was a very simple, literally just a thin ... Oh gosh, what are they called? Membrane, which made contact or not. It was a very horrible feeling thing, it was very wooly, very bleeh.

**Matt:** The whole thing was the computer, you plugged it into a television and you tuned the television into the right channel and it was blurry of course, because it wasn't very good, and yeah, and it was tiny really, you could hold it in your hand and wave it around type of thing. It was notoriously prone to overheating in some cases and there as an expansion port in the back.

**Matt:** It was a fun little computer to play around with. You would buy games from the local newsagent, for £2.99, which is about five bucks-ish I guess, and you'd put them in and it was just like listening to an old modem sound, the screeching or whatever. You'd wait four or five minutes to get the 40-odd K of data in and then you'd play your game and you'd have to hope as well that there wasn't a corruption on the tape, that it would then crash and you'd have to start again.

**Matt:** There was a lot of fun about that and you knew, you were very much exposed to how the computer worked when you just turned it on, because you'd get a blank screen with a, "Okay, what do you want to do?" Obviously as a game player you would just say, "Load the thing I'm about to put in, the cassette tape.

**Matt:** If you don't have many games, another alternative would be to buy magazines from the same newsagents you were getting the games, and they would have type-in listings at the back, and that's how I got started in programing, would be to, the enthralling picture on the cover the magazine of course would never actually meet the quality of the type-in listing that you spent four or five hours typing in.

**Adam:** This is crazy, right? Instead of buying the game on a cassette tape, you could buy a magazine and then in the back 20 pages was just all the source code, printed out in Basic. You would type it in and hopefully you didn't make any mistakes.

**Matt:** Then of course, once you've typed this thing in, you have to save it to the same unreliable cassette tape that you were loading the games off of, so you had to hope that you A, got it right, B, you were able to save it so you could recover it. Of course, you would make typos, you would make typos all over the place and that would introduce one to the process of what a program was.

**Matt:** Even if you weren't a programmer and even if you didn't understand what you were typing in, you would get the gist of what it was. Certainly if you were then curious about it, it was a definite leg in to discovering how one might make one's own. That was how I started, was starting to write little Basic programs, literally as in basically the programming language.

**Matt:** Then latterly you would start typing in these giant, instead of Basic that you could understand, there would start to be more and more of these, just data statements after data statements. Of course if you then look into it, you realize that what you're typing in is the Machine Code of an Assembly based game.

**Matt:** Unfortunately this computer, the Spectrum, did not have a built-in assembler, you actually had to go and buy an assembler, but you could of course do it by hand or if the person who had authored it, and sent off their program to the newsagent, had essentially compiled, compiled, assembled their code and then dumped it out as hex, and then just said, "Well, type that all in and then you get a game." Obviously that's much more intractable to a user.

# What Assemblers Do

**Adam:** All right, I'm going to get some of this wrong, but bear with me. Basic is a basic programing language, 10 printing hello, 20 go to 10, it just keeps printing hello, right. To do more advanced things in these games that were in the back of the book, they would drop down to Machine Code. Machine Code is a level below Assembly code, it's really just raw binary or hexadecimal. It's the actual instructions the CPU can execute. Matt couldn't really understand this Machine Code, but he wanted to understand it and he wanted to understand what Assembly was.

**Adam:** Assembly is one level above Machine Code. Where Machine Code might just have a binary representation for a jump instruction, Assembly has mnemonics, so it would have JMP for jump. Assembly also has labels, just like in Basic, so that you can jump to certain locations, like go to 10, in my example. Matt didn't have any of this, but he didn't want to program his Spectrum in Machine Code, so he persisted.

**Matt:** My very first working Assembly program, I remember vividly, I was at a swimming gala, waiting for my turn to swim, and so I must have been 13-ish, 12, no, maybe younger than that, because yeah, there's the part of the story we'll get to, but around 11 I would say, 11 or 12. I'd written out very carefully, by hand, all of the Assembly instructions for just something which scrolled a piece of text at the bottom of the screen.

**Matt:** Then I had to obviously hand assemble it, that is take the fact that this one is an LDA,62 with the equivalent bytes and then when I got home I would type in the sequence of bytes, run it with my fingers crossed, and of course no debuggers, no feedback other than it either worked or it went horribly wrong. I was very, very fortunate that probably for the first and only time in my career, a program I wrote on paper worked first time.

**Adam:** It's almost just like a simple look-up table, right? You're, I want to add, but then for that it's this hexadecimal code or something.

**Matt:** Exactly right. The assembler's job is pretty straightforward, it gets a little bit more complicated because there are often opcodes or the primitive instructions that you want the computer to run for you, have different ways of phrasing them. The word is the same that the human writes, but depending on the context it's used in, you want to use a different, an actual number.

**Adam:** It's like '80s Sudoku, instead of sitting by the pool figuring out numbers, you're looking at new codes.

**Matt:** You're looking at the charts, right, right, right. I mean probably the most important that an assembler is able to do is to allow the programmer to define labels and essential goto statements, so I know everyone hates goto and no-one should be using goto in any modern programming language, but when you get right down to the metal, that's pretty much all you actually have. All the CPU has is arithmetic instructions, comparison instructions, multiply, divide, loads and stores and things, compares and gotos or jumps or branches, they're all basically the same thing.

**Matt:** Now, the branch location has to go to essentially a label, so you're going to say, "Hey, come back to this location." Your average loop would be, "Here's the top of the loop, do some stuff, decrement the counter. If the counter is not yet zero then go back to the top of the loop."

**Matt:** Those addresses obviously change, because depending on the amount of work that you've done between the start of the loop and the end of the loop, the number of bytes of actual instructions may change, the address of where the label is may change, and so there's this huge rippling effect where, if the assembler wasn't tracking this for you, you would be on your poor handwritten stuff, scratching out everything that was an address and adding one to it, because you just had to insert an instruction right at the very whole top of the program, and of course that's a huge pain.

# Enter A Friend

Adam: Yeah, no, definitely. When you were writing out all these programs, hand-assembling it and stuff, I don't know, what did your family think or your friends? Did they think it was cool or that you'd gone bonkers, or?

Matt: I think probably the latter. In fairness, the hand-assembling stage didn't last very long, but yeah, my family I think, always thought I was a little unusual in this. I was very fortunate that on the first day of my secondary school, so that would have been high school, just before high school age, I bumped into a good friend, well, someone who became a very good friend, who was also very much into computing and the same level that I'm in.

Matt: I'm still in touch with him and still great mates, and that allowed us to form a nucleation point for a bunch of similarly-minded geeky kids, when nerdiness and geekiness was not cool. I'm not sure it is cool now, but maybe it's different than it was, especially in my, the late '80s, early '90s Britain.

Adam: Matt's school had a computer lab full of these computers, the BBC Micro and he ends up getting a BBC Micro at home as well.

Matt: At lunchtimes, people were allowed to go in and obviously use the computers to play games of course, which was what everyone was going to do, once you have a roomful. From that point of view the computers were cool and if you knew how they worked and could the latest games or whatever, then you were only cool to the people who wouldn't otherwise have thought you were cool, in that room, in that context. I mean you got at little bit of cache there, but it didn't necessarily flow outside into the PE lesson, not quite the same level of cool there, for your average scrawny, British, nerdy, kid.

Adam: Matt and his friends start making little demo applications for the BBC Micro.

Matt: We were writing little demos, little examples of how cool you could make the computer run. At the time, the same magazines that I used to buy in the newsagents, were always looking for new submissions, and so he and I would send our submissions off to Acorn User, BBC Acorn User. If we were very lucky they would print them and they would send us £10, £20, £50 with a star rating.

Matt: Then in, oh gosh, where were we? In the 1989 or 1990 era, 50 quid for two 14 year olds was a lot of money, thank you very much, so the pair of us did very well out of those. The kind of things that we were doing there would be, Mandlebrot generators, Julia Set generators, just funny little programs that made nice pictures happen on the screen.

# To University

Matt: Around the time that I was talking about, those mid-teen years when we were writing our stuff and sending to Acorn User, the Atari ST was out, the Amiga was out, and they had vastly, vastly superior sound and graphics and everything, but we were doggedly hanging on to our old ways. When I did make the leap, I made the leap to the 32-bit era.

Matt: An interesting point actually, so Acorn, that was the company behind the BBC Micro, they knew also that the writing was on the wall for their 8-bit era, and they thought to leapfrog 16-bit too. Some of the engineers that were working at Acorn at the time, looked around for a CPU that could take them to the 32-bit era. They couldn't find something they liked, they designed something and they rather hubristically called it the Acorn Risc Machine.

Matt: This was the name for the CPU, the first revision of that chip was never actually placed into a real computer, but the computer that I had had the second revision of that chip, and I've been talking about that chip all that time, because he big reveal at the end of this is that the Acorn Risc Machine became the Advanced Risc Machine, which became the ARM chip. The ARM chip was designed by the team that built the BBC Micro, based off of their experiences working with the 6502 in the late '80s, or mid '80s I should say.

Matt: Anyway, so nowadays, they're ubiquitous, there's about, probably half a dozen of the damn things in my cell phone here, they're everywhere, but they had their roots back in the era that I grew up in.

Adam: Matt heads off to university, and he spends most of his time there not going to classes, but writing games for his new ARM Machine.

Matt: Mostly, this was before virtual memory, before process separation really, it was an interesting operating system. I mostly wrote little games, I tried to write some games, there's a game called Blur, that there's a video around somewhere, that Richard, who I was still I contact with, and I wrote together. Probably the most important thing that I wrote on the Acorn Archimedes, as it was called, was an internet relay plan, an internet relay chat plan, so if people remember, back in the days before InstaMessaging and things like that, there was IRC.

Matt: IRC was essentially a federated network of messaging between hubs and you could send messages to each other, and it was sort of interactive, there were channels, a bit like slack groups these days. At the time there wasn't a client for the Archimedes, so I wrote my own. Being the person that I was and the experience that I had had, and not really having a C compiler, there wasn't C compilers ... There were C compilers, but again, like the assemblers of yesteryear, you had to go an buy them, there was no GCC that was available.

Matt: I took the very sensible approach of writing an internet relay chat client in straight Assembly. This is a fully windowed system, right, you've got drag and drop windows, there's an operating system you're interacting with, there's clipboards, you're doing TCP/IP conversations and stuff, of course Assembly is the right thing.

Adam: I know how this goes, I get out my pad and paper and start writing. I guess you had an assembler.

Matt: Thankfully the Archimedes also had a built-in assembler, so that was not a big deal, but yeah, the whole thing was written in Assembly. In the middle of that, the thing that was de rigueur for the day was that your IRC client, so at the computer lab we were using whatever, IRICS or some systems that the computer had, sorry, the computer department had available to us.

Matt: They were all UNIX C based and their UNIX things all had, sorry, all their UNIX IRC clients all had scripting languages built into them, so that you could have things that greeted people when you joined the channel, you could protect the channel, you could set the topic and all the rubbishy things that people love to do in those kinds of environments.

Matt: I decided I also wanted to have a scripting language in my IRC client. I added an object-oriented BASIC into my IRC client, which taught me two things. One, the people who had written BASIC the first time round on the Archimedes, were amazing at what they were doing. Sophia Wilson is the person I know who was most involved with it. It's just amazing, the speed of it was phenomenal, my interpreter was staggeringly slow in comparison. I learnt how bad I was at doing it. Even though I'm writing it in straight Assembly, it's not a patch on what they had done.

Matt: The second thing was that once you do this, it was a shareware program, so people were paying me 10 quid to register it, although it was freely available on download sites, and that kept me in beers at university, so I've been very fortunate that I've had a couple of things along the way that have kept me in decent ... Yeah, decent ... I can't think what the right word is, so yeah, kept me going.

Adam: You had financial assistance.

Matt: I did, I did. Yes, I did, exactly. Once it was released, somebody smart realized that the scripting language, which I had started to write more and more of the system, bootstrapping wise, well, why would I write this thing in my horrific Assembly code, now I've got this language I can write, so I would write it in that. Then things got out of hand and before I knew it I got a patch sent to me, or rather an email saying, "Hey, do you know you can take your scripting language and do this?" Someone had written a web browser, a primitive web browser, a news reader and an email client in IR BASIC, in IR client and I'm like, "Oh my God, what's ..."

Matt: I can't remember which rule it is now, there's, all programs expand until they can either produce or consume email, I think is the rule. It was definitely the case for me. That was my first interaction with somebody who I didn't know well, coming out of the blue and saying, "Your code's cool, but it can do this as well," and showing me the way. It was a really interesting moment.

Matt: Yeah, that was what I did with that. The source code to that is actually on GitHub now, I found it on an old hard drive and I was like, "Oh, gosh, now everyone can see how dreadful this stuff was." Because it's 3:00 in the morning, you're writing, you've got to think of another label name for your Assembly loop, the same as all the other loops that you've written, except slightly different, and so it's called, Womble loop Jedi three. Yeah, that makes sense. It makes no sense, no sense, unless you're high on caffeine.

Adam: Matt spends his university writing games and on IRC, and eventually he gets to the last year of school.

Matt: In about the last year of university I'd gotten chatting, over IRC pleasingly enough, with somebody who worked for a games company. When I was starting to look for a job he suggested applying to them. I did and went along and they ... The interview went very, very well, they said, "When can you start?" I'm like, "Well, you realize I'm still at university." They were like, "Oh, well, do you have to finish it?" I thought, "My parents would crucify me if I didn't actually complete my degree."

Matt: They agreed to let me come back as an intern during the summer holidays and things, but yeah, so I ended up working for a games company called Argonaut Games, and they're, the amazing people I met and things I learnt there were just quite something, and I had a great time. It was also a lot of long days, into nights, weekends, all the bad things you've heard about the games industry crunch, it was too.

# **High Level Langauges**

Matt: Looking back now, with my more open eyes, I can also see that it was not a very good environment, it was a lot more toxic than it had any right to be. There were a lot of things that weren't good about it, but it was of it's time, is probably the most charitable thing I can say about it. By this point I'd learnt C begrudgingly, and the had graduated on to C++.

Adam: Let's not skip over that, so look, there must have been some point where you were like, "Hey, I can use a high level language like C instead of Assembler."

Matt: That's true, so I was definitely put off for the longest time because of the lack of a C compiler. I came across a hooky copy of the C compiler for the Acorn Archimedes, and at that time, and I'm not proud to say it, but I was very snooty about the code generator. I'd spent my life writing Assembly, like it was a fluid language, and I mean I look back and I can look back thankfully, because of this hard disc image I found. The code's terrible, I can believe that I thought I was good at it.

Matt: The compiler code probably was about the same level of quality, but of course I didn't understand C very well, so I sneered down at it as like, this is a macro assembler gone bad. Now look, I feel, that's actually probably a great way in, for an Assembly programmer who was using macros, to just say, "Well, call this a function instead, and now I've got a thing, or I can use a hash to find something, and now I actually have got a macro, a real macro that works better."

# Market Making

Adam: I feel like this is a big moment for Matt. He finally admitted that a high level language might be useful, that it might be able to write Assembly better than he does. He's not no longer interested in Assembly, he's still going to look at the generated Assembly, but he's willing to let the compiler write it. I think this foreshadows where he ends up.

Adam: Matt leave the game industry. He moves over to the United States, to Chicago, and he gets a job at a trading firm, doing market making.

Matt: The best analogy I have for a market maker, which is not a very flattering one, is like a used car salesman. "I will buy your car for this price." Then the guy who walks in immediately after you, wants to buy the car from me, and I'm going to sell it to him for a lot more money than you sold it to me. Because my job is to warehouse the cars and provide ballast for both sellers and buyers.

Matt: That's what a market maker is doing, they are someone who is in the market and that's how you can buy Google shares at any price, because somebody somewhere has got a big stock of them and is prepared to sell them, but also to buy more of them at a seemingly fairish price. That's what I spent the first few years doing, was doing market making for particular types of US stocks.

Matt: Of course, everybody is playing a game where they're looking at the world and actually going, "Well, actually maybe I'm prepared to pay a penny more or a penny less." The thing is changing at a staggering rate, we're talking saturating a 10 gigabit ethernet line with the changes, just the change information about exchange, and there are 14 in mainland US. It's a lot of data you're processing, at essentially line rate, or getting on towards line rate.

Matt: Though the barrier to entry is, you have to be able to consume this amount of data, make an intelligent decision about what you're going to do in amongst all of that, so obviously what you need to be able to do is react very quickly.

Adam: Yeah.

Matt: Whenever you want to react to stuff quickly, and you want to deal with floods of packets, you turn to a compiled language, and in our case we turned to C and C++. Yes, I inherited a code base that was predominantly C++ 98, so that's the original-ish C++ era. A couple of years in we were looking at whether or not it would be okay to start adopting some of the new features that were coming in C++ 11.

Adam: All right, so here we have Matt who was begrudgingly dragged into C and C++ from Assembly, and he works at a place where they struggle just to keep up with the market flow. There are new convenience features coming to this language, Matt is now primed to become an expert on how the sausage is made. What happens inside a giant optimizing compiler like GCC and how does that affect his ability to write programs that can keep up with the market flow?

Matt: C++ 11 gave us two things, and many other things, huge amounts of other things, so I'm glossing over those, but it gave us the auto keyword which says, "Yeah, just, the type of the variable is, whatever I'm equaling it to," so if you did auto I = 0 you're getting an N.

Adam: Type inference.

Matt: Exactly, yeah. I know other languages have much more sophisticated systems for doing this, RUST in particular is even more sophisticated, but C++ is pretty much like, whatever is on the other side of the equals determines what you are. With some of course, wonderful C++ strange caveats and asterisks and footnotes about the weird edge cases, but it wouldn't be fun if it was easy.

Matt: We got auto and we also got the range for, and so now I could do, for auto I:vec and now I'm getting all the integers of I in the vector and that's great. Obviously, well, not obviously at all, we had been burned previously in other languages, so there was a mixture of languages that were used in the desks, some of it was written in Java, and Java is an excellent language, but we had been bitten in Java with iterators.

Matt: Because if you iterate over a range of things in Java, a new object is created, every time you do that you get a new iterator that goes over the object. The one thing that we, the Achilles heel of the systems that we had before, was that we just basically couldn't afford to let them garbage collect.

Matt: We had so much junk in there that it couldn't be done quick enough for our systems to be, to remain on and in fact the GC thing, the first it would do is try and turn off the system so that we could spend hundreds of milliseconds churning through, and then deal with the fallout of everything going wrong, because we'd missed maybe some packet off of the wire, while we were, anyway, all those things.

Matt: We were avoiding it by trying to not create garbage, and so this iteration idiom that we would have liked to have used in Java was off limits, we had to just, for NI=law, I is less than vector or size equivalent in Java. When we've said, "Let's use the new cool features in C++," quite rightly the lead programmer was like, "Are you sure that's the same?"

Matt: A pal and I sat down and we, this is going into lore slightly now, so the tale has grown somewhat in the telling, but my memory is that we wrote a very simple function in C++ and compiled it and just dumped the output with objdump and the disassembler and the demangler and whatever. We did that a couple of times as we fiddled with stuff, and then I had the idea to use the UNIX watch command, and what watch does is it runs the rest of the command over and over again, highlighting the differences.

Matt: I was able to take the compiler and sorry, I was going to say, like watch, run the compiler on temp test.C, pipe it through all these things to demangle it, get rid of some of the stuff that the compiler generates that I don't care about, and then show me that please. Then I split the terminal in half and I had VI on one side and I had the results of this on the other. I was able to make changes, and every two seconds it would immediately show me the Assembly output.

Adam: Can you picture it? Basically we have a split screen, on one side you have your text editor with a single file code, and on the other side you have your generated Assembly, which the compiler emits. It's basically nonsense to me, but not to Matt. Even to me, if I change the idiom, it shouldn't produce a whole much more Assembly. It shouldn't have new, extra allocations.

Adam: If something like that happens, then I know something's up and that I should look into it.

Matt: Of course, naturally, that was a very valuable and useful thing to be able to do, to just experiment interactively. I think, even I at the time, C++ compilation is such a heavyweight activity, that until my friend Jordan had showed me how quickly he could just knock up a thing in a temp directory, it was a log, three lines and run the compiler on it. I was like, "Well, yeah, actually that's not too bad is it, it doesn't take too long." Of course it's quite fast, it compiles four lines of code.

Matt: Until that had happened, I just would never have done it, I'd never have experimented in this way.

# Bit Shifting

Adam: Once you have this tool, one performance question you might want to ask it, is when are bitshifts a worthwhile optimization? Bitshifting is, instead of multiplying a number, you shift it. Shift an integer left is equivalent to multiplying it by two, but it can be faster in certain circumstances.

Matt: If you look at the Doom source code or the Wolfenstein 3D source code, you'll see that it's covered with things like, A equals A shifted up by eight plus A shifted up by two. You're like, "What?" A shifted up by eight, that's 256, A shifted up by two, that's four, oh you're multiplying it by 260. I see what you're doing there. You're using shifts, because shifts are faster." All right, and then you can say, "Well, okay, that's cool.

Matt: Obviously the compiler nodes are strict too, and the thing about the compiler, it's much more consistent about applying that trick than you are, and so any time you're multiplying by 260, it says, "I've got you, I know what you're doing here." At the risk of revealing one of the big spoilers in one of my talks, where I talk about this particular thing, what you can do is, you can take a particular number, I forget which one it is, it's got a certain number of set bits, and you throw it in a compiler and instead of using the shifts and adds that you see if you do a multiply by 10, it just goes back to using a multiplier.

Matt: "Oh compiler, you gave up, you gave up didn't you? You decided that my number wasn't worthy, you're just going to use a multiply instruction." If you sit and pick it apart, and go, "Well this is, A shifted up by 10 plus A shifted up by four plus A shifted up by two, minus A, because it's one less than all of that, okay right." You put that into the compiler and you see, "Oh and it still doesn't multiply. I wrote it out as shifts and adds, because that would be faster and you turned it back into the multiplier again."

Matt: It's like, "No, you're stupid, because those shifts and adds are no longer cheaper than the multiply. The multiply is five cycles and you've just generated seven cycle worth of shifts and adds." Even though you phrase the multiplier as a bunch of shifts and adds, it was able to again, unpick it and say, "What are you actually doing? You're multiplying by 16972, I'm just going to multiply by 16972."

Matt: The cool thing about that is that you can then go and say, well, I read this out of some Doom source code, which of course is 386 or 286 error, if I tell it to target a 32-bit system and say, "The architecture is that CPU," it does indeed do the shifts and adds. It goes, "No, I've got you. I know the multiplier was far too slow, I will use the shifts and adds." Now, you look at the shifts and adds, it's actually been cleverer than my example.

Matt: It was able to unpick my shifts and adds, determine is was a multiply by some high constant, and then it had a much better way of doing that, that was still shifts and adds, than my original way. It's just, this is why you trust the compiler.

# Vectorization

Adam: Another optimization that Matt can see in action using this tool is vectorization.

Matt: Vectorization specifically is an interesting technique where the compiler is able to see that it might be worthwhile doing multiple iterations of a loop at the same time. CPU's have a number of instructions that treat a register, which is maybe 64, 128, 256 bits wide, and instead of just treating it as a giant, giant number, it treats it as a structure containing a number of 32-bit values or 16-bit values or 8-bit values or a number of double precision numbers or single precision numbers.

Adam: That's crazy. I write a for-loop, and I say, "Out of all these things," and it's like, "Yeah, I'll just add them up four at a time, because I can do that."

Matt: It's so cool, and yeah, exactly, and it does this for every loop, every loop that it thinks is profitable. Whereas as an engineer, if you were actually having to write this out longhand, like old Matt would have done, you'd have to be really quite devoted to this, to always use the magic structures that do this this way and deal with all the edge cases. The compiler will happily spit that out every time it sees a loop that it thinks it's worthwhile too, which is just another reason, right.

Matt: Rather than being smart individually every time, be smart once and teach the compiler to do it, and then everyone benefits from it all the time.

Adam: In other words, if there's some trick that you think can your code faster, probably the compilers out there have already put that trick into the optimization part of the compiler.

Matt: I have all the time by the way, I know you've scheduled it out to now, but I can keep talking until you're bored of listening to me, which is, already you've shown remarkable fortitude.

Adam: No, no, it's super interesting.

# Count Set Bits

Matt: My favorite example is, counting the number of set bits. If you have a number, a 32-bit integer, I'm saying a 32-bit integer, and you want to know how many 1-bits there are in that 32-bit value. It sounds like a pointless thing, it sounds like an interview question, which I think it probably is, but there are some genuine reasons for doing it. They're used in ... Packed matrices that are, very, very sparse matrices that have lots of zeros in them. Instead of storing all those zeros, you store a mask that says, "Well, which of the following values are populated?" Then it just has the populate values immediately after it.

Matt: You need to sometimes say, "Well, how many are there to get to the next row?" Yeah, I don't need to justify it really, it's just a thing that you might want to do, reasonably.

Adam: There's a bunch of ways you might solve this, the easiest way is you have a 32-bit integer, you're just going to check if the first bit is one, and then drop if off, and keep checking it 32 times. Then there's some optimizations you can make on that. If the whole thing's zero, you're done, you can exit early, you could do some sort of bit twiddling hacks, etc.

Matt: Anyway, you're right, any of those ways, and a modern computer, a modern compiler, and you turn the optimizer on to full, and you tell it that the architecture is like a modern PC, as opposed to the default, which is the oldest thing it possibly supports, and it doesn't matter, pretty much any way you wrote that, it will take the whole thing and replace it with the popcount instruction, which is the, how many bits are set in that register instruction?

Matt: That's just mind-boggling to think of what's gone on there. You've taken essentially an order N or an order, and set bits of N, any number of ways you could write it, and the compiler authors are like, "We got you, we know what you're doing, even if you've phrased it in all these different ways." There's a normalization pass inside the compiler, there's then tricks for noticing what you're doing, idiom detection, and then it's like, "No, this is counting the number of set bits, we're going to replace it with that one instruction." That's amazing.

Adam: I totally agree. It is amazing. I means that this interview question is easier to answer in Assembly than in a high level language, because in Assembly it's just a single instruction.

Adam: What does all this knowledge about compiler optimization tell us about writing high level code though?

Matt: It's the one thing that I want people to take away from all of this conversation, is that compilers have moved onto the point now where even though it's so useful for you to understand what's going on right at the bottom and understand what the CPU is doing, what the RAM is doing, what the caches are doing, what the branch predictors doing, that's great, it's wonderful, it's exciting, it's interesting. Don't necessarily think that you can't trust the compiler to know those things, or some of them at least, and take them into account.

Matt: Trust the compiler, always trust the compiler. Write code that's easy to read, because the human is more important than the compiler now. The compiler has your back whatever you wrote, so don't trick yourself and write some nasty little thing because you think it will be a cycle faster than that. It won't be, the compiler honestly will beat you in almost everything that you can care to do.

Matt: Write the code so that your colleague, or you tomorrow morning, when you haven't got coffee, can understand and trust the compiler to just generate the right code.

Adam: In a sense, you're admitting defeat from your old days of ...

Matt: In a sense, yes, but in another sense, it's as if the scales have fallen from my eyes now, and there are just so many more smart people that work on compilers, that have the time and the energy and the will and the clever ideas to add in these \[inaudible 00:36:34\], these tricks, this knowledge of the ISA that's deeper than anything I would have these days.

Matt: Am I saying that you can't beat the compiler any more? No, of course not. There's always a case where you know more information than the compiler, but the compiler is very, very good under almost all circumstances you care to do.

# Godbolt.org

Adam: Matt's a change man, right. I mean he had already moved on to using high level language, but now with this tool, he can really see the Assembly that's being generated and all the optimizations that are happening, and this is clearly something valuable.

Adam: He puts this up on a website, on his own personal website, godbolt.org, basically unchanged. You put your C++ code on one side and you see the result on the other, and this starts to spread inside of the C++ community.

Matt: I tell, my favorite story for the whole of this is, that we were lucky enough to have Andrei Alexandrescu, who was the father of some of the template meta-programming tricks that we'll see. There's a number of books he's written. He came and gave some talks at DRW about performance. He was then working for Facebook and they were dealing with large matrix scale and there was all these things.

Matt: It was fun for me, because I spent the whole time heckling him on the Assembly code he was showing just generally, and so I kept pulling him up on that. It was good banter, back and forth, and eventually at the end, he said something along the lines of, "I think, somebody told me there's a website that you can just put your code into, and it shows you what the Assembly looks like."

Matt: At that point I blushed bright red, as everyone else looked at me and pointed and said, "Yeah, it's his." I felt like an absolute dreadful person for not mentioning it earlier.

Adam: I feel sorry for this guy. Yeah, he came to give a talk and you were poking at him, and then he's like, "I think I have a solution," and you're like, "Yeah, that's mine."

Matt: Yeah, so he and I have become friends now, so I think he's forgiven me for being quite so dreadful. I think we're all right on that front.

# On being a Verb

Matt: Yeah, so it grew and grew and it probably took a couple of years before it became more well known.

Adam: Godbolt.org now supports many, many languages, 21 as I look right now, maybe more by the time this comes out. I first came across it on Hacker News, when somebody was posting a link about the Zig language, Z-I-G, and how well it optimizes down to X86 Assembly. If you can read Assembly and you have small examples, godbolt.org has become a Rosetta Stone for code performance.

Adam: One thing Matt doesn't like about the tool though, is it's name. Yeah, I mean I think, people say, to Godbolt something, right.

Matt: Yes, yes, they do. It's something that yeah, it's ... I've been in C++ committee meetings where somebody has said, "Why don't we just put this in Godbolt and see what happens?" I'm like, "I'm in the room, you can't say that with me here, it sounds weird." I don't know.

Adam: It's fitting though, right? Because here's your story of all these, it seems like the punchline to each of your anecdotes is, "To the Assembly, let's see what it's doing."

Matt: Yes, I think, there is a reason why it was me, or rather that I was in the right place at the right time, with all the right background for this to happen, right. You're right, it is the punchline. I guess in that way, yeah, but I mean it's luck, it's luck. I mean that's the thing, people, I get invited to things like this, now, this, an enjoyable time talking to you, and I've been able to talk at various conferences that I would never have dreamt to, as just some rando who writes C++ for a living.

Matt: It all came out of a lucky break, where an afternoon's work with a friend and a bit of JavaScript and a memorable last name.

Adam: That was the shows. Matt, he recommends that nobody write Assembly now, but that everybody should be able to read it. Because of his interest in Assembly and reading the Assembly generated by compilers, he's become famous in this world of very performance-critical code.

Adam: Check out godbolt.org where you can play around with the tool that he built, that he likes to call Compiler Explorer, but everybody else calls Godbolt.

Adam: As I mentioned at the beginning, I got a new job at Earthly. If you go to earthly.dev or check it out on GitHub you can see what we're building. We just want to make builds better and builds faster and builds more reproducible. It's just an ugly, complicated area, so we have an open-source tool and we're trying to make the build experience better.

Adam: Until next time, thank you so much for listening.
