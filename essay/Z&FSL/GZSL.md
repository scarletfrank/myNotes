# An Empirical Study and Analysis of Generalized Zero-shot Learning for Object Recognition in the Wild

## Abstract

- a performance metric
- class semantic embedding, key to improve performance

## Introduction

> long-tailed distributions, AUSUC

*trait* is the ability to remember past experiences

*calibrated stacking*

Area Under Seen-Unseen accuracy Curve

## Related Work
> Few works at that time

## Generalized Zero-Shot Learning

- conventional => more general
- $A_{u \to u}$ and $A_{S \to S}$

*direct stacking* : nearly all test data from unseen classes are misclassified into the seen classes

$$ \hat{y} = arg\max_{c \in T} f_c(x) $$

## Approach for GZSL

> Elegant 

Area Under Seen-Unseen accuracy Curve(AUSUC), 

*calibrated stacking*: reduce the scores for the seen classes

$$\hat{y} = arg\max_{c \in T} f_c(x) - \gamma I(c \in S)$$

I, indicator {0, 1} indicates whether or not c is a seen class 
$\gamma$ is a calibration factor.

By varying it, we get different $A_{u \to T}$ and $A_{S \to T}$, so we can plot it.

The curve is similar to Precision-Recall Curve and the Receiving Operator Characteristic curve.

## Analysis

> 感觉是在这篇之后，写出的EXEM。

**idealized semantic embedding**

# Classifier and Exemplar Synthesis for Zero-Shot Learning

## Experiments
> 出现了non-parametric Friedman test

提到了最近的一些强有力的竞争者（ImageNet上），GCNZ和ADGP。给出了一个在采用ResNet101和最好的语义表示的结果，证明了自己的方法的优越性。

## Related Work

### ZSL Background

- two-stage approaches

    learning to predict semantic embeddings | generate instances of each class 

- unified approaches

    common space or compatibility learning | model parameter learning(build the classifiers of unseen classes by relating them to seen ones via similarities computed from semantic representation)

### Putting our methods in context



