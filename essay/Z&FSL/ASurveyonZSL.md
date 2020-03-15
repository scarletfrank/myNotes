# A Survey of Zero-Shot Learning: Settings, Methods, and Applications

## Abstract

## Introduction

*auxiliary information is necessary*

transductive and inductive:
- class-inductive instance-inductive
- class-transductive instance-inductive
- class-transductive instance-transductive

*domain shift*

## Different semantic spaces

- Engineered Semantic Spaces
    - Attribute spaces
    - Lexical spaces
    - Text-keyword spaces
- Learned Semantic spaces
    - Label-embedding spaces
        embedding of class labels
    - Text-embedding spaces
        embedding the text descriptions for each class
    - Image-representation spaces
        obtained from images belonging to each class

visual exemplars are "similar" to Image-representation spaces.


## Categorize different ZSL methods

- classifier-based methods: how to directly learn a classifier for the unseen classes
    - correspondence 
        corresponding binary one-vs-rest classifier
    - relationship
    - combination
    
- instance-based methods: how to obtain labeled instances belonging to the unseen classes and use them for classifier learning 
    - projection
    - instance-borrowing 
    - synthesizing 

- discussions
    - Performance Comparison

## Applications

**Computer Vision**
Images: image recognition, image segmentation, image retrieval
Videos: video recognition, video retrieval(event detection)

**Natural language processing**
bilingual dictionary induction and bilingual phrase table induction problems ???

**Others**
ubiquitous computing: human activity recognition from sensor data

## Future Directions

**Characteristics of input data**
time series data from sensor

**Selection of training data**
*Heterogeneous traning and testing data*

**Selection and maintenance of auxiliary information**

**More realistic and application specific problem settings**
generalized zero-shot learning

**Theoretical guarantee**

**Combination with other learning paradigms**

