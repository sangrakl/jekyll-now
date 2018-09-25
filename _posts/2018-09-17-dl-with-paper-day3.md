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
cwd = os.getcwd()
print("current working directory is %s" % (cwd))

#img의 type과 shpae를 확인하는 습관을 들여야 한다
def get_typeshape(img):
    print("type of this img is %s" % (type(img)))
    print("shape of this img is %s" % (img.shape,))
    #img.shape뒤에 쉼표를 넣어야만 typeError가 뜨지 않는다
{% endhighlight %}

{% highlight python %}
#load
dog = imread("cwd/img/dog.png")
get_typeshape(dog)
#plot
plt.figure(figsize=(13,11))
#이렇게 한번 figure를 정해주고 나면 '0' 인덱스에 저장이 되어서, 나중에 별도 지정하지 않으면 해당 figsize를 따르거나, plt.figure(0)을 통해서 동일 옵션으로 호출해올 수 있다.
plt.imshow(dog)
plt.title("dog img")
plt.draw()
{% endhighlight %}

주로 imread를 통해서 호출해오는 이미지들은 (width, height, 3)의 int matrix(nparray) 형태로 호출이 된다.

이를 float 형태로 호출하게 되면 imshow 했을 때 이미지가 이상하게 보여지게 된다.

이미지가 float 형태일 경우에는 imshow가 해당 이미지의 각 값들이 0~1에 있을 것이라고 가정하기 때문

그렇기 때문에 float 형태로 호출 했을 때는 255로 나누어서 regularization을 해주어야 한다.

{% highlight python %}
dog_float = imread("cwd/img/dog.png").astype(np.float) / 255
{% endhighlight %}

{% highlight python %}
#img를 matrix에서 vector로 바꿔보자. np.reshape를 활용하면 됨
vecdog = np.reshape(dog, (1, -1))
#(1, -1)의 의미는 (width, height, 3 or sth)을 (1, width * height * 3 or sth)으로 바꾸겠다는 뜻임. 자동으로 연산해줌
print("shape of vecdog is {0}".format(vecdog.shape,))
#다시 shape를 원상 복귀하고자 한다면?!
matdog = np.reshape(vecdog, (416, -1, 3))
#요렇게 하면 자동 연산을 통해 초기의 shape로 돌아오게 된다
print("shape of matdog is {0}".format(matdog.shape,))
{% endhighlight %}

os 함수를 통해 폴더에 있는 이미지들만 추출해서 호출 하고 리스트로 저장하는 방법을 공부해보자

{% highlight python %}
cwd = os.getcwd()
#단 os.getcwd() 함수의 경우 윈도우와 우분투에서 호환이 되지 않는 이슈가 있으므로 조심하도록 하자. 윈도우에서의 getcwd는 path를 리턴할때 \\ 이렇게 디렉토리 구분자를 두개 사용한다. os.path.isdir과 os.path.abspath를 활용하는 법이 있는데, 이건 우선 스킵

path = cwd + '\\images\\'
flist = os.listdir(path)
print("{0} files in {1}".format(len(flist),path))
for i, f in enumerate(flist):
    print("{0}th file is {1}".format(i,f))

valid_exts = ['.png', '.jpg']
# .을 빼먹지 않고 넣어주어야 한다. os.path.splitext는 .을 포함하여 끊는다.
imgs = []
names = []

for f in flist:
    ext = os.path.splitext(f)[1]
    if ext.lower() not in valid_exts:
        continue
        #break는 아예 for loop 자체를 벗어나게 하지만, continue의 경우 해당하는 경우에만 건너 뛰고 나머지 loop를 계속 돌린다
    fullpath = os.path.join(path, f)
    imgs.append(imread(fullpath))
    names.append(os.path.splitext(f)[0])

for img, name in zip(imgs,names):
    plt.imshow(img)
    plt.title(name)
    plt.show()
{% endhighlight %}