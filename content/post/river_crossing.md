---
title: 'Q3 BT: River Crossing'
thumbnail: 'img/OIP.jpg'
date: 2026-05-20T15:49:44+03:00
draft: false
tags:
  - 'brain_teasers'
categories:
  - 'Quant Finance'
  - 'Interview Prep'
---


Question 3 from  the book ["A Practical
Guide to Quantitative Finance Interviews"](https://www.amazon.com/Practical-Guide-Quantitative-Finance-Interviews/dp/1438236662) by Zhou Xinfeg.


>>>
> Four people, A, B, C and D need to get across a river. The only way to cross the river is
> by an old bridge, which holds at most 2 people at a time. Being dark, they can't cross the
> bridge without a torch, of which they only have one. So each pair can only walk at the
> speed of the slower person. They need to get all of them across to the other side as
> quickly as possible. A is the slowest and takes 10 minutes to cross; B takes 5 minutes; C
> takes 2 minutes; and D takes 1 minute.
> What is the minimum time to get all of them across to the other side?
>>>

### Information summary

- Total head count:  4.
- Max cross load:  2.
- Torch count: 1

### Speed ranking

- A : 10 minutes 
- B : 5  minutes 
- C : 2  minutes 
- D : 1  minute  


### Assumptions
- None significant to be made. 


### Solution and explanation

D goes with A, that's 10 minutes.
D brings back the torch. That's 11 minutes.
D goes back with B. That's 16 minutes.
D comes back, 17 mintes,  and takes the last route across the bridge with C, 19  minutes.


How about if we group the two slowest people together?
Ah, that would raise total time too fast.
A goes with B, that's 10 minutes.
B returns, thats 15 minutes.
B goes with C, that's 17 minutes.. Not feasible.


C goes with D , thats 2 minutes.
D returns, thats, 3 minutes.
D goes with A, that's 13 minutes.
C returns, that's 15 miunutes.
C goes with B, that's 20... woof..

C goes with D, 2 minutes.
C returns, 4 minutes.
A goes with B, 14 minutes.
D returns, 15 minutes.
D goes with C, 17 minutes.. that's probably as low as we can get.

### The trick.

If the two slowest people cross first, we'll incur a tripple time expenditure for the faster of the two. In the solution attempt, when we sent A across with B, we
had to deal with B's return and repeat sojourn across the bridge.

If a faster person moves with the slowest person, we waste time that would have been saved if that slowest person crossed with someone that
was next in ranking for slowest.

So we find means to get the slowest two out together without incurring the tripple waste described earlier. We make sure a faster person is
already across waiting to return for whoever will be left when the slow pair makes it out.

We send out the fastest two first, say C and D, let one of them return, send out the slow pair. Send the faster person back for their
fast counter part. Just like we did for the strategy that yielded 17 minutes.

Now how do we generalize this solution so it works with arbitrary max crossing limits and any total number of people crossing? I haven't figured that out yet
or if it can be done.

But we could try with an example of 10. That's people A through J. A is the fastest, crossing in 1 minute. J the slowest taking 10 minutes to cross.
The bridge can hold up to 3 at a time.  There is 1 torch. Question: Min time to get everyone across. 

A, B, C, D, E, F, G, H, I, J

We could first get A, B, C across. That's 3 minutes.
A comes back. That's 4 minutes.
A crosses with D and I and J, thats 14 minutes.
A comes back. That's 15 minutes.
A crosses with G and H. Thats 23 minutes.
A comes back. That's 24 minutes.
A crosses with E and F. That's 30 minutes. 
A comes back. That's 31 minutes.
A takes the last person across; D. That's 35 minutes.   

It seems like there's a pattern.

Anyways, that's it for this one. 



