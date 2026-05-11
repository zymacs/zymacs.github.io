---
title: "Baye's Theorem"
thumbnail: "img/bayez.jpg"
date: 2026-05-09
draft: true
tags:
  - Probability
categories:
  - Maths
---

So what is Baye's theorem? In a previous article I wrote about Probability
and tried to cover as much as I could without relying so much on the formal
representation of concepts. I would like to do that here too but it might
not be as light as the Probability article was. I'll try to make it light though.

We have probably already covered the core concepts of it even if you don't know what those are
yet. That is, if you followed the previous article.
But even if you didn't, I presume by deciding to read about Baye's you already
have some information about probability. If you don't, please read up on that first. 

Baye's theorem is a widely applicable Maths concept even far beyond mathematics. I like to think of it as how a means of updating beliefs with increased knowlegde. But let's discover that shall we?

We have a bag. This bag has bean seeds in it. We are told that 1/4 of these beans is sick.
And the rest, 3/4 that is, is healthy. What is the probability of , given a random
blind picking, selecting a healthy bean? Its an easy 3/4 right? But why? If you read
my previous article on probability you remember I mentioned every probability is contingent
on a prior. Can you tell what the prior is in this instance? It's a real important
concept to understand the rest of the article.

Here, I'll help you out. Its the given that on picking, whatever comes out
of the bag will be beans. That is, the statement has an embedded prior belief for the
probability of picking beans being an absolute certainty.  P(Beans) = 1. So the 3/4 for
healthy beans given the whole bag contains beans could be restated as 3/4 of the absolute probability that is 1, thats 3/4. 1 because its a certainty any picking will result in picking
beans.


Still don't get the relevance for that? Well you will after this news flash.
So NEWS FLASH, new info: 2/3 of the bag's contents is peas and the balance is for beans.
Well, a belief got squashed. We thought beans were the only seeds in the bag.
Now we know they are but a fraction of the whole.
Given this new information, what is the probility that on a random blind picking from _the bag, note that, from the bag not from the beans_,
we select a healthy seed given it is a bean ; P(H|B)?

Well, in the world of beans, the fraction for health is already given. It is a 3/4.

Our answer now deals with the probability of getting a healthy seed given its a bean. 

The formal statement for that is
```
P(H|B) = 3/4 
```



Currently, as far as we know that is, only seeds that are healthy are the healthy beans.
But then we get a call from the CDC that the probability for a seed in said bag being healthy
is 0.6. Oh, another belief got squashed! Bean's ain't the only healthy seeds, there's other healthy seeds than beans. Now we have the same question restated. What is the probability of choosing a healthy seed given we choose a bean?


How about we flip that? Probability of picking a bean given we pick a healthy seed?
Just a swap of variables. 

probability of picking a bean. We could keep adding more and
more information but that structure won't change much. 

It obviosly isn't. 3/4 of the whole is not beans since beans don't make up all the bag's contents but 1/3 of them. Our prior now has a prior, the probability of picking a seed.

We thought all that was contained in the bag was beans and that picking from the bag was picking from beans. That it was therefore irrelevant to consider if picking would result in anything other than beans so we gave a quick 3/4. However, this new information that 2/3 of the bag's contents
ain't beans clarified there's more to the bag than beans. Beans are not the whole, beans are part of a larger whole in which whole they occupy not (1) but 1/3.

So now, to select a healthy bean we should also consider how likely it is that we select beans.
Therefore, our answer shifts from 3/4 to ... 3/4*1/3?




We have a bag of seeds. 2/5 of the seeds are beans and the rest, that is , 3/5 is peas. Do you notice how your brain quickly reframes this as the probability for picking a bean given a random blind selection? Anyways that's not so relevant to our discussion. So we are also told
1/4 of the beans have weevils while for the peas, its an eight (1/8). Let's restate all
this info coz it might be hard to track in memory

```
P(S) # we'll talk about this later, for now you can ignore it
P(Beans) = 2/5
P(Peas)  = 3/5
```


Let's state the theorem then explain it.

```
P(A|B) = (P(B|A)*P(A))/P(B)
```

That is, the probability of some outcome A given some outcome B is the value of the fraction of A that is B in the whole divided by the fraction of the whole that is B. Does that `whole` and `fraction` language sound strange to you? Well I hope by the end of this article it won't.






I am of the opinion that all probability even in its simplest form is contingent on a prior event or follows the above stated rule. Doubt me? Well let me explain.
The common example for probability is the coin toss. It's usually stated in the following terms. On a fair coin toss, what is the probability of heads coming up? And the answer is a 1/2

```
P(H) =  probability of heads
P(T) =  probability of tails
P(H) =  1/2
```

But what about the given? I mean, the coin toss. It is silently baked in. Let's uncover it.
The probability of a head or a tail is contingent on there being a coin toss. Without the
coin toss, there is no heads or tails outcome. The probability of the coin toss is an
assumed certainty of 1 with the events heads and tails being its subsets. 

That all probability is conditional. Here. Lets "Bayesianize"
the coin toss probability. When someone asks for what the probability is  the coin will land on when a coin say, a head when its tossed, what they are really stating is the probability of a head given a coin toss. There's a silent whole, a total probability for tossing the coin based on which all other outcomes
follow, including what side it will land on.

So its not just P(H) is really P(H|T). The value of the probability of a head landing given a
coin toss  and divide that by the probability of a coin toss. Thats (1/2 * 1)/1.
Think that an over stretch?

Now how do we solve for that? We get the probability of tossing a coin 
Here. Let's rephrase the simplest probability example , in terms
of Bayes. 
Actually, first, let's look at it like it isn't.


If you've heard this so many times, just bear with it, its probably that its an effective
example is why its that commonly used. Anyways. A bag of balls. 4 Green, 6 Blue.
Not your usual blue and black so that's not so repetitive I guess.
So the question then is: What is the probability of choosing a Green ball given a random blind picking? The answer is a simple 6/10. But did you know this is the same as the probabilty
for choosing a Green ball given we choose a ball? That the initial is also contingent on some vent? Keep that somewhere.

Let's go back to 'normal' conditional probability a bit. So now let's rephrase the question. We are asked for the probability of choosing a Green ball given on the first picking we chose
a Blue ball and the picking was without replacement.
So the probability of choosing a Blue ball on the first picking is 4/10.
When we pick again after this event, there's two possible
chances, a red or a blue. The chance for the green is now 6/9 since the number of balls fell
after picking a blue in the first round. Now the probability for this to be the path, that
is, for the first picking to be a blue and the second a green is: 4/10*6/9. 




https://youtu.be/OByl4RJxnKA?si=En_JpAowNkufxk4x