---
layout: post
title: "1. Paper Review: LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection@ICML’2016"
# date: 2016-06-19 10:00:00 +0900
categories: review
tags: [LSTM, Anomaly Detection, ICML, Deep Learning]
---
* [Paper Link](https://arxiv.org/pdf/1607.00148)
# Abstract
 - 엔진, 차량, 항공기와 같은 기계 장치에는 일반적으로 기계의 동작과 상태를 파악하기 위한 센서가 장착되어 있다. 하지만 센서로 포착되지 않는 외부 요인이나 변수들이 예측 불가능한 시계열 데이터를 유발하기도 한다. 이러한 시나리오에서 정상적인 시계열 동작을 재구성하도록 학습하고, 재구성 오류를 사용하여 이상 징후를 감지하는 LSTM(Long Short Term Memory Networks) 기반 인코더-디코더 방식인 EncDec-AD(Anomaly Detection)를 제안한 논문이다.
 
 - EncDec-AD는 예측 가능한 데이터 뿐만 아니라 예측 불가능한, 주기적인, 비주기적인, 준주기적인 시계열 데이터에서도 이상 징후를 강건하게 감지할 수 있음을 보여준다. 또한, EncDec-AD는 짧은 시계열(길이 30 정도)과 긴 시계열(길이 500 정도) 모두에서 이상 징후를 감지할 수 있다.

# Introduction
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_7.png)
## challenges
 - 특정한 상황에서 센서들의 상태를 예측할 수 없는 문제 발생 (**Unpredictable factors**)
	 - 다양한 센서들로 구성된 엔진, 차량 항공기와 같은 기계장치는 기계의 동작과 상태를 파악하지만 외부적 요인이나 변수로 인해 예측이 어려운 경우 존재
		 - E.g. 수동제어, 모니터링 할 수 없는 환경 조건, 적재 등.
		- 기계장치의 적재량이 빠르게 혹은 빈번하게 바뀔 경우 적재량을 알 수 없을 수 있음 (E.g. 포크레인)
	 - 수학적 모델이나 예측 모델로 이상치를 검출하는 일반적 접근으로 해결이 어려움
	 - 이로 인해 가까운 미래라고 하더라도 시계열을 예측하기 어려움
	 - 즉, 기계의 어떠한 요인으로 인해 현재 상태를 예측할 수 없는 경우에 **정상 데이터만을 학습에 이용**하는 **LSTM based Encoder-Decoder 모델을 통해 이상치를 검출**

## LSTM Encoder-Decoder Model
 - 데이터 : Multi-sensor time-series
 - Encoder : Input 시계열의 vector representation을 학습
 - Decoder : Vector representation을 이용하여 시계열을 복원
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_12.png)
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_13.png)
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_14.png)
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_15.png)
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_16.png)
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_17.png)
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_18.png)

## Experiment
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_20.png)
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_21.png)
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_22.png)
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_23.png)
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_24.png)
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_25.png)
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_26.png)
![image](/images/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection/LSTM-based Encoder-Decoder for Multi-sensor Anomaly Detection_27.png)

## Conclusion and Review
* 기존의 이상치 탐지 모델들은 시계열이 예측할 수 있어야만 한다는 제한이 있었음
* LSTM Encoder-Decoder는 예측할 수 없는 시계열에 대해서도 이상치 예측이 가능하여 더 robust함
* 하지만 윈도우에 이상치가 하나라도 있을 경우, 전체 윈도우를 이상치라고 보기 때문에, 재현율이 낮게 나옴
* Anomaly Detection 대회에서 stacked LSTM을 썼었음
* LSTM-based Encoder-Decoder 모델은 예측할 수 없는 시계열을 다루고 성능이 좋기 때문에 적용하면 더 좋은 결과를 얻을 수 있음을 기대