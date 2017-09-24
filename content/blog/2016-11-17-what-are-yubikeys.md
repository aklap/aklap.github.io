---
comments: true
date: 2016-11-17T00:00:00Z
image: yubikey.jpg
tags:
- YubiKey
- security
- mac os/x
title: 'YubiKeys Part I: What''s a YubiKey?'
type: '/blog/post'
layout: 'single'
---
What are YubiKeys are and how do they work? The answers were somewhat confusing, so here's what I learned.

**What are YubiKeys?**

After participating in a CTF that the [EFF](https://www.eff.org/) was having, I got a free YubiKey. I had no idea what it was and tossed it into a drawer for months. Now that the Apocalypse is upon us, I decided to clean up and revamp how I used my electronic devices and remembered I had a YubiKey. (The one I have is the [YubiKey 4.](https://www.yubico.com/products/yubikey-hardware/)).  

The simplest way to understand what a YubiKey is that it is a device not too different from a USB key that helps you to log into applications and websites, and provides an additional layer of security by requiring an extra step beyond typing in a password.

**Many different protocols & modes, one theme**

The common theme with YubiKeys is no matter what protocol or mode is used for authentication, new data will be created and exchanged. Sometimes that means we create a password each time we log in, sometimes that means we create a new pair consisting of a question to ask the YubiKey and an expected answer each time we register. (It all depends on what we are logging into since the YubiKey has many different modes of use.) Either way, notice that we are 'dynamically generating' data, we never hand over our YubiKey's secret data unencrypted.

**Server interaction**

YubiKeys can be used without interacting with a server but if you're using U2F (Universal 2nd Factor) or OTP (One-Time-Password) methods to authenticate, you will. If you're a developer and trying to work with YubiKeys for a project, you'll probably need to set up your own authentication server or have to have a 'relay' architecture for your application where you hand off credentials to another server for authentication like YubiCloud.

(This is because YubiKey makes use of public key cryptography and/or tokens depending on how it's used.)

**Why would you want to use one?**

I was confused at first why anyone would want to spend money on a YubiKey when you could just have a USB with a keyfile. But I now realize that this comparison isn't fair; with a keyfile, the data that you are using to authenticate is static and deterministic, (that means it always produces the same result--unless you change it). The advantage of the YubiKey is that you can generate cryptographically strong _new_ passwords (or really, tokens to be exchanged than passwords) every time you log in or every time you register your key. So, there's nothing to remember. 

**Some of the other reasons I found to use a YubiKey:**

- especially for 2FA, no more annoying text messages or emails for apps that you frequently log in and out of
- no need to remember long passphrases, passwords, or auth codes
- standardizing 2FA for many different apps and organizations
- using cryptographically stronger passwords than the ones that you or I might be inclined to make.
- if you're working on something proprietary
- have stringent compliance standards at work 
- are worried about your personal data and security

...then, it seems reasonable to me that you might be interested in a YubiKey. Personally, since I frequent a lot of public spaces to work, I like the idea of having extra security in the event some bad hombres decide to take advantage of me getting another cup of coffee or take a bathroom break to access unattended devices. (You shouldn't ever leave your things! But life happens.)

**Things to consider:**

- **The price.** For me, I got lucky and it was free. Otherwise, the version I have costs $40 and the priciest, Neo, is $50. The makers advise you buy two keys at a time. That's not a concern if you have the money or your work is covering the cost, but for the average user that's a considerable cost. They do have alternatives like an $18 key, but that will come with far fewer features.

- **Setup.** For people that feel comfortable with new technology, have some understanding of security and facility with the command line, setup isn't much of a problem. (Though the Yubico documentation really needs to be cleaned up.) I can see the average consumer who isn't used to any of these security concepts or understands how the YubiKey works becoming frustrated with setup. Again, it would be great if the videos and articles in the knowledge base weren't so scattered.

- **Documentation.** Trying to follow the directions to setup the YubiKey turned into a choose your own adventure story. Broken links, multiple sets of instructions, recommended tools weren't there, and typos in command line instructions. I think if you follow what I've done (in the next post!), you'll be okay but if it was an average user or someone at work trying to figure this out on their own, they would have been easily discouraged. And please, let's get rid of gendered pronouns for the 'user' like 'he'; many people use YubiKeys and they are sometimes 'she' and 'they.'

- **The physical key.** Felt a little flimsy and at one point I shoved it into the USB slot on a laptop at the edge of a table and the weight of my keys and keyring on it concerned me. It is holding up, though, so maybe it's sturdier than I think? 

- **The cloud aspect.** Some people would prefer not to trust the Yubico authentication server, (YubiCloud), with storing cryptographic material. But if that's the case you can host your own authentication server(s). And if it's really a problem, you're probably not going to want to use YubiKeys at all.

- **Caveats:** U2F was backed primarily by Google, and as such, works in the Chrome browser but not elsewhere for the time being. (I did find a Firefox add-on but haven't used it.) OTP is not available for Mac OS/X and Windows OS.  

**Understanding how YubiKeys work isn't easy**

While trying to find information about YubiKeys, I was struck by the number of times people posted that they too were confused about how their keys worked, even developers. This is for two reasons that I can see: YubiKeys can be used in many and very different ways and there's too much documentation, much of that outdated and conflicting, (many of the links that come up for setting up YubiKeys are for 2.0, not the latest version).

If you don't understand what you're using because you cannot find adequate resources and you don't have adequate resources so you don't understand what you're using, you're trapped in circular reasoning.

**So, what's my experience so far?**

The setup once I got past the instructions was actually almost ridiculously simple. And for things like email, it eliminated the constant text messages I had to receive, (I'd rather save my texts for things other than auth codes). 

The key is lightweight and I don't have to remember more passphrases or codes which is fine by me. If I lose it or break it, it would be a pain to pay for more keys, but with the way things seem to be going, (remember: Apocalypse!), and the realization that most of my life is centered around my electronic devices it seems like I am getting decent value out of my YubiKey. I've made most of my peace with the fact that other security and authentication applications I use could be compromised, (see password managers); it's a lifestyle and risk choice. 

Since the future seems so uncertain right now, anything that adds security without adding more work on my end seems like a bargain.

_This is not an endorsement of YubiKey & I wasn't paid for it. I just felt like reviewing it since I've had so many friends panic about the security of their personal information & privacy in the wake of the election, and I couldn't find good explanations about how it worked or to set it up._

_**>>Part 2! If you want to setup a YubiKey for a Mac, [the link is here.](#)<<**_

**Resources:**

_This paper is for the 2.0 version of the YubiKey, but outlines the general logic behind it._

- [YubiSecure? Formal Security Analysis Results for the Yubikey and YubiHSM](http://www.lsv.ens-cachan.fr/Publis/PAPERS/PDF/KS-stm12.pdf)

_A nice diagram for the U2F scheme_

- [U2F explanation with YubiKey](https://developers.yubico.com/U2F/Protocol_details/Key_generation.html)
