---
thumbnail: "img/OIP.jpg"
title: 'Q1 BT: Screwy Pirates'
date: 2026-05-19T19:48:27+03:00
draft: false
tags:
 - brain_teasers
categories:
 - Quant Finance
 - Interview Prep
---


This is the first post am making in this series. For all the posts in the series,
I plan to share my solutions to the problems in the book ["A Practical
Guide to Quantitative Finance Interviews"](https://www.amazon.com/Practical-Guide-Quantitative-Finance-Interviews/dp/1438236662) by Zhou Xinfeg. The first
set of problems is brain teasers so let's get to the first one.


### Screwy Pirates Problem Statement.

>>>
> Five pirates looted a chest full of 100 gold coins. Being a bunch of democratic pirates,
> they agree on the following method to divide the loot: 
> The most senior pirate will propose a distribution of the coins. All pirates, including the
> most senior pirate, will then vote. If at least 50% of the pirates (3 pirates in this case)
> accept the proposal, the gold is divided as proposed. If not, the most senior pirate will be
> fed to shark and the process starts over with the next most senior pirate ... The process is
> repeated until a plan is approved. You can assume that all pirates are perfectly rational:
> they want to stay alive first and to get as much gold as possible second. Finally, being
> blood-thirsty pirates, they want to have fewer pirates on the boat if given a choice
> between otherwise equal outcomes.
> How will the gold coins be divided in the end?
>>>


### Assumptions

Not one pirate is at the same rank as the other. Ranks go  from least to highest with one pirate
at each.

Pirate number one is the highest ranking pirate and so on until pirate number last, the
least ranking.

Its a democracy. The pirate needs to always have their proposal winning by 50% to survive being ousted.

All pirates assume their pirate mates as rational and as ruthless as they themselves are.

### Solution and explanation.

_2 pirates_

Lets bring the total number of pirates down to two. If the rules stay the same, what would be
the remaining number of gold coins after voting? They will all be taken by the Senior. Why?
The Senior gets to decide what the dividing criteria is and since there's only two pirates on
board, there's no threat to the Senior's life (an event that can only occur if the Senior's proposal
is outvoted) and his win is guaranteed. The Senior therefore optimizes for
maximum profit. The Senior takes all the 100 coins.

_3 pirates_

Okay, leveling up to three pirates.  If we have three pirates, with one obviously a Senior,
the Senior will have to strategize to win the vote with a 2/3 for their proposition. Since all
are rational pirates with a preference to their own lives over money other factors kept constant,
yet brutal enough to kill for money if they won't be killed, the Senior will propose to
keep 99 coins and give the third pirate a single coin. Why the third not the second?

If the Senior proposes to give the one coin to the second , or, second ranking pirate to him, the second will vote against this senior since they know that by so doing they will get the Seniority rank and come next voting, get all the coins (as we demonstrated in the example with 2 pirates before).

Also, the third pirate or least in rank at this instance, will gladly vote against the Second pirate
since they would otherwise get nothing when the Second pirate becomes the new senior.


_4 pirates_


The most senior pirate now needs two people on his side for a democratic win. He will obviously vote
for himself. He should therefore win over one head to his proposal's side.
From the previous example we know that the third
pirate get's to win by making a proposal that denys the second any coin for the explained reasons. The Senior pirate therefore makes a proposal that gives this pirate a single coin. He keeps the rest for himself.He does this because the second ranking pirate,  would otherwise not have gotten any money. And this
pirate would prefer a proposal that makes it so that won't happen.



_5 pirates_

Okay, now for the number stated in the question. The most senior pirate now needs 3/5 votes
for a democratic win. What proposal to make and why?

Again, this pirate will vote for himself so his task is to get two extra voters.
The most senior pirate here will propose to give the least ranking and 3rd ranking pirates a coin each. These would otherwise, again, as described in the previous scenario, have gotten nothing. So they will glady
make a vote that ensures that happens. They will support the most senior pirates proposal.

The Senior will keep the remaining 98. 


_Formalizing the pattern_

If we have 2 pirates on board, the most senior takes all.

If we have 3 pirates on board, the least gets one , the most senior gets the balance
and the second gets none.

If we have n>3 pirates on board, and n is even, the nth pirate being the most senior;
the nth pirate divides (n/2)-1 of the  coins equally among (n/2)-1 pirates choosing pirates
using the series n-2i i starting at 1 and ending at (n/2)-1. The rest
they take.

if its the previous scenario but n is odd, the most senior pirate or nth pirate divides equally
ceil(n/2) of the coins among ceil(n/2) pirates choosing based on the same sequence from before sequence:
n-2i for i starting at 1 and ending at ceil(n/2)
if we have n>2 pirates on board and 
the nth pirate will always propose to give the (n-2)th pirate and (n-4)th pirates 



Alright. I guess I have to work on generalizations. That was a hard one to generalize. 



With that, see you in the next one. 

