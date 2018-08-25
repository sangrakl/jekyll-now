---
layout: post
title: "[확률/통계] 쉽게 알아보는 베이즈 정리 (What is Bayes's Theorem)"
subtitle: "베이즈 정리란"
categories: math
tags: 확률, 통계
---

딥러닝을 공부하다 보면 많이 이야기를 듣게되는 베이즈 정리(Bayes's Theorem)에 대한 공부

## 베이즈 정리란
---
"이전의 경험"과 "현재의 증거"를 기반으로 어떤 사건의 확률을 추론하는 과정  
확률 P(A|B)를 알고 있을 때, 관계가 정반대인 확률 P(B|A)를 계산하기 위해 등장하였음  
가장 큰 특징 -> **"결과를 관측한 뒤 원인을 추론할 수 있음"**  
다양한 분야의 실험 결과 분석에 사용되고 있음


> P(A) : A의 관측 확률 (evidence) - 현재의 증거  
> P(B) : B의 사전 확률 (prior probability) - 과거의 경험  
> P(A|B) : 사건 B가 주어졌을 때 A의 조건부 확률 (likelihood)  
> P(B|A) : 사건 A라는 증거에 대한 사후 확률 (posterior probability)


![베이즈정리 증명](../images/2018-08-24-1.png)
