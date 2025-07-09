---
layout: post
# title: "13. Paper Review: QRelScore: Better Evaluating Generated Questions with Deeper Understanding of Context-aware Relevance@EMNLP'2022"
# date: 2016-06-19 10:00:00 +0900
categories: Documentation
tags: [Deep Learning]
---
# Introduction
![image](/images/Lecture-4 Backpropagation/그림1_1.png)
![image](/images/Lecture-4 Backpropagation/그림 2_2.png)

# Contents
![image](/images/Lecture-4 Backpropagation/그림 3_3.png)![image](/images/Lecture-4 Backpropagation/그림 4_4.png)

# Conclusion
Forward pass시  구한  값의  차원과 backpropagation 진행  시  계산되는 gradient의  차원이  항상  같아야  됨을  유의해야하고, max 함수에서의 local gradient가 Jacobian 행렬의  형태가  되기  때문에  <![if !msEquation]>  <![endif]>값이 2*2 행렬이  된다. 또한  곱셈에  의한  미분을 local gradient로  적용할  때, local gradient의  위치와 upstream gradient의  위치를  잘  구분하여  계산을  하여야  한다.

# Reference
http://cs231n.stanford.edu/ lecture 4 

