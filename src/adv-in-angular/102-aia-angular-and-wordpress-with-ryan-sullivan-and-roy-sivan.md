---
layout: layouts/post.njk
title: >
      102 AiA Angular and WordPress with Ryan Sullivan and Roy Sivan
date: 2016-07-21 07:00:53
episode_number: 102
duration: 34:38
audio_url: https://media.devchat.tv/adventures-in-angular/AiA102Wordpress.mp3
podcast: adv-in-angular
tags: 
  - adv_in_angular
  - podcast
---

## [Angular Remote Conf](https://allremoteconfs.com/angular-2016)
&nbsp;02:01 - Roy Sivan Introduction
- [Twitter](https://twitter.com/royboy789)
- [GitHub](https://github.com/royboy789)
- [Blog](http://www.roysivan.com/)
- [The WP Crowd Podcast](https://www.thewpcrowd.com/)
02:23 - Ryan Sullivan Introduction
- [Twitter](https://twitter.com/ryandonsullivan)
- [WP Site Care](http://www.wpsitecare.com/)
- [LoopConf](https://loopconf.com/)
02:40 - [WordPress](https://wordpress.com/) and Angular05:00 - Authentication and Security
- [OAuth](http://oauth.net/)
- [A Brief Introduction to WordPress Nonces](https://www.tipsandtricks-hq.com/introduction-to-wordpress-nonces-5357)
- [Hire Otto](https://hireotto.com/)
07:38 - Data and Plugging Angular Into APIs
- [AppPresser](https://apppresser.com/)
12:54 - [The REST API](http://www.restapitutorial.com/) and Plugins; Custom Plugins
- [Help Scout](https://www.helpscout.net/)
- [Asana](https://asana.com/)
- [Harvest](https://www.getharvest.com/)
- [Chargify](https://www.chargify.com/)
21:23 - Displaying Data in WordPress Using Angular
- [Stripe](https://stripe.com/)
- [Keen IO](https://keen.io/)
25:01 - Tutorials
- [AngularJS and WordPress: Building a Single-Page Application with Roy Sivan](https://www.lynda.com/AngularJS-tutorials/AngularJS-WordPress-Building-Single-Page-Application/423997-2.html)
- [JavaScript for WordPress](https://javascriptforwp.com/)
- [Angular-Wordpress-Theme](https://github.com/royboy789/Angular-Wordpress-Theme)
- [AngularJS-Boilerplate](https://github.com/WordPress-Admin-JavaScript-Boilerplate/AngularJS-Boilerplate)
- [Josh Pollock](http://joshpress.net/)
  - [angular-wp-front-end](https://github.com/CalderaWP/angular-wp-front-end)
- [WordPress.tv](http://wordpress.tv/)
- 
Picks
- [Mailgun](https://www.mailgun.com/) (Lukas)
- [Geoff Goodman](https://twitter.com/g_goodman) updated the embedded view on Plunker (Lukas)
- [Procrastinate on Purpose: 5 Permissions to Multiply Your Time by Rory Vaden](https://www.amazon.com/Procrastinate-Purpose-Permissions-Multiply-Your/dp/0399170626) (Chuck)
- [Harry Potter and the Sorcerer's Stone by J.K. Rowling](https://www.amazon.com/Harry-Potter-Sorcerers-Stone-Rowling/dp/059035342X) (Chuck)
- [Postmatic](https://wordpress.org/plugins/postmatic/) (Roy)
- [Caldera Forms](https://wordpress.org/plugins/caldera-forms/) (Roy)
- [Calypso](https://developer.wordpress.com/calypso/) (Ryan)
- [AppPresser](https://apppresser.com/) (Ryan)
- [LoopConf](https://loopconf.com/) (Ryan)


### Transcript

**_[This episode is sponsored by Hired.com. Every week on Hired, they run an auction where over a thousand tech companies in San Francisco, New York, and L.A. bid on JavaScript developers, providing them with salary and equity upfront. The average JavaScript developer gets an average of 5 to 15 introductory offers and an average salary offer of $130,000 a year. Users can either accept an offer and go right into interviewing with the company or deny them without any continuing obligations. It’s totally free for users. And when you’re hired, they also give you a $1,000 bonus as a thank you for using them. But if you use the JavaScript Jabber link, you’ll get a $2,000 bonus instead. Finally, if you’re not looking for a job but know someone who is, you can refer them to Hired and get a $1,337 bonus if they accept the job. Go sign up at Hired.com/AdventuresInAngular.]_**

**_[Ready to master Angular? Oasis Digital offers Angular Boot Camp a three-day, in-person workshop class for individuals or teams. Bring us to your site or send your developers to ours classes in St. Louis or San Francisco – AngularBootCamp.com.]_**

**_[This episode is sponsored by Telerik, the makers of Kendo UI. Kendo UI integrates seamlessly with both AngularJS 1.x and 2.0. It provides everything you need to integrate with AngularJS out-of-the-box bindings, component configuration, directives, template directives, form validation, event handlers and much more and yet Kendo UI tooling does not depend on AngularJS. So, if you want to use it with Angular or not, that’s totally up to you. You can check it out at KendoUI.com]_**

**CHUCK:&nbsp;** Hey everybody and welcome to episode 102 of the Adventures in Angular Show. This week on our panel we have Lukas Reubbelke.

**LUKAS:&nbsp;** Hello.

**CHUCK:&nbsp;** I'm Charles Max Wood from DevChat.TV. Quick shout-out about Angular Remote Conf - AngularRemoteConf.com. We have two special guests this week. We have Roy Sivan. I hope I said that right.

**ROY:&nbsp;** Yes, Sivan.

**CHUCK:&nbsp;** And Ryan Sullivan.

**RYAN:&nbsp;** Hey, how's it going everybody?&nbsp;

**CHUCK:&nbsp;** Do the two of you want to introduce yourselves real quick?

**ROY:&nbsp;** Sure, I'll go first. My name is Roy Sivan, as you said. I'm currently a Senior WordPress or I guess a Senior Software Engineer was what they called me. But I'm really just a WordPress developer at Disney. I've been using WordPress since, I think .7 was the first version I installed or somewhere along those lines. I've been using it ever since.

**RYAN:&nbsp;** I'm Ryan. I run a company called WP Site Care. I have been using WordPress and just been in software development, more on the systems engineering side for better part of the decade now, and just happen to be here.

**CHUCK:&nbsp;** Awesome. So we brought you on to talk about WordPress and Angular which I'm sure WordPress is the first thing that people think of when they hear Angular or vice versa.

**ROY:&nbsp;** Right.

**CHUCK:&nbsp;** So I'm really curious. I mean, I can see using Angular to manage layout and things which is sort of where I've gone with it on some of the stuff that I've done with WordPress and Angular, but I haven’t gone very far down that road. But it seems like it would also be kind of handy if you could access the data with Angular. So I'm really curious to talk about how you manage all that stuff. Do you want to just paint the picture? I mean, am I being narrow-minded about how you would Angular with WordPress? How do you approach this?

**ROY:&nbsp;** Ryan, if you want to take this first?

**RYAN:&nbsp;** Yeah, sure. There are a number different ways. You're not being narrow-minded at all when you talk about being able to access data. We haven’t done this specifically with Angular in our company, but we have used WordPress and the REST API and built a number of standalone JavaScript apps for pulling in data using WordPress as kind of a CRM data store and using JavaScript to pull that information and make it readily accessible and quickly updated and look pretty too. There's definitely a bridge for being able to access data that's stored in WordPress with JavaScript.

**ROY:&nbsp;** I think the most important thing to think about that maybe most people don’t know yet is that there is a REST API that exists for WordPress. It's currently making its way into core. Half of it's in core, half of it's still kind of being developed or redeveloped for a second or third time. But that’s really the bread and butter for getting the data out of WordPress in a JSON fashion, like with a JSON object. And that’s where your Angular factors are going to connect to and they're going to work with.

When I first started working with Angular, the API didn’t exist yet. So I was doing things with admin-ajax which is kind of like the other way of doing ajax called with WordPress and just returning JSON objects back. And now, API is so much more robust than just that. So it's definitely a good way to leverage WordPress with any kind of JavaScript framework.

**CHUCK:&nbsp;** Interesting. So, if you're working with a system, you're going to build stuff with Angular on top of WordPress just kind of browsing through the REST API information, it looks like they have cookie authentication which you can use if it's just like a plugin or theme that’s running on the side. So, it's same domain, no big deal. And then you’ve got OAuth to authenticate the other way. So, if you have an external app or a mobile app, you can do it that way.

**ROY:&nbsp;** There are a couple of ways to do authentication. OAuth, I think it's still being worked on/OAuth is always a pain in the butt in my mind. I always try to avoid it at all cost. The one thing that WordPress does have also built in is the Nonce system. Basically, it's just a way to create a simple way to say, "Okay, if this matches up with what our record is, then this is a verified response or request."

Again, if you're really worried about security, what we've done in high security website [inaudible] the API will close off all access to the POST request. That way, no one is updating or essentially has no access to put in data but leaving the GET request open. Even with authentication, you can't get even to do a POST request, you have to kind of do that manually or just use the WordPress dashboard and we only leave it open for GET requests. So that was one of the more extreme cases where I've seen the security aspect of it come into place.

**RYAN:&nbsp;** I'll just jump in real quick. We have used OAuth quite a bit just for a number of different reasons but we needed kind of more persistent data. Like I said, we're using WordPress as a CRM and we use a service in the middle called Hire Otto. Shout out to Nathan, he did a great job with that. What it does is it handles the authentication piece and then we tie in to a number of third party services like Asana and Help Scout and a number of other services and use the data from our CRM and kind of sync it universally almost like super fancy as Zapier type of approach and that's a place where we found that we kind of needed that persistent authentication with OAuth. There wasn’t really no other way for us to handle that.

**CHUCK:&nbsp;** That's interesting. It’s funny because I think the more common case is going to be where you're putting it into your theme. But I can also see where people might be using Electron with Angular or Ionic or something where they're going to be sitting outside. So yeah, OAuth or the Nonces make sense there as well.&nbsp;

What kind of data can you get out of a WordPress setup? I mean, generally I think people are somewhat familiar but you have pages and posts, and then you have categories and tags. And if you get real fancy, you can actually put custom fields on different entities like the posts and pages, and you can set up custom types. And so, you can start to expand the types of data that are in the system. Can you access all of that through the API?

**ROY:&nbsp;** Yeah. It's really easy to kind of out-of-the-box have a good solution for the default data that's there. You don’t need to do much coding to actually get custom post type to be viewable within the API ecosystem. I think it's just one line and your definition of your custom post type. You can even do it after the fact. So you can even take your post tag that someone else created, let’s say their plugin and then add in API accessibility to it.

But what I do with it is I create custom endpoints. I have a lot of plugins and a lot of things that I put it on with that they don’t even deal with the data per se. The endpoints are there to probably create and read the post data but actually interact with another API, and then interact like take that data, have it interact with the post type then the response will be something completely custom altogether. That’s where a lot of the power comes into place, is really leveraging other APIs and putting them all together with your WordPress data.

**CHUCK:&nbsp;** Once you've kind of customized your API, then how do you start plugging Angular into it?

**ROY:** &nbsp; For me, it’s just frontend. I use Angular heavily on the frontend. So, I'll use all of the API, I'll create anything I need out of that. And then Angular will say either in a theme. Depending on my setup, it will either be a theme or something I'm actually working on with Josh Pollock, who is an awesome API speaker and knows a lot about the API as well. We're working on a completely decoupled frontend. Basically, the configuration of your JavaScript will include your URL but the "website" itself, the thing that we're building will be completed decoupled. So it can sit somewhere else on another domain or somewhere completely separated out from your WordPress site.

And then again, you integrate it with other data and you can have kind of your full-fledged whatever application you're building with your WordPress data and other API data all kind of combined and put together nicely. I don’t know if Ryan uses any other way but that’s how I use it.

**RYAN:** &nbsp; I want to set the record straight and clarify right now that I'm not coding anything. This is all stuff that my development team has worked on. We haven’t used Angular specifically as much but I know that there are a number of interesting projects that are using Angular. One of the things you mentioned, Chuck, was Ionic. A really cool product that people should check out is AppPresser which will take your WordPress website and create a native app with it. It has a lot of really interesting applications in eCommerce. So, you'd be able to kind of have a native application that’s living on somebody's phone where [inaudible]. So, there's a whole bunch of different ways that it can be used.&nbsp; And really, they kind of follow very closely to the same type of ways that you would use Angular on the tone. It's kind of just an interesting way to have a sort of data store but also to have like Roy was describing, some kind of more dynamic frontend that can tie together lots of different types of data from different sources.

**CHUCK:** &nbsp; Yeah, this is really interesting to me just from the sense that I just moved about a month and a half ago. I moved DevChat.TV which hosts this podcast among other things over to WordPress. And I've been looking at building a mobile app and maybe a desktop app and I've been looking at Electron and NativeScript with Angular or Angular2 in particular. And so, I've been really curious about what these capabilities are, and the fact that you can actually go out of your way and do this and then use a technology as powerful as Angular to manage a lot of the workflow and layout and things like that. For me, it's encouraging because there are options here that I don’t know that I would have had otherwise.

**ROY:** &nbsp; I always said when I first started talking about Angular and WordPress, this dates back – when I take a look at my blog, it's probably 2013/2014 when I first started. And so, I really thought of it as WordPress as an MVC framework but if you take Angular and you have to deal with the kind of view layer and the controller layer, WordPress itself can just be the model layer which allows you to really decouple WordPress from whatever it is you're building and allows you to have, let's say, the WordPress interface which you might like to upload new podcasts or new data or new posts. It allows you to really leverage whatever you want on the frontend. And whether it's a native app or a web application, whatever it may be, you're allowed to take all of the stuff integrated with Angular just like everyone else does. But in the back of the model layer, it’s all WordPress. That’s what's dealing with the database.

**LUKAS:** &nbsp; The question that I have is can you – so by introducing this REST API kind of changes the game. I know you were talking about hooking it and integrating it with other third party REST APIs that kind of do this Zapier thing. One of the reasons why I love WordPress is because the ecosystem is so rich. In other words, I need to do this thing. There's probably a plugin for that to do that for you. Can the REST API interact with installed plugins in your WordPress site? Or what's the inter-op between the REST API and the plugins that you have?

**RYAN:** &nbsp; I can jump in on that. It all depends on the specific plugin and whether it's been built to handle that. I know specifically with our use cases when we're integrating with Help Scout, Asana, Harvest and a number of these other third party services, we built custom plugins that that was their single purpose, was to be the interaction and drive. That was the single purpose of the plugin was to interact with those third party services. I would say it's definitely a possibility and there's definitely ways to tap into the functionality of each of those individual plugins, it's just a matter of whether or not the developer has kind of built it that way.

**CHUCK:** &nbsp; If you're building custom plugins, is there a way to do that?

**ROY:** &nbsp; Yeah. If you're building a custom plugin, you can integrate – I think it's the plugin developers' responsibility, is how I would place it. It would be on them to integrate with the API and not the API's responsibility to integrate with every plugin. So a developer who's creating a plugin says, "Hey, I want to be able to have people who want to use the API to do whatever with the data." It would be on them to integrate into that.

Now, if someone doesn’t, it doesn’t mean you can't. There's a lot of great hooks and filters and stuff for the API. So you can always grab that data and kind of create your own little custom plugin which then grabs the data for whatever it is you might want, whatever plugin gets created.

But a lot of bigger plugins nowadays are just doing the integration. I think WooCommerce just transferred over to the REST API. They used to have their own unique API actually, but now I think they're on board with the one that’s coming into core. And a lot of other plugins are kind of doing it following suit. They're kind of allowing their data to be accessed through those single API.

**LUKAS:** &nbsp; I think it's really interesting to me. One of the questions I had when I realized, "Oh, we're actually going to talk about WordPress in Angular," is as a content platform, I think WordPress is one of the best. That’s what my blog is on One Hungry Mind which really did well. And so originally, my questions were going to be like 'how am I going to use Angular in a blog' thinking in a very centric manner, like how does that look? My next question would be 'why would you even do that' because a lot of things are just right out-of-the-box. I guess you would need to tinker them and you'd just absolutely turn this entire conversation on its head like separate WordPress with the REST API and you can hook whatever you want on the frontend and in so much that you would actually do in Electron Angular application that consumes a WordPress REST API. And I think the rest 15 minutes [inaudible] just kind of exploded. Could you elaborate just a little bit more on taking a third party REST APIs and kind of wiring those together, because this sounds like a [inaudible] of being able to just kind of wire these things up with WordPress and so now you got a product to put to market.

**RYAN:** &nbsp; Definitely, I can talk a little bit about that. What we are doing is, and right now this is something we’re using in production, it's for our own internal use [inaudible] pretty custom needs. What we're doing is we're using WordPress as kind of a master record and we can input information into a number of different places whether we are putting it into Asana or Help Scout.

Help Scout, if you're not familiar, is like a ticketing system. And the problem we were running into was that a lot of the information we needed about our customers was living in other places. So, we had maybe an ongoing development project for them and all that data was living in Asana and we needed to be tracking the hours that we were spending on the project and all that data was living in Harvest. There was no way to really synchronize that data.

The other thing we tied into was Chargify which is a subscription billing system that we use for our customers. It was really difficult for us to be able to see all of our customer information in one place, have it easily accessible. And we tried everything with Zapier but at the end of the day, Zapier is very much copy-paste and we needed all of these data to be synchronized and live in harmony.

So we're able to use the WordPress REST API and take data - we've set up worker jobs that take data from all these different services and synchronize it, and WordPress becomes the master record. And then we use all of that data from WordPress and display it within Help Scout so that we have literally one-click access to Asana projects and we can view from that same dashboard. We can see how many hours we have for current client projects and we can see what their active subscription status is in Chargify.

There's a lot of different data from a lot of different places coming together and just living in harmony, to put it the best way I can, I guess.

**ROY:** &nbsp; I have another use case, kind of two use cases. One was this kind of frontend thing where if you want to build an application. Let's say, I was building out of very user centric application and it was a single page application that lived in one page on WordPress. Like I had a WordPress page that’s called LiteApp and that’s where that lived. And it allowed me to have WordPress do all the marketing materials and the blog. Default WordPress obviously is a very similar thing like basically it's the same style sheet. But I was able to have my blog, have my About page, have all of those marketing pages be default WordPress and that allowed me to have my app kind of consolidated. And with the user authentication, it doesn’t matter where you are on the site. You can always be authenticated into the app. And once you dive into the actual application which dealt with the Stripe payments and stuff like that, that’s where a lot of the interactions come in.

My newest use case which – you're talking about how great you love this thing and how much you love WordPress. My next use case which I want to work on which I have a GitHub repo for but it's not anywhere near done is actually stripping out WordPress admin altogether. So basically, in jQuery, I did body remove everything, and using WordPress data and basically every other API that you can deal with. Imagine you had an A/B testing like – what's it called? What's that really big A/B testing one?

**LUKAS:** &nbsp; Optimizely?

**ROY:** &nbsp; Yeah, like Optimizely, like dealing with their API. Imagine, you could actually create a dashboard which catered towards the person that logged in at that given moment. So if you're a content writer, you can have a content served in dashboard which isn’t WordPress dashboard. It's a completely new dashboard. You could have any list you wanted, you could do whatever you want with it and it's only focused on them. Then you have your accountants come in, they log in, they see the expenses based on all the other APIs you have connected to it. Your marketing team sees the Optimizely data. That’s kind of where I see the next iteration of this whole thing going. We're talking about integrating with other APIs, I don’t see a reason for it to be [inaudible] when you want to click around the WordPress admin to look at data to essentially, the API and Angular to create a brand new dashboard that is seamless for what it is unique to use the system for. Yeah, that’s what I'm going for. So that’s kind of my next iteration of this whole thing. That’s what I think should be what the community is kind of focused on next ideally.

**CHUCK:** &nbsp; I guess my question with both of these examples is how do you get that data into WordPress in the first place that you can display it using Angular?

**RYAN:** &nbsp; We have a couple of different ways. Part of it is right through the admin panel. But with some of the stuff we've set up, we're actually able to write back to the WordPress database from some of these external services. So, there's kind of bi-directionally use that we're working with.

**CHUCK:** &nbsp; Oh, that's interesting.

**ROY:** &nbsp; I think it depends on what you want to do with it. Somebody would want to take the data and store it in the WordPress database. So that way, you have the data locally. I see a lot of use cases not needing that. So, you don’t need necessarily – let's say you're dealing with Stripe, you don’t need all of your customers to be users. That might not be your use case. So you don’t need to store all of your customers in Stripe into your WordPress dashboard. You can take that data from the API, integrate it into the data from WordPress using one singular factory. So you do like whatever factory name is .query or whatever, have that call both API responses and then display that as one object doing it is whatever you need to do.

With the REST API with WordPress specifically, I might do that. I might create an endpoint which would go get Stripe customers or let's say Stripe transactions and I might go to WooCommerce locally, connect those two and then spread a custom JSON object which is a customer's transaction or whatever it might be. It's [inaudible] at that point.

So, I think that’s where you're going to start more of the integration. I don’t think you always have to think of 'how do I store it in WordPress' because you don’t always need to store in WordPress.

**CHUCK:** &nbsp; Let me talk about the use case that I'm thinking of here, and that is that I keep track of the download numbers for the podcasts in Keen.io which is a service that just tracks statistics, stores it as a JSON object, you can pull it back out as a JSON object. So what you're telling me is that I could actually just set up Angular to go and grab that data directly out of Keen and display it as part of my WordPress page instead of going through WordPress. Or would I set up a WordPress API and point it as kind of a pass through to Keen?

**ROY:** &nbsp; You can do both ways. It's really just your own use case if you find that you want to integrate it with the WordPress API. I'd say the only real reason you would do that is if you want to connect that data to WordPress data.

**CHUCK:** &nbsp; Okay.

**ROY:** &nbsp; If it has no correlation between the two and all you need is just a number from the Keen API response, there's no point in making a separate endpoint in WordPress just for that because you can just call that API directly. You kind of bring up an interesting use case that I'm kind of going to be talking about that I've kind of mentioned before, which is why would you think of this big single page applications with Angular when you can actually have micro applications which are let's say, single view pieces of UI that are on any given page. Like WordPress uses widgets, you can create a little widget which is actually an application that goes and gets your data from that API, displays it, and things like that.

So, [inaudible] be able to kind of think this is always a big picture item, I like pushing Angular as both a big picture thing like build your whole application with it. But also, if you have a small use case like something very small and Angular or JavaScript framework would just do the job better, do that and make it a small micro application which lives inside of your larger WordPress website.

**LUKAS:** &nbsp; I'm so super interested and the question I have is where does somebody go to actually learn how to try this and kind of get their hands dirty? Where's a good place to start to kind of do your 'Hello WordPress Angular' tutorial?

**ROY:** &nbsp; There's a lot of great tutorial sites. I hate to self-plug but I do have a course on Lynda that walks you through very basically how to create a single-page application for blog listing and blog detail page. It might be the best way to just start if you know a little bit of both. That was a good experience. Obviously, there's a lot of other great resources. Ryan, what do you think?

**RYAN:** &nbsp; There are definitely a number of resources. There's some example plugins on GitHub that we could show. I'm just touting some of Roy's work too. His blog is a great resource for finding some of these things and figuring out how to get started and happy to share some of the GitHub repos that have been helpful to us.

And another place as a shameless plug, Roy is actually going to be doing a full-day workshop on tying WordPress and Angular together at LoopConf which is in October. It's a event that we're hosting in Florida and it's primarily for WordPress developers but it's also, like I said, we’re going to be talking about using Angular with WordPress and exploring other interesting ways to use WordPress and kind of build communities with other popular technologies. And so, October 5th through 8th is going to be a fantastic time to learn about that.

**ROY:** &nbsp; As Ryan said, I'm doing a full-day workshop during that with my friend, Josh. Another great resource, Josh Pollock. His website is JoshPress.net. He and I are both big Angular/API people. So, we write and talk about a lot of the same things.

If you are specifically looking at WordPress, again, WordPress.tv has – I don’t say all, but a lot of the WordCamp talks video recorded and ready to go. If you just search for Angular in there, you're going to find some of my talks and probably Josh's talks, and some of the other ones that people have talked about with Angular and WordPress. And so that might be another good place to start as a free resource and figure out just to see what other people have done with it.

**CHUCK:** &nbsp; Are you using Angular1 or Angular2 with WordPress?

**ROY:** &nbsp; Currently, 1. I'm in the process of learning 2 personally. But I'm hoping by LoopConf that I'll have 2, so I can actually do a workshop with Angular2. But I find that it's easier to sell people on 1 because of the WordPress community being – it's a really diverse space with a lot of different levels of talent. So a lot of the lower level developers who are just getting into development for the first time, WordPress being that great platform that you can go from knowing basically no code to being expert. I find Angular is very similar to that especially Angular1 because I can show someone an Angular1 html template and they're like, "Where has this been my whole life? Why can't I do this with WordPress?" And I'm like, "You can. Here, I'll show you."

I like Angular1 for that. It's hard to figure out how to spin it for Angular2 because it's a little bit trickier with the syntax but definitely a lot easier than some of the other frameworks that I play along with.

**CHUCK:** &nbsp; All right. Let's go ahead and do some picks. Lukas, do you want to start us off with picks?

**LUKAS:** &nbsp; Yes, I have two picks this week. My first one is Mailgun.com, and it's basically a transactional email service for developers. I had a use case where I needed to send out a bunch of coupon codes to a list of developers that have attended a workshop and did a little bit of poking around on the internet, I was able to write a very small JavaScript code by basically putting in my coupon code CSV, attendees.csv and just basic parse through it and sent out a custom email to each one of the attendees. I was able to do this in about 20 minutes using Node. Super easy, to anybody who may need to send out a custom email to different people with coupon code [inaudible].

My second pick was Geoff Goodman who has updated the embedded view on the Plunker and it is really, really nice. I think that what he has done with it kind of the file systems and just kind of the [inaudible] that’s in the embedded view on Plunker. I think it's best in [inaudible] and probably the best online collaboration [inaudible] a code out there. So, really good work, Geoff. And those are my picks for the week.

**CHUCK:** &nbsp; Nice. I'm going to pick a couple of books. The first one is Procrastinate on Purpose. I might have picked that last week, I don’t remember. But it's a book that talks about how to make the most of your time. He has five different steps you go through that help you eliminate, automate, delegate – okay, I'm giving away the steps. But anyway, super good. If you're really busy, if you're trying to manage your time and manage what gets done and what's important, then this is a terrific technique for getting more out of your time.

The other one is I tend to listen to fiction when I'm relaxing at night on Audible. And I just started listening to the Harry Potter books again and I'm remembering now how awesome they were and just how much fun they were to read. So, I'm going to pick Harry Potter and the Sorcerer's Stone.

Roy, what are your picks?

**ROY:** &nbsp; Just because I want to re-launch this week, I really want to recommend for WordPress users Postmatic. Jason created Postmatic, he's awesome. We had a great conversation and it's a great tool for both integrating into commenting and it creates a much better commenting system with the default WordPress. It also auto-generates newsletters for new content. So it's kind of like a plugin that has multiple modules but it's a great system and I'd highly recommend it.

The only other thing that I would recommend that I really love this past week was Caldera Forms written by Josh. It's actually his plugin. It was [inaudible] as a form builder and it's fantastic. Great UI, a lot of functionality in it. Those are my two – WordPress plugins but they're definitely high in my mind right now.

**CHUCK:** &nbsp; All right. Ryan, what are your picks?

**RYAN:** &nbsp; I have three but I could get through them quick. The first one is – this might just be a nursing to the folks who listen to this podcast regularly. The entire desktop client for WordPress.com was built in NodeJS, it's called Calypso. Definitely go check that out. They're iterating on that all the time. A really nice desktop client for writing and then posts directly to your WordPress.com blog which is a little bit different than the [inaudible] in WordPress but it's an interesting project overall and interesting to see our company so involved with WordPress building an entire client application in JavaScript. So, that’s cool.

The second one I mentioned before, AppPresser, turns your WordPress site into a native app. Definitely check that out. Scott Bolinger has done a great job with AppPresser and it's a really interesting project that uses a lot of JavaScript to bring your site as a native app.

The last thing I'll mention is our conference. Again, LoopConf.com in October. Lots of development, it's all a single-track development conference and lots of WordPress talk but a lot of OS stuff in the JavaScript world too. We have some great speakers and it's going to be – we know how to do a good time. I'm co-organizing the conference with Joe, who's not here today but we know how to do a conference thing well. Definitely, go check it out.

**CHUCK:** &nbsp; Awesome. If people want to follow up with what you're doing or check out any WordPress plugins you’ve built or see what you're blogging or open-sourcing or tweeting, where do they go?

**ROY:** &nbsp; For me, it's RoySivan.com. Or you can find me pretty much anywhere on social media, GitHub, whatever, it's royboy789.

**CHUCK:** &nbsp; And for you, Ryan?

**RYAN:** &nbsp; ryandonsullivan pretty much everywhere. That’s the best way.

**CHUCK:** &nbsp; All right. For people who want to check out LoopConf, I'm assuming it's LoopConf.com?

**RYAN:** &nbsp; That is correct.

**CHUCK:** &nbsp; All right. Well, thank you both for coming.

**ROY:** &nbsp; Thank you.

**CHUCK:** &nbsp; We'll then wrap the show up and we'll catch you all next week.

**_[Bandwidth for this segment is provided by CacheFly, the world’s fastest CDN. Deliver your content fast with CacheFly. Visit CacheFly.com to learn more.]_**

**_[Do you wanna have conversations with the Adventures in Angular crew and their guests? Do you want to support the show? Now you can. Go to AdventuresInAngular.com/forum and sign up today!]_**


