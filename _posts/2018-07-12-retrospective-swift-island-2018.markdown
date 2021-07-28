---
layout: post
title:  "Retrospective on Swift Island 2018"
date:   2019-07-12 00:00:01 +0100
---

Last week, I had the chance to attend Swift Island 2018, [the very first edition of this event](https://swiftisland.nl), in [Texel, Netherlands](https://maps.apple.com/?q=53.114790,4.897072).

<figure class="image">
  <img src="/images/swift_island/texel.jpg" alt="Photo of Texel with Swift Island Flags">
  <figcaption>Credits: Niels van Hoorn</figcaption>
</figure>

Aside from local meet-ups and an event here and there happening in Lyon ([where we're based](https://h2g.io)), I'm not the kind of guy to attend a lot of conferences, for various reasons.

But when I saw what Swift Island promised, right when they first announced it, something clicked. Was it the location, the mentors, the post-WWDC-hands-on-workshops concept, the biking, the nature, the sheep, the seals, all of the above or something else? I couldn't tell you, but I was sold.

If you're not familiar with Swift Island, here's the pitch as I understood it: WWDC brings excitement and fun, but often it cools down after WWDC week, we go back to our regular schedule, and seldom have time to play with new APIs. We may even end up forgetting or not even testing something that we were eager to get our hands on when announced.

This was made famous by this very, very scientific chart by Niels van Hoorn, one of the organizers:

<figure class="image">
  <img src="/images/swift_island/chart.png" alt="Chart of excitement, fun, and confusion over time between WWDC and Swift Island">
  <figcaption>(Credits: Niels van Hoorn. You can hear the explanation on his talk "ARKit in practice" at MobileWarsaw 2018: <a href="https://www.youtube.com/watch?v=aA4Omx9kAXM">https://www.youtube.com/watch?v=aA4Omx9kAXM</a>)</figcaption>
</figure>

Swift Island aims to break this by having its conf about a month after WWDC, with workshops only.

So after an understandable initial surprise (again, not the conference type I told you, and my colleagues know it!), my boss gave me the go. (👋s to everybody at [H2G Lab](https://signal.h2g.io) by the way!)

Fast forward, and it's Tuesday 3rd of July, in a lovely venue, [right by the Wadden Sea](https://maps.apple.com/?q=53.114790,4.897072).

<figure class="image">
  <img src="/images/swift_island/prins_hendrik_hotel..jpg" alt="Photo of the Prins Hendrik Hotel">
  <figcaption>The venue: Prins Hendrik Hotel</figcaption>
</figure>

Getting on Texel is pretty easy, we were even able to opt for a hassle-free ticket, for which the staff took care of everything: train/ferry tickets, and even an itinerary to get to the location.

Public transportation was easily navigable from Amsterdam to Texel (coming from a french who had never been yet to the Netherlands and doesn't speak a single word of Dutch).

If needed we could easily contact the organization which would answer almost instantaneously and help us.

The hotel staff, the volunteers, and the organizers gave us all a warm welcome, and everything was prepared for our arrival. Clearly, a lot of work was put in, and everything went smoothly.

## Workshops

<figure class="image">
  <img src="/images/swift_island/badge.jpg" alt="Photo of my Siwft Island badge">
  <figcaption>This is how you could identify me 😅</figcaption>
</figure>

Then, the morning after, the workshops began. The format was pretty simple, but unusual enough, and efficient:
- 8 mentors, 8 workshops
- 2 days, 4 workshops each day
- We could pick 3 workshops per day
- Roughly 2 hours per workshop
- Socializing events in the evening and on the third day

The workshops I attended were, chronologically:

### First day
- Siri Shortcuts by [Daniel Steinberg](https://twitter.com/dimsumthinking)
- Dynamic Swift (`@dynamicMemberLookup` and `@dynamicCallable`) by [David Hart](https://twitter.com/dhartbit)
- ARKit Part 1 (basics, object placing, lighting, measuring, physics…) by [Kate Castellano](https://twitter.com/KateCastellano) and [Manu Rink](https://twitter.com/codePrincess)

### Second day
- Machine Learning (fundamental concepts, training using turicreate, Vision framework, and CoreML) by [Meghan Kane](https://twitter.com/meghafon)
- The other new iOS12 frameworks by [Roy Marmelstein](https://twitter.com/marmelroy)
- ARKit Part 2 (mostly focusing on ARKit 2 features: image tracking, multipeer world)

Talking about every single thing I learned throughout those two days wouldn't be possible, and I don't think anybody would be interested anyway. So I'll have to trim it down to what impacted me the most. Please keep in mind this restitution is purely subjective, on my sensibility about the topics, and what I can/envision to use day to day.

Again, let's do it chronologically.

- Daniel helped us dive deep in Siri Shortcuts, and we pretty much covered everything this (crazy) new API has to offer. I genuinely think Siri Shortcuts are gonna be big for power users, perhaps for everybody, and change how we interact with our pocket computers. They just might make Siri actually useful for me! (oops 🤭)
- Kate and Manu prepared so many things. They really made it straightforward and taught us in the best way possible. I never touched ARKit nor SceneKit before the workshop, and I was able to follow, understand, and apply what we were doing. Plus they provided some great tips and tricks, optimizations. The project ideas were great: multi-user synchronized scrum board on a wall, and making the animated Harry Potter newspaper.
- Meghan took us from nothing, explained some concepts of machine learning (tailored to her audience: we asked so much questions it became pretty much a conversation). Then we trained our own models with turicreate (through a nice and intuitive interface via a [Jupyter Notebook](https://jupyter.org)) to detect whether a painting was from Dali or Van Gogh. (Yes, a nice Dutch touch 😉). Finally, through transfer learning, we were able to take a picture and Van Gogh-ify it.

I have to mention that in every workshop I attended, a lot more material was available, I talked above just about what I _individually_ was able to do.

Over the last few years, I noticed I enjoyed much more going to workshops rather than talks. It is perhaps due to the fact that the number of talks available online grew exponentially. At any rate, locking a few hours to dive into a topic under the training of mentor in an experience I would definitely recommend. To illustrate this, look at what an attendee made by combining two workshops, right on site:

[A picture is taken, Van Gogh-ified using ML, then framed on the wall with ARKit. Pretty sweet isn’t it?](https://twitter.com/brunoscheele/status/1015561061339205632)

### Socializing

Of course, while attending such an event, one the main aspects is to get yourself acquainted with new people, share experiences, talk about our field, our products, projects.
Well, it clearly was a success as well, I met so many incredibly interesting people, whom I hope will stay friends in the years to come. (hopefully I wasn't too pushy talking about our new product, Shuttle, _your custom build management and distribution platform_ 😅. By the way, you can still sign up for our private beta here ➡️ [https://www.shuttle.tools](https://www.shuttle.tools))

Talking with insightful people from various parts of the world, and various working environments: freelancers, workers for small to huge companies, allowed me to broaden my thinking, get a sense of belonging, and make connections that I believe will be valuable both in my personal and professional life. Don't get me wrong: I know that this side effect is not exclusive to this conference, but I do believe that the overall setup made it easier to happen, and in particularly enjoyable contexts.
One crucial aspect was that thankfully, I didn't notice any wrong behaviour or toxic culture that is sometimes encountered when a lot of people suddenly gather in a small place. The organizers established a clear Code of Conduct pretty early in the process. Shout out to them for that! Inclusivity and diversity were attending Swift Island as well. 😉

[Here's a thread that expresses a general feedback I would concur with.](https://twitter.com/abizern/status/1015527893475254272)

After the last workshop, a good bunch of attendees (yours truly included, although for full disclosure I have to mention I had an e-bike) made it to the lighthouse riding our bikes.

<figure class="image">
  <img src="/images/swift_island/lighthouse.jpg" alt="Light House of Texel">
</figure>

### To sum it up

By now you probably got it: I had a great time at Swift Island. The idea behind it was on spot, and the execution met my expectations. I came back inspired, confident about what I learnt, and happy to have met new like-minded friends.

Of course, like in every event, there were some hiccups, but pretty minor in my opinion. WiFi was… let's say, _challenging_, but it didn't really impact the workshops, since many USB sticks were prepared so that every trainee could get the material without network access.

I can't thank enough the organizers: [Sidney de Koning](https://twitter.com/sidneydekoning) and [Niels van Hoorn](https://twitter.com/nvh), for putting together such a great event, always with a good mood and answers to our questions, before, during, and after the event. Of course they weren't the only ones involved, so huge thanks are in order for the volunteers as well, the hotel staff, the mentors, and the attendees, whether we met or not.

Finally greetings to everybody I got to know, in the order I met you (yeah I know… but ordering is a big deal for me!): _Naufal, Esther, Fernando, Niels, Ellen, Daniel, Sidney, Donal, David, Kate, Manu, Nabil, Paul, Meghan, Audrey, Shuichi, Chris, Boris, Marijn, Vinh_, and everybody I may have omitted (and sorry about that if that's the case).

[Look at us, aren't we cute?](https://twitter.com/SwiftIslandNL/status/1015119668007317504)