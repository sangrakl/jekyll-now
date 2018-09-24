---
layout: post
title: "[논문으로 시작하는 딥러닝] 이미지처리 실습"
subtitle: "딥러닝"
categories: deeplearning
tags: 딥러닝
---

edwith의 '논문으로 시작하는 딥러닝' 스터디&기록

## 이미지처리 실습 (matplotlib, pyplot)
---

{% highlight python %}
#기본 라이브러리 호출
from scipy.misc import imread, imresize
import matplotlib.pyplot as plt
import numpy as np
import os

#jupyter에서 inline으로 그래프를 그리고 싶을 경우에는 아래와 같은 문장 삽입
%matplotlib inline
{% endhighlight %}

{% highlight python %}
#os 기본 명령어 중 하나. getcwd (현재 작업중인 디렉토리 호출하기)

#jupyter에서 inline으로 그래프를 그리고 싶을 경우에는 아래와 같은 문장 삽입
%matplotlib inline
{% endhighlight %}