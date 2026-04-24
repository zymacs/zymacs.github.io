+++
title = 'Last Week in Code -002-'
date = 2026-04-23T10:56:29+03:00
draft = false
tag = 'LWIC'
+++


# Last Week In Code 002

And that's one week down. Episode 002 made it to the internet.
A lot's been going on in the dev space. Public dev space. My dev space too. A lot to say I have. So let's jump right in.

## Events and lessons

### Using hacker news: Good tech articles, VC eyeballs, smart people.
Ain't like I have never heard of it, I know the site hacker news. But I'd never taken time to
look at what's posted on their. I honestly thought it was like some 4chan forum for devs. Well since I couldn't prompt for fun for the challenge I took on this week,  I did. And wondered why I hadn't done so earlier. Ain't like all is good on there. Its got a fair share of jerks. But I think there's quite a lot of good dev articles. Most of them technical.

Access to the articles is only one of more that I liked about it.
I've always wondered how I'd go around pitching my product if I ever built one so big it'd need that (for one that does not have access to so many VC sponsors and fellow dev eyeballs).

Well it's got this section called `SHOW HN` that it seems is dedicated to that. An easy way
to collect github stars and contributors quick. Plus, the comment sections for the articles.
People are really nerds. Its humbling being in a comment section and not having anything to say.
Everyone seems to be some inventor of sorts. Won't mention how mean most of them seem to be. 


### Breaking Ubuntu: The cost of for bad documentation habits.

I've for long been waiting for any reason to leave Ubuntu and return to Arch and it showed itself this week. On rebooting my system to install the latest OS updates I lost internet access. I was already hating my Ubuntu experience enough so I took a whole day off to do the heavy lifting that was switching to Arch.

As with _catastrophic_ any event there was a lot to learn here. I have installed Arch before. And I think the concept here applies to problem that does not occur so often yet when it does, finding a fresh solution costs a lot of time and mental energy.

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


## The News

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