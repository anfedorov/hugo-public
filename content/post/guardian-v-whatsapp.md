+++
date = "2017-02-01"
menu = "main"
title = "The Guardian v WhatsApp"
linktitle = "Guardian v Whatsapp"
+++

### What happened?

- Nathaniel Mott wrote and The Guardian published [a false story](https://www.theguardian.com/technology/2017/jan/14/whatsapp-vulnerability-secure-messaging-apps) about a WhatsApp "vulnerability" that's more accurately described as a security trade-off appropriate for about 99.99% of their users and recommending folks use Signal instead.

- Outrage ensued, culminating in [a rebuttal](https://whispersystems.org/blog/there-is-no-whatsapp-backdoor/) by the Signal protocol's author and [an open letter](http://technosociology.org/?page_id=1687) calling for an apology and retraction, co-signed by 72 academic and industry experts.

- The Guardian [doubled down](https://www.theguardian.com/technology/2017/jan/16/whatsapp-vulnerability-facebook) with an article by Tobias Boelter, the grad student responsible for the original claim, mis-representing the rebuttals as semantic arguments over what constitutes a "backdoor".

### The Wrong Approach

While the technical parts of Mott and Boelter's falsehoods have been addressed well, the legal and political angle seems to have been missed.

For those who care about this sort of thing, WhatsApp provides an option to enable a warning when a user's identity keys change. More importantly than this fact itself, however, is that these are the identical default and setting that are provided by Google Allo for incognito chats. And more important still: while the default is the same, the "show key changes" option is wholly absent from Apple's Messages, which avoids mentioning identity keys to its users altogether.

If these folks were serious about reporting a "vulnerability" to the public, why not at least mention that Google's end-to-end-encrypted solution as well as Apple's platform have the same "backdoor"?

More importantly: why did The Guardian focus on Facebook's WhatsApp when it is materially better for verifying keys and telling users about key changes than Apple's iMessage clients are?

### Trusting Identity Keys

In the wake of this minor piece of misinformation, one important question remains hanging: can law enforcement force Google, Apple, or Facebook to lie to users about their friend's identity keys?

You see, when I message Bob over iMessage or Allo or WhatsApp, I am trusting Apple, Google, and Facebook to correctly forward me the identity keys unique to his devices. These identity keys are what allows me to encrypt my messages in a way only Bob's devices can decrypt.

I have looked and cannot find any, but if there is a legal method by which anyone can force an American company to lie to a user about how many devices another user owns or what their keys are, I'd be curious to learn about it.

[good follow-up discussion [here](https://lobste.rs/s/c6ey8s/guardian_v_whatsapp)]
