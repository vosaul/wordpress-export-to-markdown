---
title: "Don and Adam discuss Folds Transcript"
date: "2020-02-15"
---

Today we try a different format. Adam invites his neighbour, Don McKay, over to ask him questions. An interesting discussion on recursion, corecursion and the naming of the podcast unfolds.

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/13165580/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

“Imagine that the podcast is some sort of function. It takes into it my interests. I was interested in whatever, a Scala and rust and types and functional programs. So it takes in this list and then it has the step function, which is basically me talking to people where I just pulled down one of these interests, find somebody and talk to them, and I produced an episode.

If you think back to the type of the unfold, it takes in like a single thing. In this case, it’s a list of my interests and then it just keeps on producing elements until it’s done right. Which are the various episodes and it will probably never end because there must be a bug in the algorithm where like new things keep getting added to the interest collection.”

“John was saying, we conclude that since modularity is the key to successful programming, dah, dah, dah, dah, dah. I think what he means by modularity is okay, we write our fold and it’s like three lines long.  Once that exists somewhere, we don’t have to have that base case all over our code. We ended up programming a higher declarative level. The other reason is just I really like clean abstractions. There’s more to learn but once you do, you’re able to kind of have this language where you can talk about these things at a higher level”

### Transcript

**This is a machine translated transcript. Podcast page for [this episode is here](https://corecursive.com/046-don-and-adam-folds/)**

**Narrator:** This is co recursive. Today we change up the format a little bit. My neighbour, Don is a software engineer. He was over last Friday for coffee. You know, we had some super interesting conversations. I thought this would be a great fit for the podcast. So today he's back for coffee and he has some questions.

And we recorded the whole thing. I live in a fairly generic suburban house. Don lives a street or two over. He drove over because of the super cold Canadian winter. We set up in my dining room with a couple of microphones and hit record

**Adam:** Ready to podcast?

**Don:** Yep

**Adam:** All right. Let me call it at the beginning. All right,

**Don:** so first question, what is machine learning?

**Adam:** So I do not know. I know that some machines learn and that's good, I think.

**Don:** Yeah. I mean, according to what movie you're watching.

**Adam:** Yeah. I don't know anything about machine learning. So hopefully you brought some other questions.

**Don:** Um,

**Narrator:** as much as it might be fun to hear me Bumble and stumble through machine learning, I'm just going to skip forward to later in our conversation where I get to a more fun question for me to answer, which is, what is corecursion and why is the podcast called corecursive?

**Adam:** What do you think are recursion is?

**Don:** Recursion is a way to harness the power. Of repetition to get what you need. It's a way to kind of iterate over some sort of of data until you get your own common goal.

**Adam:** Yeah, I think it's a really good answer. The joke, recursion answer is like the dictionary definition where it's like recursion, see recursion and kind of loop.

That's actually not,

**Don:** that's a bad function though. I mean, come on, because that doesn't end, right? Like,

**Adam:** yeah. So let's say you want to add up a list. So we're going to calculate the sum of a list of integers. So. And see, we might have a while loop, we'll kind of have some variable, and then we'll go through the loop and we'll keep adding our element from the list to that kind of mutating that state.

And then at the end, we return that as their sum. The recursive way we have like a function called some and then how it's going to work. Is this going to take the first element of the list, the head of the list, and it's going to add that to the, some of the rest of the list, and the way I'm describing it is kind of the way your implementation works.

So you take off the first element and then you add it. To the, some of the rest of it so that some is actually recalling itself, right? So if you add one, two, three, you end up with like one plus two three, which becomes one plus two plus three and you get six that is recursion, right? That's like your basic simple recursion.

Where do we go from there? Another thing you could do is like multiply, right? So if you have something called product, it takes a list of integers and it calculates the product. So we'll do the same thing. The product of the list is the first element of the list, times the product of the rest of the list, and you kind of have the same structure where you're always like taking off the first element.

And then applying something, et cetera. Right? Right, right. And then you kind of need a base case for both of these to exit. For ad, you can say like, Oh, if my list is empty, then I will return zero. So the empty list says the sum of zero

**Don:** might mess up your product though for your product

**Adam:** function. So the interesting, great transition for product, you obviously can't use zero because you hit the empty list, multiply everything times zero.

You got zero. Right? Right. So you need to use one for product, which actually forms a Monoid. That might be a topic for another time.

**Don:** I'm taking a way off, way off the rails here.

**Adam:** We'll also like, I think we're constantly in danger of me just saying things that are incorrect, but so if you think of these two definitions, we have the product and the sum.

Both of them kind of have the same structure, so they have like, okay, here's what we do for the empty case. And then for the non empty case, we kind of have some sort of looping call. Right, right. And so there was this guy named John Hughes, not the John Hughes who made like home alone.

**Don:** Oh, okay. I thought this was going in a different

**Adam:** direction.

But yeah, John Hughes is computer scientists. He wrote this paper called why functional programming matters in 1990 and actually here, I'll pull up the paper here. I'm going to put you on the spot. It's the abstract. Of John's Paper.

**Don:** As a software becomes more and more complex, it is more and more important to structure it well.

Well structured software is easy to write and to debug and provides a collection of modules that can be reused to reduce future programming costs. In this paper, we will show that two features, functional languages in particular, higher order functions and lazy evaluation can contribute significantly to modularity.

We conclude that since modularity is the key to successful programming, functional programming offers important advantages for software development.

**Adam:** This paper is great, but you could find a free online and it just goes through some basic stuff about writing recursive functions. The thing you'll notice about these two that we described as kind of the habits, the base case, and then the second case, what John shows in his paper is like, Oh, Hey, in a powerful programming language with higher order functions where functions could take functions, you can just.

Pull that out, we can take away that logic, put it in a common commonplace, and that gives us the ability to handle this form of recursion all the time using just something built into the standard library.

**Don:** Right. So a functional approach using recursion would enable us to kind of like take that piece of looping code in anywhere you need to do that is now in a a function somewhere.

Is that what you're talking about?

**Adam:** What John is saying? Is, Hey, I made this function called fold. Fold. Does this work for you? Fold takes in two things, right? The first thing that it takes in is your base case. What do you do when you hit your empty list? The second case that you have is just the working case.

So, and my sum function, instead of being this calling itself, I can just say like list dot fold. Now, from my base case, I want to give it one. And then for my function, I just give it the addition sign. So that's just saying, Hey, fold over my list and kind of put plus signs between each camo. I imagine it like visually, like if I have this like one comma, two comma, three folds going to like take up those commas.

And just put in plus signs. Does that make sense?

**Don:** Yeah, it makes sense to me. Yeah.

**Adam:** The previous part we were talking about, I would call that manual recursion. I'm manually calling myself,

**Don:** right? Yeah.

**Adam:** Often when you see manual recursion, you can like replace it with a fold. So instead of having to call yourself, you can just say, Oh, maybe a fold should go here.

And I think that's cool. So this concept,

**Don:** it's like folding. Steel. You just,

**Adam:** you keep

**Don:** pulling the steel right, to make it stronger. I don't know. I'm reaching for now what you hear

**Adam:** the, yeah, like where does the name folds come from? Yeah. So interestingly, if you think of the structure of the fold, these examples we're talking about, we're starting with the list of something and then at the end we're getting like a single value, right?

Right. We're sort of like taking each value. And folding them all together into each other. So that's kind of how I think about it. But a lot of languages have folds because they're super useful. So Scala has like fold left and fold, right? Basically, that's just which direction you start from. It also has just a fold.

It also has something called reduce, which is the same as fold, except you don't apply your base case. Haskell has foldL and fold iron that's left and right. JavaScript and Java and Python all have reduced, and it actually to your question, right, I think reduces maybe even a little bit more descriptive of how you were thinking about

**Don:** it.

Yeah. If you think about, if you think about reducing the context compared to just the regular fold.

**Adam:** Yeah, so Ruby calls it inject, which is a weird name, and I don't know why, but I'm thinking maybe it has to do with what I was describing where it's like. If you have this one comma two comma three and it's like, Oh, inject, inject

**Don:** another.

**Adam:** Yeah. And a thing between all of these to me that,

**Don:** I don't know the word inject means a lot of different things to me.

**Adam:** Yeah. Yeah. So scala's got fold, Haskell, fold, JavaScript, Java. Python. They all have reduce, if you want to sound really smart. So there's a category theoretic term for this. It's called a catamorphism.

**Don:** Oh, okay. I'll add that to my lexicon.

**Adam:** So less commonly used, right. That would be a really long function call to like list dot catamorphism plus. Okay, so that's fold, right? We were trying, I guess you asked me what corecursion is. I'll get there, I promise. Yeah. So that's a fold. We're taking like some collection of things and we're kind of like reducing it.

We're folding it down. Right? So here's the different recursive thing. Have you ever worked in a retail environment?

**Don:** I have worked. In a retail environment though this claimer it was very limited. I worked in a computer store for a high school co-op and I had to work the till among other things and fixing computers and stocking shelves and things like that.

**Adam:** Nice. So you're at the computer store. Somebody comes in, they buy something, you know, they give you $20 and their changes like a dollar 57 how do you make a change? I guess.

**Don:** Well, I mean, how I did it is I put it into the tail. Right. And it was calculated and figured it out.

**Adam:** But then how do you decide like what dollars and coins to give them?

Oh, I see.

**Don:** Yeah. So the tray comes out. Yeah. And they're like, what do you, what do you grab?

**Adam:** Yeah, exactly.

**Don:** Well, first you would grab a dollar, right? Because that's the largest denomination of what you owe them. And then I would grab two quarters and a nickel, and because we still have pennies back when I worked retail.

I would give them too many

**Adam:** nights. You could give them change by giving them just 157 panties,

**Don:** but you, I mean, I think you would be fired.

**Adam:** Yeah. This is going somewhere. I promise you can express this like as an algorithm, right? I'm going to have a function called make change. I'm going to pass into it 157 four.

You know, a dollar and 57 cents express a pennies, and then I want it to return the change that it should hand out. Right in a C program. I'm just going to loop while there's still change left to give, find the largest denomination and then return that and keep while looping, subtracting away as we return it.

We can change this into like a recursive function. Our base cases, if somebody calls the function, I would like change for $0 million and you're like, okay, here you go. Yeah. Well you actually do, and your little function is you just returned an empty list. So that's like your base case. Yeah. It stands for get out of my store.

Oh God. I think. I may never make it through the explanation, but besides the base case, if it's more than 0 million cents, then you just look at your denominations, right? And you say, okay, we have one that's a hundred for a hundred pennies, and that's less than the amount owed. So I return a hundred plus I return the change for whatever's left.

So that's my recursive call. I'm saying I returned the first amount, and as long as there's still change to give, I just called the function again. The first loop will return a dollar second loop will return a quarter. And then a quarter and then a nickel, and then two pennies.

**Don:** It's like you're continuously refactoring what you're owing them.

**Adam:** yeah. This is recursion again, like we're calling ourselves to get work done, but if you think about it, it has a different structure. Before what we were doing is taking a list of the elements. And we were reducing them to a single one. We're here, we're kind of doing the opposite. We're being given a single value, and what we're returning is the list.

So if I give you one 57 turn a list, that's like 1205205511 or something. Right? I

**Don:** guess in my brain I went to like, I'm reducing it until I don't owe you any more money.

**Adam:** Yeah. Yeah, there is a reduction and you have that remainder and the remainder keeps carrying on until it's zero. But like from the outside caller

**Don:** you're creating, I see where you're going with

**Adam:** that.

It's exactly the same, except it's the opposite, if that, if that makes any sense. So earlier I said, Hey, you can use this fold. So you never have to manually do this call where you're calling itself. Well. You can't actually make this change thing by sticking it into fold, because the fold is always working down, taking a list and working down to a single value.

Right?

**Don:** Right. So we need to have multiple values at the end of this.

**Adam:** Yeah. And we're going to start with the single value. Instead of like having this list and taking the first element, like we're starting with a single value and traveling the remainder down. So this is called corecursion.

**Don:** Okay, I see you finally got down to answering the question.

**Adam:** I got it. I got there, I got that. So this is called corecursion and. The reason that they use the word co comes, I think from category theory because co is used to indicate that it's the opposite from my

**Don:** like cosin sign?

**Adam:** Yeah, exactly. He likes sign co-sign. So recursion is taking these values and reducing them down and the Co is taking a single value in producing some, it's the reverse direction at the type level co recursion. So we're getting someplace you can do the same trick, right? The fold trick is we don't need to manually do this call. Let's just make something. We'll put it in our standard library. This generalization of coercion is called unfold.

**Don:** It makes sense. I mean like naming things is one of the hardest things in programming, but I think they nailed it. What I would like to know though is how many other candidates there were for the name of that function before they were like, you know, the first guy came in and said, well, unfold and, well, I don't know, maybe, and there was probably like a three hour meeting about the alternatives.

**Adam:** Yeah, yeah. Somebody from Ruby, like proposed

**Don:** object. I don't think that's a word, but

**Adam:** yeah, the fold is called a catamorphism. The term for a unfold for a corecursive function is called an Anamorphism. If you look this up and Wikepedia, so it says in computer programming and Anamorphism is a function that generates a sequence by repeated application of the function to the previous result.

I think you can picture how the change-making you apply it, and then with what's left, you apply it and with what

**Don:** you have, like you have like a make change and you just apply it and then it goes through. It comes back with the remainder, and then you apply it to say make change again. And you just keep making change until there's no more change to make.

**Adam:** Yeah, exactly. Right. What did I explain so far? Why don't you give me the summary? Let's see.

**Don:** See if I've been listening. Is this a best?

**Adam:** This is done.

**Don:** All right, so what we have covered so far is the fact that corecursion is the opposite to recursion, where you will start with a single value and end up with multiple values.

Whereas in recursion, you will start with multiple values and reduce them down to one. And then we've just went into polymorphism and catamorphism and I think that's where you left off is you explained, and a catamorphism is where you take a function and apply it repeatedly until you get your rezone.

**Adam:** I think it's pretty close.

So yeah, the anamorphism is just another way. It's just, it's just the unfold. It's just another term for it. And a term for fold is a catamorphism. So this topic is like super deep

**Don:** beyond the scope of one podcast.

**Adam:** Yeah. So it's funny, I was on this podcast called programmer down. I think it was super fun.

But yeah, their first question was like, is your podcast about recursion? And I mean. I guess that could be possible. Is

**Don:** that what you're doing? This podcast is like he went on to programmer throw down and then you came and you're like, well, I have to do

**Adam:** now. Yeah.

**Don:** I have to do one about, because I've been made a fool of on this other MCASTs.

**Adam:** Exactly. Exactly. So it is a deep topic. I couldn't pull off making a whole podcast series out of it, but maybe somebody could. And then there's other things besides catamorphism and anamorphic seems like it goes deep. There's like combining them and it turns out that like a lot of complicated things can be expressed in terms of these topics.

**Don:** So yeah, I guess going back to, I like to relate everything to practical applications, so I mean in day to day work. I've done this a lot when I've worked in C-sharp. I haven't worked in C sharp in a very long time, probably five years or six years or something. But when I did four loops where kind of like what you did, right, like if you had to loop over a collection of something, you just did a four loop and I guess we kind of stayed away from recursion.

It was like a mysterious. Monster, right? Where you only hear about the bad things, right? You'd hear horror stories about a recursive function that went off the rails and had like a memory leak or looped infinitely and destroyed something. So why would I use recursion and over the, what did you call it, the imperialist.

**Adam:** In theory, this approach, I like

**Don:** most approach,

**Adam:** I call the imperative

**Don:** list. Yeah. Yeah. So the imperative reproach, I think it's mainly a lot of a lot of people are comfortable with.

**Adam:** Yeah.

**Don:** And these more advanced topics are kind of definitely from my perspective, are interesting to learn about because I'm always looking to improve myself.

**Adam:** Yeah. I mean, I want to unpack some of that. Um, so I like this idea. They're like a four loop is like, Oh, that's a simple on that can understand it, but like recursion is this monster. They can let it run out of control.

**Don:** When I was in college, it was like I was a new and you know, just learning all this stuff for the first time and recursion is hard to wrap your head around if you're like a programming student that's just like walking in and being like, computers.

I like them. I want to write programs. And your first thing is a recursive function. It's gonna throw you a little bit right where. It's more convenient to be able to see everything it's doing at face value in like a a four loop, you can see it's easier to follow, right? Whereas in recursive, you have to recursively process it in your brain.

And I think that is hard for different types of people. Right?

**Adam:** So, yeah, so I think it's totally valid. Right. Earlier when I was describing how some works, it's actually kind of declarative, the recursive approach. Like if I try to describe the code for doing the kind of. Imperative for each. Right? I'm like, okay, I'm going to make a VAR.

That's like sum equals zero and then for each and then dah, dah, dah, dah. There's just a lot going on there.

**Don:** It's very verbose.

**Adam:** Yeah. It's very verbose and it has all these details that don't seem entirely relevant, right? Like why do I even care what that variable at the beginning is called that I have to like mutate and what if I don't know like something else.

Changes it or, but like the fold, some definition, it take a list and fold over it, you know, adding the elements together. When I describe it that way, that's like almost what the code will be, right? If I use the reduce, which you like better, it'll be like lists dot. Reduce plus. You can just see that and think like, okay, in my head.

All those commas become pluses. I think it makes sense to sometimes trace it through in your head like this, cause this caused this, but you can also just think about it definitionally the function product. We take the first element of the list and we multiply that times the product of the rest of the list.

I think once you get used to that way of kind of declaratively understanding things, it's really nice. Once you understand kind of what fold means. Then when you see the code, you're like, Oh, that's easy.

**Don:** Exactly. Yeah. I think that's the word I was looking for is like it's a pattern and a lot of the times if you haven't been exposed to the pattern in the past, it can seem mysterious.

**Adam:** Yeah, totally.

**Don:** So a lot of these methods are kind of like a, they're very ambiguous to somebody who hasn't. Seeing the pattern before, whereas if it's a four loop, right?

**Adam:** Yeah.

**Don:** Everyone's seen that. You've seen that from the first day of like taking programming courses. Yeah.

**Adam:** You know, and if we go back to what John was saying, we conclude that since modularity is the key to successful programming, dah, dah, dah, dah, dah, and like, I think what he means by modularity, right?

Is okay, we write our fold. It's like three lines long or something and it has that standard. Here's my base case. Here's my other thing. Once that exists somewhere, we don't have to have that base case all over our code. W we ended up programming at kind of like a higher declarative level, like you do Skella whenever I have this kind of like pattern matching and I'm like case none and then case some, I should just use folds for that.

The other reason is just I really like clean abstractions. There's more to learn, like you have to learn what a fold is and want to unfold. Unfolded. But once you do, you're able to kind of have this language where you can talk about these things. Let's take it beyond lists. Let's talk about a tree. So let's say we write a four loop that traverses a tree.

You have elements, and they each have children. You can write something that kind of traverses it. The kind of recursively walks through each element and prints them out or something, or, or adds them up, right? And then you can do the same thing instead of having to have some complex. Code to add up all the elements in a tree.

You just do like tree dot fold plus treat up, fold product and get the same thing. So once you have this obstruction, you can just talk about these things. Like we don't work together now, but if we did and we jumped on a zoom call and you're like, I'm trying to figure out how to multiply all the elements in the tree.

I could say like, Oh, just fold over it with the, maybe this isn't an actual question that comes up.

**Don:** I mean, probably not, but I think we understand where you're going with

**Adam:** it. I've had like several times where I just have some really ugly code. There's just like some complicated logic that I'm working on.

It has a bunch of cases and it just ends up seeming super complicated. And then like you kind of look at it, and maybe this is a fold, or maybe this is a map and there's these higher order functions. Maybe this is a flat map and you start to pull it apart. And I've had this happen where you start with this big gnarly thing, you start reducing it, it gets simpler and simpler, and then it ends up just being like, oof.

And instead of having my own function, I just call this built in, but I raised the pull request on some changes I want to make to something. And then Adrian, who's on my team and really has deep kind of functional programming knowledge. He's like, Oh, it looks good, but there's like a couple of nitpicks I want to make.

And then he's like, Oh, you could change this to a fold. And like this could be a flat map, but. Basically, he would be able to point out places where the logic that I was doing could be abstracted into some of these higher order components. I mean, what actually happens is I get kind of grumpy and I'm like, Oh, I don't want to change all this, but I do.

And I learned something and I learned this new concept. And then as a team, we have these higher order concepts to talk about.

**Don:** I think like all programmers kind of like enjoy that a little bit. I dunno if it's something that's like common to have the type of people attracted to our profession, but there's something about taking through factoring, right?

There's something about taking something that, well, it works. You need to see if there's a better way to do it and that like need or drive to improve the existing code that while it may work, you just need to see if it can be better. Yeah. And I find when I was first getting into Skalla from C-sharp, that's something that I was constantly doing because I was, well, Skalla will work.

Like you could apply concepts and how you program in C sharp and you can apply them directly in discount line. It'll work, but you're not familiar with any of those higher order functions. And you look at code after you've learned some of them and you come back, you're like, Oh, I can change this whole thing and reduce it down to like maybe even a few lines where it used to be like, you know, dozen or something.

Right. And.

**Adam:** I have a strong opinion that this is useful pragmatic thing to do, but also I just really like it.

**Don:** But if you want to give Adam a present, just give him some gnarly code and send it to them and be like, can you clean this up? Yeah, that would be a present for you.

**Adam:** Yeah, right. Don't actually do that.

No, maybe. But if you think of somebody learning functional programming and they write something as like a while loop, and then like the next step, maybe they're like, Oh, I can do this without mutating this variable that I'm adding into by doing like a recursive function. And it'd be like, well, I can use a fold.

Right? So now I don't even have to write the recursion myself. It just becomes this like one-liner when you get down to this fold. The folds going to work. It's being used in other places. It's not broken. Right. So like,

**Don:** I mean, like that's the advantage of, of using some builtin functions to that. The languages, you know, that they'll probably work.

**Adam:** Yeah. We had this other example at work. I'm making a request to this web server and it's going to return to me large amounts of binary. A hundred megabytes or something, maybe more. And sometimes for certain servers that we were interacting with, it would start sending binary and then partway through sending, the connection would die.

So it would send you like 10 megabytes and it would die. Somebody quick hacked in a fix. The servers like underload or the other server has something where it just shuts down. If it kills connections that are open for too long, who knows? But. We have to deal with this. We need to get this data somehow. So there's range headers.

When you make a request, you can actually say in the header, give me from this offset to this offset in the data. This is how it's kind of like paging. Yeah. It's also how like YouTube works. Like if you skip to the middle of the video, it just starts asking for data from that point. Right? Right. So we get like our 10 megs and then something dies.

Then we have some complicated retry logic that says, okay, how far did we get. Well, let's ask for more and then that'll die and we'll ask for more. I'm going to keep

**Don:** repeating, I think, I think a lot of modern implementations of that kind of method, you can see in almost anything that's streaming, right?

**Adam:** Yeah, totally. We had this kind of gnarly code. To deal with that, and then somebody, let's just say it was me, but realize that this is unfold. What's happening is you have this function that takes in this request, and it's either going to return like a hundred megabytes or if something dies, it's going to have to keep requesting.

It'll get the first 10. And then, Oh, let me request the next 10 and then let me request the next 10 until, it's kind of like your change remainder case until we've actually gotten everything that it said was the length of the document. Well, now instead of our like wild loops, then we can just turn this into an unfold and kind of carry this through.

And so this like gnarly server access and code. Got simpler. These concepts are everywhere and they're super cool to me. I mean,

**Don:** I'm so, a lot of people, I'm sure that people listening to your podcast will also have some kind of affinity.

**Adam:** Yeah. Maybe. Who knows?

**Don:** Yeah. I recently implemented something similar that I have.

Where I needed to fetch a large data set and you you can't, you just can't do it all at once. I think we all kind of run into that where the data that you're fetching is just too large for either the, the database or the processing. Like you want to be efficient, so you page it, you take it chunks at a time.

So you just stream it in and chunks. I did it with recursion, those, well maybe I'll go back and see if I could do it with a full.

**Adam:** Yeah, yeah. With an unfold unfold. Yeah. If you were going to grab the results of some page and it only showed 10 at a time, and then you had to go to the next page, you can write an unfold where it's like grabbed the first page and then if it has a next link, then call with that and you keep on calling until there's no next and there's no next link.

So the next is your remainder from the change example. It's another example of a, an unfold. Happens all the time, man, I don't. So there's a guy that I had on the podcast, Gabe Gonzales. He wrote a bunch of things about folds. Like he went really deep on it. He showed all kinds of things can be written in terms of folds.

Once you understand the definition of these terms, you're able to write some really. Concise code,

**Don:** right? It's all of these languages share some of these operations, they just call them different things because when we're executing systems, we're all facing the same problems, right? We're all coming to the same solutions, just in difference in tax.

**Adam:** Do you know that? Like what code golf is.

**Don:** No, but seeing how I don't like golf. I don't know. I would

**Adam:** like the golf aspect of it is you're trying to do it in as few characters as possible.

**Don:** I feel like I might've done something similar or using some of the other types of websites I there like hacker rank or the

**Adam:** problem with code golf, like I think it's something fun that people do, but the code is, it ends up just like some horrible mess of symbols, but I think it's an enjoyable process.

What I'm talking about here, like using folds, using unfold, using. Some of these kind of FP concepts, I think it scratches the same itch cause you're like, Oh, how can I simplify this? But in the practical way, right? Like using fold is actually practical. Using some series of Pearl symbols to do a complicated thing and

**Don:** be a topic for another podcast is at what point does brevity sacrifice clarity.

**Adam:** Yeah. Right. A lot of what we're talking about here, it's actually more concise, but at what point is it, is it so concise that

**Don:** it's hard to understand?

**Adam:** Yeah, totally. I don't know the answer. I think that if you don't know the concepts, certainly if you don't understand what unfold is, even if it's shorter, you may not find it to be a more understandable solution.

**Don:** Yeah. I mean, you might have to consider the audience, so your team, for example, and all their different expertise levels. Because if you have, if you have some people that are more junior. And you're trying to get them onto things, dumping them into something that you've refactored several times until it's only a series of symbols and, and things might kind of be a little bit above there.

It might scare them. They might think that that's a monster that they want to avoid.

**Adam:** The more concise solution is more declarative. There's less saying what's going on in individual steps. There's less that can go wrong because there's just less code. The other thing I would say it is more dense, a harder to learn.

But once you learn fold, that concept does not just for that piece of code that you're learning. It's everywhere. You can build a complicated thing to solve this individual problem, or you can find this global concept. You're gonna have to learn about this global concept, but that learning you get to take.

With you.

**Don:** Yeah. You're going to encounter this a lot. Uh, when I learned it in college, they were teaching me to be more verbose. So that was more understandable. Right? And they wanted everything very like long names. They wanted everything very clear so that anybody could read it. And I think maybe that might've been more to the benefit of the

**Adam:** instructors that were TA

**Don:** reading everybody's assignments.

Right. They just wanted everything to be . Clear, but when you get into the workplace, you learn that that's not the case. And you don't necessarily want to be verbose anymore. You, you want to be clear, but you want to be concise. And that was, I think, a learning experience coming out of college for sure.

**Adam:** And you just made me think of like a pet peeve, right?

With people. Would say always use long descriptive, variable name, and you'd be like, okay, well what about that four loop where it's like four? I like, why isn't the name, Oh, I don't want to call it iterator or whatever, and like, well, we all know what the I means like, don't worry about the eye. Okay, well here we have four eye, four J four K.

well, yeah, that one's like I J K. Those are fine. G H past H like, no, don't do that.

**Don:** Then we don't understand. Yeah.

**Adam:** Then somebody explained to me that there's actually a, just like a larger rule that that always use descriptive names, mrs, which is the length of your name should correspond to the length of its scope.

Which describes all these scenarios, right? So the reason that an eye is fine in a four loop is it only exists in that little four loop. It doesn't need a long descriptive name. Its scope is very small. You're never going to be like, I have the tie here and I don't know what it means. Like, no, it's right there.

**Don:** You know what it means by the context in which in which it exists, because that scope is so small. Yeah. Yeah. Descriptiveness is actually costing you clarity.

**Adam:** Okay, so what did that explain so far? Like, hopefully you understand what unfold is now and you might understand what it is for the rest of your life, right?

**Don:** I think there's a point at which you start, at least at my age, things start leaving your brain as they enter them. So I might now know what fold and unfold do, but I forgotten something. I guarantee it. I guarantee something that I did know before we started this podcast is now gone.

**Adam:** Okay. Well, that might be a problem.

**Don:** It is. It's a constant problem,

**Adam:** but it's probably something like to do with calm components or something horrible.

**Don:** Maybe it's something that's irrelevant,

**Adam:** but I can bring this all back around to the core concept. You asked me at the beginning. What is corecursion . We got that. Why is your podcast called corecursive?

How would that,

**Don:** that's a good question. Yeah.

**Adam:** The very dumb answer is because I was reading a book explaining some of these concepts when I decided to make a podcast, and domain names are hard to find, so I just put in some concept names and came up with that. So that's kind of a throwaway answer, but an equally true answer is like.

Imagine that the podcast is some sort of function and it takes into it my interests, like when I started the podcast, right? So I was interested in whatever, a Scala and rust and types and functional programs. So it takes in this list and then it has the step function, which is basically me. Talking to people where I just pulled down one of these interests, find somebody and talk to them, and I produced an episode.

If you think back to the type of the unfold, it takes in like a single thing. In this case, it's a list of my interests and then it just keeps on producing elements until it's done right. Which is an elements for me are the various episodes and it will probably never end because there must be a bug in the algorithm where like new things keep getting added to the interest.

**Don:** I think in the, in this example, like the interest is one giant element of things that you're interested in and you keep, you keep, it's the change, right? It's the change. That you're trying to make and you just keep coming out with the denominations of currency, which is the podcast. It also sounds like you just came up with a name and then really tried to figure out what the explanation the

**Adam:** may also be true.

Yeah. Did I answer your question? I don't know. I think I just went on a long tangent. No, I

**Don:** think it did. I think I learned some things. I learned some things about full, I might actually go back and look at some of my previous code.

**Adam:** You can go back and be like. This code is all crap.

**Don:** It's crap. I could pull this.

I think anybody who's ever written code goes and looks at things they wrote three months ago and they just look at it and disgust and they're like, I can't believe I

**Adam:** wrote this. Yeah. That like, if you haven't done that or if you stop having that, then you're probably not learning and progressing. Yeah.

So this has been fun. I mean, keep bringing me your questions. I'll, I'll keep going on rants and then, Oh yeah,

**Don:** no, I have lots of questions, so,

**Adam:** okay. I forgot the most important part. So let's validate your learning. You came here and you were like, what is. . And why do you use that name in your podcast? So what's the answer?

**Don:** I think the answer is a coworker version is the, I wouldn't say so much the opposite of recursion. It's just the opposite result, right? So what goes in and what comes out is the opposite to what you would normally precursor. So if your recursion is turning one too many. The co recursion is turning many to one.

And a. Why is your podcast named coworkers? As far as I understand it, you sounded cool and you liked the idea and it wasn't taken. The domain name was available and then you thought about it and came up with a reason.

**Adam:** I think that's valid.

**Don:** I mean, that's completely. That's completely acceptable. There's nothing wrong with that.

Not every name for everything has to be a Eureka moment that somebody comes up with while they're in their kitchen or their shower or something. It's like, that's the name. Like it. It can just be like, I think that's cool. Domain's available

**Adam:** and it's very practical. Yeah, that's true. So is corecursion

**Don:** is very practical.

**Narrator:** All right. That was the episode. Thanks to Don McKay for being such a good sport. Hopefully this turned out all right, and Don and I can keep doing this. Maybe sometimes I'll even bring him questions. He is an expert in many things that I know  nothing about. Until next time, thank you so much for listening.
