---
layout: post
title: "4. Paper Review: Domain Aware Neural Dialog Systemg@arXiv'2017"
# date: 2016-06-19 10:00:00 +0900
categories: review
# tags: [LSTM, Anomaly Detection, ICML, Deep Learning]
---
[Paper Link](https://arxiv.org/pdf/1708.00897)

# Abstract
대화 내의 다양한 도메인에서 지능적인(intelligent) 응답을 생성하는 '도메인 인식 채팅 시스템' 구축 작업을 탐구한다. 이를 위해 'DOM-Seq2Seq'라는 도메인 인식 신경망 모델을 제안하는데, 이 모델은 도메인별 시퀀스-투-시퀀스 모델과 도메인 분류기를 활용하는 새로운 기술을 기반으로 한다. 또한 현재 발화의 특징과 이전 발화의 도메인을 포착하여 관련성 있는 응답을 형성하는 데 도움을 주며 automatic metrics로 모델을 평가하고 Seq2Seq 모델과 성능을 비교한다.

# Introduction
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_3.png)
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_4.png)![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_5.png)![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_6.png)![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_7.png)![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_8.png)![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_9.png)
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_10.png)
# Contribution
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_12.png)
# Model
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_13.png)
##  - Domain Classifier
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_14.png)![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_15.png)![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_16.png)
##  - Response Generators
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_17.png)
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_18.png)
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_19.png)![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_20.png)
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_21.png)
##  - Re-ranker
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_22.png)

# Datasets
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_23.png)

# Experiments
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_24.png)
![image](/images/Domain Aware Neural Dialog System review/Domain Aware Neural Dialog System review_25.png)

# Conclusion and Review
* 도메인 관련 답변을 생성하기 위해 두 모델을 제안
    * Ensemble based Domain Classifier
        * 고정된 몇 개의 이전 도메인 정보와 현재 utterance를 고려
    * RNN based Domain Classifier
        * 대화에서 도메인이 전환되는 경우를 고려

* RNN에서 고정 벡터에 모든 정보를 담기 힘든 문제를 LSTM based Seq2Seq with attention 모델을 통하여 개선
* 도메인마다 Response Generator 모델을 가지고 있기 때문에 시간적 측면에서 cost가 큼
* Utterance가 긴 데이터의 경우 Decoder의 time step마다 encoder의 모든 정보를 봐야함