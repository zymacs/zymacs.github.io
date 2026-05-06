---
title: Grep Fu Basics
thumbnail: 'img/linux_penguin.jpg'
date: 2026-05-03
draft: false
tags:
 - 'text-manipulation'
categories:
 - Linux tools
---

If you have used  Linux before, you have most probably heard about Grep, Awk and Sed.
These are super useful wordsmithing  tools available on all Unix and Unix-like systems.
Learning all that each can do is an insurmountable task and I'm sure you'd stand with me on that.
But having less than functional usage knowledge in at least one can waste you a lot of time while you work with text in the terminal. Which is very often.
In this article we'll look at one of the tools: *Grep*.

Grep in full stands for `Global Regular Expression Print`. It's a text search tool that was made by Ken Thompson (in one night). Link to a story on that at the bottom.

In this article we'll look at common problems you can run into that can be solved with Grep, including some regex solutions.
I'll also attach a link to a resource that helped me understand how to use regexp at the end. 

The general synopsis is as follows
```
grep [OPTION]... PATTERNS [FILE]...
grep [OPTION]... -e PATTERNS ... [FILE]...
grep [OPTION]... -f PATTERN_FILE ... [FILE]...
```
If the synopsis syntax feels cryptic, then just don't mind it. It's basic regex.
And we'll touch upon that some in this article. Its common to find that type of info representation all over programs' man entries so it helps to know how to read it. 

Okay, so we'll be using this sample text for demonstration, so you can go on and write it to some file
say, grep_text.txt

``` sh
echo "
bottle
pod
maker
plaster
polythene
boots
cops" >> grep_text.txt
```

We'll start with a simple match. The following matches all instances
of the substring `bo` anywhere in the file `grep_text.txt`. 

``` sh
grep bo grep_text.txt
```

Now the output from the previous line is not numbered. We could be interested in opening an editor at the point where the match is. To get the line number
for where a match is found, we use the `n` flag.


```sh
grep -n bo grep_text.txt
```
But what if we want to match all that does not conform to some defined pattern?
Grep has means to do that, the `v` flag. 

``` sh
grep -nv bo grep_text.txt
```

At times you could be interested in finding the number of times some
pattern matches and nothing else. The next operation does that. It is kind of similar to what
`wc -l` does.  Actually, running `grep bo grep_text.txt | wc -l` would produce the same output. You can try that out for yourself to see. 

```sh
grep -c bo grep_text.txt
```

For whichever reason you could want to have all matched text printed out. To do that you'd pass in the `-o` flag.
```sh
grep -o bo grep_text.txt
```

Now how about passing in more than one pattern? There's more than one way to do that, the first one is here, the next will be in the regex section later in the article.  Grep searches for all
lines with text matching any of the supplied expressions.

```sh
grep -e pod -e ma grep_text.txt

```
That matches all lines with substrings `ma` and or `pod`.

We've so far done only case sensitive match operations, which is the default.
To ignore case and have the pattern `bo` interpreted as `Bo` or `BO` would, (to performe case insensitive matches that is), we supply the `-i` or `--ignore-case` flag.

```sh
echo "BOB
boB" >> grep_text.txt
grep -i bob grep_text.txt
```
From the grep manual, a word is substring at the end of a line preceded by a non-word constituent character or, at the end of a line followed by a non-word constituent character. Word constituent characters : letters, digits, the underscore. To match a word, we'd follow the syntax in the next command.  

```sh
grep -w match grep_text.txt 
```

To find what text is in lines after the match you can specify the number of lines together
with the `A` flag as in the example. That returns 2 lines after every match containing line. 

```sh
grep -A2 -w maker grep_text.txt
```
This works like the previous matching pattern except it returns lines appearing before the match.

```sh
grep -B2 -w maker grep_text.txt
```
Now to return lines appearing around the match line, that is before and after, we could combine the `A` and `B` flags in the same command  as in the below example or use `C` with the numbers supplied to both A and B are the same.

```sh
grep -A2 -B2 -w maker grep_text.txt
```

```sh
grep -c2 maker grep.txt
```

_*Regexp matching*_

Now the regexp patterns. Regexp is short for regular expression.
A regular expression as per the grep manual is a pattern that describes a set
of strings. We'll look at some examples of text matching examples using
regexp.

```sh
grep -E [^a-z] grep_text.txt

```

The square brackets are used for _bracket expressions_.
They declare a list of characters from which any is a valid match for a slot.
Having the first character prepended with the carret symbol, `^`, negates
the list's matching effect.
So the pattern matches all text lines that don't have any of the characters in the list.
The list can contain comma separated characters or characer ranges like `a-z` for all lower case chars, `A-Z` for all upper chase chars, `0-9` for all numbers.
It could as well contain a combination of these say in the next example, which matches all alpha numeric characters.

``` sh
grep -E [a-zA-Z0-9] grep_text.txt
```

The same effect can be achieved with
``` sh
grep -E [[:alnum:]] grep_text.text
```

That there, the `[:alnum:]` is a grep named class of characters.
Others include `[:blank:]` for blank space, `[:digit:]` for digit, `[:punct:]` for matching
punctuation as is in the next example and more in the grep manual.

``` sh
echo ";,." >> grep_text.txt
grep -E  [[:punct:]]
```
The next pattern matches all strings with the character `a` appearing 2 consecutive times. 
Anywhere with two consecutive `a` chars will provide a match. `aaa` will match in totality
but the last a in `aaaba` won't match.


```sh
echo "aaabbfa" >> grep_text.txt
grep -E 'a'{2} grep_text.txt 
```


```sh
grep -E 'a'{1}+ grep_text.txt
```
This matches all strings with the character `a` exactly one time. The `+` has no reasonable effect and could as well be dropped to have `grep -E 'a'{1} grep_text.txt`.

The expression also has the same effect as `grep -E 'a'+ grep_text.txt` (_matches `a` appearing consecutively 1 or more times_). The last  two are ambiguous since its the default with a single character pattern. The same meaning can be gotten with `grep a grep_text.txt. It's a good means to understand how the matching happens anyways. It helps to know when to use the compexity of regex and when not to. 

How about matching the all strings at the start of a line? The caret symbol
`^` is an `anchor` character used to match a line start. It has an inverse,
"$" that matches the end of a line. To match all patterns that are at
a line's start we'd therefore do something like:

```sh
grep -E '^c' grep_text.txt
```
That'd match all lines with `c` at line start. 

Contrast that with output from 
```sh
grep c grep_text.txt
```
All lines with `c` are marked regardless of line position. 
Matching a pattern at a line's end can be done with:

```sh
grep -E 'e$' grep_text.txt
```
That'd match all lines ending  with the char `e`.

Suppose you want to match all text that starts with `a` or `b` in some file `target.txt`, what pattern would you use for that? There's more than one way to get the right effect. Let's examine one wrong solution to this:

```sh
grep -E `^a|b target.txt
```

It matches either a line starting with `a` , that `^a` that is, or , any line with the character `b`. The `|` is what's the `OR` operator when working with `grep` regexp. Back to the challenge. A sample effective answer would have been
`grep -E ^[a|b] target.txt`.
This matches all lines starting with  either a or b, not all lines that either start with `a` or have the character `b` as it was in the wrong answer example.

How about matching all lines that have characters 'p or m' or that end with `e`? That can be done with:
```sh
grep -E '[p|m,e^]' grep_text.txt
```

There's many ways to arrive at the same answer. What I provided is how I arrived at the solution and you can find your own means to with other grep options.

We just introduced the `|` operator with regex and I mentioned earlier in the
article there was more than one way to provide alternative matching patterns
than `grep -e pattern -e pattern ... file.txt`. 

```sh
grep -E 'pod|ma' grep_text.txt
```

Now you possibly have a long list of patterns against which to match some file or files (yes you can match more than one file by supplying them all in succession after defining the patterns and or options `grep pattern file1 file2..`.).

To do that, create a file and in it write all the patterns, one per line.
For instance, this saved under any name say patterns.txt
``` txt
'^[a-z]e'
[p|m]
e[a-z]$
```
Then use the pattern file to find matches with the `-f` flag. 

```sh
grep -f patterns.txt grep_text.txt
```

You can also add grep options to the file.

Prepend the first line in `patterns.txt` with `-v` so it now looks like:
```txt
-v '^[a-z]e'
[p|m]
e[a-z]$
```

Now run

```sh
grep -Ef patterns.txt grep_text.txt
```


In case you don't know what is is, pipelining is passing output from one program as input to the next. You could check 
out this [ComputerPhile video](https://www.youtube.com/watch?v=bKzonnwoR2I) on the details of that. We have looked at how to provide alternative
patterns against which to match but have not looked at how to match all supplied patterns. Say, how to match a text that satisfies pattern A and pattern B and .. .. as many as are supplied.  That can be done with linux pipelining.
Don't confuse the pipe operator here with the previously discussed `|` OR operation with regexp. Here's an example to match all lines that
both start with the character `p` and end with the character `d`. 

```sh
grep '^p' grep_text.txt | grep 'd$'
```

That's more than you need for basic grep usage. There'll probably be times when you need to get beyond the basics and I have attached a link to the GNU manual that you can ref for that. You can
check out `man grep` too.  Most of your usage of grep will not be as described here, with plain text that is. It'll usually be piping output  other  programs  (at times including grep) depending on the situation. But with what you now have, you can make your own pattern combos and do all sorts of text matching with it. 

As an extra, here's a [ComputerPhile video](https://www.youtube.com/results?search_query=brian+kernighan+grep) in which  Brian Kernighan, Grep's author, talks about how it came to be.


I hope you learnt something. 


- Regexp tutorial
  - https://youtu.be/sa-TUpSx1JA?si=kTbFEqZ0MuLdBtrI

- Article source refs
  - https://www.geeksforgeeks.org/linux-unix/grep-command-in-unixlinux/
  - https://man7.org/linux/man-pages/man1/grep.1.html
  - https://www.geeksforgeeks.org/linux-unix/grep-command-in-unixlinux/

- Bookmark worthy refs
  - https://www.gnu.org/software/grep/manual/grep.html