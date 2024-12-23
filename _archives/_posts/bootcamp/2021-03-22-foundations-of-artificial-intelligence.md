---
layout: post
title: foundations of artificial intelligence
date: 2021-03-22
tags: [study, note]
categories: bootcamp
---

# 인공지능 기초 Foundations of Artificial Intelligence

## 인공지능과 머신러닝 그리고 딥러닝 AI, Machine Learning and Deep Learning

<img width="650" alt="ai" src="https://user-images.githubusercontent.com/28593767/111931293-45a99500-8afe-11eb-875a-884bfab3682c.png">

- 인공지능은 사람의 지능과 비슷한 역할을 수행하는 소프트웨어를 의미한다.
- 인공지능을 만드려는 시도는 크게 **지식 기반 접근**과 **데이터 기반 접근**으로 나뉜다.
- 지식 기반 접근은 **문제 영역의 지식을 기호로 표현해 풀어내는 방식**이다.
  - 초창기 열악한 컴퓨팅 환경에서는 핵심 지식을 추출하여 문제를 해결하려는 시도가 주를 이뤘다.
  - 이러한 접근은 다양하고 추상적인 전문지식을 모순 없이 기호로 표현하는 일에서 어려움을 겪었다.

<img width="650" alt="classify" src="https://user-images.githubusercontent.com/28593767/111931301-49d5b280-8afe-11eb-8440-6fd09ef27182.png">

- 머신러닝으로 통칭되는 데이터 기반 접근 방식은 **프로그램이 직접 데이터를 분석해서 숨어 있는 규칙이나 패턴을 포착해 문제를 해결**한다.
  - 데이터로부터 규칙이나 패턴을 획득하는 과정을 **학습(Training)** 이라 하는데 이 _학습 과정을 프로그램이 직접 수행하기 때문에 기계학습_, 즉 머신러닝이라고 부른다.
  - 머신러닝이 제대로 작동하려면 학습 알고리즘과, 대량의 데이터, 막대한 컴퓨팅 파워가 필요하지만 *전문가로부터 지식을 추출하는 어려운 과정 없이 인공지능을 실현할 수 있다는 장점*이 있다.
- 딥러닝은 머신러닝의 한 학습 방법으로 **동물의 신경 세포를 흉내 낸 퍼셉트론(Perceptron) 을 단위 삼아 구성한 신경망 구조를 이용해 학습을 수행하고 문제를 풀어내는 방식**이다.

## 동물의 신경세포, 뉴런 Neuron

- 뉴런은 정보 전달용 신경 세포로 다른 뉴런들로부터 전기 신호를 받아들인다
- 이 전기 신호는 시냅스라는 화학적 연결 부위를 통해 전달되는데 발달 정도에 따라 같은 신호라도 더 강하게 전달된다.
- 뉴런은 **전달된 전기 신호들(Input) 로부터 자신의 출력 신호(Output) 를 만들어 낸다**.
- 출력 신호는 단순히 입력 신호값의 합이 아닌 **비선형 방식**으로 결정된다
  - 임곗값 이상이면 활성 상태, 임곗값 미만이면 비활성화 상태가 되어 *두 가지 서로 다른 값 가운데 하나를 출력하는 디지털 방식*으로 동작한다.

## 인공 신경망의 기본 유닛, 퍼셉트론 Perceptron

![percep](https://user-images.githubusercontent.com/28593767/111931303-4a6e4900-8afe-11eb-97df-86dd507d69ca.png)

- 퍼셉트론은 동물의 신경 세포인 뉴런을 모델 삼아 처음 개발되었다.
- **퍼셉트론에 주어지는 입력(Input)** *x1, ..., xn*은 *다른 뉴런들로부터 전달되는 전기 신호*에 해당한다.
- **각 입력 항에 곱해지는 가중치(Weight)** 는 *w1, ..., wn*은 뉴런 연결 부위에 형성된 *시냅스의 발달 정도*에 해당한다.
- 외부 입력과 별도로 주어지는 미리 정해진 입력값 _x0_ 와 가중치 _w0_ 는 **편향(Bias)** 라고 불리며 이 _x0w0_ 를 함께 묶어 _b_ 라는 하나의 값으로 나타내기도 한다.
- 비선형 함수 _f()_ 는 **활성화 함수(Activation function)** 라고 불리며 뉴런이 단순히 입력 전기 신호를 합한 값을 출력으로 삼지 않고 *처리를 거쳐 출력값을 결정*하는 것처럼 최종 출력을 결정한다.
  - 시그모이드, ReLU 함수 등
- 따라서 퍼셉트론의 출력은 _y = f(x1w1 + ... + xnwn + b)_ 로 계산된다.

- 퍼셉트론이 뉴런의 복잡한 기능을 모두 표현한다고는 할 수 없지만 이런 퍼셉트론을 이용해 다양한 구조의 신경망을 구성하고 가중치와 편향값을 알맞게 조정함으로써 인공지능 분야를 풀어나가고 있다.
- 퍼셉트론 *하나하나는 너무 작고 간단한 구조이지만 조직적으로 연결되어 함께 동작하면 상상하기 어려울 정도로 놀라운 능력을 발휘*할 수 있다.
- 높은 성능을 내려면 풍부하고 질 좋은 데이터를 확보하는 수고, 적절한 모델 구성을 찾는 시행착오, 그리고 하이퍼파라미터 값을 조정하는 반복 실험이 모두 필요하다.
