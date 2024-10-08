---
layout: post
title: convolutional neural network
date: 2021-04-14
tags: [study, note]
categories: bootcamp
---

# 합성곱 신경망 Convolutional Neural Network

## CNN이란

<img width="1105" alt="cnn" src="https://user-images.githubusercontent.com/28593767/114647239-b9167f00-9d17-11eb-85e4-63c3384a14ec.png">

- 합성곱 신경망은 인간의 시각 체계처럼 이미지를 인식하는 신경망으로 이미지가 입력값인 분류 문제를 잘 다룬다.
- CNN에서는 **컨볼루션 층(Convolutional Layers)**, **풀링 층(Pooling Layers)**, **완전 연결 계층**이 등장한다.
  - *이미지는 각 픽셀이 인접한 픽셀과 강한 연관성*이 있기 때문에 *컨볼루션 층에서는 출력값이 입력값의 일부로부터만 영향을 받는 국소성(Local Connectivity)이 강한 처리가 수행*된다.
  - *풀링 층은 인식하는 대상의 위치를 유연하게 처리할 수 있는 구조*로 구성되어 있다.

## CNN의 구조

- 합성곱 신경망은 이미치 처리에 알맞게 다층 퍼셉트론을 변형시킨 신경망으로 이미지 처리에 알맞게 고안된 합성곱 계층과 풀링 계층이 새로운 유형의 은닉 계층으로 이용된다.
- 합성곱 계층은 다층 퍼셉트론의 완전 연결 계층에 비해 획기적으로 줄어든 수의 파라미터만을 가지며 풀링 계층은 아예 파라미터를 갖지 않는다.
  - 다층 퍼셉트론 신경망의 은닉 계층은 완전 연결 계층이기 때문에 많은 수의 픽셀로 구성된 이미지 데이터의 경우 입력 벡터 크기가 커지면서 완전 연결 계층의 가중치 파라미터가 엄청난 크기를 갖게 된다.
  - 메모리 부담도 문제지만 많은 파라미터 탓에 학습이 느려지기 쉬우며 지나치게 많은 양의 데이터가 필요할 수 있다.
- 합성곱 신경망은 합성곱 계층이 갖는 *소수의 파라미터를 집중적으로 학습 시키는 방법으로 이미지 처리 분야에서의 학습 품질을 크게 향상*시켰다.

<img width="957" alt="cnn2" src="https://user-images.githubusercontent.com/28593767/114647247-bcaa0600-9d17-11eb-87fc-50126ad9eb44.png">

- CNN에는 컨볼루션 층, 풀링 층, 완전 연결 계층의 3개 층이 있다.
  - 이미지는 컨볼루션 층으로 입력되고 컨볼루션 층과 풀링 층은 몇 번 반복된 후 완전 연결 계층으로 연결된다.
  - 완전 연결 계층도 몇 번 반복되고 최종 완전 연결 계층은 출력층이 된다.
- 컨볼루션 층에서는 *입력되는 이미지에 여러 개의 필터 처리가 적용되어 입력된 이미지는 필터 처리 후에 이미지의 특징을 나타내는 여러 개의 이미지로 변환*된다.
- 풀링 층에서는 이미지의 특징을 잃어버리지 않도록 *이미지 크기가 축소*된다.
- 완전 연결 계층에서는 층 간의 모든 뉴런이 연결되어 있다.

### 컨볼루션 층 Convolutional Layers

<img width="1274" alt="convolution" src="https://user-images.githubusercontent.com/28593767/114647375-f7ac3980-9d17-11eb-87bd-25c67be91ff4.png">

- 컨볼루션(합성곱)은 이미지 처리 분야에서 매우 일반적인 연산으로 이미지의 특징을 강화하거나 약화시킨다.
  - 컨볼루션 층은 이 컨볼루션 연산을 통해 입력 이미지의 특징을 더 강조한 이미지로 변환한다.
- 이미지에는 각 픽셀이 인접하는 픽셀과 강한 관련성을 갖고 있는 성질이 있는데 이를 **국소성(Locality)** 혹은 집약성이라고 한다.
- *컨볼루션 층은 이러한 이미지의 국소성을 이용해 이미지의 특징을 검출*한다.

<img width="1287" alt="conv2" src="https://user-images.githubusercontent.com/28593767/114647379-f8dd6680-9d17-11eb-80c1-ed24b99a5494.png">

- 일반적인 이미지 데이터는 각 픽셀이 RGB의 3색, 즉 3개의 채널을 갖고 있다.
- CNN은 여러 개의 채널을 가진 이미지에 대해 여러 개의 채널을 이용한 컨볼루션을 적용한다.
- 각 필터는 입력 이미지와 같은 채널 수를 갖기 때문에, 예를 들어 입력 이미지가 RGB이면 각 필터에는 3개의 채널 수가 필요하다.
- 컨볼루션에 의해 생성된 이미지의 각 픽셀에는 편향을 더해 활성화 함수에서 처리한다.
  - 편향은 하나의 필터당 하나의 값을 설정하고 따라서 필터의 수와 편향의 수가 같다.

<img width="830" alt="conv_full" src="https://user-images.githubusercontent.com/28593767/114647382-f975fd00-9d17-11eb-85de-6aa395e43b6f.png">

- 컨볼루션 층은 필터마다 처리를 수행하기 때문에 완전 연결 계층과 비교해 층 간의 접속이 국소적이다.
- 즉, 시각 영역과 같이 국소적인 특징을 파악하는 데 적합한 신경망 구조라고 할 수 있다.
- 필터를 적용한 이미지 영역은 1차 시각 영역에서 단순형 세포의 수용 영역에 해당한다.

### 풀링 층 Pooling Layers

<img width="578" alt="pooling" src="https://user-images.githubusercontent.com/28593767/114647571-478b0080-9d18-11eb-9287-3519dc9ddb93.png">

- 풀링 층은 보통 *컨볼루션층 바로 뒤에 배치되어 이미지를 여러 영역으로 구획하고 각 영역을 대표하는 값을 추출해 새로운 이미지*를 만드는데 이와 같은 처리를 **풀링(Pooling)** 이라고 한다.
- 일반적으로 풀링은 *각 영역의 최댓값을 영역의 대표값으로 설정*하는데 이와 같은 풀링 방법을 **맥스 풀링**이라고 한다.
  - 영역의 평균 값을 선택하는 평균 풀링 등의 방법도 있지만 CNN에서는 맥스 풀링이 많이 사용된다.
- 풀링 처리를 하면 이미지가 축소되고 이미지를 흐릿하게 처리하기 때문에 대상의 위치 감도가 저하된다.
  - 풀링은 위치의 변화에 대해 강건성을 부여한다.
  - 또한 풀링을 통해 이미지의 크기가 축소되기 때문에 계산량이 감소하는 효과도 있다.
  - 풀링 층에서 *구획되는 영역은 고정되어 있고 학습하는 파라미터가 없으므로 학습이 진행되지 않고 채널이 합류되거나 분기되는 것도 없기 때문에 입력 채널 수와 출력 채널 수는 동일*하다.

### 완전 연결 계층 Fully-Connected Layers

- 완전 연결 계층은 일반적인 신경망에서 이용되는 층으로 컨볼루션층과 풀링층이 몇 번 반복된 후 배치된다.
- 컨볼루션 층과 풀링 층에서 추출된 특징량에 기반해 계산이 수행되고 결과를 출력한다.
- 완전 연결 계층 사이의 연결에서는 일반적인 신경망과 마찬가지로 뉴런이 서로 이웃하는 층의 모든 뉴런과 연결된다.
  - 컨볼루션 층과 풀링 층의 출력을 완전 연결 계층으로 입력할 경우 이미지를 벡터로 변환한다.
  - 예를 들어 출력 이미지의 높이가 H, 너비가 W, 채널 수가 F이면 완전 연결 계층의 입력은 크기가 H _ W _ F인 벡터가 된다.

### 패딩 Padding

<img width="1275" alt="padding" src="https://user-images.githubusercontent.com/28593767/114647577-4954c400-9d18-11eb-96e0-930701b32ca7.png">

- 컨볼루션 층과 풀링 층에서 *입력 이미지를 둘러싸는 것처럼 픽셀을 배치하는 기법*을 패딩이라고 한다.
- 이미지의 주위에 값이 0인 픽셀을 배치하는 방법을 **제로 패딩(Zero Padding)** 이라고 한다.
- 컨볼루션 층이나 풀링 층을 거치면 이미지 크기가 축소되지만 패딩을 적용하면 컨볼루션 처리를 거쳐도 이미지 크기가 변하지 않을 수 있다.
- 또한 컨볼루션의 특성 상 이미지의 가장자리는 컨볼루션 적용 횟수가 적어지지만 패딩을 적용하면 가장자리 데이터에 적용되는 컨볼루션 횟수를 증가시켜 가장자리 부분의 특징도 포함시키는 장점이 있다.

### 스트라이드 Stride

- 스트라이드는 *컨볼루션에서 필터가 이동하는 간격*을 의미한다.
- 스트라이드가 커지면 필터의 이동 간격도 커지기 때문에 생성되는 이미지의 크기가 작아진다.
- 매우 큰 이미지를 축소시키기 위해 스트라이드를 사용하기도 하지만 특징을 잘 포착하지 못할 우려가 있어 보통은 스트라이드를 1로 설정하는 편이 바람직하다.

### CNN의 학습

- CNN 역시 일반적인 신경망과 같이 역전파를 통해 학습이 수행된다.
- 컨볼루션 층에서는 필터가 학습에 의해 최적화된다.
- 출력값과 정답의 오차로부터 전파되어 온 값을 이용해 필터를 구성하는 각 값의 기울기를 계산하고 필터가 수정된다.
- 편향 또한 같은 과정으로 수정되고 오차는 컨볼루션 층을 통해 더 앞 층으로 전파된다.
- 완전 연결 계층에서는 일반적인 신경망과 같은 방법으로 오차의 전파가 진행된다.

<img width="543" alt="train" src="https://user-images.githubusercontent.com/28593767/114647580-4a85f100-9d18-11eb-9159-a797ccebf5a7.png">

### 채널 Channel

<img width="827" alt="channel" src="https://user-images.githubusercontent.com/28593767/114651160-62607380-9d1e-11eb-8899-668b17547ce1.png">

- 합성곱 연산에서 *커널은 입력 영역의 특정 패턴이나 특징에 민감하게 반응하는 방향으로 학습되는 경향*이 있고 따라서 합성곱 계층에서 출력되는 픽셀 이미지를 **특징맵(Feature Map)** 이라고 한다.
- CNN이 다루는 이미지 데이터에는 가로와 세로 해상도 외에 **채널(Channel)** 이라는 차원이 추가된다.
- 합성곱 계층의 입력 채널 수는 최초의 입력 이미지 혹은 이전 계층이 생성한 출력 채널 수로 정해지지만, 출력 채널 수는 신경망 설계자가 마음대로 정할 수 있다.
  - 일반적으로 합성곱 신경망을 설계할 때는 합성곱 계층의 출력 채널 수를 입력 채널 수보다 늘려 더 많은 종류의 특징을 파악할 수 있게 한다.
  - 이렇게 합성곱 계층을 거칠 때마다 늘어난 정보량은 합성곱 계층 사이에 배치된 풀링 계층을 통해 다시 줄어든다.
- 풀링 층을 거친 이미지는 대개 해상도가 줄어들기만 할 뿐 채널 수는 변하지 않고 그대로 유지된다.

### 커널 Kernel

<img width="446" alt="kernel" src="https://user-images.githubusercontent.com/28593767/114651157-6096b000-9d1e-11eb-8ac8-60d01957c7de.png">

- 이미지의 작은 사각 영역에서 하나의 특징을 온전히 포착하려면 커널은 _해당 영역의 모든 채널에 대한 입력 픽셀값을 볼 수 있어야 한다_.
- 하나의 특징을 포착하는 커널은 *사각 영역 입력의 모든 채널을 처리하는 3차원 가중치*를 가져야 한다.
- 또한 출력 채널 수 만큼의 특징 맵을 만들어 내기 위해 커널이 출력 채널 수 만큼 있어야 한다.
- 따라서 커널은 입력 영역 크기에 *입력 채널과 출력 채널이 모두 반영된 4차원 구조*가 되어야 한다.

<img width="638" alt="channel2" src="https://user-images.githubusercontent.com/28593767/114651561-2f6aaf80-9d1f-11eb-895c-0819c717851f.png">
