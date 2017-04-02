+++
date = "2016-02-21T09:38:27-08:00"
menu = "main"
title = "The Economics and Politics of Free Basics"
linktitle = "Free Basics"

+++

### Facebook Internet: a nutshell

Facebook's Internet.org brand is [starting to go away](http://www.wired.com/2015/09/facebook-renames-controversial-internet-org-app/). Good. The initiative is not the internet and it's not a non-profit organization. It is an advertiser funded micro-network, similar in function to earlier incarnations of AOL, and it's now called Free Basics. This is a significantly more honest name, and for that, Facebook deserves credit. Honest PR is good PR because it allows us to move past semantics and into the politics and economics of the project.

The pitch is encompassed in the name: basic internet services, like WhatsApp and Facebook and Wikipedia, provided free to users. At the heart of the argument is that for the currently un-networked world, any network is obviously better than no network.

This is true only in the extremely short term, however, because while everybody agrees that connectivity is a pre-requisite for equality and that we want to work towards everyone having access to the internet, the question which remains open is how we expand our current network to them and — perhaps more importantly — who pays for it.

### Network Expansion: paid by users or paid by advertisers

A network _paid for by users_ will be fundamentally different than one _paid for by advertisers_, but similar enough that they are *substitute goods*, meaning the presence of one will inhibit the spread of the other. By the simplest economic reasoning, in the long term, Free Basics will hurt the spread of user-funded networks like the internet, just as [free clothing hurts local textile industries](http://www.cnn.com/2013/04/12/business/second-hand-clothes-africa/).

We can predict these fundamental differences by considering the interests of those paying for the network's deployment. In particular, the difference will *not* be the set of sites included in Free Basics, as the interests there align: more sites are better, and full internet access is best. While Free Basics will likely become Free Internet, the real difference stems from the modern advertising industry's north star: modeling and targeting consumer beliefs and behavior. Therefore, the fundamental differences between user-funded networks and advertiser-funded ones will likely be in the design decisions around the privacy of the users.

### Privacy interests in practice

To see how this theory plays out in practice, let's take a look at [the techincal details of Free Basics](https://developers.facebook.com/docs/internet-org/platform-technical-guidelines):

> When people use the Free Basics Android app, their traffic is encrypted end-to-end

While end-to-end encryption prevents monitoring by intermediaries, Facebook can track your every tap and scroll in their app. Even if they don't do it now, it would certainly be in Facebook's business interests in the long term, as long as they can find a reason. This would be similar to their use of the "Like" button, the loading of which they started tracking only after adoption spread enough for the benefit of data gathering to outweigh the costs of [bad PR](http://jasonlefkowitz.net/2011/10/dont-worry-about-selling-your-privacy-to-facebook-i-already-sold-it-for-you/).

> For the Free Basics website in a mobile browser, we use a “dual certificate” model

For traffic that doesn't go through their app, Facebook decrypts, intercepts, and re-encrypts it. This interception allows for the filtering of content which might be high-bandwidth. It *also* allows for individualized monitoring on a massive scale. With that thought in mind, we get to the key sentence:

> We preserve the privacy of that information while it's decrypted by only storing the domain name of your service and the amount of data being used—the same information that would be visible using end-to-end encryption—as well as cookies that are stored in an encrypted and unreadable format.

That's a lot of distraction. Allow me to rephrase more succinctly:

> We record which site was visited, the amount of data used, and cookies.

For public sites (e.g. wikipedia, news), knowing the exact size of the payloads usually identifies the page, and cookies are how other ad networks keep track of who you are and often the consumer segments you've been placed. I'm not sure what the point of storing something "in an encrypted and unreadable format" is, but it seems safe to assume that if a segment cookie marks all the users a data warehouse considers lesbians, Facebook's models will include it even if they don't says "lesbian" explicitly.

The general implications seem clear: Facebook will know more about Free Basics users than anyone else, and will therefore be able to advertise to them better than anyone else. While Facebook might not take advantage of it until adoption reaches a point where the benefit of using this data outweighs the PR costs, there seems to me little doubt that their business and user privacy are fundamentally at odds.

### Final Thought

Practically speaking, the costs and benefits of Free Basics appear to have few obvious answers one way or the other, and depend on the extent to which machine learning is able to model human beliefs and behavior, the political systems of the countries where it is being deployed, and a multitude of other factors. I think it is important to look at the nuanced trade-offs honestly and dispassionately and not pretend or argue that either option is an obvious win.

### Ackgnowledgements

Thanks to everyone who proofread this. An earlier draft of this post is [here]({{< relref "post/free-basics-0.md" >}}).
