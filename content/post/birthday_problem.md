---
title: 'Q4 BT: Birthday Problem'
thumbnail: 'OIP.jpg'
date: 2026-05-20T18:12:54+03:00
draft: false
tags:
 - brain_teasers
categories:
 - Qaunt Finance
 - Interview Prep
---


Question 4 from  the book ["A Practical
Guide to Quantitative Finance Interviews"](https://www.amazon.com/Practical-Guide-Quantitative-Finance-Interviews/dp/1438236662) by Zhou Xinfeg.


>>>
> You and your colleagues know that your boss A's birthday is one of the following 10
> dates:
> Mar 4, Mar 5, Mar 8, 
> Jun 4, Jun 7, 
> Sep 1, Sep 5, 
> Dec 1, Dec 2, Dec 8.
> **A** told you only the month of his birthday, and told your colleague C only the day. After
> that, you first said: "I don't know A's birthday; C doesn't know it either." After hearing
> what you said, C replied: "I didn't know A's birthday, but now I know it." You smiled
> and said: "Now I know it, too." After looking at the 10 dates and hearing your comments,
> your administrative assistant wrote down A's birthday without asking any questions. So
> what did the assistant write? 
>>>

### Rephrasing question

You are not who the question says you are, the question, I think, is easier if you place yourself in the assistant's shoes. So let's give your old place's actor a replacement D.


#### Information summary
- Everyone including you , C and D knows A's birthday is one of the above stated dates
- D  knows the month
- C knows  the day
- D announces the above information, that neither D or C know A's birthday
- C learn's A's birthday after the announcement
- D too learns it after C claim's they've learnt it

You are watching all this play out,  how can you infer from it  what the actual birthday is for A ?


### Solution and explanation


D claim's C does not know the date and neither does D.
That means, whatever date it is, it ain't one with Months June or December. If it were, D would have
immediately seen it with the unique December 2nd and June 7th.

Since C now claims, on D's announcement, that they've figured out
the date. C knows the dates list has shrunk to dates with months September and March.
What they figured out must be one of 1st September or 8th March or 4th March or 5th March or 5th September.
All days are unique except for the 5th for the months March and September.

Since D on C's announcement claims they know the date too, the date must be 1st September since
in this list that's the unique month. They couldn't have figured it out if it were March since there would
have been confusion as to if it were March 4th or March 8th.

The assistant wrote down 1st September.



That's it for this one.