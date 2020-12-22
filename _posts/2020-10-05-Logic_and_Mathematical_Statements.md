---
title: Logic and Mathematical Statements
categories: [Notes]
comments: true
---

## <font color= 977FD7> Negation</font>
Sometimes in mathematics it's important to determine what the opposite of a given mathematical statement is. This is usually referred to as "negating" a statement. One thing to keep in mind is that if a statement is true, then its negation is false (and if a statement is false, then its negation is true).

Let's take a look at some of the most common negations.

### <font color= 6FBCE1> Negation of "A or B"</font>
Before giving the answer, let's try to do this for an example.

Consider the statement "You are either rich or happy." For this statement to be false, you can't be rich and you can't been happy. In other words, the opposite is to be not rich and not happy. Or if we rewrite it in terms of the original statement we get "You are not rich and not happy."

If we let A be the statement "You are rich" and B be the statement "You are happy", then the negation of "A or B" becomes "Not A and Not B."

In general, we have the same statement: The negation of "A or B" is the statement "Not A and Not B."

### <font color= 6FBCE1> Negation of "A and B"</font>
Again, let's analyze an example first.

Consider the statement "I am both rich and happy." For this statement to be false I could be either not rich or not happy. If we let A be the statement "I am rich" and B be the statement "I am happy", then the negation of "A and B" becomes "I am not rich or I am not happy" or "Not A or Not B".

### <font color= 6FBCE1> Negation of "If A, then B"</font>
To negate a statement of the form "If A, then B" we should replace it with the statement "A and Not B". This might seem confusing at first, so let's take a look at a simple example to help understand why this is the right thing to do.

Consider the statement "If I am rich, then I am happy." For this statement to be false, I would need to be rich and not happy. If A is the statement "I am rich" and B is the statement "I am happy,", then the negation of "A ⇒ B" is "I am rich" = A, and "I am not happy" = not B.

So the negation of "if A, then B" becomes "A and not B".

#### <font color= E675A7> Example</font>
Now let's consider a statement involving some mathematics. Take the statement "If n is even, then n2 is an integer." For this statement to be false, we would need to find an even integer n for which n2 was not an integer. So the opposite of this statement is the statement that "n is even and n2 is not an integer."

###  <font color= 6FBCE1> Negation of "For every ...", "For all ...", "There exists ..."</font>
Sometimes we encounter phrases such as "for every," "for any," "for all" and "there exists" in mathematical statements.
#### <font color= E675A7> Example</font>
Consider the statement "For all integers n, either n is even or n is odd". Although the phrasing is a bit different, this is a statement of the form "If A, then B." We can reword this sentence as follows: "If n is any integer, then either n is even or n is odd."

How would we negate this statement? For this statement to be false, all we would need is to find a single integer which is not even and not odd. In other words, the negation is the statement "There exists an integer n, so that n is not even and n is not odd."

In general, when negating a statement involving "for all," "for every", the phrase "for all" gets replaced with "there exists." Similarly, when negating a statement involving "there exists", the phrase "there exists" gets replaced with "for every" or "for all."

#### <font color= E675A7> Example</font>
Negate the statement "If all rich people are happy, then all poor people are sad."
First, this statement has the form "If A, then B", where A is the statement "All rich people are happy" and B is the statement "All poor people are sad." So the negation has the form "A and not B." So we will need to negate B. The negation of the statement B is "There exists a poor person who is not sad."

Putting this together gives: "All rich people are happy, but there exists a poor person who is not sad" as the negation of "If all rich people are happy, then all poor people are sad."

### <font color= FC572B> Summary</font>
Statement	 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Negation<br/>
"A or B" &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"not A and not B"<br/>
"A and B"	 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"not A or not B"<br/>
"if A, then B" &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	"A and not B"<br/>
"For all x, A(x)" &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	"There exist x such that not A(x)"<br/>
"There exists x such that A(x)" &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	"For every x, not A(x)"
