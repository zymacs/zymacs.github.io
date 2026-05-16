---
thumbnail: "img/rabbit-hole.jpeg"
title: Hunting for exportable android usage stats
date: 2026-05-15
tags:
 - rabbit_holes
categories:
 - random
---

I am doing some public accountability challenge on instagram and on
15.05.26 the theme was setting goals for improving my time management. I
was planning on discussing my problems with AI usage and how much of a
time sink my phone was. I needed to show some initial stats based on
which comparisons would be made in later updates to show improvement or
a lack thereof. I already have a dirty script for checking my AI usage
even when its not so understandable. What I did not have at all was
access to raw mobile screen time data on my PC.

There\'s a script I have used before for this purpose and hoped I could
reach for it but learnt it was based on a dump format that has since
been changed.

So I set out to understand the new format and come up with some script
to do the work for me. I ain\'t a mobile developer and wading through
all the dump info was mentally taxing. Decided I\'d get some ROI on the
task by writing about the process. Its what am going to do in this
article.

First, make sure you got adb installed to follow along. Also, make sure
your phone supports adb debugging by enabling developer options and
doing the needful with the developer settings. I already had adb
installed on my system obviously. I\'d already connnected my phone and
made the first dump with :

``` {.bash org-language="sh"}
adb shell dumpsys usagestats > full_usage_stats.txt
```

The dump looked like a dump: Martian all over the place if you ain\'t an
android dev, which I am not.

I scrolled down to the section that\'s got a lot of \`package=\` style
lines. It looked like it had all the data I needed. I couldn\'t really
tell if it didn\'t. The last dump I made I did not examine the format
that closely. Only ran the script on it and it worked fine.

So I decided to list what I needed to keep me from drifting. I needed
usage data for a select number of apps. These apps were id\'d in the
file by their package names. The names had the format
\`com.appname.something\` or \`com.appname\` for others. Id\'ing the
apps wasn\'t the problem. FIguring out what stood for \"screen time\" is
where I had the most challenge.

My tentative task list was like so:

1.  Find out what all fields in each \`package=\` line means
2.  List all apps we\'d need and their corresponding package names.
3.  Extract lines with package names mactching the packages we are
    intereted in
4.  Extract the metadata from that.
5.  Work on clean presentation
6.  Export to csv for later

Here\'s a sample package data line.

``` txt
package=com.instagram.android u=0 bucket=40 reason=f used=+4h18m16s641ms usedByUser=+4h19m28s143ms\
usedScr=+892d14h28m24s823ms lastPred=<uninitialized> expiryTimes=<none>\
lastJob=+52m49s437ms lastInformedBucket=-1 nextEstimatedLaunchTime=+3d7h47m12s335ms idle=y
```

It\'s obvious the sample package stats line belongs to instagram. But
what in the world does all that extra data mean? We have bucket ,
reason, used, usedBy, usedScr, lastJob, lastInformedBucket,
nextTimeEstimatedLaunch.

To find this out I tried looking at the api ref for the command that
produced this info. The \`adb dumpsys shell usagestats\` ref that is. It
interestingly said nothing about the usagestats service. At least
nothing I could work with. It did mention each \"service\" had a
detailed help page but the \"usagestats\" service didn\'t. Supplying
\`-h\` just dumpsys stats gave the same output as it did when I supplied
nothing.

``` {.bash org-language="sh" results="drawer"}
adb shell dumpsys  usagestats --help > output_1.txt
adb shell dumpsys  usagestats > output_2.txt
diff output_1.txt output_2.txt
```

Tried hunting for the answer from other sources but the few I found all
seemed to be in ref to the old dump format which, I\'d learnt was no
longer useful. I was so very much trying to avoid using an LLM but this
was becoming less of an option and more of an only path.

I copied one of them package lines and posted it as is in my search box.
I use startpage btw. That did not return any results as expected.

So I cut down the search query to only leave the \`package=packagename\`
portion and still got the same results: nothing.

I then searched for \'nextEstimatedLaunchTime\`. That\'s one of the
metadata keys in the package line. This led me to the site on some file under the name [UsageStatsService](https://android.googlesource.com/platform/frameworks/base/+/master/services/usage/java/com/android/server/usage/UsageStatsService.java).

Turns out its all the java code responsible for the usage stats service.
I ain\'t no JAVA dev and Java is a lot of brain pain but anyways, I was
probably going to have to read through this to get what I needed so I
did.

There was so much to decipher. I remember when looking at the useless
API page I came across an API ref for UsageStats that I didn\'t pay much
attention to as it seemed to have been geared towards app developers.
Now that I\'d given into an even harder task, reading the api source, I
guessed was going to be even easier reading the api.

But before that, I got some more metadat keys from the package line and
did a \`Ctrl+F\` for them from the service source code. Searched for
\`nextEstimatedLaunchTime\`. There was a block of code describing what
this did but I still wasn\'t getting a thing so I googled the term and
learnt it had to do with how much time it takes for the app to startup
and get fully responsive to user interaction from. More on that [here](https://developer.android.com/topic/performance/vitals/launch-time).

Now that ain\'t of any use to me so I moved on to another data point.
There\'s two that seemed promising. \`Used\` and \`UsedByUsr\`. So I
started with \`Used\`. The term is so generic and as thus didn\'t bring
forth anything usable. Got a bunch of ads for used androids mostly. So I
switched to the dorks prompt \`UsedByUsr android usagestats\' That
returned nothing.

I then switched using Startpage for a search engine to Google with the
same query. That sent me straight to the Android Api for Usage Stats. I
was recently reading about how browsers work and remember one part
talking about types of browser indexers mentioning some did the work of
indexing while others did dodged that work by piping queries to indexers
which I think is what Start page does. Its a \`metasearch engine\`.
Anyways. Just a point to note for next time I am choosing what browser
to use for research. Actually, reading the wikipedia page on meta search
engines I learnt my suspicions were true. See for yourself [here](https://en.wikipedia.org/wiki/Metasearch_engine).

But back to the topic. I now decided I\'d just focus on the UsageStats
api after all attempts to dodge it in hope of finding something more
straight forward.

I still wasn\'t understanding a thing so looked at the third result from
my search. The third result led me to [UsageStatsManager AOSP ref](https://developer.android.com/reference/android/app/usage/UsageStatsManager).

This seemed to be exactly wqhat I needed. The granularity included daily
history, weekly history, monthly and annual history intervals. Exactly
what I needed. But I did not know how I was going to run the Java to
extract this data from my phone without having to write an actual
JavaAPP.

So I googled that.

That led me to a [medium article](https://medium.com/@quiro91/show-app-usage-with-usagestatsmanager-d47294537dab) that pointed to this [github repo](https://github.com/quiro91/UsageStatsManager-Sample/).

I always hate it when these android folks don\'t package the apps. But
it happens so often that I miss out on ready made solutions. This time I
decided to do that.

But wait, I need this data in csv format. So why should I bother with
app compilation if all I\'ll get is on mobile access. ADB can possibly
help out now that I know the words to use for searching right? This led
me to searching for how to interface with android UsageStatsManager via
ADB.

There was no way to access the data with adb. At least none that I could
lay my hands on. All pointed back to the unusable \`usagestats\`
service. I caved in and did some LLM search.

I prompted Deepseek and it didn\'t get anything I did not already have.
The packaging was now starting to seem like it was my only. I was going
to have to learn how to build and compile a simple Java application just
so to add csv export functionality and interface with some usagestats
api.

So I went on to install java and android studio. Something I hope to
talk about in another article.

Well, a few hours after I\'d given up and made plans to learn JAVA
android development, I did one last search on Reddit and found out about
StayFree. I figured out how to export the data (the format was microsoft
excel but conversion to csv isn\'t my problem).

But before that, I tried prompting other LLMs just so in case I\'d
missed out on an easier solution than building the app myself.

By other LLMs I mean Claude and Gemini. The answers they gave were no
different from Deepseek\'s. They were as well outdated and depended on a
\`usagestats\` format that no longer was.

I didn\'t want all this time to go to waste that i\'d spent so I googled
for the a solution just one last time. That\'s how I got this reddit
post talking about StayFree\'s export option. And, that\'s how I got all
my screen time history from last year on the 9th of November. I went on
to turn the data into csv and plan a script to combine that data with
data I\'m collecting from my browser usage activity.

Since I could not pull any understanable info from the internet on the
why for the dumpsys format change, I dumped this article in an LLM
prompt box (Gemini\'s that is, since Gemini I\'d believe is more well
versed with the AOSP than any other LLM), and kinda figured it out. I
linked the conversation in the sources section but in summary: The stats
are now meant to tell developers why some app\'s usage was throttled and
the info they convey is more about that: app resource usage management
and not screen time reports.

The time I used for all this i 15x plus the time I thought I would and I
did not even get to complete the project. I sure do need that public insta
accountability it so seems. Classic dev rabbit hole.
Anyways. I now have the data. Also, I moved android dev up my todo list
and have set up the environment already. Oh, I also got to confirm in
action the theory I\'d consumed on how search engines work. So I guess
there\'s pluses here and there.

Thanks for coming this far and as always, I hope you learnt something.
See you when in the next one.

# Sources

-   The old solution repo: <https://github.com/dgreen85/Android-Usagestats-Parser>
-   An article on the old solution: <https://www.dsgreen.io/insights/export-android-screen-time>
-   Claude convo: <https://claude.ai/share/31eea722-8394-47e4-9c03-69e8c87cc867>
-   Deepseek convo: <https://chat.deepseek.com/share/3i67qzxr18q8lsw4jj>
-   Gemini convo: <https://gemini.google.com/share/38f956ec4393>
