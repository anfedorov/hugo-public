+++
date = "2015-12-28T11:33:01-08:00"
title = "The Economics and Politics of Free Basics"
+++

Facebook's Internet.org brand is [starting to go away](http://www.wired.com/2015/09/facebook-renames-controversial-internet-org-app/). Good. The initiative is not the internet and it's not a non-profit organization. It is [the "free" model](http://geekandpoke.typepad.com/geekandpoke/2010/12/the-free-model.html) applied to a curated micro-network like the earlier incarnations of AOL, and it's now called Free Basics. This is a significantly more honest name, and for that, Facebook deserves credit. Honest PR is good PR because it allows us to move past semantics and into the politics and economics of the project.

The heart of the argument is that for the un-networked world, Free Basics is obviously better than no network. This is true only in the extremely short term. Everybody agrees that connectivity is a pre-requisite for equality and that we want to work towards everyone having access to the internet. The open question is how we expand our current network to them and — most importantly — who pays for it.

A network paid for by foreign business interests and advertisers will be fundamentally different than a network paid for by its users (i.e. where the customers are also the consumers). But even with fundamental differences, Free Basics and user-funded internet access are in many ways *substitute goods*, meaning the presence of one will reduce the spread of the other. By the simplest economic reasoning, in the long term, Free Basics will hurt the spread of user-funded networks like the internet, just as [free clothing hurts local textile industries](http://www.cnn.com/2013/04/12/business/second-hand-clothes-africa/). And the more sites join the Free Basics platform, the more competitive it will become.

By considering the interests of those paying for the network's deployment, we can predict what their fundamental differences will be. It is not in the set of sites included in Free Basics, as the interests there align: more sites are better, and full internet access is best. The modern advertising industry's endgame is in modeling and manipulating user behavior on an individual level, and so the fundamental differecene between user-funded networks and advertiser-funded ones will be in the design decisions around the privacy intersts of the users.

To see how this theory plays out in practice, let's take a look at [the techincal details of Free Basics](https://developers.facebook.com/docs/internet-org/platform-technical-guidelines):

> When people use the Free Basics Android app, their traffic is encrypted end-to-end

End-to-end encryption is great, but in their app, because it's their app, Facebook can track your every tap and scroll. Even if they don't do it now, it would certainly be in Facebook's busines interests in the long term, if they find a way to brand it nicely. This would be similar to their use of the "Like" button, the loading of which they started tracking only after adoption spread enough for the benefit of data gathering to outweigh the costs of [bad PR](http://jasonlefkowitz.net/2011/10/dont-worry-about-selling-your-privacy-to-facebook-i-already-sold-it-for-you/).

> For the Free Basics website in a mobile browser, we use a “dual certificate” model

For traffic that doesn't go through their app, Facebook decrypts, intercepts, and re-encrypts it. This interception allows for the filtering of content which might be high-bandwidth. It *also* allows for individualized monitoring on a massive scale, and with that thought, we get to the key sentence:

> We preserve the privacy of that information while it's decrypted by only storing the domain name of your service and the amount of data being used—the same information that would be visible using end-to-end encryption—as well as cookies that are stored in an encrypted and unreadable format.

That's a lot of distraction. Allow me to rephrase more succinctly:

> We record which site was visited, the amount of data used, and cookies.

For public sites (e.g. wikipedia, news), knowing the exact size of the payloads usually identifies the page, and cookies are how other ad networks keep track of who you are and often the consumer segments you've been placed. I'm not sure what the point of storing something "in an encrypted and unreadable format" is, so I'll assume they also store the decryption key and that language is just a decoy. The general implications seem clear: Facebook will know more about Free Basics users than anyone else, and will therefore be able to advertise to them better than anyone else. While Facebook might not take advantage of it until adoption reaches a point where the benefit of using this data outweighs the PR costs, there seems to me little doubt that their business interests and user's privacy intersets are fundamentally at odds.

Practically, the costs and benefits of Free Basics have no obvious answer one way or the other, as they depend on the extent to which machine learning is able to model human behavior, the political systems of the countries where it is being deployed, and a multitude of other factors. I do think it is important to look at the nuanced trade-offs honestly and dispassionately and not pretend or argue that either option is an obvious win.
