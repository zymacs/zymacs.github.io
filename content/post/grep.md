

If you have used Linux before, you have most probably heard about Grep,
Awk and Sed. These are super useful text manipulation tools available on
all Unix and Unix-like systems. Learning all that each can do is an
insurmountable task and I\'m sure you\'d stand with me on that. But
having less than functional usage knowledge in at least one can waste
you a lot of time while you work with text in the terminal. Which is
very often. In this article we\'ll look at one of the tools: *Grep*.

Grep in full stands for `Global Regular Expression Print`{.verbatim}.
It\'s a text search tool that was made by Ken Thompson (in one night).
Link to a story on that at the bottom.

In this article we\'ll look at common problems you can run into that can
be solved with Grep, including some regex solutions. I\'ll also attach a
link to a resource that helped me understand how to use regexp at the
end.

The general synopsis is as follows

``` example
grep [OPTION]... PATTERNS [FILE]...
grep [OPTION]... -e PATTERNS ... [FILE]...
grep [OPTION]... -f PATTERN_FILE ... [FILE]...
```

If the synopsis syntax feels cryptic, then just don\'t mind it. It\'s
basic regex. And we\'ll touch upon that some in this article. Its common
to find that type of info representation all over programs\' man entries
so it helps to know how to read it.

Okay, so we\'ll be using this sample text for demonstration, so you can
go on and write it to some file say, grep~text~.txt

``` {.bash org-language="sh" results="drawer"}
echo "
bottle
pod
maker
plaster
polythene
boots
cops" >> grep_text.txt
```

We\'ll start with a simple match. The following matches all instances of
the substring `bo`{.verbatim} anywhere in the file
`grep_text.txt`{.verbatim}.

``` {.bash org-language="sh"}
grep bo grep_text.txt
```

  --------
  bottle
  boots
  --------

Now the output from the previous line is not numbered. We could be
interested in opening an editor at the point where the match is. To get
the line number for where a match is found, we use the `n`{.verbatim}
flag.

``` {.bash org-language="sh"}
grep -n bo grep_text.txt
```

  ----------
  2:bottle
  7:boots
  ----------

But what if we want to match all that does not conform to some defined
pattern? Grep has means to do that, the `v`{.verbatim} flag.

``` {.bash org-language="sh"}
grep -nv bo grep_text.txt
```

  -------------
  1:
  3:pod
  4:maker
  5:plaster
  6:polythene
  8:cops
  -------------

At times you could be interested in finding the number of times some
pattern matches and nothing else. The next operation does that. It is
kind of similar to what `wc -l`{.verbatim} does. Actually, running
`grep bo grep_text.txt | wc -l`{.verbatim} would produce the same
output. You can try that out for yourself to see.

``` {.bash org-language="sh"}
grep -c bo grep_text.txt
```

``` example
2
```

For whichever reason you could want to have all matched text printed
out. To do that you\'d pass in the `-o`{.verbatim} flag.

``` {.bash org-language="sh"}
grep -o bo grep_text.txt
```

  ----
  bo
  bo
  ----

Now how about passing in more than one pattern? There\'s more than one
way to do that, the first one is here, the next will be in the regex
section later in the article. Grep searches for all lines with text
matching any of the supplied expressions.

``` {.bash org-language="sh"}
grep -e pod -e ma grep_text.txt
```

  -------
  pod
  maker
  -------

That matches all lines with substrings `ma`{.verbatim} and or
`pod`{.verbatim}.

We\'ve so far done only case sensitive match operations, which is the
default. To ignore case and have the pattern `bo`{.verbatim} interpreted
as `Bo`{.verbatim} or `BO`{.verbatim} would, (to performe case
insensitive matches that is), we supply the `-i`{.verbatim} or
`--ignore-case`{.verbatim} flag.

``` {.bash org-language="sh"}
echo "BOB
boB" >> grep_text.txt
grep -i bob grep_text.txt
```

  -----
  BOB
  boB
  -----

From the grep manual, a word is substring at the end of a line preceded
by a non-word constituent character or, at the end of a line followed by
a non-word constituent character. Word constituent characters : letters,
digits, the underscore. To match a word, we\'d follow the syntax in the
next command.

``` {.bash org-language="sh"}
echo "match" >> grep_text.txt
echo "matchman" >> grep_text.txt
grep -w match grep_text.txt 
```

``` example
match
```

To find what text is in lines after the match you can specify the number
of lines together with the `A`{.verbatim} flag as in the example. That
returns 2 lines after every match containing line.

``` {.bash org-language="sh"}
grep -A2 -w maker grep_text.txt
```

  -----------
  maker
  plaster
  polythene
  -----------

This works like the previous matching pattern except it returns lines
appearing before the match.

``` {.bash org-language="sh"}
grep -B2 -w maker grep_text.txt
```

  --------
  bottle
  pod
  maker
  --------

Now to return lines appearing around the match line, that is before and
after, we could combine the `A`{.verbatim} and `B`{.verbatim} flags in
the same command as in the below example or use `C`{.verbatim} with the
numbers supplied to both A and B are the same.

``` {.bash org-language="sh"}
grep -A2 -B2 -w maker grep_text.txt
```

  -----------
  bottle
  pod
  maker
  plaster
  polythene
  -----------

``` {.bash org-language="sh"}
grep -c2 maker grep.txt 2>&1
```

``` example
grep: grep.txt: No such file or directory
```

*Regexp matching*

Now the regexp patterns. Regexp is short for regular expression. A
regular expression as per the grep manual is a pattern that describes a
set of strings. We\'ll look at some examples of text matching examples
using regexp.

``` {.bash org-language="sh"}
grep -E [^a-z] grep_text.txt
```

  -----
  BOB
  boB
  -----

The square brackets are used for *bracket expressions*. They declare a
list of characters from which any is a valid match for a slot. Having
the first character prepended with the carret symbol, `^`{.verbatim},
negates the list\'s matching effect. So the pattern matches all text
lines that don\'t have any of the characters in the list. The list can
contain comma separated characters or characer ranges like
`a-z`{.verbatim} for all lower case chars, `A-Z`{.verbatim} for all
upper chase chars, `0-9`{.verbatim} for all numbers. It could as well
contain a combination of these say in the next example, which matches
all alpha numeric characters.

``` {.bash org-language="sh"}
grep -E [a-zA-Z0-9] grep_text.txt
```

*:output*

  -----------
  bottle
  pod
  maker
  plaster
  polythene
  boots
  cops
  BOB
  boB
  match
  matchman
  -----------

The same effect can be achieved with

``` {.bash org-language="sh"}
grep -E [[:alnum:]] grep_text.txt
```

  -----------
  bottle
  pod
  maker
  plaster
  polythene
  boots
  cops
  BOB
  boB
  match
  matchman
  -----------

That there, the `[:alnum:]`{.verbatim} is a grep named class of
characters. Others include `[:blank:]`{.verbatim} for blank space,
`[:digit:]`{.verbatim} for digit, `[:xdigit:]`{.verbatim} for
hexadecilal characters (a to f, 0 to 9), `[:punct:]`{.verbatim} for
matching punctuation as is in the next example and more in the grep
manual.

``` {.bash org-language="sh" results="drawer"}
echo ";,." >> grep_text.txt
grep -E  [[:punct:]] grep_text.txt 2>&1
```

``` example
;,. 
```

The next pattern matches all strings with the character `a`{.verbatim}
appearing 2 consecutive times. Anywhere with two consecutive
`a`{.verbatim} chars will provide a match. `aaa`{.verbatim} will match
in totality but the last a in `aaaba`{.verbatim} won\'t match.

``` {.bash org-language="sh"}
echo "aaabbfa" >> grep_text.txt
grep -E 'a'{2} grep_text.txt 
```

``` example
aaabbfa
```

``` {.bash org-language="sh"}
grep -E 'a'{1}+ grep_text.txt
```

  ----------
  maker
  plaster
  match
  matchman
  aaabbfa
  ----------

Since its \'1\' char we are matching, we have the same effect with:

``` {.bash org-language="sh"}
grep -E 'a'{1} grep_text.txt
```

*output:*

  ----------
  maker
  plaster
  match
  matchman
  aaabbfa
  ----------

But if it is 2 \'a\'s. Things differ

``` {.bash org-language="sh"}
grep -E 'a'{2} grep_text.txt
```

``` example
aaabbfa
```

How about matching the all strings at the start of a line? The caret
symbol `^`{.verbatim} is an `anchor`{.verbatim} character used to match
a line start. It has an inverse, \"\$\" that matches the end of a line.
To match all patterns that are at a line\'s start we\'d therefore do
something like:

``` {.bash org-language="sh"}
grep -E '^c' grep_text.txt
```

``` example
cops
```

That\'d match all lines with `c`{.verbatim} at line start.

Contrast that with output from

``` {.bash org-language="sh"}
grep c grep_text.txt
```

  ----------
  cops
  match
  matchman
  ----------

All lines with `c`{.verbatim} are marked regardless of line position.
Matching a pattern at a line\'s end can be done with:

``` {.bash org-language="sh"}
grep -E 'e$' grep_text.txt
```

*output:*

  -----------
  bottle
  polythene
  -----------

That\'d match all lines ending with the char `e`{.verbatim}.

Suppose you want to match all text that starts with `a`{.verbatim} or
`b`{.verbatim} in some file `target.txt`{.verbatim}, what pattern would
you use for that? There\'s more than one way to get the right effect.
Let\'s examine one way to do this:

``` {.bash org-language="sh"}
grep -E '^a|b' grep_text.txt
```

  ---------
  bottle
  boots
  boB
  aaabbfa
  ---------

It matches either a line starting with `a`{.verbatim} , that
`^a`{.verbatim} that is, or , any line with the character
`b`{.verbatim}. The `|`{.verbatim} is what\'s the `OR`{.verbatim}
operator when working with `grep`{.verbatim} regexp. Back to the
challenge. A sample effective answer would have been
`grep -E '^[a|b]' grep_.txt`{.verbatim}.

``` {.bash org-language="sh"}
grep -E '^[a|b]' grep_text.txt
```

  ---------
  bottle
  boots
  boB
  aaabbfa
  ---------

This matches all lines starting with either a or b, not all lines that
either start with `a`{.verbatim} or have the character `b`{.verbatim} as
it was in the wrong answer example.

How about matching all lines that have characters \'p or m\' or that end
with `e`{.verbatim}? That can be done with:

``` {.bash org-language="sh"}
grep -E 'p|m|e$' grep_text.txt
```

  -----------
  bottle
  pod
  maker
  plaster
  polythene
  cops
  match
  matchman
  -----------

There\'s many ways to arrive at the same answer. What I provided is how
I arrived at the solution and you can find your own means to with other
grep options.

We just introduced the `|`{.verbatim} operator with regex and I
mentioned earlier in the article there was more than one way to provide
alternative matching patterns than
`grep -e pattern -e pattern ... file.txt`{.verbatim}.

``` {.bash org-language="sh"}
grep -E 'pod|ma' grep_text.txt
```

Now you possibly have a long list of patterns against which to match
some file or files (yes you can match more than one file by supplying
them all in succession after defining the patterns and or options
`grep pattern file1 file2..`{.verbatim}.).

To do that, create a file and in it write all the patterns, one per
line. For instance, this saved under any name say patterns.txt

``` {.bash org-language="sh" results="drawer"}
echo "^[a-d]e
^co
er$" > patterns.txt

```

Then use the pattern file to find matches with the `-f`{.verbatim} flag.

``` {.bash org-language="sh"}
grep -f patterns.txt grep_text.txt
```

You can also add grep options to the file.

Prepend the first line in `patterns.txt`{.verbatim} with `-v`{.verbatim}
so it now looks like:

``` {.bash org-language="sh"}
echo "-Ev '^c'" >> patterns.txt
```

Now run

``` {.bash org-language="sh"}
grep -Ef patterns.txt grep_text.txt
```

In case you don\'t know what is is, pipelining is passing output from
one program as input to the next. You could check out this
[ComputerPhile video](https://www.youtube.com/watch?v=bKzonnwoR2I) on
the details of that. We have looked at how to provide alternative
patterns against which to match but have not looked at how to match all
supplied patterns. Say, how to match a text that satisfies pattern A and
pattern B and .. .. as many as are supplied. That can be done with linux
pipelining. Don\'t confuse the pipe operator here with the previously
discussed `|`{.verbatim} OR operation with regexp. Here\'s an example to
match all lines that both start with the character `p`{.verbatim} and
end with the character `d`{.verbatim}.

``` {.bash org-language="sh"}
grep '^p' grep_text.txt | grep 'd$'
```

Some special characters can\'t be comprehended even with extended regex
so you have to use -P. For instance, the special char for digits .̣

``` {.bash org-language="sh"}
echo '292 abacus' | grep -P '\d{2}a' 
```

You can look into other options like `-o`{.verbatim} for getting grep to
print out only the matching and nothing else.

That\'s more than you need for basic grep usage. There\'ll probably be
times when you need to get beyond the basics and I have attached a link
to the GNU manual that you can ref for that. You can check out
`man grep`{.verbatim} too. Most of your usage of grep will not be as
described here, with plain text that is. It\'ll usually be piping output
other programs (at times including grep) depending on the situation. But
with what you now have, you can make your own pattern combos and do all
sorts of text matching with it.

As an extra, here\'s a [ComputerPhile
video](https://www.youtube.com/results?search_query=brian+kernighan+grep)
in which Brian Kernighan of the C programming language and AWK talks
about how it came to be.

I hope you learnt something.

-   [Regexp tutorial](https://youtu.be/sa-TUpSx1JA?si=kTbFEqZ0MuLdBtrI)
-   Article source refs
    -   [Geeks for geeks:
        grep](https://www.geeksforgeeks.org/linux-unix/grep-command-in-unixlinux/)
    -   [Man pages:
        grep](https://man7.org/linux/man-pages/man1/grep.1.html)
-   Bookmark worthy refs
    -   [Gnu man pages:
        grep](https://www.gnu.org/software/grep/manual/grep.html)
-   Testing tool
    -   [Regexpal](https://www.regexpal.com)
-   Further exploration
    -   [Comparing BRE, ERE and
        PCRE](https://www.youtube.com/watch?v=lgHADH9ROsM&t=457s)
        -   ERE could be buggy some times.
        -   BRE is but a subset of ERE.
        -   PRCE is safest. (though I used ERE the whole time in the
            article. Why? *for ..backward compatibility :XD*)
