---
layout: post
title:      "Why Do Arrays Start At Zero?"
date:       2018-04-04 03:53:37 -0400
permalink:  why_do_arrays_start_at_zero
---


Within the world of programming, a cursory Goolge search will lead you to the conclusion that the answer to this question is a bit [controversial](https://softwareengineering.stackexchange.com/questions/110804/why-are-zero-based-arrays-the-norm), and that it depends a lot on the [programming language in question](http://developeronline.blogspot.com/2008/04/why-array-index-should-start-from-0.html).  Let's leave that aside for the moment and assume that most arrays (like those in Ruby) start at 0. 

An array like this:

goldbars = [1,2]

Where the first two elements in the array [1,2] acutally hold the positions of 0 and 1.

If you're a word person (like me) and not a mathemetician, arguments like the one that follows doesn't quite do it to make this seem reasonable, nor intuitive:

"Dijkstra explains why we should index from 0. This is a problem on how to denote a subsequence of natural numbers, say for example 1,2,3,...,10. We have four solutions available:
a. 0<i<11 
b. 1<=i<11
c. 0<i<=10
d. 1<=i<=10

Dijkstra argues that the proper notation should be able to denote naturally the two following cases:
1. The subsequence includes the smallest natural number, 0
2. The subsequence is empty" (http://developeronline.blogspot.com/2008/04/why-array-index-should-start-from-0.html)

I find that what makes more sense is to change the metaphor.

When I originally learned about arrays, I thought of them in terms of apples in a basket. 

As in: I have a basket of apples, and I have three apples inside it. Here they are: 1, 2, 3.

If I describe my apple basket to the machine, it would see apples at the indexes of [0,1,2], which is not helpful because I don't think of the first apple I put in the basket as apple[0]. 

What is more helpful to me is to think of array elements as buried treasure.

"What?! Why?!!!" You might ask.

Well, because buried treasure implies, and empasizes, location. 

I think that imagining arrays in terms of locational assignments, instead of baskets of items, is the secret to creating a working metaphor...and conceptual understanding.

Imagine this:

a. I marked an X on the ground at the intersection of Main Street and Pine Drive
b. I buried a pile of gold bars two steps from X

What I'm saying programmatically is: you'll be interested in the value of goldbars[2].

To find the treasure, you would follow *three* procedural steps: find X, take one step, take a second step. But you will have only taken two actual steps from X. Which is probably the only part you'd describe to your friends, because the idea of finding X would seem too obvious.

(Subsequently, the implied directions here are that you'd also grab a shovel and dig, but let's let go of that part for now.) 

Standing on X = 0 steps. Step 1 = 1 step. Step 2 = 2 steps.  

In terms of the index of the array, we're at goldbars[2], which feels good to us because it feels like we just took two steps and that's all that happened.

But if we describe taking just two steps to a machine, it would only get to goldbars[1], which is an entirely different place; and there is no gold there. You'd need to remember that there are three direct instructions to describe to the machine to get to the right spot. First, you found the X, and then you counted one step. And then another. 

This lack of assumption on the machine's part is what 0 does, and why [many] programming languages begin arrays at 0.

When we tell the computer to access the first element in our array, it goes to the physical location that the array is stored in machine memory. That is step 0 (or my_array[0]), and then, the machine counts steps from there. 

If I say: "Hey machine! goldbars[0]!" I'm telling it to go dig on the X that I drew on the ground. I'm saying: "Go to the array called goldbars and dig there (grab that value)! [at the first index/instruction, which is 0, because it is 0 steps away from X]."

If I say: "Computer! Dig at goldbars[1]!" It first goes to the location of the array (step 1; element 1; goldbars[0]) and then moves one place away, to goldbars[1] (step 2, element 2.) That's because the procedural elements of instruction (minus digging) to find the value of goldbars[1] equals 2.

Again, as a user, I would interpret this whole sequence as one step. But that's because I assume meaning with everything I interact with. Machines don't. And that's why we often use -1 to explain the index of the user's input to the machine...they're a step behind us when it comes to making assumptions. This allows the user's input, "3 Apples," for example, to equal apples[2], which, to the machine means:  "go two places from the first apple element (apple[0])."

While this analogy is far from perfect, I find it helpful. Now, when I think of arrays, for example, I think of array element 3 as: my_array[2] equals[find X, two procedural steps from X, three procedural steps from X]. It helps me to process the index of the element that I mean in step with the machine.
