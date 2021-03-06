---
layout: layouts/post.njk
title: >
      093 AiA Angular Universal Patterns with Jeff Whelpley
date: 2016-05-19 07:00:48
episode_number: 093
duration: 50:45
audio_url: https://media.devchat.tv/adventures-in-angular/AiA093AngularUniversalPatterns.mp3?rss=true
podcast: adv-in-angular
tags: 
  - adv_in_angular
  - podcast
---

02:05 - Jeff Whelpley Introduction and Angular Universal Patterns
- [Twitter](https://twitter.com/jeffwhelpley)
- [Blog](http://jeffwhelpley.com/)
- [Jeffrey Whelpey & Patrick Stapleton: Angular 2 Universal Patterns @ ng-conf](https://www.youtube.com/watch?v=TCj_oC3m6_U)
- [angular/universal](https://github.com/angular/universal)
03:26 - Backend Implementations05:07 - Drawbacks
- [zone.js](https://github.com/angular/zone.js/)
12:46 - Contribution
- [Patrick Stapleton](https://github.com/gdi2290)
- [Tobias Bosch](https://github.com/tbosch)
- [Jeff Cross](https://github.com/jeffbcross)
16:42 - Caching19:04 - Other Gotchas
- Session State
- App Container
25:40 - The User Experience
- Hydration
31:29 - Installation and Running Angular Universal33:24 - The Release Schedule&nbsp;Picks
- [BB-8 Sphero](http://www.sphero.com/starwars) (Joe)
- [Black Man in a White Coat: A Doctor's Reflections on Race and Medicine by Damon Tweedy](http://www.amazon.com/Black-Man-White-Coat-Reflections/dp/1250044634) (Joe)
- [iPhreaks Show Episode 153: Using Mobile Devices to Manage Diabetes with Scott Hanselman](https://devchat.tv/iphreaks/153-ips-using-mobile-devices-to-manage-diabetes-with-scott-hanselman) (Chuck)
- [The Freelancers' Show Episode 202: Live from MicroConf: Managing a Team with Anders Thue Pedersen](https://devchat.tv/freelancers/202-fs-live-from-microconf-managing-a-team-with-anders-thue-pedersen) (Chuck)
- DevChat.tv Survey (Chuck)
- [GetHuman](https://gethuman.com/) (Jeff)


### Transcript

**_[This episode is sponsored by Hired.com. Every week on Hired, they run an auction where over a thousand tech companies in San Francisco, New York, and L.A. bid on JavaScript developers, providing them with salary and equity upfront. The average JavaScript developer gets an average of 5 to 15 introductory offers and an average salary offer of $130,000 a year. Users can either accept an offer and go right into interviewing with the company or deny them without any continuing obligations. It’s totally free for users. And when you’re hired, they also give you a $1,000 bonus as a thank you for using them. But if you use the Adventures in Angular link, you’ll get a $2,000 bonus instead. Finally, if you’re not looking for a job but know someone who is, you can refer them to Hired and get a $1,337 bonus if they accept a job. Go sign up at Hired.com/AdventuresInAngular.]_**

**_[Ready to master Angular? Oasis Digital offers Angular Boot Camp, a three-day, in-person workshop class for individuals or teams. Bring us to your site or send developers to ours classes in St. Louis or San Francisco – AngularBootCamp.com.]_**

**_[This episode is sponsored by Telerik, the makers of Kendo UI. Kendo UI integrates seamlessly with both AngularJS 1.x and 2.0. It provides everything you need to integrate with AngularJS out-of-the-box bindings, component configuration, directives, template directives, form validation, event handlers and much more and yet Kendo UI tooling does not depend on AngularJS. So, if you want to use it with Angular or not that’s totally up to you. You can check it out at KendoUI.com]_**

**CHUCK:&nbsp;** Hey everybody and welcome to episode 93 of the Adventures in Angular show. This week on our panel we have Joe Eames **.**

**JOE:&nbsp;** Hey everybody.

**CHUCK:&nbsp;** I'm Charles Max Wood from DevChat.tv. And this week we have a special guest. That's Jeff Whelpley.

**JEFF:&nbsp;** How's it going, everyone?

**CHUCK:&nbsp;** Alright.

**JOE:&nbsp;** You know Chuck, if you wanted to make it sound like there were 10 more people you could introduce random people and I'll make other voices.

**CHUCK:&nbsp;** Oh, there we go.

[Chuckles]

**CHUCK:&nbsp;** On this week's panel we have Yoda and BB-8.

**JOE:&nbsp;** Oh my gosh.

[Chuckles]

**JOE:&nbsp;** I can do a BB-8 sound. [Laughs]

**CHUCK:&nbsp;** So Jeff, we got you on to talk about your ng-conf talk, 'Angular Universal Patterns'. Can you give us a brief overview? I know we talked about Angular Universal a few months ago but can you give us the 10,000-foot view on that and then we'll talk about some of the patterns?

**JEFF:&nbsp;** Sure. So, first let me start telling what Angular Universal is. And then I can get into what the patterns are. For people that don't know, Angular Universal is the way in which you can render your Angular 2 app on the server. We have a library that if you build your Angular 2 app you basically add this library with a couple of lines of code you can basically render on the server. And the reason why you'd want to do that is if you have a consumer-facing application and you are concerned about things like SEO or the initial page load time then this can be extremely helpful. But the focus of my talk is actually going to be on the patterns and best practices for the real-world apps that Patrick Stapleton and I… Patrick and I are the ones working on Angular Universal and we've just run into all sorts of problems or challenges rather in building real-world apps. And so, this talk is focused on those patterns and best practices that we've started to develop in order to get around those common problems that pretty much everyone's going to face.

**CHUCK:&nbsp;** Gotcha. No, I think I remember right. Last time you said that you had the Angular Universal stuff running or mostly running on Express or some other Node.js framework. Is that still the case? Are there other instances out there where people are using Angular Universal with something else?

**JEFF:&nbsp;** Yeah, that's a good question. So, we are primarily focused on a Node.js backend. That's the core of what we started building on. But we've started to expand out to a number of different backends. The best one so far or the most advanced is for .NET. So, Steve Sanderson who is the creator of Knockout.js and is now working on the Visual Studio team and doing a lot of work with Angular 2 and integrating that into the new Visual Studio and Visual Studio Code, he's basically created an adapter with Angular Universal to .NET. So, you can be running your .NET backend, you're on the web server, and it uses a .NET to JavaScript bridge in order to talk to Angular Universal to do the server rendering. And then you obviously have your client side Angular 2 app as well. So, that's a pretty cool implementation that he's done. And that's already working. That's out there, something you can use. But then we also have a number of other backends that are not as far but are still in development for PHP and Java. And then there are some other ones for further down the road that we've talked about for things like Python. Again, those ones aren't nearly production ready. They're more like experimental but they'll eventually get there.

**CHUCK:&nbsp;** Gotcha. So, I'm curious then. As you start to pull in Universal and it makes a lot of sense from the standpoint of having something that's maybe a little bit more static or completely rendered by the backend. And we've talked about that like I said in the previous episodes. But what are the drawbacks? What are the things that just don't work or don't work well yet? What are the gotchas that you're finding that you have to work through or work around?

**JEFF:&nbsp;** You know, this is actually a perfect segue into my talk because that's what it's all based on. When you start building with Angular Universal you have a lot of benefit, especially when you are building a consumer-facing app and you want to get SEO benefits and the initial page load benefits. But in order to do that, you do run into some issues. So, Patrick and I identified six problem areas or challenge areas rather. And for each one of these there are things that you can do, that you should do to mitigate them. But you don't necessarily… there are easier ways and then more advanced stuff. So, I can get through all six but let me just take one as an example.

So, async is an example. On the client when you're building an application within the browser async isn't that big of a deal because you could have 10 different async operations occurring at the same time. That's what the browser is built for. And they can all resolve independently. They don't have to be coordinated. On the server, that's not the case. On the server you have a request that goes to your web server for a URL and the web server has to return something at some point. So, in your code, in your application code if you have all these disparate async pieces of code, how do you know when to return a response? And that's something that's kind of obvious at first when you start doing this. But it can be a big problem and it's a challenge that other server-rendering frameworks struggle with.

The great thing about Angular 2 is that there's an awesome, awesome solution for this because of Zones. So Zones if you don't know is a lower-level library that is built with Angular 2 that basically wraps all async calls. And you could do a ton of different things with that to track them or perform certain operations. For our purposes what we did is we used the power of zones to basically keep track of all the async calls within your app. So we know, the Angular Universal library, knows what async calls are going on at any given time. And it knows when they've all been resolved. So, you can basically set up something where the library, you don't have to add any extra code to coordinate all your async events. You just keep them disparate like you normally would on the client side and let our custom piece that's built on top of Zones keep track of everything. And then it responds back to the user whenever all that has resolved. Does that give you a good sense?

**CHUCK:&nbsp;** Yeah, it does. And just the way I think about my Angular apps it's like, “Oh yeah, I guess that really doesn't apply on the backend.” So yeah, having something that manages that for you and makes it so that it's, what's the word I'm looking for, trackable? Traceable? There's something keeping track of those asynchronous calls and making sure that everything happens in the order and in the way that it's supposed to, I really do like that.

**JEFF:&nbsp;** Yeah. It's pretty awesome. And obviously we built some custom code within Angular Universal but I have to give credit to the Angular team for the core Zones library which enables this. I don't think people appreciate how powerful or great the Zones library is.

**CHUCK:&nbsp;** Now, is that the solution to a lot of the other problems, the Zones? Or does each problem have its own solution?

**JEFF:&nbsp;** Each problem has its own solution. So, Zones is a part of one of the other problems but another example is dependencies. So, on the client side you may reference certain things that are client-specific. This is a big problem actually that almost everybody who starts using Universal runs into this. Because you're so used to in your client-side code for example referencing the window object and referencing jQuery or referencing something that is specific to the browser. And you have to do something in order to abstract out those dependencies when you're running that application in the server. So, what do you do?

For this particular problem, there are four different patterns that Patrick and I are going to go over in our talk. But the most important one is what we're calling DI swapping, which is not a revolutionary idea. But it's the thing that is particularly useful for Universal and running things in different contexts, both the web server and the browser. And so, basically what that is, is that you build an abstract class that is the interface. And when I say abstract class, in TypeScript there's not really abstract classes. It's just a class that you just don't implement methods. So, you use that as your interface. It's essentially noop-ing all of those functions. And then you build implementations, two different implementations. One for the client and one for the server. So, the client side for that, like a function, let's say it's showAlert is the function. In the interface, that function would be empty. But in the implementation for the client side you might have window.alert, the call to window.alert function. On the server side it doesn't really apply so that particular thing can be kept as a noop.

But there might be other things, like caching is one thing. On the client side you might using window [local cache] but on the server side you would use something like Redis let's say. So, by using this approach where you build these abstract class interfaces and you build against the interfaces it makes it really easy to build these powerful applications that are not content-specific. And the really great thing about this approach is that it doesn't just apply to Angular Universal. There is all this stuff in Angular 2 now where you can run stuff other than the browser. So, Electron, NativeScript, Web Workers, all this other stuff where you're running your app in different contexts. And so, the thing I just described with DI swapping can apply to all of those.

**CHUCK:&nbsp;** Yeah, we have dependency injection, right? Why not use it so that we can get the behavior we want?

**JEFF:&nbsp;** Yep, definitely.

**CHUCK:&nbsp;** It's interesting because I guess if I had thought long and hard about it I could have come up with one of these problems maybe. But I guess it didn't occur to me until you get in there and you try something and you're like, “Oh yeah, that's broken here. We've got to figure out a way around it.”

**JEFF:&nbsp;** Yeah, no. that's the whole thing is that whenever you're designing something or something's not in production you never have the full picture of what people are going to run into. So, once people are using it for real, then you have all these issues and then you start creating the solutions for those. I'm sure there are going be more as people more and more people use Angular Universal. But we've already I think encountered a lot of the common ones that we think most people will run into and come up with really good solutions for those.

**CHUCK:&nbsp;** Yeah, it's amazing what people come up with that breaks… it seems reasonable when you look at it but yeah, you didn't think about it at the time and so it breaks something.

**JEFF:&nbsp;** Yep.

**JOE:&nbsp;** So, I'd like to talk about the people that have been working on and getting this done. You mentioned yourself and Patrick Stapleton, right? I assume obviously you're also working in conjunction with the Angular team itself. So, who is all involved and what have you and Patrick been doing and how long have you been working on this? I'm interested in all of that.

**JEFF:&nbsp;** That's a good question. We started off, it was Tobias, Tobias Bosch from the Angular core team who was our primary liaison and adviser. And he was great. He is. But [chuckles] he is so valuable and important to the core team that I guess it was just inevitable that as things are getting closer to the ultimate release of Angular 2 he is just getting pulled in a million different directions. And I don't know if you guys keep track of the actual core library and the major changes there, but Tobias is like a mad scientist. He goes crazy. There are internals within core that really only him and probably Victor are the only ones who are brave enough to change them. And Tobias won't even, not just make minor tweaks. He'll just rip complete huge sections out, totally rewrite it. It's just crazy the type of stuff he does. But it is huge and beneficial.

One of the biggest things just as a quick aside is just on that note, is Tobias is working on this unbelievably complex and awesome change to core where you'll be able to precompile your entire app into these set of artifacts. And what that does is it allows the Angular team to include just the bare minimum of core code, like the size of the Angular core library is going to get reduced down an order of magnitude. And your code is going to run a lot faster because it doesn't have to actually run through a lot of different code. It just has everything pre-generated. So, that's just an example of the type of stuff that Tobias is constantly working on.

So, once he started going off in the deep end on a lot of that type of stuff, Jeff Cross started working with Patrick and I a lot more. And Jeff is great as well. He is doing a lot of stuff, combining different technologies for Angular 2. He’s actually been working on the progressive web app example that he's going demo at ng-conf, which brings in a whole bunch of different things. It brings in Angular Universal, service worker, web worker, all of this different stuff to show as an example. So, he's been great to collaborate with and you have this central point of not only [very useful] for getting feedback on the stuff that we're working on but then getting from him feedback from all these other areas and other projects within Angular 2 and the different teams that are working on them. So, that's been pretty awesome.

And then outside of the core team, because you asked about all the different people who are involved here, we also have a pretty good community of people that contribute. So, we have I would say about half a dozen regular contributors from the community. And we try to meet with them once a week on Fridays for our community meeting to talk about what the issues are and what needs to be done. And they help with everything from little documentation changes to small and large modifications to the library. And building example apps, everything like that. So, it's been great to… as you guys know, the Angular community is just really, really awesome and really strong. So, it's definitely been, if anything I think that Patrick and I haven't used them enough. That's one of the things that I've talked with Patrick about, of trying to push more to the community because they are really able and love to help out.

**JOE:&nbsp;** Awesome.

**CHUCK:&nbsp;** So, one of the things that I keep looking at with Angular Universal is that it builds the layout on the backend and then puts it up or serves it up basically, so it serves up fully-formed HTML. I'm curious how that works with caching. That's one thing that I keep looking at and going, “Yeah, if I could get it to render everything and then just cache it so that it's really blazing fast, it doesn't have to do all that calculation again,” are there any gotchas with that? Or are there good implementation patterns that we deal with there?

**JEFF:&nbsp;** Yeah, that's a good point, too. So, we actually have a rudimentary way of doing that. The problem is we haven't enabled it by default, what you're describing. And just to reiterate so that it's clear is when you make that request to the server, obviously all the data has to be gathered at that point in order to render the page on the server. And then that's passed down and then client re-renders part of that page so it does by default right now with Angular Universal re-pull all of that data. So, it makes essentially the data calls twice. And from that sense the time to get to where the client has fully taken over is longer than it would be if you were able to reuse that data. You can use that data. You could do that actually right now. But the problem with trying to enable that by default is that it doesn't actually yield benefits in all cases. Because what happens is you pull the data on the backend and the way that you share the data is you put it in the HTML of the payload for the server page.

And depending, it always depends on what your app is doing. Because sometimes the size of the data is so large that it actually slows down the initial download of the page so that your initial time to see the server-rendered page slows down even though the client rendering speeds up. So, it's not necessarily a win every time. What we're trying to do is to add a flexible, configurable library and parts of the library where you can specify basically okay, I know for my particular page that because the dataset is small, this is totally fine. So, use that caching mechanism. And then for this other thing where it's this huge dataset, it's actually better to take a different approach.

**JOE:&nbsp;** Awesome.

**CHUCK:&nbsp;** So, what are some of these other gotchas that you run into with the Angular Universal that you've been able to solve?

**JEFF:&nbsp;** Yeah, I'd love to actually… we had to cut, I mentioned six, right?

**CHUCK:&nbsp;** Uhuh.

**JEFF:&nbsp;** There's no way, we only have 20 minutes for this talk.

**CHUCK:&nbsp;** Oh, wow.

**JEFF:&nbsp;** So, there's just no way to talk about all six. So, we ended up doing, even though we're going to throw it up on the screen like, “These are the six problem areas,” we actually are only able to talk about three. [Inaudible]

**CHUCK:&nbsp;** I blame Joe. I blame Joe.

**JEFF:&nbsp;** [Laughs]

**JOE:&nbsp;** [Laughs]

**JEFF:** No, it's a good thing. It keeps it tight. I actually don't mind that. But what we're going to do is we're going to publish afterwards details on the other three. But I'd love to talk about some of that. Actually, let me just run through all six. And I want to talk about the ones that aren't going to be in the talk, because I think some of those are interesting.

So, the six are gap events, which has to do with the preview and I have to talk about that in a little bit, async like I mentioned, dependencies. And then the three ones we aren't going to talk about are session state, app container, and scalability.

**CHUCK:&nbsp;** Mm.

**JEFF:&nbsp;** Yeah, and I know [chuckles]. All of them are interesting. Session state, [inaudible] to [take] that one. The problem there is that on the browser when you're running an app there's only one user. It's one user and it's a long session. But on the server it's completely different. There are many different users for shorter sessions; or rather the lifetime of that request is shorter. So, how do you for example, you access a ser-… like on the client typically you'll have a service let's say that accesses some data like active user for example. And on the client in the browser it's essentially global, global state data. And so, you just get that and that's easy-peasy. But on the server that's hard because if you have global data then that's going to be globally accessible to all the different requests. And you don't necessarily want that. You want to isolate it to just the request that is currently being accessed.

**CHUCK:&nbsp;** No, it's okay. Give me something I can blackmail Joe with.

**JEFF:&nbsp;** [Laughs]

**JOE:&nbsp;** Ha.

**JEFF:&nbsp;** The way that most server render, server frameworks like Express handle this is that they use middleware where you actually have to pass down the request object to all the different functions. So, you're explicitly passing it down. But the problem with a client-side app like Angular is that you're using dependency injection. So, we don't actually have this pass-down callback mechanism like middleware does where you can pass down that request object everywhere. You sort of have to have it available. And so, the way that we solve this problem is it gets into the inner workings of how the DI and the bootstrap process works.

So, with the Angular 2 bootstrap, that's where you setting your dependencies for what you're using in your app. But in Universal what we do is we actually have a multi-level bootstrap where there is a top-level bootstrap for the entire application, like globally. And then there are some sub-bootstraps. And for the purposes of this discussion, really only two are relevant. There's one that's a little bit abstract and I [inaudible]. The app is the higher level one and then the platform injector is the one that is specific for a request. So, that means that every single time a request comes to a server it is re-bootstrapping that particular part. And so, you do want to only do the minimal in that bootstrap because it's running every time. But this is where you can inject all the services that you have, the session-specific stuff. And that provides a great solution.

If you look at other server-rendered frameworks they don't have this. They actually, it's a big problem actually because they don't have the types of, the power of dependency injection. It's in Angular 2. They don't have this ability to do this bootstrap that I just described. So, they have to explicitly pass down that object, everything. And that could be a real pain in the butt. You have to include that object in all of your functions, pass it all the way down. And it just gets treated like a lot of cruft you're adding everywhere. So, I think that's a pretty elegant solution that we'll definitely add some more information about for after the conference. Does that make sense for session state?

**CHUCK:&nbsp;** Yeah. And the way you described it was the same way it works in Rails and just about every other framework I've used too, so it's not unique to Express or anything like that. It's a pretty common way of handling it.

**JEFF:&nbsp;** Yep. For app container, so the problem there is that when you bootstrap on the client, you are bootstrapping to an app root. So, that's typically an element within the body of HTML. But on the server even though that same thing does occur, on the server you are handling the entire HTML document. It's something that you aren't necessarily doing on the client side. You just expect that it's there because it comes from the server. But when you are running the Universal app and you want your Angular Universal to handle everything, it has to handle the actual HTML document on the server as well. And so, what we've done there is we've created essentially this special HTML element that is essentially the way of controlling through Angular the entire HTML document. And that's extremely useful for things like when you want to set various values in the head section of the document. On the server side, you want to set the title, you want to set the meta tags, that type of stuff, from the app. Or if you want to do various coordination among multiple apps, sometimes you might have multiple apps on one given page. Angular does have that ability to bootstrap multiple apps on the page. But on the server side you have to be able to have that top-level thing that coordinates everything. And so, by having this HTML element that's available, that's our solution for handling that on the server. I should mention you don't have to use that. That's an optional thing. If you don't want to use that, you can still use the traditional way which most people actually are, of you have in whatever your server framework is, whether it's Express or .NET or whatever, you can have Express or .NET or anything control the index.html. You can defer to that and keep Angular to just that app root. But if you want Angular to [take] control of everything, you can do that too.

**JOE:&nbsp;** That's interesting. So, what about the user experience? What's the user experience like when using Angular Universal? Or now and the desired one in the future?

**JEFF:&nbsp;** Well, first of all I think until the end of time we're going to want to get things faster. Performance is like a never-ending problem. I think every talk that Brad Green ever gives, he talks about how much faster Angular is with all these different changes. And it keeps getting faster which is great. But just the reality is that it's fast now. We have various things on our board to make it even faster in the future with caching, with optimizations, et cetera. But the one thing that's… I didn't talk about gap events.

So, the first problem that we're going to talk about during the talk is the problem related to a server view is displayed to user almost immediately. But then the client kicks in some time later. On slow devices, the amount of time between those two things, the server view being displayed and when the client kicks in, it can be significant. It can be four to eight seconds, or maybe more depending on where they are and what type of device they have. And so, there's this problem of what is that user experience in between those times? And during the transition. Outside of performance and just raw performance, that's probably the biggest UX thing that we focus on. And the solution for that is we've built a library called Preboot which handles a lot of that. And there's still a lot of stuff that we're going to build in the future along those lines. But today at least, the way it works is that there are two primary functions of Preboot.

First, it's to record all events that occur on the server view. So, Preboot is an inline piece of JavaScript that's included with the server view. So, once the server view comes in it doesn't have to wait for Angular to bootstrap or anything. It's just there right away. And it's recording events. The user clicks, they type in a text box, click on a button, anything like that. And then once Angular kicks in, once the client is done bootstrapping, Preboot will replay all those events to Angular. So, let's say if you have for example a click event on a button, your user clicks on that button, once Angular kicks in even though Angular wasn't alive at that point, it was the server view, once Angular kicks in it will actually process that event. And there are other things, smaller things along those lines. Obviously when you click a button you might want to show a spinner and stuff like that. You can make your configuration changes or set certain configuration options within Preboot so that it does things like that.

But the second major thing outside of the event recording and replaying is the buffering. So, this is the way in which the transition between the server view and client view occurs. There are two different approaches that you can do when you're talking about this, like switching between the server view and the client view. One approach is, that isn't the approach that Angular Universal uses but other server-side frameworks use, is hydration. At a general level, it's called hydration, which means that the client-side framework essentially reads what's in the server view, what's currently being displayed, and it does some sort of diff. It sees, “Okay, this element is already existing. This one is not.” And it diffs out and it either adds event handlers to the existing server view or adds new elements that doesn't exist. There's all that type of stuff.

And we tried this. The first version of Angular Universal was basically using hydration. The problem with it is that it was significantly slower than re-rendering. And that's due to some of the Angular internals which have a lot of optimizations for the initial render time where it was just so much faster to just render everything again rather than trying to attach everything. Because if you think about it, there's a lot of work to go into search through the existing DOM, do a diff, and then make the changes. As opposed to just not even worrying about that and re-render. But you run into the problem of a jank because of the switchover between the re-rendered client view and the server view.

So, that's where the Preboot, the second major feature of Preboot comes in, which is buffering. The way that works is that Preboot will create an offline buffer. You're basically creating a div that is display none. And that's where when Angular 2 bootstraps it writes everything to that buffer. So essentially if you were to look within your Chrome Dev Tools you would see during those four to eight seconds while Angular is bootstrapping, four to eight seconds is a super long time. It's much less than that. But during the time that it's bootstrapping you would basically see two elements. One is hidden and one is… the visible one being the server view and the hidden one being the client side that's running and doing all of the generation of the client view. Then once it's done and the events are replayed, so it's slowly up to speed with what the server view is, then Preboot just basically flips them. It just does a flip of the hidden view for the displayed view. And basically as long as the data has not changed, the user doesn't see any difference. It's just a very smooth transition.

Obviously, if the data is completely different between what the client is generating and what the server did, then you might see some jank. And that is something that we're working on with some of the caching stuff that I mentioned. But in most cases, you shouldn't.

**JOE:&nbsp;** Now, what about installation and running Angular Universal?

**JEFF:&nbsp;** So, that is something that getting into the field like DX, developer experience, it's better than… we started off, it was very raw. And we got to the point, we created adapters for many different types of server frameworks. We have a specific one for Express, a specific one for Happy.js, and other ones, where it comes down to basically just implementing one function for the most part. You basically set your Express, for Express let's say, your rendering engine just like… or your template engine rather just like you would set any other template engine. The Angular Universal is built as a template engine for Express. And then you just pass in your various configuration options to that. So, the API surface area is super small. It's just for all intents and purposes one function.

The thing that we're working on more for the developer which does need work for sure is there are tons of different options. Okay, there are three levels to this. So, one is that the options you pass in, there are a lot of different things you can do there. And I think just from our experience of people trying it out it isn't quite clear all these, what they should be passing in to do what. So, we need to improve that both in terms of better warnings, better documentation.

And then documentation in general. We have not done a good job of documenting everything and having it out there. That is something that we're in the process of working on with Naomi and a lot of the other core team members. We're starting to create these micro-sites for some of the libraries like Universal that has all the documentation. So, it is something that we are working on there. So, I would say that it's, for DX I would give us a B now. I think that it's going to improve greatly over the course of the next couple of months.

**JOE:&nbsp;** That's cool. What is the schedule like for Angular Universal, for now and into the foreseeable future?

**JEFF:&nbsp;** In terms of release schedule?

**JOE:&nbsp;** Yeah. Yeah, release schedule. I don't know if you're doing typical releases or what. But what's that like?

**JEFF:&nbsp;** So, we do try to get in stuff as quickly as possible. We don't have things as formalized as in the core team. So, the core team has a very defined process like when and how they group up changes and that type of thing. Patrick and I are kind of rogue. [Chuckles] We do try to follow many of the same processes. When it comes to release schedules right now we're just getting stuff out there as soon as we can get it out there. But we've already noticed even in the past week as more and more people start to use it, it is becoming evident that we have to get way more formal in terms of how we're planning out changes and we're releasing and how we're notifying everyone of changes, formal release notes, all those types of things. So, I would say we're in transition right now between our rogue days and the more formal this is a production library ready for everybody to use and this is exactly how we do things and these are our processes and everything like that. And what we'll go towards for that is basically following the same schedule and the same processes that are in the core team right now. But that is something that is also, we'll start to formalize within the next couple of weeks.

But one thing I should mention because a lot of people were asking us of, “When can I use this in production?” And for that, what we've been answering it and what I think will shortly change… so, what Patrick has been answering for this is that it's definitely ready to build on, for sure. There are dozens of people that are working with us on the Angular Universal Slack channel building real apps using Angular Universal. And they work. They're great and everything. So, it's definitely for building apps. Just use it. For actually launching in production, I would say not today yet, like right [chuckles] today. There are a couple of specific things I want to see in before we get to that point. Specifically a couple of things in core that Patrick is working with Tobias on. And there's half a dozen still stuff in our queue. So, we're close for sure. But I would not today… I'm building an Angular Universal for GetHuman, the company I work for. And we're not ready regardless but I'm not planning on actually pushing it into production until we have these half a dozen or so changes into the library.

**JOE:&nbsp;** Gotcha.

**CHUCK:&nbsp;** So, I think it's obligatory for us to ask then when it will be ready for people to use generally.

**JEFF:&nbsp;** [Laughs]

**CHUCK:&nbsp;** And then I think it's obligatory for you to pull a Brad and be coy about it.

**JEFF:&nbsp;** Yeah, yeah. Okay, okay. Actually I'll one better. Whenever Angular core is ready for production, whenever Brad declares that Angular core is ready for production, Angular Universal will be ready.

**CHUCK:&nbsp;** Oh, I see.

**JOE:&nbsp;** Nice.

**CHUCK:** So, you're just going to let Brad play coy.

**JOE:&nbsp;** Nice.

**JEFF:&nbsp;** Exactly. [Laughs] Yeah.

**CHUCK:&nbsp;** Well, you're fired.

**JEFF:&nbsp;** [Chuckles]

**CHUCK:&nbsp;** No, that's fair. We're all hoping that all of this stuff lines up and makes our lives a whole lot better. And so, it'll be really interesting to see what people do with Angular Universal along with Angular in general and just have whatever it is that it winds up being capable of.

**JEFF:&nbsp;** Yeah, I'm excited. I think that up until now there had been hardcore people that have been building stuff. Obviously a wide range of different type of developers have been starting to play around with Angular 2. But if you're building a real app right now, you've got to be kind of hardcore. And it's going to be exciting once A, we start seeing apps in production. And I'm not just talking about Angular Universal. I'm just really excited for any Angular 2 apps. I've gotten a preview of a number of bigger companies that are building [stuff] in Angular 2, some really awesome stuff. And I can't wait until those for example get in production. But then as that expands the second thing is once it rose out to everybody and people see, “Okay, it's definitely here,” and everybody starts building their Angular 2 apps, migrating their existing Angular 1 apps and it becomes mainstream, that's going to be really, really exciting.

**CHUCK:&nbsp;** Do you think you're going to have more things shake out that are issues once it starts being used more widely?

**JEFF:&nbsp;** Yeah, I'm sure. I'm not deluded enough to think that we've thought of everything. For sure. I do think… the way I view it is that if I had to compare where we are relative to… we keep close watch on other server rendering libraries. React, Ember has one now, and we know them pretty well. And right now even not being production-ready there are a couple of things that we've built that I feel are better than what is in their solutions just because of the approach we took and the power within Angular 2.

The thing that's a minus for us is, a big minus right now is obviously not having stuff in production. Because the reality is it's only when you have something in production and real-world users are using it, then something becomes mature and it really solidifies. Even if I… we had no issues in GitHub and [inaudible] things clean, I would still soon, once the first app gets into production, there's going to be all sorts of different problems we'll have to overcome. But I think we're on the right path.

I think that, I would say yes, that based off of just the pace of where the Angular core team is, I don't know. I have no inside knowledge of whatever. But [inaudible] pace, I think we're within months away or closer of the release. So, within six months let's say, end of year, I would expect us to have reached at least the maturity level where I would be much more confident in saying, “Okay, this is definitely head and above everything else. This is the best solution ever.” [Chuckles] I would say that now, but I would just be kind of, I don't know, a hack or something like that. [Inaudible] trying to say. So, I'm just trying to be a realist. But I think I will truly be able to feel that once I have my own app in production, I know that it all works, there are no issues and feel on solid ground. Which I think by the end of this year, we'll basically get there.

**CHUCK:&nbsp;** Awesome.

**JOE:&nbsp;** Cool.

**CHUCK:&nbsp;** So Jeff, is there anything else that we should have gone over that we didn't?

**JEFF:&nbsp;** One thing that I'll mention just in terms of ng-conf, this goes a little bit beyond my talk. We are going to have a workshop first of all. So, we have the talk where we're going to go over these problems and patterns like I mentioned. We're going to have a workshop the second day where we'll try to get everybody getting a basic Angular Universal app running and then go over some of the problems that we talked about within our talk. But then in addition to that, Patrick and I are going to be around. And one of our goals and the thing I talked with Patrick about is we're going to consciously try to find the people that are really interested in server rendering, in Angular Universal, understand their problems, and try to help them. So, if you are thinking about using Angular Universal which in my mind really means if you have a consume-facing app, something that's you've build that's publicly available to people on the internet, you should number one, you should be using Angular Universal. And assuming you are, I want to talk to you. So definitely, if I don't find you at ng-conf definitely come out and seek either myself or Patrick out and we'd love to talk to you.

**CHUCK:&nbsp;** Alright. Well, I don't think I have anything else to add. Do you have anything you want to bring up, Joe?

**JOE:&nbsp;** Just that Jeff is awesome. And I'm looking forward to his talk. Of course it will have already been played. So, if you're listening to this podcast you should get on YouTube and watch it.

**CHUCK:&nbsp;** Yeah, it was super good. We'll just say that right now.

**JOE:&nbsp;** [Chuckles] Yeah. This was the best talk of the whole thing. It was the best talk this year.

**CHUCK:&nbsp;** I know, right?

**JEFF:&nbsp;** [Laughs]

**CHUCK:&nbsp;** And we'll tell all the other speakers that too, won't we?

**JOE:&nbsp;** Yeah. [Laughs]

**CHUCK:&nbsp;** Alright, well let's go ahead and get to our picks then. Joe, do you have some picks for us?

**JOE:&nbsp;** You bet I do. So, I bought the Sphero BB-8 droid quite a few months back. And…

**CHUCK:&nbsp;** I'm jealous.

**Joe:&nbsp;** It's really cool. I've had a ton of fun with it. My kids have had a ton of fun with it. So, I've really enjoyed having it. We're actually going to had Sphero… we've had Sphero come in the past ng-conf. We're trying to get them to come again. We've got a few more days to try to work that out. But there's been an update where you can update the software and it'll watch the new Star Wars with you and react to the Star Wars movie.

**CHUCK:&nbsp;** No way.

**JOE:&nbsp;** As it watches the show. Yeah. So, I haven't done that yet, done the update and actually watched it yet, because I actually haven't had a chance to watch all of the new… sit down and watch the new shows since I've bought it on DVD. But I'm going to do it. But I'm just more excited about the fact that they did this, regardless of how well it actually plays out. What a cool thing to do. So, I'm going to pick the Sphero droid.

And then I've also, I've already once this week picked on JavaScript Jabber this audio book but I'm going to pick this again. Read an audio book recently or been listening to an audio book, I'm about halfway through it, called 'Black Man in a White Coat'. And it's reflections by an African American medical doctor about race issues in medicine. And it's really interesting. He does a great job presenting it in a relatively non-controversial way. So, I highly recommend checking it out if you're interested in this topic at all. Great read. And those are my picks.

**CHUCK:&nbsp;** Awesome. I've got a couple of picks as well. So, before this episode I actually recorded… it's the regular recording time for the iPhreaks podcast. And we had Scott Hanselman who's actually been a guest on this podcast on the show. And we were talking about mobile technology and diabetes. And I didn't realize that Scott is type 1 diabetic. I'm type 2 diabetic. So, it was a really interesting conversation. It was also interesting to see that everybody else who is there on the panel also had some relation to people who were diabetic. But anyway, it was really, really fascinating and it's kind of inspired me. It's kind of funny how when somebody says something it seems obvious but you never really got there yourself. So, he got on me about checking my blood sugars. And anyway, so I'm definitely going to be checking that out. And I guess I'm just going to pick in general keeping tabs on your health.

It's funny because I was talking to somebody else at MicroConf. That episode will come out on The Freelancers' Show within a week or so. And he asked me why. He asked me the why for the business. Why do I do the podcast? Why do I have a team of people that help me do all this work? And to be honest, my first thought was, well because it's fun. But that wasn't really a why. It wasn't enough. It wasn't a fulfilling thing. And I realized that, and I'm going to send an email to this effect to the email list probably before this episode comes out, but I realized what I really want to do is I want to make an impact on people's lives.

Now if that's hey, you learned this cool thing on Angular 2 and it saved your company a bunch of money and you were able to keep your job or your customers were able to get more done in their day or something like that, that's cool. If knowing this stuff gets you to the point where you have a better advancement in your career, you're able to contribute better to people who matter to you, then terrific. And if we cover a topic or mention something about health or mental health or something else where it affects you or I've had several people tell me about this show, JavaScript Jabber and Ruby Rogues in particular, that it inspired them to go try something because we told them they could do it and it turned out they could. And so, they got a better job or they got a job, their first coding job, or they went out and they built some app.

And so, I really just hope that there's something, talking about health for a minute, and I've been doing the primal blueprint and I'm going to start checking my blood sugar regularly and things like that, it's stuff that we don't talk about on the show but it's stuff that matters. And the reason we do this is because we care about people. We care about the people in our lives. We care about the people that we interact with at work. We care about our families. We care about all of these different things. And ultimately, at least for me, the purpose is that these people are people that I can say something that goes into their life and makes a positive difference. So, if we've made a difference for you, I'd love to hear from you. My email address is [chuck@devchat.tv](mailto:chuck@devchat.tv).

And then I'm also just going to pick in general if there is something&nbsp; that we can put out there that will help you, I've put together a survey. It's like four or five questions. And they're just basically that. What can we talk about that will make the biggest difference? How hard is it to find a solution? What kind of a difference would it make for you to have that solution? And I'd really just love to be able to get your feedback on that. So, if you go to DevChat.tv/survey then you can hit that. And hopefully you can tell us what we can do to make a difference for you. And then like I said before, if you have those stories, then I would definitely love to hear them and love to share them with the other hosts on the shows. So anyway, that was a little longer than I planned on doing. But yeah, that's what I've been working on lately is just getting to the point where I can really focus on making that kind of a difference for people.

Jeff, what are your picks?

**JEFF:&nbsp;** I just have one that's a little bit of a plug actually. On May the 4<sup>th</sup>, May the 4<sup>th</sup> is actually going to be a pretty big day. So, it's Star Wars day first of all. It is the beginning of ng-conf. My talk is going to be on May the 4<sup>th</sup>. It's my daughter's birthday. So, a lot of stuff going on. For some sadistic reason, I agreed for it to also be the launch date of the new products that we have coming out for GetHuman. Some stuff outside my control on the date or whatever. But basically this new service that we've been beta testing for a while is going to go live in which basically it's something where GetHuman can take over you entire, all of your customer service problems. So, you never essentially have to deal with a company ever again.

So, right now we offer advice, we give ways of contacting a company. But this new service would basically be one where you pay us and we would just do everything. We would fight down your bills, we would get you your rebates, if you were locked out of your account, whatever it happens to be. You don't have to deal with these companies that typically are pretty bad and take up a lot of your time. So, that's something that has been extremely popular in our beta testing, limited exposure. And we've been growing pretty rapidly. So, I'm excited for our official launch and that type of thing. And my only worry [chuckles] [and hope] is that everything doesn't go south as I'm about to step on stage. And I think I'm going to have to just turn off my phone and [chuckles] hope for the best. But no, it's going to be great. I can't wait.

**CHUCK:&nbsp;** Alright. Well, I'm going to go ahead and wrap this show up. But thanks for coming, Jeff. We'll hopefully have a link to YouTube or wherever the ng-conf folks post the talks. And that way people can go check out what you and Patrick have to say. And I think on behalf of all of us, we just really appreciate all the work that you and the other members of the Angular team and Angular Universal team put into this stuff. Because in some ways, I guess we all get paid to do this work. But in other ways, it is put out there free for us to take advantage of and really enjoy and make the most of. So yeah, I just want to put that out there.

**JEFF:&nbsp;** I appreciate that, Chuck. Thanks a lot.

**CHUCK:** Alright. Well, we'll go ahead and catch you next week. Hopefully for us, since for us it's still before ng-conf. See you at ng-conf. And if not, then we'll see you on the internet.&nbsp;

**_[Bandwidth for this segment is provided by CacheFly, the world’s fastest CDN. Deliver your content fast with CacheFly. Visit CacheFly.com to learn more.]_**

**_[Do you wanna have conversations with the Adventures in Angular crew and their guests? Do you want to support the show? Now you can. Go to AdventuresInAngular.com/forum and sign up today!]_**


