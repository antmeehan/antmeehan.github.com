---
layout:     post
title:      "Keep Blogging"
subtitle:   "The gaps between posts will get shorter?"
date:       2015-08-15 21:30:00
author:     "Ant"
header-img: "img/post-bg-03.jpg"
comments:   true
---

So it has been a long time between posts, but life has been pretty hectic. Work-wise I've been leading a large project (which has required a fair bit of overtime) so I haven't had much spare time. The project has however <s>moved</s> been dragged into a more continuous delivery model, and as a side-effect of the security system design we have built a simple feature toggle system. Not all bad then, as it has given me further ideas for [FeatureVersioning](http://antmeehan.com/FeatureVersioning). But more on that in a later post.

# cycle-with.me
Today I wanted to get some ideas down for [cycle-with.me](http://cycle-with.me). I went for [ride](https://connect.garmin.com/modern/activity/865666821) with some friends for this first time in a while today. And it is usually on these rides that I spend some time thinking about cycle-with.me (between trying to keep up and doing my part on the front).

Let's start with thoughts on why cycle-with.me hasn't really gained any traction.

**1. No one is using it.** I haven't really "got it out there". Besides telling some friends and occasionally handing out some business cards, and I haven't done anything to get more users signed up. (On an interesting side-note, there was one ride organised in [Gouda](https://www.google.com.au/maps/place/Gouda,+Netherlands) -- I'm not sure how they found out about it in the Netherlands!).

**2. The system is too closed.** Group cycling is a much more inclusive activity. One person may suggest a ride, but the invitation process is much more fluid. Friends invite other friends and the more the better when it comes to participation in a ride.

**3. Email notifications.** Cycle-with.me currently only supports email notifications of invitations to ride and updates to the organiser on invitee responses. While a lot of people have email on their phones these days, the use of OAuth (Strava, Facebook and Google+) has meant that a lot of users have work emails receiving their notifications. Even if someone does get an email, they also need to sign in to respond.

##Ideas for v2
So how can I rectify these issues? Here are some ideas.

**Make the system open.** Remove the requirement to log on to use cycle-with.me. Sure, creating an account should give greater benefits, but the basic use should be as frictionless as possible. This will help spread the word too.

**Make an app.** Everyone loves a phone app. It also makes the next point easier (and cheaper).

**Push notifications.** Email doesn't cut it. SMS is too expensive. People want push notifications, and on iOS I'd like to build the ability to accept an invite as part of the notification, using the extra actions:

![](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/Art/notif_ctr_banner_actions_2x.png)

##How to get there
The challenge of course will be achieving these ideas. The code-base for the current version was very thrown together without much architectural consideration. I've learnt a lot about SOA since then as well. This means re-write from scratch, perhaps just keeping some of the brand design (since I can't afford to pay someone to be my designer).

I'll try to keep blogging more on my progress, as even writing this post has helped a lot.