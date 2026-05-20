---
title: 'Q2 BT: Tiger and Sheep'
thumbnail: 'img/OIP.jpg'
date: 2026-05-20T15:09:36+03:00
draft: false
tags:
 - brain_teasers
categories:
 - Quant Finance
 - Interview Prep
---


Brain teaser number two from  the book ["A Practical
Guide to Quantitative Finance Interviews"](https://www.amazon.com/Practical-Guide-Quantitative-Finance-Interviews/dp/1438236662) by Zhou Xinfeg.


### Question statement

>>>
> One hundred tigers and one sheep are put on a magic island that only has grass. Tigers
> can eat grass, but they would rather eat sheep. Assume:
> **(A). Each time only one tiger can eat one sheep, and that tiger itself will become a sheep after it eat
> the sheep.**
> **(B). All tigers are smart and perfectly rational and they want to survive. So will the sheep be
> eaten?** 
>>>


### Assumptions

1. Each time only one tiger can eat sheep.
2. A tiger will become a sheep after it eats the sheep.
3. All tigers are smart and perfectly rational: They want to survive. 
4. The tiger that eats a sheep its the whole sheep. There is no "meat sharing".
5. Tigers have two food sources: grass and sheep. 

### Solution and explanation

The question is if the sheep will be eaten. Lets reduce make it simpler by reducing the number
of tigers down to one.

_1 tiger, 1 sheep_

It'll definitely eat the sheep. There's no fear that after it becomes a sheep, itll be
eaten. There won't be tigers left to do that after it turns. 

_2 tigers, 1 sheep_


The sheep won't be eaten since each will be afraid they'd be next in line for being eaten
by the tiger that does not turn into a sheep.


_3 tigers, 1 sheep_

The sheep will be eaten. One tiger will eat the sheep well knowing the remaining two won't dare to eat it. From the previous example we know that in a scenario where there's two tigers and 1 sheep the sheep ain't eaten for the previously provided explanation.

_4 tigers, 1 sheep_

The sheep will stay alive. All tigers will be afraid of becoming the sheep that will certainly
be eaten as per the reasons stated in the 3 tigers, 1 sheep scenario.

_The pattern_

Whenever there's an even number of tigers, the sheep is safe. Otherwise, the sheep gets eaten.


That's it for this one. 