---
comments: true
date: 2016-05-28T00:00:00Z
tags:
- leviathan
- wargame
- bash
- command line
- solutions
title: Ltrace & Symbolic Links with Leviathan
type: '/blog/post'
layout: 'single'
---
After finishing Bandit, I moved on to Leviathan, the suggested wargame after Bandit. With only 7 levels, it didn't take long at all to complete. What was slightly different about Leviathan is the use of ltrace and symbolic links. 

ltrace is a Linux command short for 'library tracer.' It intercepts calls made while executing a process, including to and from the system in addition to dynamic library calls and signals receive; they all get recorded. It's introduced in Bandit, but used more extensively in Leviathan. This is one of those powerful commands that seems almost like magic; it can turn a seemingly blackbox situation into an incredibly explicit and verbose autopsy of calls and signals. 

In fact, I was so curious about ltrace that I decided to later go back and read it's man page...until I realized that [it's not available on OS/X](http://stackoverflow.com/questions/1258481/ltrace-equivalent-for-osx). (Alternate commands on OS/X are dtrace and dtruss.) At some point, I'd like to dig into how ltrace works on a lower-level just because it seems so magical to me.

The other command that is noteworthy in Leviathan is ln. Although this command was not used in Bandit, it was mentioned in Schott's command line book that I linked in my Bandit post. Creating symbolic links, aka soft links or symlinks, are useful whenever you want to reference a resource that may be changed. The example that Shotts gives is a versioned resource going say, from foo-1.1 to foo-2.0. Whenever we update our resource, the file name would be changed, causing errors and breaking our programs unless we always changed our code to reference that new file. We can make things easier for ourselves by having a symbolic link like "foo" point to the specific file for us. 

For the visual, a bootleg ASCII diagram:

    Programs need a resource and foo links to the specific resource file they need.

    program_A ___
                 |____        foo-1.5
                  ____foo --> foo-2.0
    program_B ___|            foo-1.0              


So the symbolic link is just a pointer or reference (in colloquial rather than compsci terms) to the actual resource, and all the dependent programs will be able to access the resource no matter what the version of it is. It's a bit like git if you've used it for version control, moving the head of a branch to whatever version you want it to reference.

Because Murphy's Law, the next day after I finished Leviathan I installed MIT-Scheme, and happened to update homebrew among other things on my computer. When I went to write this post, I was unable to start the Jekyll server for my blog because according to the errors in the trace I had a missing library. I realized that updating homebrew must have caused the MIA library file as it could not find the correct versioned lib file. [(This was my error.)](http://www.mattburkedev.com/overcoming-ruby-error-sha1-bundle-not-loaded/) I was then able to create a symbolic link that pointed to the correct binary, and with one command in bash was back to running my blog on localhost. [(Working solution found by force linking.)](https://coderwall.com/p/n9bnug/missing-the-openssl-lib-when-rbenv-install-2-1-0-dev) Lesson: The homebrew symlinks giveth, the update taketh away.     

Anyway, let's get to the contraband. Leviathan is actually an old wargame, and there are many blog posts with solutions available online, hence my lack of remorse. If you are truly stuck, or have finished it and want to compare solutions, I've created a gist for it [here](https://gist.github.com/aklap/313849eb385a134062f86b913d230c7a). Because of the briefness of this wargame, I have no notes on the gist unlike my solutions for Bandit. 

