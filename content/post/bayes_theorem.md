---
title: "Baye's Theorem: Informal Proof and an Example."
thumbnail: "img/bayez.jpg"
date: 2026-05-14
draft: false
tags:
  - Probability
categories:
  - Maths
---


Alright. I have tried to find the easiest way to explain Baye's. I have watched quite a number of
videos and read quite a number of articles to suppliment what I already know and to get better
devices for delivering the explanation. At this point I  think its now just me being a perfectionist.
So I'll teach it as best as I can get myself to: Using proofs.

First let's state it formally

```
P(A | B)     = (P(B | A) x P(A))/P(B)
```


Where P(A|B) means the probability of event A happening given event B has happened.
In other words, in B's world, what is the probability of A happening.

Now let's derive it.

The point is clearer with a venn diagram. Say we have two circles A and B.
A has 5 elements and B 6. The intersection has 2 elements. The probability of
event A given the sample space (which is all elements in both A and B) is 5/9.
Wait where does the 9 come from? A has 5 elements, some of which include B's (from the intersection).
So to get the total number of unique elements with A and B combined, we add the elements
in A only, those in the intersection then  those in B only. Those in A  only are (5-2) which is 3, those in B only are (6-2)
which is 4, adding the 2 from the intersection brings us to 9.

So P(A) = 5/9. P(B) is obviously 6/9. P(AnB) which is the intersection or number of elements in both A and B is 2/9.

Now how about P(A|B)? We have already defined this to mean the probability of A in B's world or the chances of
A happening given B having happened. In a venn diagram we would zoom in to assume only that which was in B is what
existed and our total number of elements was the total number of elements in B. Our P(A|B) would then be
tne number of elements in B that are also in A out of the B world sample space which is the number of elements in B.
That would have been Num elements in (AnB) out of Num elements in (B).

P(A|B) would therefore have been 2/6.
Why over 6 not 9? We are in B's world. P(A|B) means, in a world were the bound's are B's bounds, what are the chances
of A? Just like it was in the given sample space of 9 where the bounds are all elements in A and B and P(A) was actually
`P(A| sample space = num elements in both B and A =  9)` , here we have `P(A | sample space  = num_elements in B =  6)`.

But word B is subdivided into 2. The elements that belong to B only and those that appear both in B and in A.
What's in the other world? What are the chances for B only? Thats a simple 1-2/6. The whole is world B.
If one part is 2/6 then the balance can be easily inferred from subtracting the known part from the whole.
P(B only | B) is 4/6.

```
  P(B | B) = P(AnB | B) + P(B only | B) -- eq1
  P(A|B)  = num(AnB)/num(B)             -- eq1.1

  P(A | A) = P(AnB | A)+ P(A only | A)  -- eq2
  P(B|A) = num(AnB)/num(A)              -- eq2.1
```

Notice the intersection is shared across both P(A|B) and P(B|A).

It seems to me like we could use P(A|B) to get P(B|A). Since P(B|A) is `num(AnB)/sum(A)` and and multiplying P(A|B) by num(B)
would give us num(AnB), a component of P(B|A)'s numerator.  The same could be said of P(B|A).
Multiplying P(B|A) by num(A) would give us num(AnB). In otherwords, num(AnB) is either P(A|B)*P(B) or P(B|A)*P(A).
Based on that we can rewrite the above statements to have:

```
  P(B|A) = (P(A|B) * num (B))/ num(A)
  P(A|B) = (P(B|A) * num (A))/ num(B)
```

But the theorem got P(B) and P(A) not num(A) and num(B). That ain't no prob. In the world of all elements in A and B,
the number of elements in the sample space for P(A) and P(B) are the same. So if P(A) is 5/9 and P(B) is 6/9, dividing
P(A) by P(B) is equivalent to dividing the number of A elements with the number of   B elements. The denominators
cancel out. So the last two expressions could be re written as

```
  P(B|A) = (P(A|B) * P(B))/ P(A)
  P(A|B) = (P(B|A) * P(A))/ P(B)
```

Now that the conceptual ground is laid, let's use the theorem.

We have a popular Telegram channel called SureOdds that provides `sure odds` for soccer matches.
This channel is right about its predictions 90% of the times. You want
to place your bet on ManPity's match for tomorrow and sure odds said it'd
win this match. Would you bet a win or a loss for ManPity?

I'm guessing you'd place your bet on ManPity winning since SureOdds said it
would and, its right a huge `90%` of the times. So there's a 90% chance ManPity
will win, right? Well.. not really. 

The stats we are given are useless for our usecase. We are interested in the probability of SureOdds
being right about a ManPity win prediction. Not any other kind. We'll have to do some math to figure that out.
ManPity's statistical chances for winning this particular style of match are at a 0.4.
That puts the probability for loss at a 0.6. Also, looking at more statistics,
the numbers for how often SureOdds has been right about a ManPity win given it actually won stand at
a 0.15. And those that about it predicting a win when ManPitty actually lost stand at 0.2.
Given the numbers, let's keep that 90% to the side and establish SureOdds actual credibility. 

```
  # our data
 
  P(W)   = Probability of ManPity winning = 0.4
  P(L)   = Probability of ManPity lossing = 0.6
  P(S|W) = Probability of SureOdds predicting a win given ManPity actually won (from past stats) = 0.15
  P(S|L) = Probability of SureOdds predicting a win given ManPity actually lost (from past stats) = 0.2
  P(S) = P(S|W) * P(W) + P(S|L) * P(L) # predict win and pity wins OR predict win and pity loses = 0.15*0.4 + 0.2*0.6 = 0.18
  P(W|S) = What we need = Probability ManPity shall win given SureOdds said it will = (P(S|W)*P(W))/P(S)
         = (0.15*0.4)/0.18
	 = 0.3
  # how about P(L|S)
  P(L|S) = P(S|L)*P(L) / P(S) = 0.2*0.6 / 0.18 = 0.67
```
That means there's a 67% chance for loss, given prediction ManPitty will win, P(L|S)!
And for a win, its a measly 30%!
Interesting right? If this ain't fraud then I don't know what is.

Well that's one example and I guess itll cut it. Coming up with these on my own ain't the easiest task. 


_There's a lot of numbers flying around here and its likely I made an error somehow somewhere, if
you spot one or want to talk about any of what's on here please reach out to me via my BluesSky or Email linked down in
the footer section._

If you want to consume more info on Baye's, here's some cool sources I found online.

### Sources for more reading.
- [Wikipedia article on Baye's](https://youtu.be/OByl4nKA?si=En_JpAowNkufxk4x)
- [Vertasium video on Baye's](https://youtu.be/OByl4nKA?si=En_JpAowNkufxk4x)
- [LessWrong's Eliezer on Baye's](https://youtu.be/OByl4nKA?si=En_JpAowNkufxk4x)


### Baye's in the news , Baye's in practice
- [Simpson's paradox](https://adambear.me/post/2025-08-05-statistics-in-court/#fn2)
- [Courts fighting Bayesian reasoning](https://www.theguardian.com/law/2011/oct/02/formula-justice-bayes-theorem-miscarriage)

There's so many applications for Baye's in the news I hope to add more to those I'll list below when I collect them. But with that, I hope you learnt something and, see you in the next one.
