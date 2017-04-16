+++
date = "2015-10-11"
menu = "main"
title = "Judicial Side Doors and Single User Encryption"
linktitle = "single-user-encryption"
+++

## In Theory

Bruce Schneier [writes](https://www.schneier.com/blog/archives/2015/09/tsa_master_keys.html):

> Someone recently noticed a Washington Post story on the TSA that originally contained a detailed photograph of all the TSA master keys. [...] The whole thing neatly illustrates one of the main problems with backdoors, whether in cryptographic systems or physical systems: they're fragile.

Except in the case of cryptographic systems like full-disk-encryption, they are not. In the TSA baggage key scenario, a copy of the physical master key need to be present wherever baggage is screened. In the cryptographic realm, it's possible to send a "lock" to the secure location of the master key, decrypt it, and send it back opened. Only one copy of the master key ever needs to exist, and so it's intrinsically a simpler system to protect.

There are many considerations to be had in the debate about full disk encryption, but the [oft-repeated argument](https://www.eff.org/deeplinks/2015/08/it-again-law-enforcement-officials-anti-encryption-new-york-times-op-ed) that it is impossible to have a secure backdoor accessible only via lawful judicial orders does not strike me as very persuasive. One does not need to look far to find secure backdoors [built into full disk encryption](https://secure2.sophos.com/en-us/lp/sem/enterprise-encryption-trial.aspx):

> We chose to pay for Sophos encryption because of its better administration and data recovery options, even though we have free access to BitLocker via our Microsoft Campus Licensing Agreement.

What are "data recovery options"? That's another name for a legal side door, and I would wager that among corporations with the resources to administer them, most laptops have it enabled, even if they contain the keys used to access production systems storing sensitive user data.

Just because side doors can be secure does not mean we should legally mandate them, however. A more convincing argument is that legislating away phones or computers running one algorithm or another is simply infeasible in the real world.

## In the Real World

Let's say a law was passed in the US prohibiting encryption with single-user access, and I was coming back from Russia or China with a smart phone I bought there, where it's legal. Would the border agent tell me "sorry, your phone is too secure to be allowed into America"? That seems unlikely.

Then there appear to be two alternatives: either (1) people can bring into the US more secure devices than can be legally bought here, or (2) US law enforcement can keep developing methods for preventing, finding, and prosecuting crime in the world we find ourselves in today, one where many people, not just those with extraordinary resources, carry devices that only they can access.

What kind of effect will these options have on the systems of criminals and law enforcement (LE)?

Creating a two tiers of "foreign devices with single-user encryption" and "American devices with a judicial master key" will definitely make some criminals easier to prosecute. Unplanned crimes of passion or those committed by low-resource individuals and will be easier to solve. These cases might keep LE busy and getting promotions, while criminals who have training or resources will naturally get less attention solely because it's harder to prosecute them. Especially egregious resourceful criminals will still be worth the trouble, but there will be a large class of slightly smarter criminals who are simply not worth the trouble when simpler cases abound.

On the other hand, making the default phone a strongly encrypted device [seems scary](https://www.nytimes.com/2015/08/12/opinion/apple-google-when-phone-encryption-blocks-justice.html). Let's think about it in the long term, though. Making it cheaper to be a sophisticated criminal actually weakens the power of criminals with resources, since LE will choose which cases to pursue based more on the severity of the crime, and less on who is the easier target. More LE resources will be devoted to finding informants, turning conspirators, and infiltrating gangs, not simply prosecuting anyone who had an unecrypted phone full of incriminating evidence.

While the short term is less certain, imagining these two possible long-term futures, there appears to me little ambiguity as to which is preferable. The important question to answer is "when?", and considering the state we find ourselves in presently, the answer might very well be "now".
