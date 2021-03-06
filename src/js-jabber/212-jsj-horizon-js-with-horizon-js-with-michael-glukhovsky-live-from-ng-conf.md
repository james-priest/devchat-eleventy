---
layout: layouts/post.njk
title: >
      212 JSJ Horizon.js with Horizon.js with Michael Glukhovsky: Live from ng-conf!
date: 2016-05-18 07:00:23
episode_number: 212
duration: 40:10
audio_url: https://media.devchat.tv/js-jabber/JSJ212JavaScriptJabberHorizonLive.mp3?rss=true 
podcast: js-jabber
tags: 
  - js_jabber
  - podcast
---

02:34 - Michael Glukhovsky Introduction
- [Twitter](https://twitter.com/mglukhovsky)
- [RethinkDB](https://www.rethinkdb.com/)
- [@rethinkdb](https://twitter.com/rethinkdb)
02:35 - [horizon-js](https://github.com/ging/horizon-js)04:52 - Versus Open Source [Firebase](https://www.firebase.com/)06:15 - The Security Model
- [Horizon.io](https://horizon.io/)
07:56 - The Admin Interface09:16 - RethinkDB + Horizon10:56 - Versus [Meteor](https://www.meteor.com/)13:35 - Message Format14:26 - Getting Started19:01 - Real-time21:24 - Security26:56 - The Grand Vision; Use Cases32:17 - Managing Deployment with Redundancy &nbsp;Picks
- [That Conference](https://www.thatconference.com/) (Joe)
- [AngularConnect](http://angularconnect.com/) (Joe)
- [React Rally](http://www.reactrally.com/) (Joe)
- [Soft Skills Engineering Podcast](https://itunes.apple.com/us/podcast/soft-skills-engineering/id1091341048?mt=2) (Dave)
- [May the 4th](http://www.starwars.com/news/the-history-of-may-the-4th) (Chuck)
- [The Developer Preview](http://horizon.io) (Mike)
- [The Art Spirit Paperback by Robert Henri](http://www.amazon.com/Art-Spirit-Robert-Henri/dp/8087888561) (Mike)
- [React Rally](http://www.reactrally.com/) (Jamison)
- [Uncanny Valley Podcast](https://itunes.apple.com/us/podcast/uncanny-valley-podcast-uncanny/id535761300?mt=2) &nbsp;(Jamison)
- [Kishi Boshi](http://www.kishibashi.com/) (Jamison)
- [David R. MacIver: On criticizing programming languages (without criticizing their users)](http://www.drmaciver.com/2015/12/on-criticizing-programming-languages/) (Aimee)


### Transcript

**_[This episode is sponsored by Frontend Masters. They have a terrific lineup of live courses you can attend either online or in person. They also have a terrific backlog of courses you can watch including JavaScript the Good Parts, Build Web Applications with Node.js, AngularJS In-Depth, and Advanced JavaScript. You can go check them out at FrontEndMasters.com.]_**

**_[This episode is sponsored by Hired.com. Every week on Hired, they run an auction where over a thousand tech companies in San Francisco, New York, and L.A. bid on JavaScript developers, providing them with salary and equity upfront. The average JavaScript developer gets an average of 5 to 15 introductory offers and an average salary offer of $130,000 a year. Users can either accept an offer and go right into interviewing with the company or deny them without any continuing obligations. It’s totally free for users. And when you’re hired, they also give you a $1,000 bonus as a thank you for using them. But if you use the JavaScript Jabber link, you’ll get a $2,000 bonus instead. Finally, if you’re not looking for a job and know someone who is, you can refer them to Hired and get a $1,337 bonus if they accept a job. Go sign up at Hired.com/JavaScriptJabber.]_**

**_[Let's face it. Bookkeeping is hard and it's not really what you're good at anyway. Bench.co is the online bookkeeping service that pairs you with a team of dedicated bookkeepers who use simple, elegant software to do your bookkeeping for you. Check it out and get your free trial today at Bench.co/JavaScriptJabber for 20% off today. They focus on what matters most and that's why they're there. Once again that's Bench.co/JavaScriptJabber.]_**

**_[This episode is sponsored by Rangle.io is putting on a free webinar that introduces Angular 2 components. It will be April 25th from 12 to 1pm Eastern Time. To sign up, go to JavaScriptJabber.com/Rangle. That’s ‘JavaScriptJabber.com slash R-A-N-G-L-E’.]_**

**CHUCK:&nbsp;** Welcome everybody to JavaScript Jabber. We are live at ng-conf. This week on our panel, we'll just go down the line and have everyone introduce themselves real quick and then we'll get started. Go ahead, Joe.

**JOE:&nbsp;** I'm Joe, one of the organizers of ng-conf.

**DAVE:&nbsp;** I'm Dave Smith.

**CHUCK:&nbsp;** I'm Charles Max Wood.

**MIKE:** I'm Mike Glukhovsky, one of the founders of RethinkDB.

**JAMISON:&nbsp;** I'm Jamison. I'm out of breath because I just crowd-surfed up to the stage. Sorry.

[Laughter]

**AIMEE:&nbsp;** I'm Aimee Knight.

**CHUCK:&nbsp;** Alright. So, we are talking this week about Horizon, correct?

**MIKE:&nbsp;** That's right, yeah. Horizon.

**CHUCK:&nbsp;** Do you want to give us a quick rundown for people who don't know what it is?

**MIKE:&nbsp;** Absolutely. So, it's important to first say this is a new project from the RethinkDB team. I think you guys had my co-founder Slava on JS Jabber a couple of episodes back. And just for those folks who don't know what RethinkDB is, it's an open source database that's really great for building real-time apps. It allows you to subscribe to streams on queries and it makes it much easier to build things like Google Docs or Slack, anything where lots of clients are connected and talking to each other in real-time. And so, we have a lot of users who are building with Rethink today and they're building amazing applications. And they come to us with lots of questions and problems.

And a lot of them are trying to figure out how to build a real-time app or a JavaScript app even simpler than it is today. Because right now if you want to get started, you want to build a JavaScript app, there's a lot of work just to get up and running with Angular or React or anything else you want to play with. You got to go through a whole ton of steps. You got to figure out how to build your backend. You got to figure out how to write code to be able to get data from your database or from someplace into your browser.

And so basically, Horizon is this new project and it's built on top of Rethink. It uses RethinkDB's two properties which are linear scale because you can scale out linearly nodes, you can grow clusters, and you can push real-time updates from RethinkDB. And what it is, is a complete open real-time backend, open source, that runs on your laptop or you can deploy it to the cloud. And it comes with a database, a backend, all the things you need. You can connect to it from your browser. It's a standalone server. And start writing your React or Angular app with no backend code and get from 0 to 60. And then when you're ready to start writing backend code it's a series of Node.js modules. You can then hook into your Express or Koa or Hapi stack.

And what it does is it tries to take every problem that people try to solve when building real-time apps or JavaScript apps, things like: how do I get data out? How do I authenticate users? Identity, access control, session management, all the issues that people just keep writing over and over, all the boilerplate code. And it tries to abstract it away into convenient modules that you're able to use in your app. And so, you can get started with this backend with no backend code whatsoever. Just write it straight from the browser. And then when you're ready to extend it, it's extensible. It's open source. It works with the Node.js ecosystem.

**JAMISON:&nbsp;** So, you said a lot of words. And…

**MIKE:&nbsp;** Yeah.

**DAVE:&nbsp;** That's what I was going to say. [Laughs]

**JAMISON:&nbsp;** In my head it does mean open source Firebase. Is that a fair comparison?

**MIKE:&nbsp;** It's a fair comparison. So, it feels a lot like open source Firebase. It runs on your laptop, it gives you a backend that you can connect to from your browser. But it's more than just Firebase because Firebase and other services like them, backends as a service, as developers when you have an API that limits what you can do, it limits what you can build in your app. And so, at some point people grow past the bounds of what you can do with a backend as a service. And so, because Horizon is both a complete backend server so it runs like Firebase, you can connect to it, but also it's a bunch of Node.js modules you can then extend it. And you can write custom backend code and you can take it beyond what you could do with just a backend as a service.

**JAMISON:&nbsp;** Sure.

**MIKE:&nbsp;** So, you can still access the database. You can still use any Node module you want to work with.

**JAMISON:&nbsp;** Okay. That makes sense. So, the idea is at some point Firebase might not… you want to do something weird that Firebase doesn't support.

**MIKE:&nbsp;** Right.

**JAMISON:&nbsp;** You can just plug that into the server that you control because it's, you're running it. It's Horizon. It's Node.

**MIKE:&nbsp;** That's exactly right.

**JAMISON:&nbsp;** Okay, that makes sense.

**CHUCK:&nbsp;** Now, is that extended through something like… because you're saying Node.js plugins. So, are we talking something like Express or some other framework? Or is it more along the lines of, “Oh, here's a really convenient way to write functions that do stuff in Horizon”?

**MIKE:&nbsp;** No, it's just Express. It's just plain straight JavaScript and npm modules. There's no magic about it.

**CHUCK:&nbsp;** Okay. I'm also wondering a little bit. Is there some kind of… because whenever I think about these systems, I remember CouchDB kind of did this with an HTTP interface. And now we have Firebase. And everybody solves these security issues at least and authentication issues in different ways. And some of them work really great and some of them really don't. I'm a little curious. What is the security model around something like this to keep people from taking advantage of the fact that you essentially have a database out there that anybody can touch from anywhere in the world?

**MIKE:&nbsp;** Yeah, that's a really good question. So, when people start using Rethink we had these people come on GitHub and they would open these issues and they would ask us the question like, “I'm opening this stream from the database and I'm doing it from the browser.” And the first time that people did that we were like, “Don't do that. Use the database behind a backend.” You want to make sure that you secure access to the database. After the 50<sup>th</sup> person asked us, we were like, “Well, there's something here.”

**DAVE:&nbsp;** [Laughs]

**MIKE:&nbsp;** “We've got to figure out why people are asking us this.” And that's where Horizon stemmed from. And so, you could think of Horizon as it gives you a bunch of convenient tools. But the security model is incredibly important, because that's how you control access to data from the backend. So basically, it's designed so that you can both declare security rules like similar to something like Firebase but it's much more sophisticated where you can actually do programmatic control.

And we've been building it with feedback from… we have a private developer preview right now. And there are over a thousand developers who have been building it with us in private. It's at Horizon.io. And we've gone through a ton of work iterations on what would be a really good security model? And the answer is that you need to make it really simple to be able to just declare, this role needs access to this kind of data, and then be able to extend it so that it works with your functions and can actually use it when writing programmatic code. Because at some point you're going to go past the bounds of what security rules can do.

**CHUCK:&nbsp;** Right. But what does the admin interface look like? Because I definitely, going back to CouchDB in particular, I had nightmares because your admin interface was through the same web interface that you were accessing everything else. And so, I was always worried. “Okay, how do you control this?” because somebody has an attack vector right there.

**MIKE:&nbsp;** Yeah.

**CHUCK:&nbsp;** In the web interface to get at this. So, is there some kind of backend config that you give it?

**MIKE:&nbsp;** Yes.

**CHUCK:&nbsp;** Or a list of users? Or here's the database? Or how does that all go?

**MIKE:&nbsp;** So basically, you do 'npm install horizon'. Then you start up a project. You get a couple of folders. The folders are: one folder where you drop your static files and it just runs the server off of that, then there's a set of configuration files you can declare things like security rules, that one on the backend. There also is a web UI which allows you to do things like see the number of connected clients or interact with the Horizon backend. But it's designed so that it's secured from day one. We don't build features, [by] the RethinkDB team, we never build features that are insecure. We always try to make sure that we build it in a way where you can expose it to the world and not have to worry about it.

**CHUCK:&nbsp;** Right. So, you set it up so that I can configure it and say, “I'm the admin,” and then I can actually go into this admin interface and I can add users or add roles and see all the other stuff. But that initial access is something that is controlled offline.

**MIKE:&nbsp;** Yes.

**CHUCK:&nbsp;** Okay.

**JOE:&nbsp;** So, my Rethink, existing RethinkDB skills which are impressive by the way…

[Laughter]

**MIKE:&nbsp;** Thank you, thank you.

**JOE:&nbsp;** Am I going to be able to leverage those when working with Horizon?

**MIKE:&nbsp;** Yeah, so the beauty of Horizon is that our vision is that people are running RethinkDB clusters already. A lot of people don't want to think about running a database. This is what we discovered. We started building databases and then a lot of people don't want to think about what database they pick. There are reasons to pick a different database, for example a RethinkDB if you want real-time updates. It's a good reason to use Rethink right? If you want a schema-free database, that's another reason to look at something like Mongo or Rethink because your development practices need to change. But for a lot of people, they don't want to think about it. And so, for Horizon it just gives them a whole stack. But for existing RethinkDB users, what Horizon allows you to do is use it on an existing cluster, drop it on top, and now you're able to let your JavaScript developers just start building real-time apps very quickly on top of your existing real-time dataset.

So, an example of this is there's a team at NASA that uses RethinkDB and this is one of the coolest use cases that I've heard of so far where they're actually using it to track the sensors that are used on space suits on the space station, the International Space Station, like oxygen sensors. And then they use RethinkDB to process the data in real-time for their new infrastructure. And so, for them, that team, they can drop Horizon on top and now any NASA developer who knows JavaScript can start building dashboards and start building apps on top of it. And this is really amazing because it democratizes access to real-time datasets. And it makes it so that if you're a small agency and you just want to build something quickly, you can get started. But if you're a large team with lots of datasets, lots of tools deployed, you can use something like Horizon to allow more developers to build apps more quickly

**DAVE:&nbsp;** So, I'm still struggling to really understand exactly how I would put Horizon into production. But what you're describing sounds a little bit like Meteor where it puts the server between the database and the client so you have to think less about that server piece. Is that a good comparison?

**MIKE:&nbsp;** That's an apt comparison. There's a philosophical difference in how Meteor approaches building JavaScript apps. If you step back for just a moment and you look at how people build JavaScript apps today, there are really three patterns that people follow. One is they go and they assemble stacks off of GitHub. The MEAN stack, the [free] stack. You pick JavaScript components and try to figure out how to glue it together usually using something like Webpack, something like that. The issue with that of course is that it's hard to get started. It's hard to add new tools. It's hard to figure out how to start building your app when you move past the bounds of what that basic stack gives you. The second pattern is like Firebase or some sort of backend as a service which dramatically removes all this, all the components for you so you don't have to think about it. But ultimately it will limit if you want to grow past the bounds of what you want to build.

And so Meteor, they did a really great job. Two years ago they set the bar for developer experience where they tried to organize an open source stack for how you use JavaScript. And the way they did this was to tightly couple a bunch of components, things like MongoDB and a bunch of Meteor components up the stack and say, “We're going to give you a really polished experience. It's going to be the way we described that we're going to use it. It's going to be prescriptive. And it's a walled garden that you can basically build your apps inside of. But it's going to work really well and fluidly.” And for a lot of people that works well but it doesn't really work within the bazaar of open source. It doesn't really work with the engine of open source developing new tools. And over time, there's been a lot of pressure for the Meteor stack to evolve. And because it's been so tightly coupled, it's hard for people to add new tools.

And so, in contrast Horizon, what it is, is it's designed so that it will work the open source ecosystem. It still gives you a consistent stack but it stops at the view layer. It doesn't define anything that you do in the view layer.&nbsp; So, you could build React or Angular, Cycle, Vue, straight JavaScript or whatever you want to use. And the server exposes WebSockets by default. So, you connect to the server view WebSockets. We're going to add adapters for things like GraphQL or Falcor because we make no opinions about how you get data in or out. And it's more of a purpose-built tool and a convenient set of tools that allow you to basically add open source components easily. And we've already seen people extend it in really amazing ways. So, this community has been building with us for the past couple of months. Some have just released a really lovely… it's called Lovely.js in fact.

**DAVE:&nbsp;** [Laughs]

**MIKE:&nbsp;** But it's a really lovely library that makes it…

**DAVE:&nbsp;** How apt.

**MIKE:&nbsp;** That makes it dramatically easier to work with React. And so, we expect that people will extend it in lots of really interesting ways. And they'll add as the JavaScript community keeps innovating, keeps building new things. And we're going to add it to Horizon.

**DAVE:&nbsp;** Does Horizon… well you mentioned that it uses WebSockets to communicate between server and browser. Does it also define what the message format is for those or is that up to the developer?

**MIKE:&nbsp;** So the Horizon API, it's basically a simpler version of the RethinkDB query language. The query language for RethinkDB is too powerful. It's a full programming language. You can't put that in the browser. You can't do access control in it. So, we basically designed an API by the same team. And that format is defined by us coming out of the Horizon server. But it's very easy to add adapters like I said for things like GraphQL where there is no format that would map to something that the WebSockets will use. They have their own approach towards solving these kinds of problems. And we fully expect that people, we want people to create different ways of getting data in and out of the backend. So, we don't define anything but we do give a first-class experience if you're using a Horizon API.

**AIMEE:&nbsp;** So, I have a question. So, when I was doing the bootcamp, when I got started with programming one of the very first things that we ever did was hook up Firebase to our frontend. So, do you think that Horizon is going to be as easy to get started as it would be if I was using Firebase?

**MIKE:&nbsp;** Yeah, I think it's going to be incredibly easy to get started. In fact, that's one of the big adopters we've seen. We've seen two adopters in the getting started rapid prototyping camp. Agencies which just need to ship new projects all the time. They don't want to deal with the hassle of building stacks all the time. And people who are in schools, like dev school. They're like, this is exactly what we want because we can offer our developers a consistent set of tools and practices and tell them we've made a Horizon stack. Maybe we added one or two components that will help you when you're learning. But it should help people adopt new technologies like React or Angular and not have to think about every single component across the stack, not have to deal with Webpack, not have to deal with all these intricacies.

**CHUCK:&nbsp;** Related to that, I'm wondering as you get new people involved, one of the nice things about Firebase is the setup is I go get an account. With Horizon it sounds like I have to go and actually get it. I have to install RethinkDB and install Horizon. Is that something that new people really can do without having a lot of experience with things like command line or npm or some of the other package managers like Homebrew on the Mac?

**MIKE:&nbsp;** That's a very reasonable question. So, we're going to offer a pre-built package that people would just download. Because we already distribute RethinkDB on Homebrew as a DMG so you can just install it. But more importantly we're going to have, coming out in the next couple of months we're going to have a cloud service called Horizon Cloud which will, you can run it wherever you want. You can deploy it using Kubernetes which is an amazing piece of technology or Docker, whatever you feel like doing. But we're going to offer a very simple way to just get your Horizon app up and running. So, you just type 'horizon deploy' and you have this tool that's been installed in your machine.

And so, if you're a novice developer you probably should start to learn the command line. But you don't need to have brew and npm necessarily on day one. So, we're going to allow people to just get started with a basic stack. But most developers these days, even if they're novices, have these tools. And we want to make it easy to get onboarded no matter how you get started. And with the cloud service it'd be pretty easy to basically allow people to get the app instantly within 10 seconds on the cloud.

**CHUCK:&nbsp;** Yeah. The other question that I have as far as people using it is that I've been involved with people who run bootcamps not only in JavaScript for web development but JavaScript's become, “Okay now I'm going to build a desktop app with Electron” or “I'm going to build a Windows app with WinJS” or “I'm going to build an Xbox app with WinJS” which apparently you can do.

**MIKE:&nbsp;** [Chuckles]

**CHUCK:&nbsp;** Or I'm going to build a mobile app with NativeScript. And so, there are all of these different areas that you're working in where yeah it's data access but it's not the same from one platform to the next. And your concerns change. So, is Horizon something that any of these people should be able to go, “Boom, I set it up and now I'm going to start using it for my application”?

**MIKE:&nbsp;** Yeah, so JavaScript is amazing because the community has taken it to places that I would not have expected five years ago. [Chuckles] It's amazing because if you look in the frontend we now have sophisticated tools for software architecture, things like Angular and React that think about the world using components, unidirectional data flow. These are really solid principles in software engineering. On the backend, Node is async, massively parallelized, really great for these kinds of apps. And so basically we're seeing it pop up, as you mentioned, like mobile, in Electron apps. And Horizon will be useful in all of those contexts. So, we already have people who have shipped apps to the App Store on Horizon and we expect that if you're building… the idea behind being able to build an app and share 80% to 90% of your codebase with the desktop version and the mobile version and the web version, that's a really beautiful vision of how to build software because you have common codebases. And the data stack should be common across them as well.

And so, we're adding features hopefully that will make it easier for use in a mobile context. We expect to be able to do things like push notifications and other services that, services like Parse offered before they ended. And so, we want to be able to let those developers say, “Okay, what's the next thing? And I want to be able to use all this cool technology today. I'm just going to use this common stack and build it for desktop, for mobile, for web.” And I expect we're going to see JavaScript go into even more exciting places.

**JAMISON:&nbsp;** I find myself listening to your questions differently today, Chuck. There's something about you that just makes me…

**MIKE:&nbsp;** [Laughs]

**JAMISON:&nbsp;** Want to… Chuck is wearing a Jedi robe for all the people that can't see. So…

**MIKE:&nbsp;** [Laughs]

**CHUCK:&nbsp;** These are not the libraries you are looking for.

[Chuckles]

**JAMISON:&nbsp;** That's perfect. I have a vague question that I hope becomes less vague as I ask it. In my experience I've built some apps that have a real-time component. But the whole app is not real-time. And I can't tell if that's because I'm an old man who isn't cool and with it and everything should be real-time or…

**DAVE:&nbsp;** Yeah, that's it.

**JAMISON:&nbsp;** Yeah.

**DAVE:&nbsp;** You can stop now.

**JAMISON:&nbsp;** Okay. Thanks, Dave.

[Laughter]

**JAMISON:&nbsp;** Done. Or is that a common pattern that you expect to see? Or do you expect by making the tooling better for building real-time apps that apps will migrate more towards real-time. Does that make sense?

**MIKE:&nbsp;** Makes perfect sense. So first of all, I do think as tooling improves people are just going to start to use these features more readily. But look at Angular 2. So, observables are an amazing bit of technology because they allow you to think about unbounded data streams and really deal with them with an amazing set of tools. We're a huge fan of things like observables and anything with reactive data obviously, because Rethink is all about that. And Angular 2 has observables throughout and now people are talking about them and now they're a staple. Similarly, promises took a little while for things to hit. But once the community understood why it's valuable, everyone just started using them for everything. And so, between things like observables and promises as the fundamental underpinnings of tools to work with, Horizon is all about observables. It just uses RxJS 5 and you have the ability to use all of the observable functions as well as higher-level things from Horizon. And so, I think that as these tools get democratized, people just naturally adopt them. It's the bazaar of open source. People go and grab tools you would never expect using them in ways you wouldn't expect. And then now they've become lingua franca for the web.&nbsp; Now, everyone's using JavaScript.

**DAVE:&nbsp;** What if I don't expect to have too much of a real-time need in my app? Do you think Horizon is still valuable?

**MIKE:&nbsp;** Yeah.

**DAVE:&nbsp;** Can you tell us about that use case?

**MIKE:&nbsp;** There are two modes for getting data out of the backend, at least in the default API. There's fetch and watch. And so, watch will just open unbounded stream. You write some query and because RethinkDB is running under the hood you could do really sophisticated things because the query language allows you to do things like joins or distributed operations you would normally find in a SQL database. So, all those features filter up to the Horizon frontend. And you can just get data out with fetch. And you can open a stream. It will just keep pushing you updates with watch. So, to move from one context to the other is really easy. And it keeps developers from thinking about this. They just think, “How do I expect to use this? Do I need live updates or not?” and they turn it on or off.

**DAVE:&nbsp;** So, you mentioned security which obviously is one of the main motivations for a layer like Horizon between your database and the client. When a client tries to run a watch or a fetch, how does Horizon decide whether they have access to do that?

**MIKE:&nbsp;** Yeah. So as I mentioned, there's basic configuration to establish security rules where you can basically define roles and you can do more sophisticated templating. And so, you just define, “I have this type of user and they should have access to this type of data.” And when the client connects, they say, “I am this type of user.” And they're authenticated against the backend server.

**DAVE:&nbsp;** But what if I have a multi-tenant environment where it's like not just this type of data but these records in this table are mine and those other records are some other user's. How does that work?

**MIKE:&nbsp;** Yeah, so basically people own documents and you're able to share permissions between each other.

**CHUCK:&nbsp;** So, I have one more security question. As a business person, I love the ready-made solutions. I don't have to develop them. I don't have to pay anybody to develop them and I'm not spending time on them. I just set them up and they work. But as a DevOps person and a programmer, I hate the ready-made solutions because…

**JAMISON:&nbsp;** [Laughs]

**CHUCK:&nbsp;** I have to freaking update them, right? So, anything that I have running WordPress, if a new version comes out and I don't update it that day, I'm going to get hacked. It's not quite that bad but some days it's that bad.

**DAVE:&nbsp;** I'll hack you. It's cool.

[Laughter]

**CHUCK:&nbsp;** So, the issue is you want some sort of automatic update or you have to keep tabs on what's going on with Horizon. So, what is the update cycle on that? Are you going to release on a regular basis? If there's a hot fix that I need, how am I going to know that?

**MIKE:&nbsp;** So, RethinkDB has spent a long time thinking about this because security and databases go hand-in-hand. You need to be extremely security conscious. So, we have a very aggressive release cycle. We ship security patches very quickly if they're necessary. And we have a whole process we've gone through. RethinkDB is used by some of the largest institutions in the world. One of the biggest online brokerages in the world with over 25 million users runs every day for the web and mobile apps. And they trust their security to it. And so, we've worked with them because we have enterprise customers to figure out what do you actually have to do to communicate? It's not just about the technology, it's about the communication. And so, Horizon is built by the same team. We have a similar approach. We're going to be able to post security advisories if needed. And you just update through npm if necessary.

The other nice thing is that even though Horizon and RethinkDB seem like they're separate, they could be shipped as a complete stack. So, when you have a change rather than having to figure out, “Do I have to update one of five or seven components?” there's one consistent environment. And this is really great for larger teams as well because as you said, DevOps teams are like tearing their hair out trying to figure out “What do we need to update?” There are whole products that will just scan Docker images to figure out what are the security vulnerabilities and [inaudible] to update this? So, consistency helps solve this problem for large teams.

**CHUCK:&nbsp;** Right. But is there a security mailing list I should be on? Or does it notify you somehow? Or…

**DAVE:&nbsp;** I'll let you know after I hack you. It's cool.

[Laughter]

**MIKE:&nbsp;** There isn't a security mailing list right now for Horizon, but because it's still in developer preview. But as soon as it's ready to launch we're going to ship all the things necessary for production.

**CHUCK:&nbsp;** Okay.

**JAMISON:&nbsp;** Chuck, I think you have a rosy view of what [homegrown] tools security [chuckles] is like [chuckles] if you're more worried about installed tools than… I mean, I'm going to write you an app and it will be hackable from day one instead of when an exploit comes out. So…

**CHUCK:&nbsp;** Yeah, a lot of times they are hackable from day one. But if it's a known exploit and it's a target that is rich with information that people want…

**JAMISON:&nbsp;** okay, so you're saying like Metasploit versus someone explicitly targeting you.

**CHUCK:&nbsp;** Yeah.

**JAMISON:&nbsp;** Like someone just port-scanned the internet and be like, “Oh, they're running WordPress 1. Now they're owned.”

**CHUCK:&nbsp;** Yeah. Yeah, they're running Horizon and so I'm going to see. Okay, I'm going to attack it this way and I'm going to try and get in that way. And I'm going to see if they have a weak password or this or that. There's only so much you can do. But if there's an exploit out there for an older version of Horizon, then I want to know, “Hey, go update the thing so that people can't exploit that against you.”

**MIKE:&nbsp;** So in RethinkDB we solve this problem by basically every 24 hours checking if there's an update available and then pinging you as soon as it's available. So, in your UI you see a thing drop down and saying, “You're out of date. You've got to update this.” When you start the server it's going to tell you, “This server is out of date.” Because you shouldn't be running an out-of-date database server. It's such a critical part of your infrastructure. And so, Horizon's going to have very similar facilities. We've tried to solve this problem for many years now so I'm pretty confident that we're going to come up with something that works. It's also that security is built on trust.

So, you use tools. Any tool you have that we… we download tools from npm all the time or different projects. And we just trust that their security is good. And that may not be very well placed, because [chuckles] if somebody forgets to… they leave the password in an insecure place and suddenly everyone's hacked. So, there's been a bunch of instances with cloud services where this has happened. And I would actually argue that having it be something you can self-host if you're that security conscious, putting it in a place that you care about, watch all the network activity that's happening. Open source sheds a light. Sunlight is the best disinfectant especially for security. So, it's not just that you're trusting us. It's that you're trusting that everybody in the community is also looking at it and saying, “What's wrong with this code?” And you can't do that for most cloud services. So, being open source I think actually is a huge advantage in that respect. And then having it come from us, we're a team that knows how to do this for a long time, hopefully gives people some trust that they're going to be able to have faith in it.

**JOE:&nbsp;** Chuck, if you ask another security question I'm going to fall asleep.

[Laughter]

**CHUCK:&nbsp;** I was actually going to ask Joe…

[Chuckles]

**JOE:&nbsp;** Yes?

**CHUCK:&nbsp;** We've talked a lot about how it works and what it does. We've talked about… you've managed not to scare me off.

**MIKE:&nbsp;** That's good.

[Chuckles]

**CHUCK:&nbsp;** So, the next question I have is I'm trying to catch the vision. I think we get the idea behind RethinkDB. We have the streams of data that we can push to, we can pull information out of. We can make requests to the API. But what's the grand vision? What am I specifically going to be thinking, “Oh, I want to build an app like this”? And maybe you can give us some examples of apps that have been built on Horizon.

**JAMISON:&nbsp;** To-do list.

**AIMEE:&nbsp;** [Chuckles]

**CHUCK:&nbsp;** That's right. TodoMVC [inaudible].

**JAMISON:&nbsp;** That's the world's foremost to-do list.

[Laughter]

**MIKE:&nbsp;** Always a favorite. Exactly.

**JAMISON:&nbsp;** Yeah.

**CHUCK:&nbsp;** But it's that kind of thing, right? What kind of result? If I'm thinking, “Okay, I'm going to build this kind of app” or “I'm going to solve this kind of problem” or “I see this sort of thing going on in my app” I should be thinking “Oh, Veri-… Horizon,” not Verizon.

**DAVE:&nbsp;** Verizon, that’s something else.

**CHUCK:&nbsp;** Sorry.

[Laughter]

**CHUCK:** Horizon is my solution. It is the way that I want to go.

**DAVE:&nbsp;** I think the important thing here Chuck is that this is the JavaScript community and Horizon is young. So, you should use it.

[Laughter]

**MIKE:&nbsp;** That's right. That's right.

**CHUCK:&nbsp;** That was my other question. I'm saving it.

**JOE:&nbsp;** I just want to know how many different kinds of to-do apps I can build with it. That's what I want to know.

[Laughter]

**MIKE:&nbsp;** Every flavor you can imagine. All the to-do apps.

[Laughter]

**CHUCK:&nbsp;** They're right over the horizon, Joe.

**JOE:&nbsp;** Right over the horizon.

**MIKE:&nbsp;** The puns are starting.

**CHUCK:&nbsp;** Yeah.

**JOE:&nbsp;** Yeah.

**MIKE:&nbsp;** Yeah, so to answer your questions, the easy answer is if you're building a JavaScript app right now and you don't want to deal with authentication, identity, access control, permission and session management, anything that you need to do to build an app, this is going to be an easier way to get started. It's going to be an easier way to continue to grow your app. And it's going to scale with you to millions of users. Because RethinkDB is running under the hood and RethinkDB's been battle-tested by a lot of people. And it can scale to 30-plus nodes easily. Teams have demonstrated running at a million ops per second in Amazon infrastructures without breaking a sweat. And it's really great for this kind of real-time apps. The thing is that the reason why Horizon is interesting is because it allows you to use technologies you would not otherwise know how to get started with. So, a lot of people building with newer frameworks, things like Cycle or Shasta, I think you guys were talking to the Shasta guys before…

**CHUCK:&nbsp;** Yup.

**MIKE:&nbsp;** All these projects are like, people want to get started. They don't know exactly how to get started with them. So, this makes that process easier. But fundamentally, because it's built on a real-time streaming architecture that is designed to scale to millions of users, if you're building anything with connected clients, chat, mobile, IoT, lots of connected devices talking to each other, anything where you have large amounts of data that's constantly changing and you need to be able to figure out what's happening with it, how to react in real-time, this normally, if you're starting with Rethink there's all this code to build on top of it. And Horizon takes that experience and raises it to the browser. So, it makes the process of building these kinds of app dramatically easier and democratizes the ability for people to build these kinds of real-time streaming connected apps. If you want to build Slack, if you want to build something today, that's a very hard problem. And with tools like this, it just makes it dramatically easier.

**CHUCK:&nbsp;** So, I'm going to get to my other question now, Dave.

**DAVE:&nbsp;** You have my permission.

**CHUCK:&nbsp;** I'm a fan of boring technology.

**MIKE:&nbsp;** Me too.

**CHUCK:&nbsp;** It makes my life easier because people have already proven it. They've shaken out all the bugs. They've worked out all of the ways to use it. I don't have to be that adventurous and I can pretty much count on it doing what it says it's going to do on the tin. So, this feels like something new. Rethink's been around for a few years but Horizon is a new-ish thing. So, is this something I just need to get over and try it? Or is this not for the faint of heart quite yet?

**MIKE:** That's a good question. So, Horizon is brand new. In fact, it's been in developer preview and we started building it at the beginning of this year. It turns out that JavaScript is a little bit easier to write than databases.

[Laughter]

**MIKE:&nbsp;** So, our teams are building RethinkDB and we ship a new release of Rethink every six to eight weeks. So, we have an extremely fast, rapid iteration cycle. We have a polished team that just knows how to build software incredibly well. And I say that because they are way better than I am at building software. I would not touch building the lower levels of RethinkDB. And at this point, the codebase goes from Assembly all the way to JavaScript. So Horizon, we built it very quickly. We also had a lot of huge contributions from the community. So, it's moving extremely quickly. If you're faint of heart, wait a month maybe. And by then we're going to be shipping it to the public. And you'll be able to know that it's being used by some of the best teams out there, because there are already banks and large institutions that are experimenting with it. And they're not really faint of heart about it because most of the heavy lifting is done by RethinkDB. Horizon is like a thin JavaScript layer and that's pretty easy to test and figure out what works and what doesn't.

**DAVE:&nbsp;** If I wait a month will it be legacy? If I wait a month will it be legacy? [Laughter]

**CHUCK:&nbsp;** It is [JavaScript].

**MIKE:&nbsp;** Well, it's JavaScript.

**DAVE:&nbsp;** I've been burned before.

[Laughter]

**MIKE:&nbsp;** Yeah. So, our goal is basically like the JavaScript world moves so quickly. Everyone has framework fatigue. It's really hard to figure out what to look at next because it's almost like this sporadic change of technologies. And Horizon is, it's an attempt to try to slow that down and to give you something that you can rely on that you can then add your experimental technology on top if you want to play with it.

**JOE:&nbsp;** I heard that you've already announced version 2 but it won't be out for two years.

[Laughter]

**MIKE:&nbsp;** In the past two minutes. Yeah, exactly.

**DAVE:&nbsp;** Apropos, Joe.

[Laughter]

**MIKE:&nbsp;** It's the age of npm, right? We're just shipping releases nonstop.

**DAVE:&nbsp;** So, I have an Ops question. One of the things my team has struggled with is that we want redundancy in our web app and we have backend and we have frontend. But it's hard to manage deployment when you have redundancy because you ship new code here and then it makes a request an that request ends up getting routed back to the load balancer to some server that doesn't have the new code yet. And now it's like, “Oh crap, 404,” or something like that. Does Horizon help solve that problem?

**MIKE:&nbsp;** Yeah, we plan to solve that problem. Because if you're shipping new versions of your app constantly, version 2, version 3, version 4, every two minutes, you want to be able to do rolling application upgrades. You want to be able to phase out versions of your app over time. And so basically we're building, it's a little bit hard to do in Horizon itself because that's an Ops question, not a development question. But Horizon Cloud is a service that will basically support all these things. You could do it yourself by using open source tools like Kubernetes and building a lot of custom code. But Horizon Cloud will be a very easy way to ship new versions of your code, new versions of your app, do rolling backups, all the things you need to be able to make sure that you don't have to deal with any Ops headaches.

**CHUCK:&nbsp;** Alright. Well, we need to get to pick. We have to get over before there's a speaker. But anyway, I'm really looking forward to Angularizon. And yeah, let's go ahead and get to picks.

[Laughter]

**CHUCK:&nbsp;** Joe, why don't you start us off with picks?

**JOE:&nbsp;** Well, since we're here at a conference I want to be a little conference-oriented in my picks. So, I'm going to miss out this year on That Conference which is actually the name of the conference.

**DAVE:&nbsp;** Aww. That's a tradition for you, right?

**JOE:&nbsp;** It is. It totally is. It's the first year I've missed it for three years. So, I'm really just disappointed to be missing it. So, I'm going to pick That Conference

I'm also going to pick AngularConnect which is coming up this fall with more Angular goodness in London. Awesome place to go and visit. Just, I don't want to live there. It's too rainy.

**DAVE:&nbsp;** Too rainy? [Laughs]

**JOE:&nbsp;** And finally, I want to pick React Rally which is an awesome React conference done by Jamison Dance.

**JAMISON:&nbsp;** I've been scooped.

**DAVE:&nbsp;** Our very own Jamison Dance.

**JOE:&nbsp;** I've been duped.

[Chuckles]

**JOE:&nbsp;** I stole some thunder here. I've been to React Conference, React Conf. And I've been to React Rally. And I won't publicly state which one I enjoyed more.

**DAVE:&nbsp;** Oh.

[Laughter]

**JOE:&nbsp;** I'm going to hint very subtly that React Rally is awesome, coming up in August.

**JAMISON:&nbsp;** August, yup. August 25<sup>th</sup> and 26<sup>th</sup>.

**JOE:&nbsp;** And tickets?

**JAMISON:&nbsp;** I will tell you more when it's my turn to pick.

**JOE:&nbsp;** Alright.

**JAMISON:&nbsp;** Thank you.

**JOE:&nbsp;** There we go. Those are my picks.

**CHUCK:&nbsp;** Go ahead, Dave.

**DAVE:&nbsp;** Alright. I have one pick for you today and it is an almost brand new podcast hosted by none other than Jamison Dance and some other guy. Oh, it's me.

**JAMISON:&nbsp;** It's Dave.

**DAVE:&nbsp;** [Chuckles] And the name of the podcast is Soft Skills Engineering and it's to our knowledge the only podcast that's about development but not about technical stuff. It's about social skills, titles, organization stuff. Right, Jamison?

**JAMISON:&nbsp;** Yeah, yeah. I think we talked about, what did we talk about last time? Titles and pressure in a development team.

**DAVE:&nbsp;** How to onboard new engineers.

**JAMISON:&nbsp;** Yep, all that kind of stuff.

**DAVE:&nbsp;** Organizational processes.

**JAMISON:&nbsp;** All the other stuff that is important.

**DAVE:&nbsp;** Anyway, there's so much stuff in this space. And people have been telling us a lot. It's super valuable. In fact, I was walking in the front door of the conference this morning and they were like, “Hey, you do Soft Skills Engineering.” I was like, “What?” [Laughs] I'm like, “One of our three listeners is here right now.” So, Soft Skills Engineering. Subscribe on iTunes or Pocket Casts or wherever you get your podcasts.

**CHUCK:&nbsp;** You heard it right here, folks. They're world-famous. Alright, I've just got one pick that I'm going to share here and that is May the 4<sup>th</sup>.

**DAVE:&nbsp;** [Chuckles].

**CHUCK:&nbsp;** And if you can actually see, I don't know if they're doing a video of this or not. But if you get to see this, you can see that I'm in a Jedi robe.

**DAVE:&nbsp;** It looks awesome. It's just, it's an opportunity to just have some fun, get out and make people smile. I've seen people smile at me all over the conference and it's just because it's different. But yeah, it's a fun day. Just go out and do something fun with people you care about for the next May the 4<sup>th</sup>.

**DAVE:&nbsp;** And by fun you mean force choke people, right? [Laughs]

**CHUCK:&nbsp;** I tried. It didn't work.

[Laughter]

**CHUCK:&nbsp;** Alright Michael, what are your picks?

**MIKE:&nbsp;** So, first I didn't mention it before but if you want to sign up for the developer preview my pick would be to go to Horizon.io to be able to sign up and get involved in the project.

But I always love the JS Jabber picks because I find cool bits of culture in some it. And so, I wanted to share one of my favorite books that I always, it's the kind of book I give to a lot of people. And it's called 'The Art Spirit'. It was written by an art professor, an artist himself named Robert Henri from 1880 to 1920. I want to say he lived in that time period.

**DAVE:&nbsp;** Now, that's legacy. [Chuckles]

**MIKE:&nbsp;** Yeah. And he gave a set of lectures and essays on what it means to create art. And software is a vehicle for ideas and art is a vehicle for ideas. Art is very important to us at RethinkDB because it allows us to represent ideas and to share what it means to be building software. And so this book, it's the kind of book where you read it and you wake up at 3am and the words are in your head. So, I would urge anybody if you care about your craft, if you want to find some… if you're feeling a little bit low and need to find some way to be inspired, go read 'The Art Spirit'. It's going to be a really special experience.

**CHUCK:&nbsp;** Man, now I feel so uncultured.

**MIKE:&nbsp;** [Laughs]

**CHUCK:&nbsp;** Jamison, what are your picks?

**JAMISON:&nbsp;** Sorry, I'm just writing down 'The Art Spirit'. I have, let's call them three picks. So, the first one is the second half of what Joe said. Ng-conf is awesome and I'm really glad to be here. And I'm in no way trying to say like, “Ooh, I'm better.” But I do run a tech conference. It's called React Rally, about React, in August in Salt Lake City. And tickets are on sale now at ReactRally.com. And it's a really good time. We'd love to see you there.

My other pick is, it's an article that came out a week or two ago called 'Uncanny Valley'. It's basically an essay by a woman who worked at a tech company in Silicon Valley. And maybe more than any other article I've read it captures the coolness and the weirdness of being in that culture where it's all about… you can't just do your job. You have to water slide into the office.

[Laughter]

**JAMISON:&nbsp;** And then Segway your way up to your desk and I don't know. There's just some really weird stuff that you don't really notice until you back off. So, I love that article.

And then my last pick is I think I'm just going to pick Kishi Bashi. It's an artist who makes awesome music.

**MIKE:&nbsp;** Yes. Kishi Bashi is amazing.

**JAMISON:&nbsp;** Oh, nice. Now you know it's good because Michael agrees.

**MIKE:&nbsp;** [Laughs]

**JAMISON:** Those are my picks.

**AIMEE:&nbsp;** Okay. I have to look here. I have a running list of things that I write down as I find them. And this is one I think will be fitting for today because I am sitting in a room full of Angular developers [writing React] right now. But it is a blog post and you're going to have to check the show notes for this because it's a really long URL here. But it's just about criticizing programming languages. So, I think it is worth the read.

**CHUCK:&nbsp;** I think I just had somebody recommend that one to me the other day.

**AIMEE:&nbsp;** Oh, really? Okay.

**CHUCK:&nbsp;** Yeah. So anyway, interesting. But yes, it's very, very interesting. So, yeah.

**AIMEE:&nbsp;** Yup.

**CHUCK:&nbsp;** I'll back you up on that one. Alright, well we're going to go ahead and wrap up the show. Thank you to our live audience.

**DAVE:&nbsp;** Thanks, everybody.

**JOE:&nbsp;** Yay.

[Applause]

**_[Bandwidth for this segment is provided by CacheFly, the world’s fastest CDN. Deliver your content fast with CacheFly. Visit CacheFly.com to learn more.]_**

**_[Do you wish you could be part of the discussion on JavaScript Jabber? Do you have a burning question for one of our guests? Now you can join the action at our membership forum. You can sign up at JavaScriptJabber.com/Jabber and there you can join discussions with the regular panelists and our guests.]_**


