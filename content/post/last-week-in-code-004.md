---
title: 'Last Week in Code 004'
thumbnail: 'img/lwic.png'
date: 2026-05-11T17:41:08+03:00
draft:  false
---


It's four weeks already! I spent most of last week writing. I mean, I did give time to other projects beyond writing too but it was mostly writing. 
I thought I had quite a lot to write about and that I was going to produce as much.
But that's not really what happened. I only wrote 3 articles.  There was some lessons to learn from that still. And I'll share those. 


_Teaching, the best way to learn_

## The Protege Effect.
I have installed and reinstalled Arch quite a number of times but all of that was me following already written guides. When I set out to do the task my self,
to write a guide on how to install Arch, I realized I did not know even quarter as much as I thought I did. There was this drive to be able to explain why some
command came after the other and why some step did not have to be done in some way. I found myself reading articles on how differeant parts of the OS work that I
don't think I'd have ever gotten the motivation to read if it wasn't for the writing task. And this phenomenon carried across all articles.

I have way more drafts than what's published for that reason.  I think the only article's I let out, were the one on TCP (Which wasn't my intended article as what I intended to write about turned out
to have needed way more reading before I'd be able to explain it in my own words). I collected scraps from my attempts to write about why downloads are slower with small files
and zeroed on the easier alternative, [how TCP downloads work](https://zymacs.github.io/post/http_downloads/). Then for the article on [Probability](https://zymacs.github.io/post/probability_basics/), thinking about it from the lens which I did made me understand it
more intuitively and arrive at conclusions of my own (like, all probability could be expressed in term's of Baye's theorem).

Now I tried to follow it up with an article on Baye's theorem
but after 3 days of reading , and trust me it would be so unlikely I'd fail a simple question on Baye's, I realized transferring the intuitve explanation to someone else was
way harder than I had already acknowledged it would be. I still learnt alot about what I did not know anyways. And developed better mental models for explainign to others, and to myself.

This whole task developed in me a respect for people that know how to explain technical concepts with as much ease as they seem to have. [The Organic Chem tutor](https://www.youtube.com/@TheOrganicChemistryTutor), and [Ben Eater](https://www.youtube.com/@BenEater) or any other educator on YouTube for instance.
It also got me interested in if this was a formally recognized means to learn since it was non trivially effective in how it deepened my understanding for the topics I read about. And
that's how I learn't about its formal name, [the protege effect](https://www.growthengineering.co.uk/protege-effect/).

Something wrong here. 

## Notes as a living document.

There was some sadness during all this. Some folk , after they are done with school, never get to use any of the work they studied in class. And for that reason, they never get
to feel the consequenes of not having written and or kept good notes. I am not one of those. I have read about the importance of writing and maintaining notes from different sources
but did not appreaciate that advice until it was 5 years late. The fields I hope to have a career in need for me to have explanatory depth for concepts spanning 4 years of school.

Now that ain't the annoying part. The annoying part is I studied virtually all of the 'hard' concepts I find myself going to YouTube for! I got grade A's in some of the classes.
But what do I have to show for it? Nothing. That feeling I am doing double work and will have to for years of notes unwritten ain't a good one. I have learnt the hard way and
that's one of the why's for this blog, and for last week's writing activity.

I find that even when the first writing drafts ain't complete, I always have somethign to return to that grows as my knowledge grows. That I don't have to spend hours again going through
some long youtube video when I already wrote notes and explained it to myself in them. Its like , you have 5 pages explaining 3 hours of content which when you read those five pages, all
the locked memories fromw when you consumed the 3 hours of content are retrieved to working memory.

_Random rant on other projects I spent my time on_

## In other projects

_Scripting_

Scripting. How much efficiency can be gained from the smallest of solutions and the importance of small but efficient scripts is , I think, something that's not given as much attention as it deserves.
A script to make sure you don't commit your passwords to github. A script to clean your downloads folder. A script to deal with port assignment. A script to make sure your directory structure
is uniform across all your computers and ensure it stays as defined. All these are small "unimportant" but frustrating problems devs face which, at least for me, compound into major discomfort for
the developer. Or just a normal computer user, a hobbyist maybe.

However, getting oneself to  write these small scripts is interestingly hard.
I mean, they are easy to write but the fact that their ROI is not understood well enough makes it hard to get one to write one for themselves. Maybe there's another reason and I'd like to hear. 

I have a numer I have written for myself, other's vibe-coded. ,

One dirty but _very efficient_ script to clean my downloads folder, and another one I vibe coded to manage port assignment. Just an aside, there's always this sense of satisfaction when I get into
my messy downloads folder and with one command, wish all the mess away. That feeling my writing energy was not wasted. I like the port assignment script too but you know how it is with
AI written code and the sense of ownership. I am hoping to add another to handle my git operations after I read about git hooks. But anwyways, point is, automation and scripting has way
more value than its given. Interesting as I was searching for folk online to corroborate my sentiments I found [this video](https://www.youtube.com/watch?v=aqfsoTZ4PHY) speaking along the same lines.


_A radio server_
Imagine having a streaming service where you control the EPG. Or  one that could grow to have some AI agents act as DJ's but on your own music doing what you configure them to do. Well,
I'd day that's imagining having your own broadcasting station and I made one step towards that when I set up streaming with [Snapcast](https://github.com/snapcast/snapcast) last week. I think I mentioned this somewhere among the
docker projects in last week's episode but I probably did not link it. Here's an exposed endpoint that's always live when I am. 
- [indieradion](indieradio.keithnambale.com/radio.mp3)

## Misc.

I talked about having too many drafted articles. More on that problem. I think I am going to have to put up a section on what drafts I got in my drafts folder and what article I am working on.
It'll probably help keep me from drifting and also, send notice what article is coming next. You have probably seen that section "In-the-pipeline".

Also, I messed around with my 'baseURL' settings and messed up the font-awesome configuration for the social icons. But , the usual problem, I did not record how I set them up. The icons still work
though. I should be working on that _soon_. That and the search feature.


## In other news

### News Updates
- [Google fraud defence is just WEI](https://privatecaptcha.com/blog/google-cloud-fraud-defence-wei/)
- [France moves to break encrypted messaging](https://reclaimthenet.org/france-moves-to-break-encrypted-messaging)
- [Meta's embrace of AI is making it's employee's miserable](https://www.nytimes.com/2026/05/08/technology/meta-ai-employees-miserable.html)

### Cool articles
- [Three Inverse Laws of AI](https://susam.net/inverse-laws-of-robotics.html)


### Random finds
- [WebRTC for the curios (Used by ChatGPT's low latency speech service)](https://webrtcforthecurious.com/)
- [Since you arrived (What your browser knows about you)](https://sinceyouarrived.world/)


As always, I hope you learnt something from this log and hope to see you around in the next one. 