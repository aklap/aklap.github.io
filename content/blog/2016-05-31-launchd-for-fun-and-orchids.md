---
comments: true
date: 2016-05-31T00:00:00Z
image: launchd_demo.gif
tags:
- launchd
- os/x
- bash scripting
- daemon
title: Launchd for Fun and Orchids
type: '/blog/post'
layout: 'single'
---
I learned about Launchd and creating daemons to buy an orchid. 

Over the Memorial Day weekend there were sales everywhere. Department stores, electronic sellers, boutiques...but the sale that I cared about most was at an orchid nursery. Because I wanted [this.](http://sunsetvalleyorchids.com/htm/photo_detail.php?prod=507)

Then the website went down Sunday afternoon. Dark times. 

This got me thinking: I can curl endpoints and get their status,

 **Why couldn't I just create a daemon to run in the background and check when the site was back up, sending me notification or just popping open a new tab in the browser with the website?** 

 (I like, _really_ wanted this plant.)

I discovered that creating daemons for Mac OS/X is quite simple. All we have to do is create an XML file (and this should be familiar for anyone working with React...) and have that execute a bash script. 


That's it.

**Before You Start**

The official docs for Launchd are simple and easy to understand, but there are two things that I feel miss the mark: 

1. Unclear as to how to start your daemon. It's literally one command:
    
    Start:
    launchctrl load plistfilename.plist

    Stop:
    launchctrl unload plistfilename.plist

    I think this is because the docs tell you to use the GUI. Which brings me to...

2. The insistence on using the Launchd visual GUI. 
    
    Firstly, it costs $10.

    It also seems a very strange choice to push the visual GUI on Launchd's users. Only a small group of people are writing daemons for OS/X; we can assume that these are people that have more than the average person's understanding or comfort with how their OS and computers in general work, as well as programming ability. These are not people that prefer a visual GUI to the command line. 

    There's also nothing that can't be done in the command line or in the plist file itself that the GUI can do. 

**First step: Make a plist**

We create an xml file, our 'process list,' with the extension .plist and usually put that in either root or a specific user's Library/LaunchAgents/. 

Therefore, we need to think:  What do we want this process to do and in what context? If a process is run by the system, we call it a daemon. If it is run under a specific user, it is an agent. I use them interchangeably here because I'm lazy, but they're all background processes.

**What goes into our plist?**

Like an HTML document, we have tags that contain information about the process itself. We should have a name for our process, (hint: Apple likes to do reverse domain name with that, which is why you will see things like: com.applestore.whatver.app). That is in the 'label' tag. Take a look at the example file I have for checking the status of my blog site:

<img src="/assets/site_checker-plist.png">

Everything else like scripts to run, intervals to run the process, keeping connections alive--all of them are options that can be added to the file in between 'key' tags. The docs are explicit about what we can add, so I won't try to mention them all here. I'm not sure what exactly happens with these, but I think of them as a hash that contains keys corresponding to values that the OS acts on.

For the simplest of apps, that's it. cd into where you have your plist saved, probably ~/Library/LaunchAgents/. Run: 

    launchctrl load name.plist

and your process should run.

But what if I want to run a script?

**Add a script.**


Just add the path to that script between key tags in your plist file.

<img src = "/assets/site_checker-sh.png" >

Here I have a few lines where I curl the url of my blog site, (you can sub in any website), get the status code, and if the site is functioning fine then I open a tab in the browser with the now working site, log the date in a file, and end the process.


**What can I do with this?**

Anything you want. On Mac, run 

    launchctl list

and look at all the processes that make your laptop work! 

You could take my own Launch Agent here, and slightly altering it, use it to ping websites to make sure they're running, logging their status codes or errors to file, (helpful if your maintaining or working on a few sites). You could create a server and have it send emails out at regular intervals. You could create a daemon and script to purchase tickets for a concert if it's released in batches. Any situation where it would be tedious or highly repetitive for you to do something over a long period of time is a good candidate for creating a daemon or background process.

[You can also take a look at my code for this project here.](https://github.com/aklap/site_checker)

**Helpful links:**

- [Apple Docs on Launchd](https://developer.apple.com/library/mac/documentation/MacOSX/Conceptual/BPSystemStartup/Chapters/Lifecycle.html)
- [Launchd official tutorial](http://launchd.info/)
- [Alvin Alexander's blog post on Launchd jobs](http://alvinalexander.com/mac-os-x/mac-osx-startup-crontab-launchd-jobs)
- [Setting Launchd Interval](http://www.splinter.com.au/using-launchd-to-run-a-script-every-5-mins-on/)
