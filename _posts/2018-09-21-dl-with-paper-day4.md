---
layout: post
title: "[논문으로 시작하는 딥러닝] Regularization"
subtitle: "딥러닝"
categories: deeplearning
tags: 딥러닝
---

edwith의 '논문으로 시작하는 딥러닝' 스터디&기록

## Regularization, Overfitting
---

딥러닝 뿐만 아니라 머신러닝 전반에 있어서 가장 중요한 Problem 중 하나

> Regularization이란?

Overfitting을 막아주는 것

> 그렇다면 Overfitting이란?

training error 는 감소하는데 test error 가 증가할 때

NN에서 차원이 증가한다는 것은 더 deep한 Net을 구축한다는 것을 의미

더 좋은 성능을 낼 여지는 있지만, regularization을 해주지 않으면 overfitting이 발생할 여지가 큼

이미지

ㅏ먼이러

> Overfitting을 막는 법

1. Get more data

2. Use a model with the right capacity

3. Average many different models (Ensemble)

4. Dropout, Dropconnect, BatchNorm

Weight Decay

### Batch Normalization

평균으로 빼고 분산으로 나누면 됨

장점

1. learning rate를 빨리할 수 있음. 발산하지 않음

2. Dropout, Weight Decay를 안해도 된다


데이터가 많지 않으면 모델의 형태를 구성하는게 매우 중요함

여러번 해보면서 최적의 모델을 얻을 수 있음

층을 256개 쌓아 봤다가, 512개 쌓아 봤다가, 계속 바꿔가면서

