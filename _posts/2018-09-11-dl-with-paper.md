---
layout: post
title: "[논문으로 시작하는 딥러닝] 4가지 CNN 살펴보기"
subtitle: "딥러닝"
categories: deeplearning
tags: 딥러닝
---

edwith의 '논문으로 시작하는 딥러닝' 스터디&기록

## 4가지 CNN 살펴보기: AlexNET, VGG, GoogLeNet, ResNet
---
ILSVRC에서 1등을 했던 구조들

Layer가 많아질수록 성능이 개선될 '여지'가 많다.

## 1. AlexNet
parameter의 수를 아는 것이 중요하다.

11 x  11 x 3 x 48(다음 layer의 채널수)

세번째 layer를 자세히보면 네번째 layer로 넘어갈때 두개로 나눠져있던걸 concat(사슬화)해서 합쳐줌. 이때 parameter 변화를 유심히 봐줄 필요 있음

다른 gpu에 나누어 학습시켰기 때문에 두갈래로 나누어져 있음. 요즘은 gpu 성능이 높아져서 이렇게 하지 않음

ReLU 이야기가 처음으로 나옴

LRN (Local Response Normalization) --> 이해가 잘 안됨

Regularziation은 'Data augmentation'과 'dropout'

label preserving transforming을 통해 aumentation 진행 (e.g. flipping, croping)

단 숫자는 flip augmention하면 안됨. domain을 명확히 알고 augmentation 진행

만장이 있으면 2000만장으로 뻥튀기 가능

color variation도 가능. 이 부분도 여러 training data에서 RGB 채널 값을 유심히 파악한 후에 noise를 넣어야 함. 빨간색이 많이 나오는 data에 빨간색을 다른 색으로 대체하는 noise를 섞으면 오히려 성능을 저해할 수 있음

학습데이터에서 허용할 수 있을만큼의 noise를 삽입

Dropout의 경우 AlexNet에서는 그냥 output에 0.5를 곱해주었음. 최근 NN에서는 중간중간 layer들을 probabilistically 하게 선택함

## 2. VGG
간단한 방법론으로 좋은 성능을 냈다는 직관을 줌

이 논문 이후로 기본적인 뉴럴넷은conv는 3 x 3을 하고 stride는 1, max-pooling or average-pooling을 활용하고 있음

## 3. GoogLeNet
22 Layers Deep Network

Inception Module의 등장

1x1 conv, 3x3 conv, 5x5 conv, 3x3 max 로 나눠서 진행하고 최종에 concat

하지만 그건 naive ver이고, actual ver는 1x1 conv를 전처리해서 dimension reduction을 노림

이를 통해 parameter의 수를 줄여서 효율 증대

Network in Network(갈림길 구조)를 통해 고정된 receptive field를 벗어나 더 다양한 결과를 가져올 수 있음

이를 multicapability라고 부름

At Inception v4 : 5x5가 없이짐

3x3를 두개 했을 때랑 5x5 한개를 했을 때랑 parameter는 9 + 9, 25 로 차이나는데 receptive field의 크기는 5로 똑같음. 이를 활용하였음

또한 1x7 , 7x1 같은 conv layer를 활용하여 receptive field를 매우 키우고 정작 사용된 parameter를 획기적으로 줄임

왜 잘되는지는 알 수 없음. 그냥 저렇게 했더니 잘됐다더라.

## 4. Resnet

152 layers network

방법론이 굉장히 범용적이여서 다양한 곳에 응용할 수 있음

Is deeper network always better?

What about vanishing/exploding gradients?

> Better initialization methos / batch normalization / ReLU

Any other Problems?

> Overfitting?
> *Degradation problem* : more depth but lower performance

Residual building block : input과 desirable ouput의 차이를 학습

유일한 제약 : input과 output의 dimension이 같아야 함

여기서도 bottle architecture 사용해서 param 줄임

한계 : 100개 정도의 layer는 문제 해결을 했는데, 1000개가 넘어가면 여전히 degradation 발생
