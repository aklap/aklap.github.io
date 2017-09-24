---
comments: true
date: 2016-10-17T00:00:00Z
image: gmeredith_illustration_victorian_woman_snake.jpg
tags:
- Python
- Matasano
- Cryptopals
- learning
- security
title: 'Learning Python with Cryptopals: Set 1'
type: '/blog/post'
layout: 'single'
---
I’ve started doing the Matasano Cryptopals challenges. I thought it would be a good way to learn Python, as well as learn about encryption and get experience working with bytes and encoding.<br>

__The first set is up on GitHub here: [https://github.com/aklap/cryptopals-solutions](https://github.com/aklap/cryptopals-solutions)__

By ‘done’, I mean I’ve satisfied the requirements for the challenges, but I’m not finished with the set. It needs to be heavily refactored, and in no way do I claim my solutions to be ‘Pythonic’ (or 'idiomatic'). There are also 2 challenges that ask for a key, but don’t ask explicitly to decrypt to plaintext; I’d like to complete that, too, though it’s not required.

**Learning Python**

I think I did okay for never having coded in Python beyond a few for loops for the tutorials on Sam Bowne’s site, and running through a few tracks on Codecademy in a day or two. Prior experience with Ruby I’m sure helped with picking up Python basics, since they are said to be similar.

I like that there are immutable data types and structures like the tuple, (had never worked with that data structure before and had only read about it in an old data structures/algorithms book.) I do realize how terribly nerdy it may be to get excited about tuples.

Although now, I see more difference between the languages than I thought I would having spent ~week in it. I see Lisp-like syntax, and I like the familiarity of the pdb debugger (a la the gdb debugger, I’m guessing?) and how it enables you to step into code, (I went to a Ladies Who Linux meetup where I saw it in action for syscalls and I’ve been intrigued ever since). My other thought is that Pry reminds me of pdb, too; maybe inspiration? 

The one thing I wasn’t really loving was the huge paradigm shift between v2~ and v3+. I ended up going to a meetup hosted by a company that uses Python and thought it would be the perfect place to refactor my code; until I realized that everyone there was using 2 and not 3, as I was. There was confusion as to what my code was doing and what it was operating on in terms of types and what it was returning. There was puzzlement that calling str() in 3 didn’t do what it was supposed to. Then I had to solve one of the challenges using v2 because of a library issue, and started reading and using v2.7. Aha, here was what the problem was: the version changed the languages’ built-in types!

That’s…kind of a huge deal! Truly, a schism had occurred. And then everything from the night before (as it often does…) made sense; apparently the str type had become the bytes type in v3, and many of the decoding functions and methods had changed; no wonder the person I had been working with didn’t understand what the prefix b was and byte array was.

**Challenges Review: What I liked!**

As far as the challenges go, they are very well done! Everything builds on top of one another, so that I can see that I could and probably should refactor the functions I created as a library to be used in the latter challenges. Sneaky, sneaky.

I also had to stop a few times to read up on encryption algorithms. I had a vague idea of what they were doing but didn’t know how they were doing what they were doing to use a Rumsfeldian turn of phrase. And although I had some understanding of what terms like ‘nonce’ or ‘IV’ were from when I heard a talk a few months ago, that talk was very math focused (algebra) and so I didn’t realize people could consider the term ‘nonce’ different than 'initialization vector' and didn’t know how that applied in code. Now I do.

**And what I didn't like so much.**

The only thing I didn’t like about the challenges were the instructions. Sometimes the terms used were nebulous and vague. And especially for Challenge 6. For instance when you say work with 'raw bytes' what exactly does that mean? Going back to differences in types in Python 2 vs Python 3, 'bytes' can have very different meanings. 

Also, part of that is just me. I’ve always had problems with word problems and instructions. 

Anyway, that combined with the red herring they threw out on #6 about the key being the one with the 2 or 3 lowest hamming distances caused me to backtrack and redo that challenge a few times. (I also didn’t really read all the instructions, either... again, I guess because I don't really like them). In fact, the key wasn’t even in the lowest 4 or 5... The way I solved that challenge  seems a bit hacky to me, so I hope I can refactor that into something more elegant.

**Should you do it? Yes.**

Overall, it was a great way to get a crash course in Python. Would I have finished it more quickly had I done it in JS or Ruby? Probably. Would my solutions be cleaner? Maybe. But I think I got what I needed to out of it, and if you do this plus Sam Bowne’s tutorials, I think you’d be off to a good start as a beginner learning about security.

In any case, it was a  fun and not intimidating start to learning about encryption.