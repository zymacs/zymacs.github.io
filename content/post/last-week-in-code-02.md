---
title: Last Week In Code -002-
date: 2026-04-23
draft: true
tags:
  - lwic
categories:
  - WeeklySeries
---

# Last Week In Code -002-

Episode 002 made it to the internet. Yay. 
A lot's been going on in the dev space. A lot to say I have. So let's jump right in.

## *Events, Lessons*

### Have you heard of Hacker News Before
_**If you haven't, please do yourself a favor and add it to your bookmarks**_

But I guess you  have. I wonder what your opinions are about it. Ain't like I have never heard of it personally. I know the site hacker news. But I'd never taken time to look at what's posted on there. Honestly, I thought it was some 4chan-like forum for devs. I was not so far from the truth though. But I digresss.

Since I was running an anti-AI challenge this week, I needed some replacement for the leisurely prompting I was doing with AI. HN was that. I then wondered why I no one had mentioned all it had to me earlier.

Now it ain't like all is good on there. Its sure got some jerks ready to bite you for posting. But that's all internet forums for you. But I think there's quite a lot of good. First the dev articles. Most of are obviously technical. I mean, its Hacker News. I read quite a number of well written ones this week. Some AI news. Some just insights from experts.

More to the same point, it seems a collection point for the lastest hottest updates in tech. I got to read release articles for GPT 5.5, GPT Image, Claude and Qwen before I saw any youtuber talk about said models. Oh Meta's keylogging practices as well. Before they pulled the update. 


And there's still more. So I've always wondered how I'd go around pitching my product if I ever built one. For one that does not have access to so many VC sponsors and fellow dev eyeballs, this seemed like free a free goldmine for exactly that. 

Still, same point. It got a section called `SHOW HN` that it seems is dedicated to that. An easy way to collect github stars and valuable contributors.

Valuable contributors? Yes, valuable contributors. Most folk on there are really nerds. So
if you can put up with nerds and you got a complex project. You should probably take it to HN. 

### Breaking then Dumping Ubuntu

**_And the cost for a lack of a Personal Knowledge Management System_**

So I can't tell what OS you use. I'm assuming you use Linux. Or, windows?

I personally daily drive Linux. As for what distro, I'd been settled with Arch for years. 1.5 years precisely. And that was after a good amount of distro hopping.  But then for 'work' reasons, I switched to Ubuntu. And boy do I regret that! I've since been waiting for any reason to give me the motivation I needed to return. That wish was granted this week.

On rebooting my system to install the latest OS updates, I lost internet access next boot up. Now I know a fair share of networking. I didn't get frustrated. Took it as a message it was time to leave. I've been waiting I said. I don't play with networks daily. Best I do is `nmcli connection up conname`. Beyond that everything always just seems to work fine.
So I knew attempting to fix the issue was going to cost me a moon rotation. But then installing Arch takes probably equally as long. So I packed up my data and took a whole day off to do the heavy lifting that was returning to Arch.

After all this time using it daily, it was really frustrating to me I had to take as much time as I did with the last installation. The last time I did was about a year ago. And I remember there was a lot of cursing and googling before I got it running. Now you might say, Just use AI. But this was during when I was not allowed to use AI as per my rules. So I stayed on path and made peace with the fact it was going to be one straining day.

But that was a good thing on the other side. As it is with _catastrophic_  event.
And I think the concept here applies to problem that does not occur so often yet when it does, finding a fresh solution costs a lot of time and mental energy.

There's a lot of talk about learning to find solutions online. But not so much on how to maintain those solutions . To optimize them for quick access should the problems resurface.

I hated that i had to source articles on 'how to do this' and 'how to do that' when I'd already done that countless times before. Ain't saying you should memorize it all. But am sure you can attest to this, a solution thats in your words at arms reach takes way shorter to apply and costs way less mental energy.

Oh, I know about the installer scripts but I'm sure I'll want to learn how it works soon so I opted for the manual method. Saves time in the long run.

I should be writing a `how to install arch` article soon among others, just as a counter measure.

### The cost of addiction to quick llm solutions: Frustration at the slightest error

So as I mentioned in an earlier article, this site uses Hugo, the static site generator.
But save for installing the theme and running (`hugo server run`) to build the site, I have no idea as to how it does what it does. Should I? There's a lot to know. And it was working fine so
what was the reason to.

But I'm learning the price of that mentality. Maybe its part of the challenges am facing for using too much AI. Or it'd been a long day fighting Arch. Anyways. I installed hugo. Simple `sudo pacman -S hugo`. CD'd into the sites folder and ran the previously mentioned command, `hugo server run`). Expecting it'd just work Iike it was on Ubuntu. Well.. Error.. I didn't even read what it was. The gibberish that was the error message made my brain scream. I ran the command again,so surprised why it wasn't working. More frustrated realizing I didnt have the option to use AI. _trust me even if I did, experience has shown how painful llms can be with linux errors_.

So I tried changing a few random things. So sick after all I'd gone through installing the OS, I was going to end the day with a message 'Go back to Ubuntu'. 

So I opened a brower window and was like, hmm. How about I read the error message and try to find if anyone's faced the same problem before. Yep, something that simple does not easily come to mind when you are used to things always working fine out of the box, and throwing it at LLMs.

And i did. The hugo version I was using had a documented issue that wasn't going to be fixed soon. So I tried looking into how to install older versions with pacman. But that seemed so involved and i was so tired so I settled for the node version. Which after humbly sitting down and trying to understand the errors it was throwing, I got it to work. NO LLMs were used. Felt good about that.

Now the news.


## In The News

### My take.
   - So I mentioned I was reading a lot of Hacker News this week? Well you don't have to be doing that to notice the pattern sweeping across major LLM companies. Every time a new version is released. Its better. Its best. And its why the internet will never be the same again.
   - Here's some new releases from just last week. Notice the pattern for yourself.
     - GPT 5.5
     - Qwen
     - Claude

### AI and the AI resistance
- Meta keylogging and screenshotting employee's work computers to make LLM's better.
- Poison fountain, .ass subtitles and more.

### Insightful dev articles
- The rules of software development




That's enough for e002
Hope to meet next week. It's in the plan. If with anything to share or any comment to put across, my socials: Bluesky, Telegram.
