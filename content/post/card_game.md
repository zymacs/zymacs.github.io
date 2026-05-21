---
title: 'Q5 BT: Card_game'
thumbnail: 'img/OIP.jpg'
date: 2026-05-21T15:43:01+03:00
draft: false
tags:
 - brain_teasers
categories:
 - Quant Finance
 - Interview Prep
---



Question 5 from  the book ["A Practical
Guide to Quantitative Finance Interviews"](https://www.amazon.com/Practical-Guide-Quantitative-Finance-Interviews/dp/1438236662) by Zhou Xinfeg.


### Card Game Problem Statement
>>>
> A casino offers a card game using a normal deck of 52 cards. The rule is that you turn
> over two cards each time. For each pair, if both are black, they go to the dealer's pile; if
> both are red, they go to your pile; if one black and one red, they are discarded. The
> process is repeated until you two go through all 52 cards. If you have more cards in your
> pile, you win $100; otherwise (including ties) you get nothing. The casino allows you to
> negotiate the price you want to pay for the game. How much would you be willing to
> pay to play this game?
>>>

### Info processing

Card count is 52.

2 cards picked each time.

Both are black, dealer's pile.

Both are red, your pile.

One red, one black, discard hand.


### Solution and Explanation

Bring the number down to 10. Is there any one way to deal the cards so you win?
There is none! The game always ends in a draw and your opponent wins.

10 cards (5r, 5b)
- 2b      :  (5r, 3b)
- 2r      :  (3r, 3b)
- 1b 1r:  :  (2r, 2b)
- 2b      :  (3r, 0b)
- 2r      

Black: 4
Red: 4
Draw: ..
You lose

How about if for all pickings, the pair picked is a single color till all of that color is exhausted from the deck?

Total Card count: 10 cards (5r, 5b)
|Picking Round | Black picked |  Red picked | Red left | Black left | 
|---| --- | ---|  --- | --- |
| 1 | 2    | 0 | 5 | 3 |  
| 2 | 2    | 0 | 5 | 1 |
| 3 | 1    | 1 | 4 | 0 |
| 4  | 0    | 2 | 2 | 0 |
| 5  | 0    | 2 | 0 | 0 |
|Total | 4  | 4 | nil | nil|


Total for black is a 4, total for red is a 4. It'll always be that way regardless of the deck size, if
there's an equal number of each of black and red.

This is a rigged game. There's always an equal number of red and black pairs.
The game will always draw. house always wins. I would not play it.


That's it for this one.