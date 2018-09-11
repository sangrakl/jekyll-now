---
layout: post
title: "[논문으로 시작하는 딥러닝] CNN의 기초"
subtitle: "딥러닝"
categories: deeplearning
tags: 딥러닝
---

edwith의 '논문으로 시작하는 딥러닝' 스터디&기록

## Convolutional Neural Network
---
input -> convolution -> subsampling -> FC -> output

conv, subsampling은 feature extraction을 해주고

FC는 classifier의 역할을 해줌

conv filter가 input image를 모두 slide하면서 check하기 때문에 대상 물체가 이미지의 어디에 있어도 상관이 없음

Compositionality : Hierarchy Structure가 주는 장점이 있음

> ![CNN의 기초](../images/2018-09-12-1.png)  
> [input, output, filter]]

input image의 channel이랑 filter의 channel의 개수는 같아야 함

out channel의 숫자는 결국 filter의 숫자와 동일하게 됨

convolution layers에서의 param 보다 fc에서의 param이 더 크다.

그래서 최근 트렌드는 fc를 없애는 fully convolution layer를 하거나, fc를 간소화해서 전체 param의 수를 줄이는 방향으로 가고 있다.
