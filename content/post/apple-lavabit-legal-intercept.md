+++
date = "2015-10-11"
title = "Apple, Lavabit, and Legal Intercept"
linktitle = "Apple, Lavabit, Legal Intercept"
+++

This post summarizes my thoughts about what seem to be persistent misunderstandings about Apple's iMessage and FaceTime cryptographic system and their relation to Lavabit's legal case. The post ends with some history as well as opinions about security as it pertains to communications infrastructure.

# Apple

Apple says they couldn't comply with a wiretap order on iMessage and FaceTime [even if they wanted to](http://www.apple.com/privacy/privacy-built-in/), but Nicholas Weave, echoing an idea often repeated, [says otherwise](https://www.lawfareblog.com/iphones-fbi-and-going-dark):

> [...] to tap Alice, it is straightforward to modify the keyserver to present an additional FBI key for Alice to everyone but Alice [and] an FBI key to every request Alice makes for any keys other than her own.

> [...] Apple’s architecture for iMessage supports wiretapping

He is right that Apple could intercept your communications if they wanted to because they control the key servers that introduce the callers to each other. They can also do so because they made the hardware and software you use to make the call.

The big difference between that and a wiretap is "can the government order them to do so?", and the answer is "no". Even if they could, because the protocol can be [reverse engineered](https://news.ycombinator.com/item?id=6435902), a sophisticated enough target could analyze the traffic to see the extra key.

I understand that Nicholas is not a lawyer and so might not realize that "wiretap" has a very specific legal definition. Neither am I, but I think it goes something like this:

- It's a power we've decided to give investigators
- once they get approval from a judge
- to order communications to be copied over to them.

In security lingo, a wiretap allows investigators and judges to order a company to perform a [passive attack](https://en.wikipedia.org/wiki/Passive_attack) on information flowing through their systems.

I imagine the reasoning for giving judges this power is very much like that of a subpoena order used to hand over information or compel testimony related to a case. But there is no legal reasoning which justifies ordering someone to lie, be it to their friends or family, customers or business partners. This is as true for Apple's key servers as it is for an online search for a doctor. Ordering people or companies to lie is simply not the kind of power investigators or judges have [1].

# Lavabit

Lavabit's "secure" email system's design was flawed in light of the laws they operated under. I'm not wholly sure why Snowden (allegedly) chose to use their service, but it almost certainly wasn't because he expected his emails to remain hidden from a federal investigation.

At the crux of Lavabit's failure is that they didn't use [forward secrecy](https://en.wikipedia.org/wiki/Forward_secrecy) on their https connections, something OpenSSL has supported [since 2011](http://googleonlinesecurity.blogspot.com.au/2011/11/protecting-data-for-long-term-with.html). This means that handing over their private key rendered all of their user's traffic retroactively insecure.

So when a judge ordered Lavabit to hand over their key because it fit the definition of information pertaining to a crime, they responded with the legal equivalent of a hissy fit. After some fines and what I imagine as stern talks from their lawyers boiling down to "unless you want to go to jail for a while, you should obey the judge's orders", they decided to forgo the promises made to their users, hand over their private keys, and close shop.

Had Lavabit used forward secrecy, they would have been in a significantly stronger legal position to protect their customer's privacy because a judge cannot order them to keep using a compromized key, and forward secrecy would ensure the key wasn't useful retroactively.

# More than wiretaps

Although it's outside of the scope of the point I'm trying to make in this article, it's important to note that the executive has other tools at their disposal for extraordinary crimes like terrorism, espionage, and sophisticated criminal conspiracies.

The legal details here vary, but there are [administrative subpoenas](https://en.wikipedia.org/wiki/National_security_letter), which could force an Apple employee to hand over their private key without telling the company [2], [executive orders](https://en.wikipedia.org/wiki/Executive_Order_12333) which reorganize the rules that the executive agencies work under, and plain old hacking authorized by [AUMF's](https://en.wikipedia.org/wiki/Authorization_for_Use_of_Military_Force_Against_Terrorists). Checks on these are significantly more complex because they involve disclosing secret techniques and methods to more parties, sometimes even the targets, and so using them is not wise for the prosecution of ordinary crimes.

As long as there exist extraordinary crimes, investigator require extraordinary powers to combat them. Of course checks on these powers are needed, but they are fundamentally different from those on a wiretap order.

# Some History

While state sponsored hackers and the like are interesting, the availability of end-to-end crypto affect us immeasurably more day-to-day. The most complete evaluation of cryptographic communications I can find was [done by the EFF](https://www.eff.org/secure-messaging-scorecard). In this section, I want to add some history to the services you have likely heard of:

### Microsoft's Skype

The original architecture of Skype as released in 2003 had a peer-to-peer network and needed to be end-to-end encrypted so that routing peers couldn't listen in on calls. The eBay acquisition in 2005 did not include the p2p network that routed these calls, and Skype remained an end-to-end encrypted service until Microsoft acquired it in 2011 and replaced the p2p infrastructure with one that routes all calls through their servers.

### Google's Hangouts

A similar story happened with the [Gmail voice and video chat plugin](http://gmailblog.blogspot.com/2008/11/say-hello-to-gmail-voice-and-video-chat.html) introduced in 2008, which connected callers directly over the internet and so required end-to-end encryption for similar reasons. That was deprecated and replaced with Hangouts in 2013, which routes all traffic through Google servers. Although I hear that Google intends to again provide end-to-end encryption by default in the near future, their currently mass-deployed systems all include access to the contents of the message and are susceptible to wiretaps.

### Facebook's Messanger

Facebook's messenger started by using Microsoft's Skype technology and recently replaced it with their own centralized routing infrastructure. As far as I can tell, end-to-end crypto and challenging wiretaps has never been on Facebook's radar.

### Apple's iMessage and FaceTime

Apple has the largest deployed telecom system which uses end-to-end crypto and is not susceptible to wiretap orders. Unlike Lavabit, though, Apple seems to have checked the laws before building the system, not after receiving a subpoena. In jurisdictions where such systems are illegal (e.g. Saudi Arabia) Apple [disables FaceTime entirely](https://support.apple.com/en-us/HT204042).

### Blackberry's BBM Protected

The enterprise messenger from Blackberry, [BBM Protected](http://us.blackberry.com/enterprise/products/bbm-protected.html) was introduced in 2014 with end-to-end crypto for chats. Although I haven't used it personally, I hear it's quite popular in the business world.

### Open Whisper Systems

[Open Whisper Systems](https://whispersystems.org) also provides end-to-end cryptography on voice calls and text chats, but relatively few people use them. The biggest design difference between their system and the two before is that they have released their source code, meaning finding weaknesses in their design or implementation doesn't involve any reverse engineering and so is cheaper both for security researchers and attackers alike. Given their relatively limited resources and deployment, this trade-off makes a lot of sense.

# Opinions

A security system is like a chain in that it is as strong as its weakest link.

There is little contention that adding support for wiretap orders to communications infrastructure increases the number of links in its chain and so can only decrease its security. This is especially true against passive attackers acting not wholly within the law, such as in cases of [foreign espionage](https://en.wikipedia.org/wiki/Operation_Aurora) or [sub-legal intercept](http://cdn01.androidauthority.net/wp-content/uploads/2014/06/SSL-Added-and-Removed-Here.jpg).

Let's look at a couple of links in this chain:

- *The Superusers*: People who have access to internal tools need to have that access logged and reviewed. If they interact with strangers, they should be aware of possible phishing attacks. This is pretty obvious, not enormously costly, and straightforward to implement.
- *The Coders*: Reviewing each other's code before deploying it is standard practice for software engineers, as is keeping a version history of who changed what and when. This makes sneaking backdoors into code a relatively high-risk attack.
- *The Sysadmins*: Someone connecting to a production server and downloading data without a trace can usually do so with significantly less risk of being caught. Tools that would allow one to record or mirror raw network traffic going to and from a machine are standard on most production systems because they are necessary for debugging. Forcing sysadmins to pair is one possible way to address such an insider problem, but is relatively costly. Modeling traffic patterns on production machines is another, which leads to a relatively complicated disguise / detect with a second level of security / insider problem.
- *The Datacenter Technicians*: I'm not totally sure what goes into the physical security of a datacenter, but add to the chain all of the people with unchecked physical access to the hardware.
- *The Hardware Manufacturers*: I know next to nothing about this, just that manufacturers might ship corrupted hardware.

Now, ask yourself "how strong is the weakest link?". There sure are a lot of them, and many are human! This is why organizations who care about building highly secure systems do extensive background checks on every employee, rejecting anyone with any potential for blackmail or undue influence, and even then [make them pair up](https://www.schneier.com/blog/archives/2013/07/nsa_implements.html). I have yet to hear of this being done in the private sector, even at companies which may soon be [handling the metadata of all of our phone calls](https://www.washingtonpost.com/news/the-switch/wp/2014/05/22/nsa-reform-bill-passes-house-despite-loss-of-support-from-privacy-advocates/).

The costs of background checks and access reviews is real and measurable. There is also the less quantifiable but very costly atmosphere of distrust between coworkers that pairing entails. Unlike a background check at the entrance which creates an in-group of trusted people, pairing enforces a mindset between colleagues as potential adversaries trying to sneak one past you.

Many of these costs can be mitigated by using end-to-end encryption. In particular, if the datacenter never sees the plain text of the message, the majority of passive attacks by insiders vanishes. Active attacks are still possible, but significantly more risky for the attacker.

While it's important to acknowledge that legal intercept is an enormously valuable tool used by law enforcement today in a variety of circumstances, it's also worthwhile to realize that its value is decreasing every year and that it's nearly worthless against even moderately sophisticated actors. The costs of maintaining highly secure systems which also support wiretaps is more than most, if not all, private companies are willing to bear.

It might be time to look at the costs to productivity and security of supporting wiretap orders which only works against unsophisticated actors anyway, and ask whether we will prosper more by building communication systems which support end-to-end encryption for everyone, instead.

End-to-end encryption is not new. It has been available to techies for decades, broadly deployed by Skype from 2003 to 2011, and now by iMessage and FaceTime since 2012. While it's true that both technologies have been used to make [some criminal prosecutions more difficult](http://www.theregister.co.uk/2013/04/04/leaked_imessage_memo_dea_denied/), they have most certainly been used to protect the targets of attacks, as well.

[1] This is not to be confused with a gag order, where a judge can order someone to keep from commenting publicly on a legal matter, or keep quiet about something else.

[2] Unlikely, if their legal orientations are anything like Google's. Another possibility is that Apple receives and complies with a subpoena but does not change its private key.

*Earlier versions of this post erroneously mentioned a subpoena issued to Lavabit where the courts had actually used a [pen register order](https://www.law.cornell.edu/uscode/text/18/3123) to get Lavabit's encryption keys.*

*Thanks for reading. Feel free to [shoot me an email](mailto:me@anfedorov.com) with corrections, questions, or thoughts.*

*Thanks, also, to everyone who proofread and provided feedback on this post. This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](http://creativecommons.org/licenses/by-nd/4.0/).*
