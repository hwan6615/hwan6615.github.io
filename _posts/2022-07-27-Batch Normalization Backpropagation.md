---
layout: post
# title: "13. Paper Review: QRelScore: Better Evaluating Generated Questions with Deeper Understanding of Context-aware Relevance@EMNLP'2022"
# date: 2016-06-19 10:00:00 +0900
categories: Documentation
tags: [Deep Learning]
---
# Introduction
DNN(Deep Neural Network)가  학습할  때  가중치  값들이 training dataset에  최적화  되면 Overfitting이  발생한다. Overfitting이  발생하게  되면 validation dataset에  대해  잘못된 classification을  할  가능성이  생긴다. 예를  들어 training dataset이  빨간  자동차라고  한다면  이  빨간  자동차에  대해 DNN의  가중치  값들이  최적화가  된다면  노란  자동차, 검정  자동차에  대해서는  자동차가  아니라고  분류할  가능성이  생긴다. 이  문제점  즉 overfitting이  발생하지  않게  하기  위해  가중치  값들의  분포를  완화시켜주면서  동시에  잘  분류할  수  있는  가중치  분포를  찾을  필요가  있다. 이를  위해  사용하는  방법  중  하나인 Batch Normalization에  대해  살펴보고 Backpropagation을  진행해보겠다.[1]

# Contents
![image](/images/Batch Normalization Backpropagation/Batch Normalization Backpropagation_1_5.png)
![image](/images/Batch Normalization Backpropagation/Batch Normalization Backpropagation_2.png)
![image](/images/Batch Normalization Backpropagation/Batch Normalization Backpropagation_3.png)
![image](/images/Batch Normalization Backpropagation/Batch Normalization Backpropagation_4.png)
![image](/images/Batch Normalization Backpropagation/Batch Normalization Backpropagation_5.png)

# Conclusion
Batch Normalization의 Backpropagation 하는  과정을  직접  해보면서, Batch Normalization에  대해서  부정확했던  개념을  더  명확하게  할  수  있었고, 어떤  이유로 Batch Normalization을  사용해야  하는지에  관해서  알게  되었다. 또한  γ  와  β의  역할에  대해서도  확실하게 알게 되었는데, γ  와  β를 사용하여 scale 해주고, 이를 통해서 정규화의 정도를 조절해주는 역할을 수행할 수 있게 된다.



# Reference
[1] 꾸준희, “[Deep Learning]Batch Normalization,” 2020. https://eehoeskrap.tistory.com/430.

[2] 싸코, “문과생도  이해하는  딥러닝(10)-배치  정규화,” 2018, [Online]. Available: https://sacko.tistory.com/44.

[3]  Kyleluther, “Why Batch Norm Causes Exploding Gradients,” 2020, [Online]. Available: https://madewithml.com/projects/153/why-batch-norm-causes-exploding-gradients/.
