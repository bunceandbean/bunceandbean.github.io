---
layout: post
title: "Making Flippy Floppy: A Proof by Strong Induction"
comments: false
share: true
description: "Making Flippy Floppy: A Proof by Strong Induction"
keywords: ""
---

<p align = "center">
  <img src = "../../assets/images/sms.webp">
  <br>
  <em>No one makes a monkey out me...</em>
</p>

## Stop Making Sense

I recently got the opportunity to attend the _Stop Making Sense_ 4K re-release. _Stop Making Sense_ is widely considered to be the best concert film of all time (by more people than just myself, I promise), documenting a Talking Heads' performance in 1980's LA for their tour of the same name. As a gigantic fan of Talking Heads, it was probably one of my highlights for 2023. I attended the IMAX theater in Indianapolis for opening night, and the film was shown on the 70mm screen (the same one used for _Oppenheimer_ earlier that month). David Byrne's suit was bigger than ever! In honor of the re-release, I decided to intersect my love for Talking Heads and my current TA position in CS182: Foundations of Computer Science. Here I will document one of my favorite strong induction proofs. By the end, you will have learned a useful proof method and how a Talking Heads song may relate to it.

## What is strong induction?

Strong induction is simply a way to prove specific propositional statements (usually of the mathematical or algebraic variety). You may have heard of pure induction, whose mathematical expression is as such:

$$ \begin{array}{rl}
    & P(n_0) \\
    & P(n) \to P(n+1)\\
    \hline
    \therefore & P(n) \space \forall n \geq n_0
  \end{array}$$

Here, we have a base case ($$P(n_0)$$), and our induction hypothesis (the implication). With both of these proven, we can successfully prove the generic $$P(n)$$ (for some $n$ greater than or equal to our base case). This type of proof is used widely by people in mathematics, computer science, and more. Usually, most computer science students will be introduced to this early on their career, as it is used to prove upper-level concepts they might encounter as they move through their degree. However, there is also two other types of induction that often times students struggle with. This being structural induction (a whole other beast) and ***STRONG*** induction. So what exactly is strong induction, and why is it considered ***STRONG***? Well, it is actually the exact same as normal induction, with one twist. Instead of one base-case, we can have _multiple_. So instead of $$n_0$$, we have $$n_0, n_1, n_2, ..., n_k$$. Having multiple base cases seems a bit redundant, but it can actually make our lives much easier. When we are making our induction hypothesis, we usually say $$\forall k \geq k_0$$, meaning we can only really work with $$k$$ when we are trying to work out our proof. Strong induction with multiple base cases gives us another tool. With strong induction, we say $$\forall \space k \geq i \geq k_0$$. Since we have values between our first base case and $$k$$, we can utilize all of these values in our proof. This is what makes strong induction so ***STRONG***.

## Making Flippy Floppy

<p align = "center">
  <img src = "../../assets/images/sms-suit.gif">
  <br>
  <em>Everybody, get in line!</em>
</p>

Now that we know why strong induction is so useful, let's see it in action! Here is our problem: **Prove that every positive integer can be represented as a sum of distinct powers of two.** Some examples of this would be:

$$\begin{array}{ll}10 = 2^3 + 2^1\\57 = 2^5 + 2^4 + 2^3 + 2^0\end{array}$$

We can represent this problem in a more mathematical sense, where we have a function:

$$f(x) = \sum_{i=0}^{n} C(x, i)\cdot 2^i$$

Where:

$$C(x, i): \mathbb{Z}_+^2 \to \{0, 1\}$$

While this math seems a bit complex, it is actually pretty straightforward with some explanation. We are turning our positive integer $$x$$ into a sum of powers of two between zero and $n$ (where $$n$$ is just some integer). The difficult part appears to be the $$C$$ function. This function simply outputs a zero or a one, depending on our positive integer $$x$$, and our current $$i$$ value. The powers of two that appear in our sum are being multiplied by one, while those that are not are being multiplied by zero. The algebraic specifics of this function are a bit complex and are not actually necessary to prove our statement, thus we will leave it in the listed form. From here, we have our base cases:

$$P(1): f(1) = 2^0\\P(2): f(2) = 2^1$$

Then, we must build our inductive hypothesis, that being:

$$P(k) : \left(f(k) = \sum_{i=0}^{n} C(k, i)\cdot 2^i \right) \space \forall k \geq i \geq 1$$

Now, we can do our inductive step. Notice how we had two base cases. This was chosen on purpose, as our first two powers of two make up one and two, the base numbers of odd and even numbers ($$2n$$, $$2n + 1$$). Given our next number ($$P(k+1)$$), we can use facts and our base cases can help us prove that the next number follows. Every even number is simply a number $$n$$ being multiplied by two. And thus, so are our even numbers when we make it a sum of powers of two. Therefore, if $$k+1$$ is even, we can represent it as two times a positive whole number:

$$k+1 = 2 \left (\frac{k+1}{2} \right )$$

Since $$\frac{k+1}{2}$$ is less than $$k$$ (and is also a positive integer), according to our inductive hypothesis, it can be represented as a sum of powers of two (or, $$P(\frac{k+1}{2})$$ holds). If we then multiply this sum by two, we simply increase each power by one and thus $$2 \left (\frac{k+1}{2} \right ) = k + 1$$ can be represented as a sum of distinct powers of two when it is even, or, $$P(k+1)$$ holds when $$k+1$$ is even. Cool! We proved it works when our next number is even, but what about odd numbers? Well, this is where our base case comes in handy. An odd number is simply an even number plus one ($$2n + 1$$). Since we have $$2^0 = 1$$, we can simply slap this term onto the end of an even number $$k$$. It is guaranteed that $$k$$ will not have a $$2^0$$ in its sum since it is even and two must be able to be factored out of it. And thats it! We have proved $$P(k+1)$$ whether it is even or odd, and thus have proven our original statement by strong induction. But, how does Talking Heads connect to this proof?

## Start Making Sense

<p align = "center">
  <img src = "../../assets/images/sms-lamp.gif">
  <br>
  <em>Hi yo - you got light in your eyes!</em>
</p>

While this proof may seem like a weird but interesting fact about integers, it actually proves a foundational part of computer science. That being: binary! Representing integers as the sum of powers of two is exactly what binary is, where our choice of including a power or not is based off of ones and zeros. For instance:

$$10 = 1\cdot 2^3 + 0\cdot 2^2 + 1\cdot 2^1 + 0\cdot 2^0 = 1010$$

You could do this proof for any base you'd like! Base three, base four, hex, and even normal decimal numbers we use every day. That is why I call this proof: Making Flippy Floppy. If you ever did an introductory CS class in high school, you may have made those <a href="https://www.youtube.com/watch?v=v83Uvg_ySK8">flip flop machines that count up in binary</a>. Now that you made flippy floppy, I encourage you to listen along to the Talking Heads (live) song of the same name and feel a sense of pride for finishing a pretty cool proof.

<br>
<div class = "container">
    <div class = "container" style="left: 0; width: 75%; height: 152px; position: relative;"><iframe src="https://open.spotify.com/embed/track/6Wvil8gMMUbozPd33pSrll?utm_source=oembed" style="top: 0; left: 0; width: 100%; height: 100%; position: absolute; border: 0;" allowfullscreen allow="clipboard-write; encrypted-media; fullscreen; picture-in-picture;"></iframe></div>
</div>