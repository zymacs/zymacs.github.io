---
title: Gitignore files
date: 2026-04-17
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

_If you want to just look at a summary of what rules you can use for creating your files, there's one at the very end of this article_


Okay. Gitignore files hold entries for all information you would like to keep untracked. 
That could be temporary files, or database files (say sqlite3 files) or something else.
In git, they are located in the repo's base directory. They exist under the name `.gitignore`.
Creating a new repo does not auto create a '.gitignore' file so you have to create it yourself.

``` bash
touch .gitignore
```

Rules in a .gitignore file are applied recursively to all files and subdirectories in the same folder as the file.
Also, you could have multiple .gitignore files, but let's keep that for `man gitignore`.
Let's call the entries in a .gitignore file rules from now on.
Here's a sample rules file that includes what I think will be the commonest usecases you'll come to need.

### Rule's we shall look at in this article.

```
a
a/
*.ext
!lib.ext
a/*.txt
a/**/*.txt
*.[oa]
/a
*/a/*.txt
**/a/*.txt
```

Before anything, for a folder to be tracked, it should have at least a file.
Any folder that does not have at least a file or a sub directory with one will not be tracked. This does not need any .gitignore rule to be true.
We'll also assume the .gitignore file above is in the repo's root or base directory.

Okay, so first rule matches all files and directories whose name is exactly 'a'. This rule is applied recursively in the the folder `rootdirectory`.
All folders named 'a' that have files in them won't be tracked. All files named 'a' located anywhere in the repo won't be tracked.
Anything in a folder named 'a' by implication, won't be tracked.

Now how about if I only want to not track directories named 'a'. That's the second rule `a/`.
Adding a forward slash to a name pattern tells git to ignore only matching directories, and not files.
So to match only directories with some name pattern, you'd have to append a forward slash to it.

Git also supports globbing patterns. For instance , the rule ,`*.ext`, ignores all files (and directories but I wonder why a directory would have that name)
ending in `.ext` in a repo.
The seventh rule `*.[oa]` ignores all files endign with characters 'o' or 'a'. So both  _'/somedir/bo.a'_ and _'gop.o/'_ would have been ignored
by this rule.

Now you could run into times when you want to have exceptions for your rules. And Git supports that too.
In the fourth rule `!lib.ext`, right after `*.ext`, the '!' at the start tells git to make an exception for the file 'lib.ext' to any rule that would ignore it.
From the sample ruleset, Git  knows to ignore all files ending in '.ext' but also to include 'lib.ext'.

What if you don't some rule to be applied recursively? You could prepend the rule with a forward slash. The rule `/a` only applies to the files and directories
in the same location as the .gitignore file called 'a'. Appending a forward slash to this rule `/a/`  means ignoring only folders named 'a' but applying this rule only in the same folder as the '.gitignore' file.

How about ignoring all files and or directories matching a certain pattern under some directory located elsewhere than in the root directory?
That's what's applied in the rule `a/*.txt`. It ignores all files (or folders) with the names ending in `.txt` that are directly under folders named `a/`.
But there's a caveat! It only does this if the pattern's root folder , `a` for this example, is in the root directory. Say `rootdirectory/a`.
To apply this to folders one level deep, say `rootdirectory/b/a`, it'd have to change to `*/a/*.txt`. The `*` char would match anything in the root directory (but a forward slash) then the pattern `a/*.txt`. Say,

```
rootdirectory/somedir/a/file.txt
````

It however wouldn't match `rootdirectory/somedir/anotherdir/a/file.txt`.
For unrestricted depth, we'd apply

```
**/a/*.txt
``` 

From this we can see that Git applies all rules relative to the root directory.


Here's another sample rule to match all files ending in `.txt` at any depth in any a directory named `a` located at the project's root.

```
a/**/*.txt
```

You can mix these rule formations and do make all sorts of interesting rulesets but why would you do that? To have fun? Anyways.

Lastly, on templates. So there's a whole lot of '.gitignore' templates out there for different kinds of projects. Pre written rules ready for you to copy and paste
into your `.gitignore.`. And that's a good thing. It probably saves time that'd be taken writing your own. Or helps you include patterns you could otherwise have forgotten.

But personally, I maintain a single .gitignore template. Keep adding to it all sorts of patterns for files and folders
I tend to ignore (and that could include online templates too but I haven't sourced from any online templates before.).
Then I have  means to auto populate every project's .gitignore from the same global file. 

And here's what's interesting, I ignore my `.gitignore` too! I mean, I might be ignoring certain things I don't want folk to know am
ignoring.. so.. 

Anyways, that's a whole lot on such a small topic. So let's have the summary. Just in case you skipped to the end.

## Rules Summary (TLDR)

- Recursively ignoring all files and folders whose names match some pattern `a`
```
a
```


- Recursively ignoring only folders whose names match some pattern `a`
```
a/
```

- Ignoring all files and folders whose names match some pattern `a` that are located in the root directory
```
/a
```


- Ignoring all files in directory named `a` that's located one level deep below the root directory say root is `/` and we want to ignore `a` in `/b/a/somefiles`.
```
*/a
```


- Ignoring all files and folders located any number of levels deep below the root directory say ignoring `a` in  `/b/c/a/somefiles`. 
```
**/a
```



With the building blocks and conceptual understanding from this article, I'm sure there's not much extra that you'll need. But when you do, say for nested `.gitignore` implementations, you can look at `man gitignore`.

I sure do hope this helped somehow. See you in the next one and... HAPPY HACKING. 


