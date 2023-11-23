---
layout: distill
title: Label Smoothing - what it solves and how it works
date: 2023-11-22 15:25:00-0300
description: An intuitive explanation of label smoothing
tags: machine_learning
giscus_comments: false
bibliography: 2023-11-22-label-smoothing.bib
related_posts: false

authors:
  - name: Raul Almeida
    url: "https://almeidaraul.github.io"
    affiliations:
      name: DInf, UFPR
---

## Introduction
There are two explanations here: a short and a long one. I suggest you read
both in this order, as the short one might provide an overview of what is
going on.

This all comes from the original paper by Christian Szegedy, Vincent Vanhoucke,
Sergey Ioffe, Jonathon Shlens and Zbigniew Wojna that proposed label smoothing
as a regularization technique<d-cite key="resnet"></d-cite>.

> It is also important to note I am talking exclusively about classification
> in this article, so when you read "neural networks are fun" you should
> actually understand "**classifier** neural networks are fun".

## TL;DR (short explanation)
The general idea of optimizing a neural network's weights during training is
that you want the network's answers for inputs of different classes to be as
distant from one another as possible.

Labels are usually represented in one-hot encoded vectors, where
one value is equal to 1 and all others are equal to 0, representing the
probability of each class (and, since this is ground truth, we know one class
has probability 1 and all others have probability 0).

Intuitively, the problem is that your model could learn to make the
probability of the most likely class to be infinitely greater than the others'
(and understandably so, since 1 is infinitely greater than 0). This leads to
a model that doesn't adapt well yet feels pretty confident about its decisions
(☢ overfitting, poor generalization ☢).

Label smoothing consists of choosing an Epsilon value and changing the ground-
truth labels `y` as follows: $y = (1-\epsilon)y + \frac{\epsilon}{|y|}$.

With this, nothing is infinitely greater than anything anymore, and your model
learns to keep outputs adequate.

## Long explanation
Now for the long explanation. I will follow the general structure of the
authors' explanation<d-cite key="resnet"></d-cite>, but in my
eyes this is less straight to the point in order to make it easier to
understand. Just like the authors, I will use the cross-entropy (CE)
  loss in my explanation.

### The problem
Let's say you're optimizing a neural network's weights by minimizing the CE
function over the softmax of its outputs and the expected outputs. There are
a couple of things to notice here:

1. Before the softmax function, your neural network outputs logits, which are
   unnormalized log-probabilities of each class.
2. Logits are normalized with the softmax function so that your neural
   network's predicted probability for class `k` is $\textrm{SoftMax}_k = \frac{e^{\textrm{logits}_k}}{\sum_i\log(p_k)\textrm{expected}_k}, i \in \textrm{classes}$
3. With `p_j` as the predicted probability of class j and `expected_j` as
   the real probability of the same class, $\textrm{CELoss} = -(\sum_{k\in\textrm{classes}}\log(p_k)\textrm{expected}_k )$

So we can conclude that if you're minimizing CE, you're aiming to maximize the
log-likelihood of the correct label. **You can't** maximize this with
finite values of $\textrm{logits}_k$ . You can, however, get pretty close by making
$\textrm{logits}_{\textrm{true class}} \gg \textrm{logits}_i \forall \i \neq \textrm{true class}$,
i.e., by making the ground-truth class logit much greater than all others. If you've read the
short explanation, this is what I meant by "infinitely greater".

Making the ground-truth class logit much greater than all others leads to two
problems:

**Overfitting.** What your model is learning is to assign full probability to
the class it expects to be true, which indicates a very strict learned
representation.

**Little adaptation capability.** It is easy to see at this point that your
model is encouraged to output logits so that the largest one is a lot different
than all others. What's important to notice here, is that the gradient
$\frac{\partial\textrm{CELoss}}{\partial\textrm{true class logits}}$ is in the range
$[-1, 1]$, which reduces the model's ability to adapt. You can see this as
encouraging the model to create very radical outputs and then not being able to make
corresponding radical corrections in the optimization step (because the gradient doesn't
explode like the weights do).

In summary, these two problems mean your **model is too confident,** which is
the final problem that label smoothing solves.

### The solution
Now we need to solve this confidence issue with your model. What the
authors<d-cite key="resnet"></d-cite> proposed is to change
the ground-truth label $y$ as follows: $y = (1-\epsilon)y + \frac{\epsilon}{|y|}$

Or,

```
y' = (1-epsilon)*y + epsilon/len(y)
```

For a chosen `epsilon` value. With this change, if the estimated probability
of a single class `k` gets very close to 1, all others will be very close to 0.
Since no probability is "allowed" to actually equal to 0, the softmax output
won't explode, and the computed CE value will be large (i.e., this scenario
will be avoided in the optimization process).

That's it! I hope you find this helpful.
