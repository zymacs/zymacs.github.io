---
title: Git ignore files
date: 2026-04-16
tags:
  - git
  - development
categories:
  - Development
  - Git
---


## Git ignore files

So I've been trying to make my way through Progit. I have accumulated a whole lot of information so far and I was afraid
for how not so often I used it. That I was going to forget it all. 
Hence my decision to share some of that with you, and with my future self.

In this post we'll look at something you probably have never read about in isolation, gitignore files.

They hold entries for all information you would like to keep untracked. 
That could be temporary files, or database files (say sqlite3 files) or something else.
In git, they are located in the repo's base directory. They exist under the name `.gitignore`.
Creating a new repo does not auto create a '.gitignore' file so you have to create it yourself.

You can have multiple .gitignore files in a repo. But which 


Okay, so let's call these entries 'rules' from now on.
The gitignore files tracks what files to ignore or (not ignore) based on the names of the files.

Deciding what rule to use to match some name can be tricky some times. Some are easy.
A rule to match all files with the name "dont_track" would be like
```
dont_track
```

We can also use regular expressions, say to match names based on last , first , middle characters or some combination of that. Emacs for instance
has temp files ending in '~' so to match all these we would need a rule like
```
*~
```
This would take care for any such file any number of levels deep in the repo