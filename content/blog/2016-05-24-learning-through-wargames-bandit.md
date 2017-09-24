---
comments: true
date: 2016-05-24T00:00:00Z
title: 'Learning Through Wargames: Bandit'
type: '/blog/post'
layout: 'single'
---

Post-bootcamp I thought I had a decent understanding of the command line, but realized how ridiculous that thought was. It was relative to other new programmers that I had spent time with–not exactly a large sampling.

What did I even mean by ‘the command line’? Was it that I had memorized the few commands to navigate directories and make files and folders in the terminal? What about shell scripting? (Which I didn’t even know what shell scripting was and had partly bombed a coding challenge because of that.) Could I ssh into a remote server? Did I understand what the shell *was*? 

The more I reflected on it, the more I realized that I knew very few commands and even less about how they worked. I was also bothered by the fact that I couldn’t understand what was so attractive about working in the terminal or using shell scripts, since I had seen so many other people at the bootcamp I went to forget commands (or maybe never even learn them), misunderstand how file systems and directories worked ([like this](https://twitter.com/kosamari/status/724049533253095424)) and in frustration continually opened the Finder on their Macs to find and manipulate files.

**From Linux to Wargames: Resources**

Realizing this, I went to where I always go: to [No Starch Press](https://www.nostarch.com/), to look for a book on the command line. I ended up with this: [“The Linux Command Line: A Complete Introduction” by William E. Shotts, Jr.](https://www.nostarch.com/tlcl) Prior to this my only other command line knowledge came from [Zed Shaw’s “Command Line Crash Course”](cli.learncodethehardway.org/book/) that I worked through last summer at breakneck speed and in a near panic. It’s a good course but just the tip of the iceberg in terms of understanding the shell and commands and with the short amount of time I gave myself to get through it, not enough time to get lost in the material by exploring my own computer’s file system and breaking things.  Exploring your own computer and trying to break things is exactly how Shotts’ book teaches. The chapters are thorough and provide a lot of context, historical and Unix-wise, for each command. I highly recommend it.

While working through the beginning of this book, I decided to go to a Linux meetup. I went mainly because I wanted to install Linux on an unused laptop out of curiosity. The meetup that day however, was about web security and I saw what could be done with mastery of the command line: the ability to connect to remote servers and computers, explore directories and execute scripts at will.

About 2 weeks ago, during RC Start week at the Recurse Center, one of the Recursers held a workshop on the command line. By far, it was the most practical discussion I had about the command line and shell scripting, and one of the highlights of the week there, (in no small part because of Pris’ ability to take all my rapid-fire questions). In addition to showing us the ’say’ command on OS/X (which I mentioned could easily be made into a program to read to the user), she also mentioned a wargames site: [overthewire.org](http://overthewire.org/wargames/). 

I wasn’t immediately able to start it, but have worked on it off and on the past week or so and finished the latest level over the weekend. I’ve made a quick gist of all the solutions I used to get through the levels of Bandit which at the moment stands at 26, [here.](https://gist.github.com/aklap/25144e83c7c18457e9eb29d733500d85)

**Review of Bandit**

Bandit is the entry-level wargame on the site, and provided a good review of basic commands for navigating files and directories and piping streams. Moving through the levels introduced me to powerful commands for networking and authentication, like ssh, openssl, netcat and telnet leading me to spend a fair bit of time reading their man pages. 

What I realized was that 1) I hadn’t been exposed to anything about networking before and 2) I was inadvertently learning on the fly about network protocols and the like via the command line. That alone makes wargame sites like overthewire invaluable to a beginner. Running through it a second time, I could see that I had made a huge jump in confidence with using bash and scripting.

I can understand that most instructors and authors of beginner learning materials skip over this stuff because they assume you're starting off with programs and scripts that work isolated on your own computer; it's an assumption that thanks to Bandit I don't think is right for everyone or even useful.  

In any case, I finally learned to write shell scripts in Ruby and did end up writing a small program to parse text files of Aesop's tales using the say command--creepy, but fun. Never could have done it without Bandit--well worth a try! 



