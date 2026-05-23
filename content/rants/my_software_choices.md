---
title: "My Computing Environment & My Software Choices"
thumbnail: "img/terminal.png"
draft: false
pager: false
tags:
 - rant
categories:
 - random
---

This'll be a long mostly unstructured monologue about what OS I use, what software choices I've made and the some brief reasoning for those. A second draft that I decided to make live for reasons I mention at the end of the article. First on using Arch then onto software choices.

So I use Linux. Arch Linux. And for a window manager; i3. 

Now I did't start here. I went through the common natural evolution of the Linux User. 

In my first Linux days, I had a fare share of [distro hopping](https://www.youtube.com/watch?v=OZeCN_DdqaM) and the dopamine hit that provides. I honestly at times reinstalled operating systems just for the same reason one would grab a  beer to alleviate depression.

I hopped from Ubuntu onto Mint then to Kali, to Parrot, the list is endless. I'd say I tried virtually all distros that were real popular then. I reached a point where I ran out of 'new ones' to try out and went back to older ones. Thought it'd be that way for ever. It so seems to be that way for some. But not until I installed Arch.

All distros I installed before Arch had graphical installers. You know how it is. Create a bootable drive,
plug it in, click click and you are in. Arch was different.  For all the Unix-like and Unix Operating Systems I've installed, none was as involved as Arch. FreeBSD was a bit non-conventional but it did not give anything close to what Arch did. Oh, I sure will add something to this piece about FreeBSD but I guess that'll be later. Hard as it was I eventually got it running. 

But that was only the start of the process. I had to choose a window manager. I had to deal with audio. Bluetooth
had issues. There was nothing at all in the home folder (something I discovered I actually really liked). It had
no default apps installed at all. Almost all I needed I had to figure out how to install.

I can't count how many times I broke my system and took full weekends off on repairs. It broke really often.
I did have my times folly with Ubuntu also. And this ain't a joke, I did run into times when I mistakenly
"rm -rf /home".

But even when I didn't read as deeply, that's problems that happen so rarely today. 


People have different reasons for using Linux. Some are looking for a means to rebel against Windows. Those
don't usually last so long. Others have it forced on them for work. But that's rare. Any such work should
only deploy enthusiasts in my OP. But then for others, when we get to say Arch, .. Gentoo , BSD and the new
OG : GUIX, the reasons change. I installed Arch just because everyone on youtube said it was cool. But then
I learnt why I was actually pulled to linux in general after I did.


-- to add new paragraphs here.

Why Arch not Ubuntu? Control hunger and hatred for bloat, The Peace ...
Plus, I sure do hate that  '.snap' folder in the Ubuntu home directory. It makes the directory look disproportionately off in ways I can't explain. And why i3? I hate bloat, I'd like to learn to work with my keyboard. I have debian on my tab though. Ain't about to change that ever. Blame it on microsoft. 


I have intentionally chosen to leave the installation mostly bare. There's  no service to handle notifications. The wallpaper is non existent. No lock screen.  There is no File Manager. The core utils are a more than sufficient replacement. Its mostly all configs and terminal commands. 

There's not a lot of clicking and dragging. A few instances when using my browser.
I actually wish there was none. You know, that tends to kill flow. If you use the terminal for long, you'd relate to the reluctance to do any operation that'll take your hands away from your keyboard I am sure.

For editing, I use Emacs. Well calling Emacs an editor is such an insult. And I ain't trying to do that.
I sure know what it can do. I'd say, I've only scratched 0.5% of it for the 7 to so months of shallow usage
I've had with it. I can't mention all that's good about it but suffice it to say, past some level
of learning  (yes, it requires a significant amount of learning), you'd become a FOSS advocate and never turn
back.


My experience with FREE BSD

I like Arch, I cant say BSD is better than Arch. Both are good in their own respect.
Still growing and I think as I do I will be more capable of putting in words what I mean by that.
But, BSD is indeed its own world.
I like how it incentivises self reliance. It does that like no other OS I have used before.
It does so in a way that evokes a feel you can't ignore. I guess the only reason i left it is a lack of a community online to relate with while i was in. I definitely have a PC lying around with FREEBSD on it when I have the means. Or just have months where I daily drive FREEBSD for the feeling of independence.
I didn't like doas though. Sudo just feels more powerful.


You will definitely enjoy [this one](https://youtu.be/7Adl1BTCwoY?si=5TJSbrakx9-tdwI-) on linux users.
Or even [better](https://www.youtube.com/watch?v=lE4UXdJSJM4) .



I've not  seen any editor yet, unless a derivative of emacs, that allows running more than one language in the same file. Oh I called it an editor again..my mistake. It also supports internet browsing, music playing , project management, the best mgt tooling aroung git: Magit. And if there's
anything you want it to do that ain't built yet, learn Elisp and you'll have it.

Plus, with all the power it provides, its baffling that its totally yours to modify. And to resell. 
See the GNU licence.  _[Dancing in the GNU Light](https://youtu.be/lE4UXdJSJM4?si=uaYH5lwoCFScLnoe&t=144)_.

A  huge percentage of my PC usage is editing files so you can bet if my PC is open, its open too.
That, my terminal and my browser. 

Speaking of browsers. My browser works more than just a means to access files on remote servers.
I started out wanting to "live in the terminal": Use MPV for media playback, ranger for file management, 
just avoid the GUI as much as I could.

But that's changed to the browser as I've gotten more and more into self hosting. I've for long wanted to have unified access to all my media consumption activity for analytics and AI project ideas and,
having a browser centric means for media consumption really solves that problem.

Plus, with the oncoming world id drama, I don't think there's ever been a better time than now for someone to learn to self host.

My browser plays my videos (Jellyfin) , handles pdf reading, views my photos (Immich), plays my music (Navidrome, AzuraCast). The list of things is endless. There's these days a containerised version for almost any app you could think of. 

On what browser it is, its firefox. But I like Librewolf better. I think it ain't so much about the browser being 100% spy proof but about the perception its trying to be. Firefox seems to be failing at providing that perception
of recent. Now I could write an article as long just talking about my browser's extensions but I'll try to keep
it brief.


I wish I had a self hosted password management solution (yes, that has its downsides. but what doesn't?). But what
I have is better than, for my definition of better that is, the Google Pass alternative. I now use Bitwarden. Its closer to my ideal perception of privacy than any alternative I can currently get myself to access.

I think the only problem I currently have with it is that I need internet access to get in. I tried the self hosted solution before I opted for the freemium version after I found out how super involved the setup was.  I'll come back to that later when I settle I'm sure. But for now, password management related issues never register on
my radar. 

It generates passwords and provides safe storage for them. That's like basic stuff all
password managers do. It checks leak databases to ensure the passwords you use have not been exposed in some recent leak. You know how on most websites you have to fill in all these bio data forms? It
keeps entries for that your data and auto fills that in when those forms pop up.

And it can keep more. It supports user defined entries. The premium version also supports document storage. So you could maybe keep your CV or whichever other document at hand.

Hand on red hot coal, I had this idea exactly as its built out by Bitwarden  for a unified bio data and secrets manager. But you know how when you try to build something then you learn why those more capable than you opted to use a ready made solution? I guess thats what happened. Its a project I haven't taken off
my list though. If the self hosted version does not provide these features when I set it up I will consider
reviving the project.

I don't consume any ads. And I use the internet. Thats so rare these days. Unless its apps like instagram
where there hasn't been made yet a way around them, I wonder why anyone still finds it normal fighting
through endless redirects to strange websites just so to read a 5 paragraph article. For this service, I
use ublock origin. Chrome only supports the lite version but if you want to use ublock origin you could as
well install librewolf, or , at least better than Chrome, firefox.

I usually like to keep local copies of certain website pages for offline reference among other reasons. I initially used to use weptopdf for that but have since found it frustrating all the steps involved to get that working. I mean it ain't many but if there's a means to have fewer steps then whoever provides those means makes webpdf feel slow. I use Single File for that now. I don't always want the pages I save turned to pdf anyways. It keeps them in their original form: html and css.

I don't get it why websites today expect readers to read with bright light beaming straight at their eyes.
Why isn't dark mode the default mode I still wonder. For ensuring that is while I browse the internet, I use
darkreader. It automatically, for as long as it is switched on, provides dark mode even for pages that
don't have it built in. It sometimes gets things wrong but very rarely. I honestly can't remember when that
last happened to me. Shift+Alt+A to toggle between light mode and dark mode. 


Some extras.

There's certain websites as I build some variant of a local internet that I'd like to have a deep copy of.
An archive if you may. For that, I use httrack. 


This article is a half ready draft that I decided I'd publish and make better while its live so you
can hope its going to go through a lot of changes. If you are reading the earliest version of this
then I'm sure you did not find any links to the software I mentioned. I find that I see my mistakes
more clearly when I read my site after its live than when its only available on localhost. I haven't figured
out why that is yet.

But anyways. That was a long monologue. A strange way to suggest some software but I hope you picked something.
I wish this blog had a comment section and I will make that wish come true soon. But for now, my BlueSky or my Email will do. Please don't hesitate to reachout if with any comments or any suggestions regards you think I
might be interested in. IN THE NEXT ONE.. 

