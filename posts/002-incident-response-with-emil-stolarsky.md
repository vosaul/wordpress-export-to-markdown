---
title: "Incident Response with Emil Stolarsky"
date: "2020-05-31"
---

#### Preparedness and Enabling Accurate and Quick Incident Responses

An Incident Response does not end when an incident is over; it continues to provide support for a successful investigation, documentation, and historical knowledge to help improve the technical incident response process itself. 

In this episode, Emil Stolarsky goes in-depth with Incident Response and how it can teach the tech industry about responding to problems.

<iframe style="border: none;" src="//html5-player.libsyn.com/embed/episode/id/6123812/height/90/theme/custom/thumbnail/yes/direction/backward/render-playlist/no/custom-color/87A93A/" width="100%" height="90" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

“But the reality it turns out is that humans, while we might be good at solving these complex problems, we'll often forget the basics, or we'll often forget something that's easily overlooked, but it's really important to the recovery.” - Emil Stolarsky

“The only way we can fight those biases and do an effective analysis of what went wrong is by having other people point them out.” - Emil Stolarsky

“Because postmortems retrospectives are super valuable. You don't want to repeat the same mistake.” - Emil Stolarsky

### **Transcript**

**This is a machine-translated transcript. Podcast page for [this episode is here](https://corecursive.com/002-incident-response-with-emil-stolarsky-p/)**

**Adam:** Welcome to CoRecursive, where we bring you discussions with thought leaders in the world of software development. I am Adam, your host.

**Adam:** All complex systems eventually fail and software is becoming more and more complex. Incident response is preparing for and effectively recovering from these failures. Emil Stolarsky is a production engineer at Shopify where his role shares many similarities with Google's site reliability engineers, also known as SREs.

In this interview, Emil argues that the academic study of emergency management and industries such as aerospace and transportation has a lot to teach software engineers about responding to problems. You'll hear Emil argue that we need to move beyond tribal knowledge and incorporate practices such as an incident command system, rigorous use of checklists, and why we need to move beyond a move fast and break things mindset.

I think you'll enjoy this interview.

## **Four Components of Emergency Response**

**Emil:** Hi. Thanks for having me.

**Adam:** So you've given some talks about incident response. What is Incident Response?

**Emil:** Incident response is a field where we look at how systems can fail, both organizational and systems we build and how we can optimize recovery back to their normal state and everything around that so that is mitigating the system failure, that organizational and figuring out how to organize the human response component, that bringing the system back to running and then doing a retrospective and looking back at the system and seeing what lessons we can learn from the system failing and making sure that it doesn't fail the same way in the future, or if it does that we can minimize the impact it has.

**Adam:** Is an incident response made up of several pieces or steps?

**Emil:** Yes. In my research into incident response. When you're sort of looking into this field, and it's to maybe my naive surprise, I discovered there's this whole body of work where there's sort of institutes that are going and looking and these sort of the term I'll use is an emergency management and it's broken down into four components.

It's broken down into Mitigation, Preparedness, Response, and Recovery, as the four components. So mitigation systems will fail. Things will break. How do we reduce the risks and make sure we have a safe failure? An example of this is like on a construction site, you might mark off zones under the crane where people can't walk as the crane's operating because if the crane breaks for whatever reason, something can drop in that area.

For us in software, that might be something like having bulkheading or circuit breakers. Say, remote services, networking, preparedness is how we do this I think like the human component. The analogy I always think of in tech would be on-call, but you don't ever want your system to break, but you assume it will.

And figuring out organizationally who is going to be the person who comes in and gets alerted. when that breaks, that'd be preparedness. The response is actually fixing if the service is broken. You need to bring it back up and then recovery will be going and looking and doing a retro on it and recovery sort of you getting back to business as usual or operating, and if we're going back to the tech analogy, a response will be, you say switch over from a highly available database. Your first one goes down, your second one is up, so bringing into the second database which is the secondary will be the response and then the recovery will be standing up a new highly available database and having a new secondary for the database that's running.

**Adam:** So you had mentioned bulkheading. What is bulkheading?

**Emil:** Bulkheading is when you have, say, slow external service and you have a bunch of app servers calling out to it. Bulkheading is this idea that you don't want all your app servers to be waiting on a response permit where you will sort of say, have allow-only per service connections in your app link to be connected to one service.

And you assume that if that percentage goes over or if the number of connections goes over, you can assume that the latency and that service is too high. And so you'll do a quick failure and you'll just return a failed connection and the service will have to go into its own degraded state.

It comes from the idea of in shifts where you have bulkheads and ships where if you have water leaking into a particular portion of the ship, you don't, you want to isolate the damage where you can handle a, say a quarter of your shifting underwater, a quarter of your app servers being tied up in one service, but you can't handle all of them being tied up because then you have no more app capacity.

**Adam:** And so it's, it's mitigation because you're, you're mitigating a further disaster of some sort.

**Emil:** Right. You're lowering the risk of failure. So you're identifying your risks and you're saying, how can we lower the impact, if this risk manifests and we have an incident or an issue with it? And that would be mitigation.

**Adam:** Mitigation is preventing problems. You had an anecdote about how airlines or airline manufacturers tackle mitigation by tracking parts. Could you share that?

**Emil:** Right. So in my Strange Loop talk, I brought up this idea of how every single part in an airplane is tracked meticulously. It's tracked when it was first manufactured, when it was put into the aircraft, when it was last serviced, how many flights it's been on, and what sort of its operational history.

And then after a certain amount of time, mechanics will have to go and sort of inspect the part and decide whether or not it can continue flying or maybe it needs to be fixed, replaced, etc. And I was thinking, well, if this looks like in a codebase. So we often, when we design systems, we'll build up the system we'll think a lot about how the system operates, and then we'll ship it. But we don't track usage individually, say function calls. And so it'd be interesting to imagine every time you deployed code. We started tracking how many calls there were to every single function, and you said after a billion calls to this one function, you'll open an issue to go and look and to sort of examine, "Hey, did we design this properly? Is this becoming technical debt? Should we just leave it as is? Should we remove it and move to a different model? Should we be a factor?" And of course, like if you have a large enough codebase, that's unrealistic. But that idea of tracking the age of code is interesting I think.

**Adam:** I like this idea, it's interesting. So if you're tracking it by the number of calls that are happening to an in production, I guess, that's going to lead to refactoring kind of the code paths that get called the most. I could think of some alternate ways like where you could say if it's the code that these calls or is calling these changes, then maybe it should be reviewed.

**Emil:** Also, I think the age of code would be very interesting. If you had a heat map, a least recently touched code, which wouldn't be too hard to generate by looking at the commits of a codebase. It'd be interesting to see what the oldest and what's the newest parts of the codebase. And maybe like the oldest parts work the best you don't need to touch them, but having that sort of looking at code from that perspective could be very interesting rather than just like a ship and then go back and fix it when it becomes this big issue of technical debt.

**Adam:** It's like, "look at this code that hasn't been looked at in a while, it should be reviewed again."

**Emil:** And it's this, the practices of meticulously tracking parts in the airline industry came from having a series of accidents that were due to part failure and in retrospect and sort of, "Hey, we need to be constantly tracking this to know because we know that certain parts will have, will fail under these conditions or will fail after these many uses."

And I haven't seen an analogy like that, that we can use an in tech or that we're currently using in tech. So it could be an interesting approach and it could lead to some sort of different perspectives of how we prioritize maintenance work on our own codebases.

**Adam:** Should we be tracking the probability of failure across our software components?

**Emil: O**ne thing we do at Shopify today is we use resiliency matrixes excessively, and it resiliency matrix is you'll have on your Y-axis, you'll have, you'll have a grid on your Y-axis, you'll have every component and an application, and then on your X-axis, you'll have different services across the entire application architecture.

And you can track, there'll be sort of like three entries for every service. So the first one will be healthy, the second one will be degraded. And the third will be doubt or complete outage, and then you can sort of track the state of the component in the application to see how it'll react in that condition. If the database is partially down, can the applications still served something, or is it just going to return a complete 500?. If the elastic search is down, search what might be down, but you can still complete a checkout. And we've been looking at sort of trying to figure out what are the different failure scenarios and in more complex systems, say like aerospace and airlines in complex industrial processes, like in chemical plants.

They'll build diagrams out for every single individual component, and then though, attach different probabilities or risk factors -- may be that component failing. And then they'll also map out in these trees the different relationships and dependencies they have between different components. So maybe a door, a cargo door will fail if two particular bolts will fail, or maybe it'll only care if one of those bolts will fail.

And then the bolts have their own dependency of trees of like. What will cause them to fail and building out these sorts of maps of how can our systems fail? What is the chance of them failing in different scenarios is powerful. It allows us to sort of realizing, "Hey, maybe a whole large chunk of our application is dependent on this one component" and then that tells us, "Oh, we have a very high risk in this component, all our best effort, or it'd be best for us to sort of direct all our efforts to mitigate that one component to make sure it's a lot more resilient to failure."

**Adam:** So it helps you to kind of pinpoint, I guess like linchpins are very...

**Emil:** Exactly.

**Adam:** ..elements that could have cascading failure stories, I guess.

**Emil:** Yeah. So in the talk I talked about probabilistic risk assessment, which is sort of the overarching topic of what are the different sorts of ways you can look at a system and figure out the chances of it failing in different scenarios. And what the different components rely on each other, et cetera.

**Adam:** What was the preparedness in emergency response?

## **Preparedness in Emergency Response**

**Emil:** Preparedness is how the responders prepare, for lack of a better word, to an incident or failure. So in my talk, I talked about the incident command system. The incident command system was developed after a series of forest fires in Southern California, the response to them was mismanaged. And what ended up happening in the LA city fire department and the LA County fire department both competed and they had this sort of miscommunication and almost chaos and how they responded to the fire. And after the fire, sort of after the fire was extinguished, people went back and looked at it and they saw that these two organizations sort of not communicating together substantially exacerbated the size of the fire and the impact of it. And they went off and they developed a system organizing response to fires, and it was called the Incident Command System. And the idea behind the incident command system is that during incidents, out of just failures you'll have one person who's in charge, uh, responding to the incident, and they'll have complete or almost complete authority on how to respond to it. And they'll delegate and they'll say something like a portion of people needs to go respond to this. And that structure and placing that structure and having that structure laid out beforehand was very valuable. 

An interesting analogy for an incident commander would be a composer in an orchestra. The composer can't play every instrument individually in the orchestra as well as the musician. Yet, without the composer, we wouldn't have like the final piece or the final composition won't be as great.

And so it's this idea of somebody who's organizing the response is important. It makes that every individual component, the sum of it, much greater than the absolute sum of it.

**Adam:** Does that mean that the person who is the incident response person? What are they in charge of?

**Emil:** I'll, I can give you an example of how this works at Shopify. At Shopify we have a dedicated IMOC role. So an incident responder role, and that's an on-call rotation of production engineer. So at Shopify, our roles, we call it a production engineer. And so in addition to their normal on call, they'll sometimes go onto this other on-call instead. And what'll happen is if an incident is severe enough, the IMOC will come in and they'll be sort of.

There'll be the incident command, the incident commander. And what that means is their job is to make sure that all the on-call personnel that is necessary to mitigate the issue or to respond to it are present. They'll facilitate that, so if on-calls need to get somebody else to come online. The IMOC will go and make sure that happens.

If there's like the unlock will be the person who's in charge of tracking the incident. And so if a new responder comes online, they'll update them on the situation. They'll also be the ones who communicate with stakeholders. So in the past,  if an incident was superior enough, we, there wasn't, it was nobody's job specifically to go and update the status page or write the status based message or say inform leadership and this IMOC is the formalization of it. And it's interesting. When we first rolled this out, you sort of realized that there is implicitly this already. If you think back to times when there's an outage or a severe enough incident, there are one or two people who are managing the process.

But they're never elected. It's never, they never come in and go, I'm the one who's responding. It just sort of naturally happens with having a dedicated, I'm off role or dedicated incident commander well, you can not only sort of clarifying who's going to be doing that role but then you can also roll out appropriate training and give the best techniques. 

So one thing we have is we have an IMOC bot, which is a chat-up spot that's integrated into our main chat-ups tool that'll help coordinate the actual incident. So during incidents, we can add notes that will then later show up in our RCA docs with this, uh, the IMOC bot, we'll also send one-on-one Slack messages to certain people with checklists.

So, for example, it'll say "make sure to update the status page." It'll say "if this makes sure to lock deploys, does this look like a broken code issue? Can you roll back? It's been three hours. Do you need to swap it? Swap out your IMR sort of a world right now with somebody else." And so all this formalization is very powerful and putting a term on it and putting the idea on it, and then having dedicated people focus on that role has tremendously helped us with reducing our time to recovery.

**Adam:** IMOC, their job is to not actually address the issue, but kind of coordinate the addressing of the issue. And another thing you kind of led into there was checklists. Could you expand on the checklist?

## **The Power of Checklist**

**Emil:** So in my research around emergency management incidents, I was reading about airlines and sort of the power of checklists. And I happened upon this story of the B17  and sort of the origin of checklists and airlines. And the story goes in the ’30s the US Army/Air Force was trying to procure new bombers and all the major airline manufacturers had developed their own sort of prototypes, for this competition.

And Boeing had developed the B17. Which had all these sorts of amazing capabilities? It was more resilient to damage. You could fly farther than any of the competing prototypes. It could carry a lot more weight, and so many people were really excited about this, but it was also with that, with all those added features, it was also a much more complex plan, and they had brought all these prototypes out.

To a test airfield out in Seattle and on the second test flight for the B17 just before take-off, the airplane crashed. And during the investigation they had realized there was a pilot error. There's a particular valve that has to be open just before takeoff and during takeoff, but immediately after it has to be closed.

And the two pilots have forgotten to close it and in the investigation, a bunch of the pilots, the test pilots for the army went off and they started thinking like, what do we do? Because this wasn't, these weren't novice pilots. One of the pilots was the chief test pilot for the army at the time, and when they came back, they didn't introduce or roll out new more additional training.

Instead, they came back with this idea of a checklist and this was the first checklist in airlines and in aviation. The checklist was quite basic it had sort of do these say three or four steps for just before engine start or before takeoff, during takeoff, after takeoff, etc.

And the reason they rolled that out was that they had this realization that the system was so complex that you couldn't remember every single component right when you needed it in your brain at all times. They had put down the most important steps onto this list that pilots can follow and this sort of took the whole industry by storm, where now if you think of a profession that uses checklists, pilots are immediately going to jump into your head.

In a cabin checklists are built into the dashboard with the computer. They also have binders full of them, and whenever there's an incident or an issue onboard an aircraft, the first thing I probably will do is take out the checklist and start going through the steps. And when you look at more generally other industries, I've also started beginning to adopt this in the military, in medicine. And when you look at sort of the before and after of mistakes or failures or meantime to recovery with checklists. Everything gets substantially better, and it's almost, it's almost a malice not to start using a checklist, surprisingly. 

It was surprising to me because when you go and you think of a checklist for me personally, I was thinking of a checklist as something that took the thinking out of responding to an issue. If a human responds to a critical issue, why do they as critical thinker, why do I need to use a checklist? But the reality it turns out is that humans, while we might be good at solving these complex problems, we'll often forget the basics, or we'll often forget something that's easily overlooked, but it's really important to the recovery.

And the analogy I used in my talk was this idea of automating thinking. In tech, we and in programming, we automate everything that's manual and repetitive all the time because why would we redo it? But an incident response checklist, you're doing that, but for your brain, almost. So going back to the example of the IMOC bot, if you have an incident in production. Luck applies. Don't let new changes go out unless they're related to the response, but you're gonna. While it seems like a very obvious thing to do, there's going to be those situations where you, it skips your, you sort of, that thought, sort of skips your brain or whatever and you forget to lock the place and somebody deploys a new code and it exacerbates the issue.

Checklists are sort of this thing that lets us go like, okay, there's an incident of production. What do we do first? Lock deploys second, go down to the debug checklist, and you can have a second debugging checklist or whatever to sort of start figuring out, are we seeing, how did the database is looking, how is the edge network edge looking? What are our apps? Is it capacity? So on and so on. And then when you actually see that there's an issue in a particular component, you can then, that's where you want to save all your sort of thinking and time and focus all your energy on that complex problem and figuring that out because checklists can't help, can't always help with those type of problems.

**Adam:** So why, and maybe this is just a very small detail, but why do we want to lock deploys when an incident happens?

## **Why Lock Deploys When an Incident Happens**

**Emil: W**e follow that process to lock deploys just because failure happens from change and systems break when something changes because before they break, they're in a stable state. And so the idea is, is that if you lock deploys, you won't be changing anything new. So you have your current sort of you won't be introducing new changes that could change the response.

**Adam:** There's already an incident taking place. Aren't you already in a non-stable state?

**Emil:** Right, but you don't want to be introducing more changes during that. You want to figure out what change brought you to the point of incident and then mitigate that, fix it, or remove it.

**Adam:** Makes sense. So, checklists are another example of an area where other fields have things to teach us about, how to respond to outages. What can pilot communication teach us about responding to incidents?

## **Crew Resource Management**

**Emil:** Another really interesting thing that came out of my research from the other industries was Crew Resource Management.

And there was a story that I happened upon for United Airlines Flight 173 and the story was, it was a flight from JFK to Portland. And on the approach to Portland as they were lowering the landing gear, the pilot heard a thump and the gear down success light didn't turn off, so they weren't sure if their gear was actually down.

So they aborted their landing and they started circling around the airport. Try and keep out the issue and figure out what had happened. And he did that for about an hour until they decided to start an approach to land and all their engines began to burn out. They lost power and the airplane crashed just before the runway, it turned out that the airplane had run out of fuel.

When investigators went and looked at the flight recorders, they had heard how both the first pilot or the first officer and the flight engineer had warned the captain that they're running out of fuel. But the captain didn't respond or didn't acknowledge, and they had assumed that he had acknowledged or kind of heard the issue, but he just chose not to do anything about it and didn't deem it a problem.

Around this time there's a series of incidents. Where a breakdown of communication was one of the core reasons the accident had happened. Maybe there was a miscommunication between the air traffic controller or the pilots, maybe the tower and the pilots, between pilots within the cabin where one pilot might have identified an issue and brought it up to somebody else, but nobody acknowledges it or they assume that the person who brought up the issue, we'll fix it, whatever it might be. And this has led to countless, almost countless. And so what had happened, almost countless, actually, this, and what happened is the FAA, which is the agency in America that regulates Aircraft Aviation, with NASA went and did a workshop to try to figure out how to rectify these issues. And NASA came out with this idea of Crew Resource Management. It is a formalization of best practices in communicating in high-stress situations where time is almost of the essence.

Some of these things are, they use a very basic, it'll be like clearly indicating who you're talking to, specify the issue you're noticing, specify why you've, how you've noticed the issue. So maybe that gauge is broken, talk about, or mention how you plan to resolve the issue and wait for acknowledgment from the person you're talking to. Even as a reciting these, it seems so basic. It seems so obvious like, of course, I'm going to be like, “Hey, captain, I'm seeing this problem. This is why I'm seeing like..” It's, there's nothing. Nothing that's going to blow your mind. But what the airline industry noticed is that when they formalize these ideas and when they sort of train them and almost like making it second nature for anybody who's a pilot to use these techniques, the results are, you can't sort of, you can't debate the results. It works. 

When in my research I was listening to talks from pilots talking about near misses or accidents that were involved in. In every single one of them. The pilot will talk about how they use Crew Resource Management to more effectively communicate. They said they might tell their copilot to look at an issue, or they might know if one person's debugging stuff, if the other one's flying the plane. And having that really helps. And I was thinking as I was reading through this stuff about passes since I've been involved in incidents where, let's say there's maybe a major outage and a bunch of people come in and start helping, there'll be sort of three or four people who'd be like, Oh, I think this is broken, and they're four separate things.

And then one of those gets ignored or it gets lost in the noise, and then an hour later people circle around back and they realize that one of those was really the issue that was, that was what needed to be fixed in the very beginning. And you go, “okay, why did we miss it?” And it's because we don't have this same structure where sort of there's when you're going and looking at the emergency, like emergency management and other industries sometimes a lot of it are processes. 

## **Forcing an Acknowledgement is Powerful**

**Adam:** Is it the forced acknowledgment? I could see how that would be valuable. I've actually seen this happen where I think this would help him in terms of mitigation, where somebody mentions off-hand, the master database. Hard-drive is almost full, and it just kind of rolls, you know, everybody moves on. But that is, that is that kind of the piece that nobody acknowledged, like, “Oh yeah, that's something important.”

**Emil:** Right, and forcing that acknowledgment is really powerful. And it's also I've seen oftentimes where somebody that will just make a statement, but it's not directed to anyone. And so nobody will take ownership of it at that moment and directly up making a statement to somebody. Well, it could force a conversation around it.

**Adam:** So is that like how does that influence how you guys do things at Shopify?

**Emil:** So one of the things we're looking at is modifying our uncle training and talking about these ideas and talking about how. What are the best ways to communicate and sort of point out issues you're seeing, talking about how the United Airlines Flight 173 the captain not acknowledging, was that a time when the captain was above all, in charge of the aircraft and you couldn't sort of challenging them.

And with a Crew Resource Management is this idea that there might be a hierarchy in terms of managing the incident response, but you want to get rid of human fallibility and social interaction sometimes where you might be a little nervous to say something because somebody is your superior or whatnot, and it's sort of like, get rid of these ideas you're trying to fix the problem. You're all equals, how can we best do this? And I was, I was mentioning how this feels like process a bit and obvious process and in the emergency management industry, a lot of stuff sometimes just process. Like I was reading NTSB investigation manuals and the NTSB is the national transportation safety board.

It's the agency in America that is responsible for, for any transportation-related accident, figuring out what happened and then once they figure out what happened, deciding whether or not they need to either issue new regulations or a bulletin or like an issue of sort of here's the device and how to avoid these accidents in the future.

And it's an agency of 500 investigators whose job is to investigate and figure out the root cause of accidents. And when you're reading the manual since it's a government-issued manual, the first few pages are talking about expensing items and when you expense an item to make sure to keep the receipt and you're in this, it's like, “okay like this is pretty obvious I don't need to know this.” But for other stuff like calling out, calling out, people are getting, trying to like break down this formality in social settings between people is actually very beneficial. And it's like the, I think one of the reasons the tech industry has been looking more and more into this is because you have to look for these golden nuggets in the rough or that needle in the haystack where you have to work through, like can sometimes like really thick manuals, but then a few of those pieces in there is very valuable.

**Adam:** Yes. It sounds like you've, you've extracted some great nuggets with checklists, Crew Resource Management. Have you learned anything about root cause analysis from this world?

## **Root Cause Analysis**

**Emil:** So it's interesting in some regards, the tech industry is actually better at root causes or figuring out or doing, postmortems, retrospectives than other industries. So other industries have a very much operator-error focused mentality. So they'll try to figure it out who messed up. And then they'll just fire them, which I find in the tech industry, we've been a lot better off going, what happened? How do we make sure this doesn't happen again?

And it's important. Dave Zwieback is a director of engineering. I believe it's Pandora and he has a book on postmortems. It's a very interesting book where it's his idea, he gives this example of, a story, a technology sort of group in a bank and how they had an incident and somebody was fired for breaking the system and how they sort of think through and discuss it like whether they should have shipped by the operator, should they have fixed the root cause or whatever it might be. And he talks about how really what retrospectives are and post mortems are, is trying to figure out what went wrong and controlling for bias. People as humans are biased for many different reasons.

And the only way we can fight those biases and do an effective analysis of what went wrong is by having other people point them out. And so some sort of biases that you might have is attribution error or an attribution bias. Where you'll identify sort of the root cause of an incident to a single person.

**Adam:** How does bias affect in generating a root cause analysis?

**Emil:** An example would be if you think of an incident. And you build a linear timeline and this idea of a linear timeline is also partially broken. But suppose, for now, we'll go, we'll have a linear timeline. There could be a point where an operator, a programmer, operations engineer, production engineer makes a change, and the system breaks and it looks when you look at it in that sort of context or in that way. It looks like that person made that decision. They made a decision to ship broken code. They made the decision to delete the wrong database. I really think back to the adage that kid lab had a while back where an operator there had logged into the wrong database machine to do maintenance and ended up deleting the wrong database.

When you in that post mortem it's written. So and so logged in and deleted the master database or primary database. It looks like they had logged in, they knew they were on the primary database and they decided to delete it. But that's not the case, right? People think they're making the right decision up until the moment they make a mistake.

And so we have all these different biases. When we look back, it's important to try to build tooling and use different processes to control for them and to try to lower the chance of having those biases come into our decisions going forward because postmortems retrospectives are super valuable.

You don't want to repeat the same mistake. And if you can figure out what this is sort of like. Core reason or root cause that's causing multiple other issues throughout your system. That's invaluable, but it's important we get there the right way,

**Adam:** So you have to make them try and find who is at fault, but more look in terms of process or how you would change processes, right. Is that the idea?

**Emil:** For instance, at Shopify, we expose a lot of tooling around, say flushing our caching system, and an example might be, I don't believe you've ever had this issue, but suppose somebody accidentally flushes the caches without intending to. One approach in the retrospective could be. Why on earth did you flush the caching system? Do you cause issues? Suppose, but another approach could be, why was it so easy for you to flush the caching system without the intention to do it?  Why would somebody make a mistake of being on the wrong database node? Why was it sort of easy to ship broken code?

And maybe the conclusion is, is that because in order to have. “Perfect Code” or have such a test suite that like it's that particular bug could be super low. The cost of it is too high. Maybe it takes too much time to run the test suite and so the tradeoffs, we say, “okay, this is a risk we've decided to take.”

But having trust in the people in your organization is very important. And figuring out the systems around them and ensuring that they have the right tools to not cause issues is where postmortems should focus on.

**Adam:** I've seen where a way that that's handled is, is with the 5 Whys. Like “Dave deleted the database, but why?” And then you kind of is that a useful way to get to these root causes or,

## **Methods in Eliminating Biases** 

**Emil:** So that's one of the ways, and there are many ways out there and I'm still going out and like trying to categorize and each one has its own bias. So one, that's one interesting I liked the idea of was a Causal Factor Tree.

And this is one used by NASA where they'll build out a tree, all the different components involved, different events, and how different components failed, and then each of those events or components will have sort of leaves or nodes and trees under them. Then we'll talk about how they failed or have they gotten to that state and what the RCA is about?

And I like it because you get to see sort of like the reality is that like an incident very often is multiple things going on in parallel and each thing has its own independent timeline and in a Causal Factor Tree, you can sort of lay all that out. But then another thing that happens with the Causal Factor Tree is that very often when you go far back enough, you'll hit sort of an organizational component, and then that'll be at the bottom of the tree.

So why someone might be like, they weren't enough engineers to fix the technical debt, let's say in an example and so he could have like a bias in that sense. You'll never find an approach to a problem with or to a post-mortem without any biases. What you should be doing and aiming to do is looking at the different sorts of tools you can use, the biases that will come with those. And then keep an eye on making sure you don't succumb entirely to those or that you're aware of them and making sure that like you're accounting for them and your decisions and your conclusions. 

**Adam:** Once you've generated your RCA and you know, try different methods to eliminate biases from it, is there an end result or what's the goal? Well, actually, let me rephrase this whole question, should we as an industry be tracking RCAs and some sort of global cross-industry manner?

**Emil:** Okay. Yes. 1 million times yes. And in the rest of this podcast is me shouting “Yes”. Then maybe we should do that. 

## **Capitalizing on Lessons Learned**

So another story that I came across in my research and I find it very exciting, is the aviation safety reporting system. The director of the aviation safety board was giving a speech, and you talked about how. The reality is that every single airline has a huge database of all the accidents or near misses they've experienced. So, airlines are legally required to report access that has occurred but if it's a near miss, they don't have to, and he's, the director was saying where we're not capitalizing on these lessons, we're learning because only the lessons are staying silent. They're not being shared across the entire industry. And what came out of that is a data, the database was started where every pilot can submit an anonymous report of an accident that had occurred or a near miss that occurred.

And the database is managed by a neutral third party. In this case, it was NASA and anybody in the industry, even you can go and look at this and read the reports and you can see. What had happened, What was the sort of environment that had happened? And in addition, the FAA, you actually get legal immunity, I believe, for up to five or 10 years after an accident has occurred, if you submit the report. So if you submitted a report and you did something that was wrong or illegal, but you talked about it and you let other people learn lessons from that mistake. You can't be faulted for that. And that's a really exciting idea because while we have our own different flavors of systems we all build, we're all, they're all very similar.

If you take a sort of web application that's running rails, it's using MySQL as its main database, choosing elastic search for search. It's using Reddit for its job queue system. I bet there've been numerous incidents in every one of those companies that are very similar and that if the first company had talked about this mistake they made, maybe the replication setup wasn’t optimal.

Maybe a particular setting has a different sort of symptom that you don't expect as a problem until something else completely different in this architecture breaks. All those other companies wouldn't have had to pay the same price and figure out that lesson on their own. Imagine if there was a third party database or data, a database that didn't have any goals of profit, but just to better our industry where every company can submit their service disruption reports, their retrospectives, talk about the lessons they've learned, and anybody else can go and read about them.

We'll have to automize maybe some of the specifics, but the ideas are largely the most important part. You can even sort of think that something for us would be in the tech industry. This organization would then go off and be able to develop best practice guides, right?

If you go and look at all the different failure scenarios say Nginx active production, you can say this is one of the most optimal ways to run Nginx and production. Take into account all these different, very common incidents.

**Adam:** This is a great idea. I can imagine an Nginx consulting company putting out some sort of white paper where they looked through all the incidents and, you know, they're advising everybody about, you know, best practices. Why anonymous?

**Emil:** So nobody can go out and get blind, I guess. I know anonymity provides protection where we don't necessarily care who was involved in the accident. We care about what has happened because of the individual. The individual themselves can be like, you can swap out a different person and if the process and systems in place will cause people to create well, to make mistakes, then it doesn't matter who that person was.

What matters is what happened and what made that happen and what the repercussions of that work so we can go and mitigate them.

## **SRE Role and Mindset**

**Adam:** That's a great idea. You had mentioned earlier -- SRE. So that's a Google role. I believe how the SRE role influences how you guys do things at Shopify?

**Emil:** The SRE role is Google's term for it. Production Engineer is really a synonym. It adopts the SRE mindset, but the difference is largely only in the name. Okay.

**Adam:** Could you expand on that? What does the role encompass?

**Emil:** The idea is traditionally in companies there will be a developer role and an operator role or an operations engineer and developers would write the software of the service that will run in production. I know we'll throw it over a fence to the operation engineers who will deploy that service and manage it, maintain it. So if there's an outage, the operations engineers are going to be the ones who are going to try and fix the service, not the developers who wrote the code. The idea with the SRE role is, instead of having this divide, the operations engineers build the tools and systems that developers can then use to run their own software. So imagine if you had your own internal Hiroko. Developers would write their code and then he pushed to Hiroku and then they can sort of they can monitor their own application, they can figure out if the application needs more resources in a particular type. The SRE’s in an organization would build Heroku almost internally and the actual manifestation of what that looks like in reality is different. But conceptually it's very similar

**Adam:** And the value of having such a new position is?

**Emil:** You can, one way to think of it is, as your SIS service scales up, the number of machines you're managing or dealing with also grows the number of operations engineers you need as your service grows, scales linearly with that. Within the SRE type role, since the focus is on, it's, you can always think of it as developers with strong systems understanding who are automating a lot of the manual processes you would have in a traditional operations role. They'll scale logarithmically.

You need a substantially smaller organization to be able to manage a large service. And it also forces a much healthier sort of idea around interacting with our infrastructure. So there's this idea of pets vs cattle, where before if you're manually managing a system, you would treat each computer or server as a pet, you would manually fix it. You would come in and you try to figure out what the problem is. It's very like one-on-one. With the SRE model it is that you want to automate everything. You want an automated way to do all of this and so you'll treat your computers like cattle where you'll, they'll all be treated the same there won't, there won't be any special stuff like different configurations. If a computer is misbehaving, you can just wipe it and reinstall the same sort of configuration that you had and all the other computers and treat it not as an individual, but as part of a herd.

**Adam:** The difference is that a pet, you know, each pet has a name and is unique to you, where every cattle is the same?

**Emil:** An example would be if you have like cache1, cache2 to cache3, cache like that's treating them like cattle, but if you have like rails cache, page cache, whatever your each cache server is like unique and the infrastructure and is it a special and different, and that's not great for longterm manageability.

## **Move Fast and Break Things Model**

**Adam:** So I want to be conscious of your time before we go. What do you find to be the problem with the, uh, the Facebook model of old “move fast and break things”?

**Emil:** I think two things. One, in the tech industry, in the past and when we were younger, the services that we built, their impact on the people around us, and their impact on society was much smaller in scope. People's lives didn't rely on this thing called the internet. Today, when our services fail, there's a problem, the consequences can be terrifying. People can't travel, banking grounds to a halt. Our 911 response services can't work anymore, so on and so on and the list is countless. And the terrifying thing is that it's growing, it's that list is growing by the day. We're constantly modernizing and connecting all these different things that before were analog, and now they're becoming digital.

And we need to, as an industry, start to appreciate the responsibility we have to people who are technologists. And approach our service of the things we build and the systems we built. Maybe not with the extreme of managing a nuclear reactor, but there's a lot of lessons out there that we can learn to make sure that our systems are more stable and are built with that understanding of their importance of staying up and available and move fast and break thing indicates to me this old idea, it's this time before when if things broke, it's fine, and we need to move to something where we can't just let other people pay the price of our systems breaking.

**Adam:** I think that's a great thought and that's a great place to leave this with. So Emil. Thanks so much for your time, and all your great insights.

**Emil:** Thank you, I had a ton of fun.
