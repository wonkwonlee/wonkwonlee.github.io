---
layout: post
title: regression analysis
date: 2021-03-27
tags: [study, note]
categories: bootcamp
---

# 회귀 분석 Regression Analysis

## 신경망의 세가지 기본 출력 유형

![three](https://user-images.githubusercontent.com/28593767/112080349-304b6e00-8bc5-11eb-98d4-ae2dbc1929de.png)

1. 회귀 분석 : 어떤 특징값 하나를 숫자로 추정하여 출력
2. 이진 판단 : '예'나 '아니오' 가운데 한 쪽을 택해 출력
3. 선택 분류 : 몇 가지 후보 중 하나를 골라 선택 결과를 출력

## 회귀 Regression

- 회귀는 옛날 상태로 돌아간다는 의미이다.
- 통계학에서는 연속형 변수 사이의 모형을 구한 뒤 적합성을 측정하는 분석 방법을 말한다.
  - 다시 말해, 입력값들을 근거로 미지의 변숫값을 추정하고 예측하는데 이용된다.
- 딥러닝 알고리즘에서의 값 추정 또한 신경망 모델이 입력 데이터를 근거로 출력값을 추정하는 것이다.

![problem](https://user-images.githubusercontent.com/28593767/112080345-2f1a4100-8bc5-11eb-95c2-cbf5089d817b.png)

- 머신러닝을 적용하기 위해서는 _y = Θ_0 + Θ_1x_ 형태의 함수를 만들어야 한다.
  - 세타(_Θ_)는 구해야 할 미지수, 기울기와 편향을 나타낸다.
- 이러한 매개변수 값을 적절한 값으로 설정하기 위해 머신러닝이 활용된다.
  - 학습 데이터를 기존에 작성에 작성한 함수에 대입하여 세타를 정한다.

## 최소제곱법 Least Squares Method

![lsm_d](https://user-images.githubusercontent.com/28593767/112080347-2fb2d780-8bc5-11eb-9ca3-e02280b33464.png)

- _y_ 와 _fΘ(x)_ 의 오차가 0이 되는 것이 가장 이상적이지만 그래프에 있는 모든 점에 생기는 오차를 0으로 만드는 것은 불가능하다.
- 따라서 **모든 점에서 생기는 오차의 합계가 가능한 작아지도록** 한다.

![lsm](https://user-images.githubusercontent.com/28593767/112080351-30e40480-8bc5-11eb-99d5-f24b0872e0cf.png)

- 목적함수 _E(Θ)_ 로서, E는 Error의 머릿글자이고 _x^(i), y^(i)_ 는 i번째 학습 데이터를 의미한다.
- 각각의 학습 데이터마다 생기는 오차를 제곱하여 모두 더하고 그 값에 1/2을 곱한다.
  - 양수와 음수가 섞여 있는 경우 계산이 어려워지기에 오차가 양수가 되도록 제곱을 수행한다.
  - 또한 제곱의 효과는 오차가 큰 값에 대해서 더 큰 오차값을 부여한다.
  - 전체에 1/2을 곱하는 이유는 결과로 나온 식을 간단한 모양으로 만들기 위해 붙인 상수이다.
  - 최적화 문제에 상수를 붙여도 최솟값이 존재하는 위치는 변하지 않는다.
  - ![square](https://user-images.githubusercontent.com/28593767/112080354-30e40480-8bc5-11eb-831a-4079d2d9e3e9.png)
- 이렇게 **계산된 _E(Θ)_ 값이 가장 작아지게 되는 Θ값을 찾는 것이 목적**이고 이것을 **최적화 문제**라고 한다.
  - Adam 알고리즘 : 딥러닝 옵티마이저
- 목적함수 _E(Θ)_ 이 작아진다는 의미는 오차가 작아진다는 의미이고 이러한 기법을 **최소제곱법**이라고 한다.

## 경사하강법 Gradient Descent

- 계산한 목적함수 _E(Θ)_ 를 감소시켜야 하기 위해서는 매개변수 *Θ*를 적절하게 조절해야 한다.
- 하지만 기준값을 비교해 가며 계산하는 방식은 효율적이지 못하다.
- 따라서 *변화하는 정도를 구하기 위해 사용되는 미분*을 활용한다.

![gd](https://user-images.githubusercontent.com/28593767/112080356-317c9b00-8bc5-11eb-831b-4e22672f5ccf.png)

- **𝜂(에타)** 는 **학습률(Learning rate)** 이라 하는 양의 정수로 이 _학습률의 크기에 따라 최솟값에 도달하기까지 갱신해야 하는 횟수가 달라지게 됩니다._
- 즉 학습률로 인해 **최솟값에 수렴되는 속도가 달라진다**는 겁니다.
- 학습률이 _적절한 값을 가지면 조금씩 최솟값을 향하여 x값이 줄어들게 된다._
- 반면 학습률이 너무 크면 x값이 줄어들지 않게 되거나 혹은 최솟값에서 멀어지게 되는데 이것을 **발산**이라 한다.
- 또한 학습률이 너무 작으면 최솟값으로 이동하는 보폭이 작아져 갱신횟수가 늘어나게 된다.

![gd_d](https://user-images.githubusercontent.com/28593767/112080342-2cb7e700-8bc5-11eb-89a3-179d0225a638.png)

### 목적함수의 미분

![pde](https://user-images.githubusercontent.com/28593767/112085079-36454d00-8bcd-11eb-9c07-5109d23b2054.png)

- 목적함수의 _fΘ(x)_ 는 **_Θ_0(편향), Θ_1(가중치)_** 의 두 매개 변수를 가지고 있는 **2변수 함수**이다.
- 따라서 매개변수 갱신식은 편미분으로 나타낼 수 있다.
  - ![pde_eq](https://user-images.githubusercontent.com/28593767/112085087-38a7a700-8bcd-11eb-9402-111e1447656b.png)
- 최종적으로 매개변수 *Θ_0, Θ_1*의 갱신식은 다음과 같다.
  - ![theta](https://user-images.githubusercontent.com/28593767/112085089-39403d80-8bcd-11eb-8ffe-c27f7c1b9cf9.png)
- 이 식에 따라 매개변수를 갱신해가면 알맞은 1차함수 _fΘ(x)_ 를 발견할 수 있고 임의의 x값에 대한 출력값을 예측할 수 있게 된다.

## 다항식 회귀 Polynomial Regression

- 함수의 모양이 일직선이 아닌 곡선의 형태가 더 필요한 경우 _fΘ(x)_ 를 2차함수 혹은 더 큰 차수의 식으
  로 정의하면 곡선의 형태를 그려낼 수 있다. + **_fΘ(x) = Θ_0 + Θ_1x +Θ_2x^2_**
- 하지만 무작정 차수를 늘려가는 방식은 **과잉적합(Overfitting)** 문제가 발생할 수 있다.
- 결과적으로 매개변수가 _Θ_3, Θ_4,..._ 이렇게 늘어남에 따라 같은 방법으로 갱신식을 구해줄 수 있고 이러한 **다항식의 차수를 늘린 함수를 사용하는 것**을 **다항식 회귀(Polynomial regression)** 라고 한다.
- 다항식의 매개변수 갱신식은 다음과 같다.
  - ![poly](https://user-images.githubusercontent.com/28593767/112085502-00549880-8bce-11eb-8f7c-58f80680da0c.png)

## 다중 회귀 Multiple Regression

- 변수가 두 개 이상인 경우 _fΘ(x*1,x_2,x_3) = Θ_0 + Θ_1x_1 + Θ_2x_2 + Θ_3x*_ 로 정의할 수 있다.
- 변수가 n개인 경우 일반화 하여 다음과 같이 나타낸다.
  - ![fn](https://user-images.githubusercontent.com/28593767/112085501-ffbc0200-8bcd-11eb-8dd1-1c9ebabc2a8d.png)
- 매번 n개의 x를 쓰는 대신 매개변수 *Θ_n*과 변수 *x_n*을 벡터 형태로 표기한다.
- 일반적으로 벡터끼리 곱할 경우에는 이렇게 한쪽을 전치(Transpose) 한 후에 곱셈을 수행하여 내적을 취한다.
  - ![vec_c](https://user-images.githubusercontent.com/28593767/112085500-fe8ad500-8bcd-11eb-9cd3-26963a9a9429.png)
- 다중 회귀의 매개변수 갱신식 역시 _u = E(Θ), v = fΘ(x)_ 로 두는 것은 같지만 변수가 많아짐에 따라 일반화하여 j번째 요소인 *Θ_j*로 편미분해야 한다.
  - ![pde_j](https://user-images.githubusercontent.com/28593767/112085505-00ed2f00-8bce-11eb-9c0c-3274981f825e.png)
- j번째 매개변수의 갱신식은 다음과 같다.
  - ![theta_j](https://user-images.githubusercontent.com/28593767/112085507-00ed2f00-8bce-11eb-870c-9444c25710bb.png)
- 이렇게 여러 개의 변수를 사용하는 것을 **다중회귀(Multiple Regression)** 라고 한다.
- 다만 경사하강법은 모든 학습 데이터의 개수만큼 반복해서 계산해야 한다는 점 때문에 학습 데이터가 많으면 많을수록 학습에 대한 시간을 많이 소모하게 된다는 단점이 있다.
  - 이러한 경우를 극복하고자 이후 더 효율적인 다양한 기법이 등장한다.

## 확률적 경사하강법과 미니배치 경사하강법 Stochastic Gradient Descent & Minibatch Gradient Descent

### 확률적 경사하강법 Stochastic Gradient Descent

![dia](https://user-images.githubusercontent.com/28593767/112094180-22561700-8bde-11eb-9b2c-5b7f5eb50c9f.png)

- 최소제곱법의 단점에는 계산이 많이 걸리는 것 외에 **지역 최솟값(Local minimum)** 에 빠져버린다는 문제가 있다.
- 일반적으로 초깃값은 난수를 사용하여 선택하는데, 그렇게 매번 초깃값이 변하면 지역 최솟값에 빠지게 된다.

![sto](https://user-images.githubusercontent.com/28593767/112094183-24b87100-8bde-11eb-8ca5-d8d26dc91efe.png)

- 최소제곱법의 매개변수 갱신식이 모든 학습 데이터의 오차를 사용하는 것에 반해 확률적 경사하강법에서는 학습 데이터를 **무작위로 한 개 골라서 그것을 매개변수 갱신**에 사용한다.
  - k : 무작위로 선택된 인덱스
  * 무작위로 한 개만 고르기 때문에 배치 크기는 1
- 기존 방식과 달리 학습 데이터를 무작위로 선택해서 해당 시점에서의 경사를 사용해 매개변수를 갱신하기 때문에 지역 최솟값에 빠지기 어렵다.

### 미니배치 경사하강법 Minibatch Gradient Descent

![sto2](https://user-images.githubusercontent.com/28593767/112094185-25510780-8bde-11eb-8775-dc3f6805a208.png)

- 최소제곱법과 확률적 경사하강법의 중간을 취한 것으로 **미니배치 경사하강법** 이라고 한다.
- 학습 데이터를 무작위로 하나 선택하는 대신, 학습 데이터를 **무작위로 m개만 선택해서 매개변수를 갱신**하는 방법이다.
- 무작위로 정한 m개에 선택된 학습 데이터의 인덱스 집합을 K라고 두고 매개변수를 갱신한다.
- 일반적으로 default로 설정되어 있다.

> 중요한 것은 확률적 경사하강법이든 미니배치 경사하강법이든 학습률 𝜂에 대해서는 반드시 적절한 값으로 설정해야 한다는 점이다.

## 회귀 분석과 손실 함수 Regression Analysis and Loss Function

- **손실 함수(Loss function)** 혹은 **비용 함수(Cost function)** 는 신경망이 추정한 값을 정답에 비교할 때 얼마나 정확한 지를 알려주는 정략적 지표를 의미한다.
  - 함수라는 표현이 붙은 이유는 입력이나 매개변수(가중치, 편향)에 따라 그 값이 달라지기 때문이며 **손실** 혹은 **비용**이라고 부르기도 한다.
- 일반적으로 회귀 분석에서는 *신경망의 추정값이 얼마나 정확한지 평가할 때 평균제곱오차를 평가지표로 사용*한다.

### 평균제곱오차 Mean Squared Error

![mse](https://user-images.githubusercontent.com/28593767/112094186-25510780-8bde-11eb-9890-720e9d7d239f.png)

- *각 출력 성분에 대한 추정값과 정답사이의 차이인 오차를 제곱한 뒤 모두 합해 전체 성분 수로 나눈 값*을 의미한다.
- 손실 함수도 목적 함수와 마찬가지로 오차를 **제곱하는 연산 때문에 항상 0 이상**이며 _신경망의 추정이 정확해질 수록 오차가 줄어들며 0에 가까워진다_.

### 손실 함수 계산 예제

![mse2](https://user-images.githubusercontent.com/28593767/112094187-25e99e00-8bde-11eb-8a3e-aab073ce23fa.png)

> AI타릭 보다 아무무의 MSE가 더 값이 작기에 승부의 신 결과는 아무무가 이겼다.

## 딥러닝에 등장하는 다양한 값들

> 딥러닝 모델에 쓰이는 다양한 값들은 크게 4가지로 분류할 수 있다.

1. 입력값 : 학습에 사용되는 데이터처럼 외부에서 주어지는 값
2. 중간계산 결과 : 신경망 연산 부분 즉 순전파나, 손실함수값에 영향을 미친 모든 성분에 대하여 손실 기울기를 구하는 과정인 역전파 처리과정에서 생성되는 값
   - 학습 과정에서 최소화 대상이 되는 손실 함숫값이나 성능에 대한 평가 지표로 지속적인 관찰의 대상이 된다.
3. 파라미터 : 학습이 진행됨에 따라 값이 변하고 그러면서 순전파와 역전파 처리에 계속 이용되는 값
   - 퍼셉트론의 가중치나 편향, 혹은 매개변수가 이에 해당한다.
4. 하이퍼 파라미터 : 학습 횟수, 미니배치 크기, 학습률처럼 딥러닝 모델의 구조나 학습 과정에 영향을 미치는 각종 상숫값
   - 딥러닝 알고리즘을 실행하는 동안은 값이 변하지 않는다.
   - 항상 고정불변인 값은 아니고 끊임없이 값을 바꿔가며 실험해야 하는 값이다.

## 비선형 정보와 원-핫 벡터 Nonlinear Data and One-Hot Vector

- 상수값들은 대소관계나 비율이 나름대로 타당한 의미가 있는 선형적 특징을 띈다.
- 하지만 _남자, 여자, 어린이_ 등과 같은 정보를 숫자로 표현한다면 각각 0,1,2 처럼 표현을 해야하는데 이러한 정보는 타당한 선형적 의미가 존재하지 않는다.
- 이러한 *비선형 정보를 항목 별로 분할하여 해당 항목만 1, 나머지는 0으로 나타내는 방식*을 **원-핫 벡터(One-hot vector)** 표현이라고 한다.
- *남자, 여자, 어린이*의 정보를 [1,0,0], [0,1,0], [0,0,1] 이렇게 세 정보 항으로 구성해 원-핫 벡터로 분할해 표현하면 입력 벡터의 크기가 1에서 3으로 늘어나게 된다.
- 따라서 **입력의 크기가 증가하게 되어 size가 급격히 늘어난다는 단점**이 있다.
