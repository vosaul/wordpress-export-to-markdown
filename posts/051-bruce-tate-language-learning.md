---
title: "Learning a new programming language with Bruce Tate"
date: "2020-05-05"
---

#### Finding Joy in Learning Programming Languages

There’s joy that can be found in language learning and pain as well. Whether you’re a beginner or an expert, there are still some things you can only discover by picking up a new language. 

Bruce Tate will tell us how learning new languages rekindled the spark of joy for him.

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/14285750/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

_“_I find that learning a new language mixes a lot of joy in that pain, and that's when I grow most rapidly as a developer.”

“You can't break somebody else through their own pain. They have to learn their own lessons, and they have to, at some point in the model, they have to feel more and more pain to break through to the expert.”

“When you visit other places, when you learn other languages, the world gets smaller.”

### **Transcript**

**This is a machine-translated transcript. Podcast page for [this episode is here](https://corecursive.com/051-bruce-tate-language-learning2)**

**Bruce**:  Even though you get marginally better at what you’re doing, you’re not doing the things that make you curious and joyful and the things that brought you into programming in the first place.

I think it’s actually poison. 

**Adam**:  Hello and welcome to CoRecursive. I’m Adam Gordon bell. That was Bruce Tate. His books about programming languages are super fun. Today, he’s going to tell us about leaving Java to explore less mainstream programming languages and what he thinks is broken in our industry, and how we can fix it.

## **Leaving Java**

**Adam:** I started off by asking Bruce about his career as a Java developer.

**Bruce**: I probably started writing Java in 96 and went independent in 2000.

**Adam**: So you started off in Java then you left for greener pastures. I guess what I know about you is your kind of books about **Seven Languages in Seven Weeks**. So why learn another language? You were in Java for a long time. Conceivably, you could have stayed in Java till today.

**Bruce**: Yeah, conceivably, and a lot of my friends did. So there’s a big speaker circuit called No Fluff, Just Stuff, and a huge number of the big Java developers were there. DHH was built in Ruby on Rails, and Ruby language was attractive to me. I got in it just before the rails framework blew up. 

And there was another guy, though. His name is Dave Thomas. I was at one of these No Fluff, Just Stuff talks with Dave Thomas, who after that time has become my mentor and a good friend.

I started saying, well, I bet Ruby can’t do this, and I bet it can’t do this. No bet it can’t do this. And you know, the consummate British gentleman stares me down and says, Bruce shut up until you’ve done something non-trivial in this language, and then come back. And so I went away with a business partner named Justin Ghetland and we built this application and we built it in just a small fraction of the time that it would take to build a similar job application. I mean because it was right in Ruby sweet spot. It was babysitting this big fat relational database with a very tiny web UI, and there were a lot of things that can do that better than Java could at the time.

So we did that, and with so much success. This is a pretty significant competitive event.   I lived in Austin, Texas, and there was a tiny town called New Braunfels, a proper German name. And they had this company called Autogas, which was a huge company with a small niche.

And they basically started the auto fueling. And the problem was that after they started that business, there were all these customers that didn’t want to go into the stores anymore, right? So it became this rewards company, right? So that they had to incent you to go into the stores with great coupons. So that’s, that’s why you always see these programs, like, did you get your rewards today for your latest fuel?

But they were having problems with a particularly nasty job implementation. And I told them on just a raw gamble that I could build their system for one-third of their cheapest build. And actually did that and made a good amount of money with it. So that’s how I got into Ruby. 

## **Leaving Ruby**

**Bruce**: And then at some point, the same thing happened to me within Ruby that was happening to a lot of people. I was hitting a wall from a lot of perspectives, from an organizational perspective, from a memory perspective. And I read the same paper that everybody else was reading called the “Free Lunch is Over.” That was the one that said as processors double in speed, we get the economic benefits and our industry benefits. But one of the things that’s happening is that we are not getting all the benefits out of Moore’s law that we used to or for physics reasons. Because if you keep cutting the circuit in half, eventually the space between your circuits is going to be just several atoms thick and that’s what was happening.

So we kind of hit this wall. We couldn’t double things in performance anymore by just doing the same thing by cramming the same chip into something smaller. What we had to do was to stack them like plates in the pantry, and when we stack them, the languages that work on them had to walk and chew gum at the same time.

They had to be concurrent. And so I wrote **Seven Languages in Seven Weeks** because I was afraid. I was terrified that the Ruby wasn’t going to get it, do everything that I needed to do and kind of the cool kids that I knew were leaving the room and moving on to something else. And I was watching this happen, but I didn’t know enough to know what the next thing was going to be. So I wrote that book hoping to bring other people with me and then several doors opened.

**Adam**: Wow. I wouldn’t have guessed that you wrote it from fear because it seems kind of fun, oh, let’s take a tour of things.

## Erlang and Joe Armstrong

**Bruce**: It started to be out of fear, and then that was really the time that I became a language buff. There’s a language called Erlang that I’m sure you’re familiar with, but for your listeners, the Erlang language is a language with a good chunk of the world’s messaging traffic.

It’s a language that was developed at Ericsson, created by a couple of gentlemen named Robert Vrding and Joe Armstrong and a few other people that aren’t as well known. Joe Armstrong got the first draft, the first two chapters I ever wrote on this thing, and I didn’t know that he was going to get the two chapters.

The two chapters were Erlang and Prolog. My editors sent them and said, “Hey, I’m sending this up for review,” and I said, “Okay, cool.” After a little while I thought, “Who did you send those chapters to again?” And she says, “Oh a guy.” I knew her by this time, and I said, “Who did you send the chapters to?”

She says, “It’s Joe Armstrong, but it’s going to be good. It’s going to be fine.” So he wrote to the publisher back and almost killed the project dead in its tracks.

**Adam**: Oh.

**Bruce**: I was a new developer, right, of functional languages. I don’t know any of that stuff. Anyway, Joe’s note was not the super kind, gentle note that he is known for, right?

It was like, “This book is in trouble. I get the sense that this author knows Erlang very well,” which was not true.  I mean, there’s a first, it was based on his example, which is why he thought on a new, well. He said, “This author knows nothing about Prolog.” So anyway, I kind of tucked my pride into this tiny little bag and then just approached Joe and said, “Hey, can you teach me some Prolog?”

And he did it. And so doors started opening for me. You know, I noticed a couple of people that have been on your last show, you know Edwin Brady, he did an interview for one of my books and Philip Wadler and DHH. I got to meet through one of the early books. It was a very exciting moment for me because Joe was so excited about the Prolog and as his joy kind of bled off on me.

So we were working on this problem, playing Sudoku.

**Adam**: Was this a phone call?

**Bruce**: Yeah. Just an internet call. Here, I’m this nobody developer talking to Joe Armstrong, who’s really one of my idols, right? I kept trying to code the algorithm for the solve. He said less, and I would cut code away and cut code away until all that was left was the rules of the game.

I mean, literally it’s like this thing has like nine cells and all the rows, columns and squares have to be different. And then I press enter and the solution pops out. Right. And you know, I’m on a different continent and Joe is laughing. And I say, Whoa, what’s this about? Is he making fun of me? 

No, it’s the joy of the language! He said, “You just had your Prolog moment and I was here to see it.”  So it was just a beautiful moment.  And I mean, we are going to miss Joe Armstrong, but that was a wonderful moment to be on the phone and to share it with them.

 I mean, I didn’t have any idea at the time about his affinity with Prolog. It was great. Since then I’ve kind of talked to Dave Thomas. And I mean, lots of other people about why learning languages is so important. And I’ve spent a long time trying to internalize that.

**Adam**: That’s a great story. I did talk to Joe myself very briefly. When he put out his Erlang book, I got to like the early edition, and then I emailed him a couple of questions. Yeah, he responded right away. I don’t think I had any extensive phone calls with him, but he was very available.

**Bruce**:  He was, he was such a gentle man. He was the ultimate ambassador for that language. The ultimate investor. Just very kind.

## **Why Should People Study Programming Languages**

**Adam**: So you mentioned it briefly there, why should people learn programming languages. I assume you’re not using Prolog day to day, but you found it valuable in some way.

**Bruce**: I have spent many, many years thinking about this, and I have finally settled on why it’s so important. So have you heard of the Dreyfus Learning Model?

**Adam**: No, I have not.

**Bruce**: The Dreyfus learning model is an old air force model for teaching pilots. And there’s some science behind it. Basically there’s this big old pyramid.

So if you Google for Dreyfus, you’ll find all kinds of resources for it. A lot of the things were based on it, but there’s this big pyramid, none of the bottoms, you always have some flavor of a beginner. And on the top, you always have some form of expert. And the Dreyfus model believed that you taught experts and beginners and everyone in between different ways.

For beginners, you learn mostly by lists. Joe Armstrong eventually wrote the forward for **Seven Languages in Seven Weeks**. And he would say, so the way to learn programming at the very beginning, you’re going to code the programs side by side, and then you’ll add to the program and then eventually you’ll be able to do it yourself.

That’s very much the way the Dreyfus model works. One of the things that are interesting is that when you’re at the bottom of that pyramid, there’s this thing called pain, and there’s a lot of it. So I’m working with a mentoring program for women and minorities in tech in Chattanooga, and there’s a man named Evan Miller.

He was watching me teach this woman a particular concept. She would struggle with something and then I would kind of make a little correction and she would struggle with it. Then Evan would shake his head and she would struggle and I would make corrections, and Evan would shake his head. So I finally got frustrated and I turned around and I said, “What?” He said, Bruce, she’s got to feel her own pain

**Adam**: Yeah.

**Bruce**: At the bottom of that Dreyfus pyramid, and we all know it. You can’t break somebody else through their own pain. They have to learn their own lessons, and they have to, at some point in the model, have to feel more and more pain to break through to the expert.

But we’ve found that developers need to scale that pyramid so many times because the pace of technology is advancing so quickly. So I find that learning a new language mixes a lot of joy in that pain, and that’s when I grow most rapidly as a developer. That’s kind of the model I’ve built my company around.

There’s a tiny little subscription that you get, and then we basically knock you down the whole mountain, the whole pyramid. Let you climb up again. Knock it down and climb up again. Every two months there’s another language and you get knocked down the pyramid to climb up again. I think it’s really important.

**Adam**: So is it because they’re learning a new language is hard or because it’s fun? I don’t know what.

**Bruce**: Yes. It’s all of that. It’s hard. There are a lot of things that are important here. The first thing is that you get your brain, you get out of your expert’s brain and into your beginner’s brain.  The ability to go from one to two, to three, to four, to a five, that’s the core skill of our program.

It’s not whether you can code React or whatever. It turns out, if you invest in people in this way and people, there are companies like Google that have invested in this approach, let developers play. When they play, when they experience pain, and when they experience joy in the context of learning, magical things happen.

**Adam**: I learned before, there’s like an HR type term for this.

**Bruce**: Is there?

**Adam**: Yeah. Well, maybe HR is not the right term. Maybe economics. The economic term is like discretionary input. So it’s like input that people feed into their work that is discretionary. That’s like above their requirements.

**Bruce**: Yes. And I think that we ought to think of it as an investment. If you wind up clearing the deck for somebody for the whole, let’s just say Friday afternoon or Friday morning, if you clear the deck, magical things happen. It turns out that you’re going to, the first couple of months, it’s going to be an investment.

It’s not the sunk cost. If that money will come back because that developer will get more tools in the box and that developer will learn to learn more quickly, and as new technologies come online, they won’t be afraid to deploy them. It will 100% pay for itself. The way to turn a passionate, beginner programmer to a passionate intermediate is to give them a playtime.

The way to turn a passionate, intermediate to the passionate advanced developer is to give them playtime. And when you do that, you get the benefit of basically lower costs for a little while. You get the benefit of somebody who actually enjoys what they do and the endorphins that kick in when you’re enjoying the learning process are just supercharging the whole development improvement cycle.

## **Friday Projects**

**Adam**: What if I’m just a developer and I want to learn something new, like how do I find time for that in my world?

**Bruce**: That’s a loaded question.  There are a number of questions, and one of them is where are the resources and how are they shaped? That’s a problem because the resources for an expert are different, or the resources for a beginner. So if you want to make a habit of going down to the bottom of climbing up to two or three or maybe even a four in a language on a regular basis, then you have to have media that’s not just a book, or not just a video series or not just a like a test first problem, like an exorcism.io or something  is a great resource for that kind of thing. One problem is where do you get the media? The second problem is how do I get my boss to buy off on this concept?

And those are difficult problems. And of course, we have our take on it. We believe that you have to have multiple types of media to learn. We have links so you can go off and read, tiny problems that you can go solve. We have pieces, a slice of a book, a slice of the video, but whatever your take is, this is all kind of new stuff.

And some people believe you shouldn’t script the fun. No. I think that you can, and you should script the fun and that if you do screw up the fun, you learn more quickly. Other people believe that, as soon as you start scripting the fun, it becomes not fun anymore and you don’t get the same endorphins.

I don’t know what the science behind that is, so that’s hard. And it’s also hard to make the case to management, Hey, I’m going to do something that is other than what you told me to do and you’re going to be happy that I did it. So that’s a statement of faith. And so you basically have to be able to defend yourself and talk about the test cases, like Google.

So there are a number of companies that I work with that do the Friday projects, but the people that do them will make that investment. Their developers tend to grow. The complete non-answer!

**Work On Finding Your Joy**

**Adam**: It’s an answer. It’s tricky. I get what you’re saying. What about if I can push on this issue? What about if my work is not collaborative with this? If I just need to do my job, how do I prioritize learning in that type of world?

**Bruce**: So I believe to be a healthy developer, there are all kinds of studies. I just gave a talk in Bangalore called Joy, and I wanted to give that talk in particular - it’s a functional programming conference. I wanted to give that talk in particular because we’re starting to notice that Mumbai and Bangalore developers under stress are developing heart problems at the same rate and even a more extreme rate than similar groups in the United States. 

I wanted to give the talk that says, Hey, you have to take care of your career. You have to work on finding your joy. You have to do things that make you curious and take you away from your day to day programming profession. And your value system that is the Western value system, isn’t considering all of the facts.

I’ve been thinking about this and I think that the way that we’re building developers is wrong. I think that we don’t think enough. I think that we tend to build people to the point where they can do these repetitive things very quickly to the point where they don’t enjoy them anymore. And then we ask them to keep doing them under more and more pressure as the codebases grow.

And with raising expectations because now you’re maintaining a larger code base doing the same thing. We’re not giving people enough breaks to, and not just breaks to walk away from the keyboard and take a walk, but breaks to allow the brain to grow in other ways.

**Adam**: Yeah, I would agree to that. And that the whole service industry, which like a lot of the Bangalore kind of world is billable hours. I think that that is just stressful in and of itself. Like it’s very tightly measured.

**Bruce**: It is broken. So after the fact that they’re basically upside down from the United States where most where, a lot of those companies serve. You take a highly motivated population that lives probably an hour and a half out of town because everywhere is an hour and a half from where you work.

So you build in three hours of the day. Then you say you have to be around on both of the margins. When people come in and when people leave, and you have to be productive during the rest of that time, and that’s a recipe for killing a generation of fathers that never know their kids. I think it’s a really difficult thing.

So the nice thing about being at the functional programming conference there was, many of the leaders in Bangalore were there. I was able to give that talk that said, Hey, don’t discount your personal passion and your joy. I saw people that were 40, 50 who just bread down and cry because it resonated so well.

I don’t think that they’re alone. I think that we have a whole generation of developers in this country.  If you think about the pattern, we’re successful with the software development model and we say, Hey, keep doing the same thing and you know, more and more tickets.

Then at the same time, we’re growing the code base. We’re not providing time to refactor and make the code base better. Even though you get marginally better at what you’re doing, you’re not doing the things that make you curious and joyful and the things that brought you into programming the first place.

I think it’s, it’s actually poison. 

**Adam**: It’s great talking to someone like Bruce who’s been in the industry for more than five years. Our industry is so young and I think we have lessons to learn. One of them is what Bruce is saying here. You can’t build a long career at a place where the work is never fun, where you just have to crank out ticket after ticket.

There’s a related question that I wanted to ask Bruce as well. 

**Adam**: Does learning a language have to have some payout in career aspirations?

**Bruce**: No. No. Learning languages, I mean, for Joe Armstrong, it was the Prolog moment.  You know, as I wrote Seven Languages in Seven Weeks, I didn’t expect to sell a single copy of that book. That was about bringing people on the joyful journey with me. And in an age where every publisher is trying to strip the personality of a  book, actually comparing languages to movie characters, it just didn’t fit. Right?

What I was trying to do is move a person’s head with me, is when I went from page 89, the end of IO, to 90 the beginning of Prolog or whatever. You know, when you went from Prolog to the functional family of languages, I was trying to bring people along the journey and move their brains.

The payout is secondary. The joy is the journey, right?. So I have this coding club at a high school in Chattanooga where a lot of the kids don’t have their own computer. We basically just pair around a problem. So we were working on Tetris at the time, and we throw out the t-shirts for Groxio and for our conferences, and they kind of strut in and they love them.

But the favorite t-shirt that I ever saw was a t-shirt that said, “I hate programming, I hate programming. I hate programming. It works. I love programming!” I said, “Yes!” That person gets it. That’s the joy.  That’s tinkerer’s  joy.

**Adam**: I always found that side projects can be very enriching sometimes just because you get to throw away, like a professional world. There are deadlines, there are things to do, and then if you just get to build something on the side, and in my mind, I’m like, whatever I’m building here is going to change the world.

But actually the fun of it is that it doesn’t actually matter that I can just build it and throw it away and there’s no bug reports or whatever.

**Bruce**: So there’s a great talk at our Lonestar Elixir conference in Austin. The talk was the “Grand Bank of Jon Jon” where this guy said, Hey, there’s this framework called Nerves so we could code stuff. And so what I really want to do is put an ATM in front of Amazon. So he actually made this hardware-software project that let the kids put in a card and pay with Jon Jon bucks.

And his name is Jon, right, and he actually pays for products on Amazon. And they would kind of teach their kids financial responsibility, but he had more fun with that project. They’ll never use it for anything besides the house, but he had more fun with that project than anything. So I completely agree with you.

## **The Most Fun Language**

**Adam**: So what if I just ask you some questions about languages. What’s the most fun language that you had fun learning?

**Bruce**: There’s a lot of different categories there, and I’ll answer a few of them. One of the questions is, what’s the most mind-bending programming languages? And there are probably three. One of them is a language called Elm from a guy named Evan Czaplicki, and he worked for Prezi for a while,

Worked at No Red Ink for a while. And that language was a user interface language, but it was strongly typed and it was a beautiful React style and flow. But it worked that way end to end. And that was just mind-blowing. So Evan had built this Mario game and you could code on it a little bit here and you know, change of parameters and suddenly Mario was jumping higher.

That was mind-blowing. So the second one, you’ve had Evan Brady on the podcast before?

**Adam**: Yeah.

**Bruce**: He has this concept called Dependent Typing. There’s a research field called dependent typing where you build not just the character of a type end, but also values into the types as well.

So that if you have a list of six and the list of seven and you add them together, you have a list of 13. And what was interesting for me about that language is I kept saying, I don’t get it. I don’t get it. I was just grinding through these types and having a horrible time. And then so I ground through the types and says, Oh man, the functions are going to be terrible. And then I started using the tool and I kept pressing tab. And the program just wrote itself. I said, Oh, I think I can see where he’s going here. Because once you get all the thinking done, and in the language itself, the rest kind of wrote itself. So that was really cool.

**Adam**: Yeah. He had an example in his book where I think it was transposing a two-dimensional array, and like you didn’t even type anything. It was just like hitting buttons and then it was like you wrote out the type and then you kind of autocomplete autocomplete autocomplete.

**Bruce**: Right. It was insane. I had a very similar experience with run length and coding, like a zip algorithm. That was cool. So the third one is there’s a program called MiniKanren which is Clojure Meets Prolog, which was absolutely mind-blowing. I wrote about that in Seven More Languages in Seven Weeks.

It was Jack Moffitt, I believe, who wrote about that language and it was so stunning. He had the story algorithm. He had like a story generator that was cool that would basically take these beginnings and ends and weave together a plot in between, based on facts and language. There are certain languages like Smalltalk that are beautiful but flawed in fundamental ways.

Like Smalltalk. It’s great to work in until you have to extract the freaking program from the image. You can’t get it out to package it. I’m like, where’s the line around this program? Well, with a Prolog, it’s input output. And so when you can marry Prolog with a language like Clojure, that is about as extensible as a language could be, beautiful things can happen.

So unlike those three, in those ways. I think that Elixir is a really cool language. That’s my favorite at the moment. I like Elixir because it has this idea of OTP, which is super advanced. Simple concepts that kind of grow up in an advanced way. Have you ever seen the IT Crowd the British comedy?

**Adam**: I have, I have seen it a little bit.

**Bruce**: Did you try turning it off and on again?  That’s every episode built to answer the question. Did you try to turn it off and on again? Well, that’s OTP. So if you have a little server and anything breaks, it’ll shut it down and turn it on in the last known good state. So I like that. But I also like that I can take my beginners and I could teach them Elixir.

And there are simple transformations. We do them in pipes, which means you feed the output of one function as the input is the first argument for another function. And when people see pipes, they say, Oh, I get it. I get that you can build a program in this series of transformations. So yeah, those were some of my favorites. 

And the last two that I’ve explored, there’s the Crystal language, which is kind of like a high-performance Ruby, which is cool. A fully typed Ruby, and I get a lot of the dynamic feeling of Ruby, but instead of doing it with opening the classes, they get with macros. And so that one is wild. All the things that I thought wouldn’t be possible with the stronger typing.

You know you can get about 90% of the way there. So that was fun to see.

**Adam**: Yeah. You would think a strongly typed Ruby is not anything like Ruby or.

**Bruce**: Right. Well, it turns out it’s pretty different, but the programs look very, very similar. So they did a lot of investing in their macro system and a lot of them investing in type inference. And so they got surprisingly far, I would say. And then the last one that was interesting was a language called Pony.

Have you talked to any of those folks yet?

**Adam**: No, I had a request from somebody to interview someone about Pony before, but I’m not familiar with it.

**Bruce**: The one you want to talk to is a guy named Sean Allen. He’s just a brilliant guy. So the guy who built it, and this is a guy named Sylvan Clebsch but it’s a really fascinating language because they built this C like language in terms of performance with typing. That’s turned up to 11 so really, really extreme typing, and they bake into the language this concept of reference capabilities, which are part of the types. And a reference capability won’t let a program compile if there are any concurrency type conflicts in there.

**Adam**: Oh, it sounds a little bit like Rust, I guess.

**Bruce**: Yeah. But more like a 100% safe on the concurrent level. So Rust solves it for a narrow window of the system, and it’s very much cooperative. Right. And with Pony, if anything is broken in there from a type perspective, it won’t compile. So you spend a lot of time fighting the type system, but once you beat the type system into submission, your program works and it will work.

I like language creators that try to think of language creation from a completely different perspective. That one’s interesting because it’s like, what if we had the performance of C, which is copyable. And one of the problems with the Elixir language is that you can’t do high density and place computation because everything is immutable.

So with Pony, everything is mutable as it is with C, and there are just type roles that enforce concurrency safety. It’s kind of cool. And to see that applied in the places where they did like financial systems.

## **Engaging Your Curiosity**

**Adam**: I feel like this might just be my own feelings. There’s always a danger when I learn something new that I want to use it a lot in places that maybe it doesn’t fit.

**Bruce**: Oh, that’s terrible. When you really engage that curiosity and get so hooked on something that looks interesting enough to actually jump into your bag of tricks, it sounds like a bad thing.

**Adam**: Yeah, I guess. I don’t know.

**Bruce**: So let me say it this way. If you learn like you’re a Scala developer, you like currying. When I think in terms of currying, even when I’m building frameworks in Elixir, there are problems that I will carve up that way.  Having been exposed to Scala and languages like it that effectively curry. And Idris, it was another one.

There are languages, so there’s a man at our conference. We had a back and forth on a podcast. They’re called Elixir Outlaws, I think, and he was talking about embracing the joy of programming. And one of the things he likes to do is code games. And I mean, board games, not like Tetris.

**Adam**: ahh 

**Bruce**: He loves to code this program called the longest or this problem called The Longest Road and Settlers of Catan, which is a common board game.

And that’s a Prolog problem. I told him so, and I said that it’s really interesting that you struggle with that problem in Ruby. But you were excited about solving that problem in Elixir because the guy who created Erlang loved the Prolog. Which is the ideal language for that problem. And that’s why your solution gave you so much joy. The language and the genealogy of Elixir had Prolog.

And that kind of led to the four comprehensions, which were kind of created by Prolog’s unification. So, learning languages changes the way it provides tools in the back. It doesn’t necessarily mean providing something you use every day, but it gives you tools in your toolkit.

## **Enliven Yourself and Your Career**

**Adam**: It strikes me that maybe you’re a perennial early adopter. You’re a very curious person and you hit Java on the upswing and then you hit Ruby

**Bruce**: Yeah. And get some advantages out of that. Some disadvantages too. Right. So I made some mistakes at icanmakeitbetter. I can tell you about sometime. I adopted some stuff that was a little early and we were okay.  Mostly we were okay because we were building on such high leverage  technologies because we were willing to pick our eyes up and we were willing to say, okay, what can I build with a small number of very good developers,

 **Adam**:   What can be built with a small number of very good developers. I feel like everything good was built that way at some point, you know, around 2007 I got the book programming Erlang that Joe Armstrong wrote that we’ve been talking about and it was just so much fun, and I was always telling all my coworkers that we should be using Erlang for things, which we, which we never did.

Which kind of gets to Bruce’s point about how sometimes just learning things and exploring your curiosity is just a way to like enliven yourself and your career. Just to bring some of the joy back to it.

I think it’s a great message and I recommend people check out Bruce’s talk called [Joy](https://www.youtube.com/watch?v=rDLq9hFRWBw).

Before I let Bruce go, I wanted to check in with him on whether he agrees with me that people should be spending more time doing this. Just playing with weird technology just for the sake of it.

**Adam**: So if everybody has followed your path and learned a number of languages, how is the world different?

**Bruce**: I would say that there’s less fear. I say that there are, just like when you visit other places, when you learn other languages, the world gets smaller. We all know people who treat our favorite database model as a religious platform or our favorite framework as a religious framework. When you’ve seen a few, maybe not so much. We talk about things in terms of their strengths and weaknesses. We’re more able to adapt new things and programmers are happier and healthier.

**Adam**: Sounds like a good world.

**Bruce**: I like it. 

**Adam**: So this has been great. Bruce

**Bruce**: Yeah. For me too. Thanks for the invitation. I really, really appreciate it. I saw DHH’s talk and I really appreciate your interviewing style. You’re really good at this.

**Adam**: Oh, thanks. I try, I don’t know.

**Adam**: That was the show. Sorry, I got it out a bit late. I did actually reach out to Sean Allen who Bruce introduced me to, and so there should be a super interesting interview with him coming soon. Stay subscribed to the podcast if you want to hear that. It seems like Bruce might be a great resource for me, able to introduce me to all kinds of interesting people.

Until next time, thank you so much for listening.
