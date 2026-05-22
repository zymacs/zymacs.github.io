---
title: 'Probability Intuition : The Basics'
thumbnail: 'img/probability.jpg'
date: 2026-05-08
draft: false
tags:
  - probability
categories:
  - Maths
---

How likely it is that some outcome will be the outcome given some event. That is what probability is.
Its a ratio. Given an event, there's many possible outcomes. The probability of some outcome being
the outcome that happens is a ratio of how much of the outcome is represented in total outcomes to the total number of possible outcomes. For unweighted or equally likely outcomes at least.

Its a very important foundational concept in a lot of Computer Science Fields.
Without understanding how it works, you'll have a hard time understanding more advanced concepts like the Baye's theorem, or
wrapping your head around what's going on with Markov chains or,  working with the foundational concepts for most of modern AI i.e:  Neural Networks. I'll try to explain my understanding of it to you here without using any formal terms. So don't be surprised if you don't see a
lot of `P(A n B n C)` or `posterior` and the such. There will be time for that. 

So, say we toss a fair coin that then falls on one of its faces. The event is tossing the fair coin that'll fall on its face with each face having equal chance of being THE FACE.

Now when a coin is tossed, there's a lot of resulting events upon which we can bet:
- Standing: It could fall on one of its faces or stand on its edge
- Making sound: it could produce sound or make no sound,
- Rolling: it could roll or not roll.

We therefore for simplicity idealize the coin toss event and assume only one of these happens when we toss the coin: landing on one of its faces. We now make bets for what side it will land on. There are two possibilities: The Head and The Tail.
In a given question, we want to find the probability it will land on its head.
The total representation for the head side among the total sides for a fair coin is 1.
The total number of sides is 2. The probability then is, sincce each side has equal chance of being THE SIDE, 1/2.
Its a 50 50 chance.


Lets look at another example. There's 3 possible weather conditions for the day Monday.
Each is equally likely to happen. It could rain, shine or be windy. What's the probabillity it will rain?

The total number of possible outcomes here is 3. Rain is represented once among the outcomes. So the probability is 1/3.

If you are following, you have probably already noticed from the two examples that total probability sums up to 1.
For the coin toss, it was 1/2 chance for each side. Which sums up to 1. For the weather conditions, its 1/3 for each condition. Which sums up to 1. And thats how it ought to be. If any calculation for how probable some outcome will be evaluates to a number more likely than absolutely likely , which is 1, it is wrong. Absolute probability? 

How likely is it that a given a bag of 10 black balls, a random blind picking will produce a black ball? Absolutely likely.
Since the total number of black balls is 10 and the total number of balls regardless of color is 10, the probability is a 10/10 which is 1. Makes sense right? Yes right it does. 

One other thing to note: Probability can't be less than 0. Which is: an outcome can't be less probable than than absolutely impossible. If we are given a barn of 10 birds and asked what the probability is a random picking from the birds will yield a cow, the answer is a 0/10.
0 cow outcomes / 10 possible outcomes.


Okay, let's level up.
Say we have a die. This die got 5 sides: A, B, C, D, E.  A, B, C, D, E coincide with numbers 1, 2, 1,4,5 respectively.
We are told side A is twice as likely to appear as any of the other sides.
We are then asked for the probability the face of the die will be a `1` when on a roll event, it lands flat on the ground.
This is two questions in one. So first we find the probability for each side.
Remember we are told A is twice as likely to appear as the rest. This implies the rest have the same probability `p` and A has probability `2p`. But we also know total probability for all outcomes from this rolling event is 1.
So we find p buy summing up all them probabilities and equating the sum to 1 to solve for p.
That is

``` python
2p + p + p + p + p = 1
6p = 1
p = 1/6
```
So p(A) is 2/6. Which simplifies to 1/3. We now find what one of these outcomes will be a 1. This might be a bit confusing but itll make sense.  1 appears on A and on C. 1 can appear if either one of A and C comes on top.
So we got to add these side's probabilities up.
`P(A) + P(C) = 1/2`. That's how likely it is we shall get a side with a number 1 on it. 

Look at it this way. If we have five sides: A, B, C, D, E.
P(A=1) = 1/3, P(B=2) = 1/6, P(C=1) = 1/6, P(D=4) = 1/6, P(E=5)=1/6. Summing up all likelihoods for some event's outcomes evaluates to 1. 
Now out of these likelihoods, we need those that coincide with the value 1 being on top.
And that's the sides A and C. Hence it follows that the answer is P(A) + P(C). That is `1/3 + 1/6`.
Which gives us 1/2. Actually, if you add up the probability of 1 appearing and the probability of all else appearing  (1 not appearing that is), you still have total probability as 1 as earlier stated.
Let's do it.

```
1/6+1/6+1/6 = 3/6 = 1/2
```

That's for sides B,D,E.
Add that to 1/2 for sides A and C and you have 1.

Restating my earlier claim. **The sum of the probability of some outcome and that of its inverse is always 1**. 

Okay, lets make it even more complicated. Say we have our coin from earlier. We flip the coin 2 times. We want to know what the probability is that we shall get a head come the last flip. 

Here's the possible outcomes
|Path | Outcomes (short) | Outcomes (full) |
| ------ | ------ | ------ |
|1.1 | HT |Head to Tail|
|1.2 | HH | Head to Head|
|2.1 | TH | Tail to  Head| 
|2.2 | TT |Tail to Tail |





The total probability for the all final outcomes resulting from flipping a coin twice is 1.
There's a number of outcomes, 4 outcomes that is, each sharing some fraction of the total chance that is 1.
For the outcome following structure 1.1 in the table above, where we have a Head on the first flip event,  then a  Tail.
The probability of getting a Head, P(H), iis 1/2. P(T) or the probability of getting a Tail is 1/2.
Multiply the two to get that path's probability, a  1/4.

Multiply not Add? These are two events happening one after the other not two possible outcomes from a singular event.
It ain't a  "you get a head or a tail" situtation. Its a you get a head then a tail probability situation.
The next event updates the previous one hence the multiplication. Or to be more precise, a proportion of what came from the previous event makes it to the next. 1/2 of previous event's probability
is 1/2*1/2. `of` here denotes multiplication.
But no worries if that's still hard to understand.  We'll look at a probably better example to drill down this concept right after I'm done with this one.

One other thing to note is for this example,  the second coin flip's outcome isn't really affected
by the first one's. SIt's however still a good example to make the point for why its multiplication and not an "OR" or
addition situation.

Do the math across all 4 paths in the table  and you have 1/4 for the paths 1.1, 1.2 to 2.2.

Continuing with the question, the probability for getting a head is a summation of probability
shares for all paths ending in H. Thats 1.2 and 2.1. Thats 1/4 + 1/4 which is 1/2. 

Back to that multiplication principle with this example.
We have a bag of balls. The number of balls is 10. 4 are red, the rest are blue. 6 that is.
We are going to have 2 blind picking events. Every time we pick a ball, we shall place it outside the bag. That is, we shall
be picking without replacement. Now the question. What is the probability that come last picking event, we shall pick a red ball?


Alright let's deal with it.

_First picking_

We have two possible outcomes for what color the ball will be: Red and Blue.
What is the probability we shall get a red ball? Its the number of red balls out of total number of balls.
Which is  a 4/10. What is the probability we shall get a blue ball?
You could go back and calculate that from the number of blues or just subract
4/10 from the total probability and get the same answer: 6/10.


_Second picking_

Now moving on to picking event number 2, and here's where you need to pay close attention.
What is the probability of choosing red given in event 1 we chose red?
Is it 4/10? I mean there's 4 reds out of all balls right? Well, if you were following closely, I mentioned, we placed the balls we picked
out of the bag. We did not place them back into the bag. So the total number of balls fell to 9 after picking event 1. Also, since
in the previous event we placed a red ball out, the number of reds has fallen to 3.
So the probability is a 3/9. Calculating what the probability of choosing a blue ball is given we chose blue in round 1 follows the same concept. It'll be a 5/9.
It helps to visualize these probabilities as a tree and I have attached an image of one below.

![Probability tree for 10 ball problem](ptree.png)

_Add to the first ball that **P(Picking a Ball)** is 1. The probability of picking a ball is 1. I think it makes it easier to understand the rest
of the tree._



So now the question. It asked for the probability of choosing a Red.
Like in the coin flipping example, we'll calculate the probability  for each outcomes path then we'll extract
the probability values for paths ending in red and sum them up. The latter part, the addition, you already understand from a previous example. So let's focus on the path probability part of it.

For path one, its a Red on round 1 then Red for round 2.
First we get a 4/10 then we further split it up into Red and Blue.
The Red end path's probability is ... 4/10 * 3/9.
The Blue end path probability is 4/10 * 6/9.

Why? Total previous probability is 4/10. A fraction of the previous event's probability results in Red, the other fraction results in blue. The sum of these gives the whole that is 4/10. The fraction that results in Red is 3/9 of the whole, which whole is 4/10.
The inverse for this is 6/9 of 4/10. Its the same as it was for event 1.

```
P(Picking Balls) = 1.
P(Red Balls) after P(Balls) = Num Red Balls/ Num balls * P(balls) =  4/10 * 1 = 4/10.
```

Here its something like;

```
P(Red ball) = 4/10.
P(Red ball now) after P(Red ball previous) = num_red_balls now /num_balls_now * p(red_balls_previous)
num_red_balls now /num_balls_now * p(red_balls_previous) = 4/10 * 3/9.The prior is a whole. All that sprouts from it is a fraction of it. 
```


Also, for the probability we get a Blue ball after event one resulted in a Red ball, why is it a  6 for the number of blues and  not a 5?
We picked red out in the previous event so the number of sixes remained intact.
That's why. Examine that tree some more and itll make sense.


Think of it this way. If you have to bet on 10 things happening consecutively. Its highly likely you might
get the first bet right. Not absolutely but, relative to getting two in a row at least. It would not make
sense even outside math to assume it'd be more likely to be right about three outcomes from a random event in
a row than about 1.

Here's another intuitive explanation/example. You have 5 rounds of poker to play.  You bet on winning them all, the chances you win the first 2 should obviously be higher than those that you win the first 4. The chance that you win the first one is highest here obviously. 

Okay, that's a whole lot for a single article I think. I should keep the rest for the next one. Which I am not sure when it will be out
but hope to have it out. I am writing all these in preparation to hopefully explain neural networks. So I dream to write about
Matrices, Probability, Baye's, Simple N-gram models and all before that happens. Let's see how it goes.

Again, I hope you learnt something and see you in the next one. Oh, if I made a mistake anywhere, please freely reach out to me at [zymacs@zmail.com](mailto:0nkzhmhoq@mozmail.com)  or via [BlueSky](https://bsky.app/profile/zymacs.bsky.social) point it out. I'd highly appreciate that.



Still here? So I was reading through what I a random statement I made stood out.

> The prior is a whole. And all that sprouts from it is a fraction of it.


_I found and still find that really interesting. I mean, it makes you wonder: **Is there a prior that has no prior?** How deep is this prior rabbit hole? In this our world, the total possibility is 1. Could it be that this 1 is a 6/10 in reference to some prior where more is possible , say the remaining 0.4 ? Can we even know?  Still if there's a prior to our world, maybe even for that world theres another prior.
Interesting how intuitively trying to understand Probabilities can lead to questions about limits for knowledge and what's possibe_

Anyways, Adios. 