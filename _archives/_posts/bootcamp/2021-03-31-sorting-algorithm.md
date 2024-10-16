---
layout: post
title: sorting algorithm
date: 2021-03-31
tags: [study, note]
categories: bootcamp
---

# 정렬 알고리즘 Sorting Algorithm

## 정렬 Sort

- 정렬이란 **데이터를 특정한 기준에 따라서 순서대로 나열하는 것**을 말한다.
- 프로그래밍에서는 데이터를 가공할 때 오름차순이나 내림차순 등 데이터를 정렬해서 사용하는 경우가 많다.
- 정렬 알고리즘은 **이진 탐색의 전처리 과정**이고 데이터를 정렬하면 이진 탐색이 가능하다.
- 정렬 알고리즘에는 _선택 정렬, 삽입 정렬, 퀵 정렬, 계수 정렬_ 등이 있다.

## 선택 정렬 Selection Sort

- 데이터가 무작위로 여러 개 있을 때, **가장 작은 데이터를 선택해 맨 앞에 있는 데이터와 바꾸고, 그 다음 작은 데이터를 선택해 앞에서 두 번째 데이터와 바꾸는 과정을 반복**하는 방식이다.
- *가장 원시적인 방법*으로 **매번 가장 작은 것을 선택한다**는 의미에서 선택 정렬 알고리즘이라고 한다.
- *즉, 가장 작은 것을 선택해서 앞으로 보내는 과정을 반복*하다 보면, 전체 데이터의 정렬이 이루어진다.

```python
array = [7,5,9] # Initialize an array

# Find the index of min value
for i in range(len(array)):
    min_index = i
    # Loop after the min index
    for j in range(i + 1, len(array)):
        if array[min_index] > array[j]:
            min_index = j
    # Swap the current value and min value
    array[i], array[min_index] = array[min_index], array[i]

print(array)

>> [5, 7, 9]
```

> **스왑(Swap)** 이란 *특정한 리스트가 주어졌을 때 두 변수의 위치를 변경하는 작업*으 파이썬에서는 간단히 리스트 내 두 요소의 위치를 변경할 수 있다.
>
> 다른 대부분의 프로그래밍 언어에서는 *명시적으로 임시 저장용 변수를 만들어 두 요의 값을 변경*해야 한다.

```python
array = [3, 5]
array[0], array[1] = array[1], array[0]
print(array)

>> [5, 3]
```

### 선택 정렬의 시간 복잡도

- 선택 정렬은 _N - 1_ 번 만큼 가장 작은 수를 찾아서 맨 앞으로 보내야하고 매번 가장 작은 수를 찾기 위해서 비교 연산이 필요하다.
- 선택 정렬의 시간 복잡도는 **_O(N^2)_** 이라고 표현할 수 있다.
- 선택 정렬은 기본 정렬 라이브러리나 다른 정렬 알고리즘에 비해 매우 비효율적이지만 *특정한 리스트에서 가장 작은 데이터를 찾는 문제*는 코딩 테스트에서 자주 나오므로 익숙해질 필요가 있다.

## 삽입 정렬 Insertion Sort

- 데이터가 무작위로 여러 개 있을 때, **데이터를 하나씩 확인하며, 각 데이터를 적절한 위치에 삽입하는 방식**이다.
- 삽입 정렬은 **특정한 데이터를 적절한 위치에 삽입한다**는 의미에서 삽입 정렬 알고리즘이라고 한다.
- 선택 정렬에 비해 실행 시간 측면에서 더 효율적인 알고리즘으로, 필요할 때만 위치를 바꾸므로 _데이터가 거의 정렬되어 있을 때_ 훨씬 효율적이다.
  - _선택 정렬은 현재 데이터의 상태와 상관없이 무조건 모든 요를 비교하고 위치를 바꾸는 반면 삽입 정렬은 그렇지 않다._
- 삽입 정렬은 특정한 데이터가 적절한 위치에 들어가기 이전에, 그 앞까지의 데이터는 이미 정렬되어 있다고 가정한다.
  - 삽입 정렬은 첫 번째 데이터는 이미 정렬되어 있다고 판단하고 두 번째 데이터부터 시작한다.

```python
array = [7, 5, 9, 8]

for i in range(1, len(array)):
    # Decrease by 1 from i
    for j in range(i, 0, -1):       # print(j) -> 1 2 1 3 2 1
        # Swap the current value with previous value
        if array[j] < array[j - 1]:
            array[j], array[j - 1] = array[j - 1], array[j]
        else:
            break

print(array)

>> [5, 7, 8, 9]
```

> **range()** 의 변수는 start, end, step의 3개이고 *step에 -1이 들어가면 start 인덱스부터 end + 1 인덱스까지 1씩 감소*한다.

### 삽입 정렬의 시간 복잡도

- 삽입 정렬은 선택 정렬과 마찬가지로 반복문을 2번 중첩해서 사용했기 때문에 시간 복잡도는 **_O(N^2)_** 라고 표현할 수 있다.
- 삽입 정렬은 현재 리스트의 데이터가 거의 정렬되어 있는 상태라면 매우 빠르게 동작하고 최선의 경우 **_O(N)_** 의 시간 복잡도를 가진다.
  - 거의 정렬되어 있는 상태로 입력이 주어지는 문제의 경우 삽입 정렬을 이용하는 것이 적절하다.
- 퀵 정렬과 비교했을 때 보통은 삽입 정렬이 비효율적이지만 정렬이 거의 되어 있는 상황에서는 더 강력하다.

## 퀵 정렬 Quick Sort

- 지금까지 배운 정렬 알고리즘 중에 *가장 많이 사용되는 정렬 알고리즘으로 대부분 프로그래밍 언어에서 정렬 라이브러리의 근간*이 되는 알고리즘이다.
  - 퀵 정렬 비교할 만큼 빠른 알고리즘에는 **병합 정렬(Merge Sort)** 알고리즘이 있다.
- 퀵 정렬은 **기준 데이터를 설정한 다음 큰 수와 작은 수를 교환한 후 리스트를 반으로 나누는 방식**이다.
- 퀵 정렬에서 큰 숫자와 작은 숫자를 교환하기 위한 기준을 **피벗**이라고 한다.
  - 피벗을 설정하고 리스트를 분할하는 방법에 따라서 여러 방식이 있는데 가장 대표적인 분할 방식으로는 **호어 분할 방식**이 있다.

### 호어 분할 방식을 이용한 퀵 정렬 알고리즘

1. 리스트에서 첫 번째 데이터를 피벗으로 삼는다.
2. 피벗을 설정한 뒤에는 *왼쪽에서 부터 피벗보다 큰 데이터*를 찾고, *오른쪽에서 부터 피벳보다 작은 데이터*를 찾는다.
3. 그 후 큰 데이터와 작은 데이터의 위치를 서로 교환한다.
4. 이러한 과정을 반복하면 피벗에 대하여 정렬이 수행된다.
5. 현재 왼쪽에서부터 찾는 큰 값과 오른쪽에서부터 찾는 작은 값의 위치가 서로 엇갈리는 경우 *작은 데이터와 피벗의 위치를 서로 변경*한다.
6. 이렇게 피벗의 왼쪽에는 피벗보다 작은 데이터가 위치하고, 피벗의 오른쪽에는 피벗보다 큰 데이터가 위치하도록 하는 작업 **분할 혹은 파티션(Partition)** 이라고 한다.
7. 이러한 상태에서 왼쪽 리스트와 오른쪽 리스트를 개별적으로 정렬한다. (재귀 함수)

<img width="1281" alt="quick_1" src="https://user-images.githubusercontent.com/28593767/112918003-d99ee080-913e-11eb-939d-8a2051626a88.png">

<img width="1281" alt="quick_2" src="https://user-images.githubusercontent.com/28593767/112918007-dc99d100-913e-11eb-9b8f-bbd2ffdc06a4.png">

<img width="1281" alt="quick_3" src="https://user-images.githubusercontent.com/28593767/112918008-dd326780-913e-11eb-9de3-cb99e9aa9712.png">

```python
array=[5,7,9,0,3,1,6,2,4,8]

# Quick Sort algorithm
def quick_sort(array, start, end):
    # If a element is 1, nothing happens
    if start >= end :
        return
    pivot = start       # Pivot is the first element
    left = start + 1    # Left pointer is one after pivot
    right = end         # Right pointer is the end

    # While-loop if left is smaller or equal to right
    while left <= right:
        # Find a larger value than pivot
        while left <= end and array[left] <= array[pivot]:
            left += 1
        # Find a smaller value than pivot
        while right > start and array[right] >= array[pivot]:
            right -= 1
        # If left and right pointers cross, swap pivot and smaller element
        if left > right :
            array[right], array[pivot] = array[pivot], array[right]
        # If pointers do not cross, swap smaller and larger element
        else:
            array[left], array[right] = array[right], array[left]
    # After partition, recursion on left and right side of new pivot
    quick_sort(array, start, right - 1)
    quick_sort(array, right + 1, end)


quick_sort(array, 0, len(array) - 1)
print(array)

>> [0,1,2,3,4,5,6,7,8,9]
```

```python
array=[5,7,9,0,3,1,6,2,4,8]

# Quick Sort algorithm in pythonic way
def quick_sort(array):
    # If a element is 1, nothing happens
    if len(array) <= 1:
        return array

    pivot = array[0]    # Pivot is the first element
    tail = array[1:]    # List except pivot

    # Partition left and right sides
    left_side = [x for x in tail if x <= pivot]
    right_side = [x for x in tail if x > pivot]

    # After partition, use recursion on left and right side of new pivot
    # Return a list of left side, pivot, and right side
    return quick_sort(left_side) + [pivot] + quick_sort(right_side)


print(quick_sort(array))

>> [0,1,2,3,4,5,6,7,8,9]
```

### 퀵 정렬의 시간 복잡도

- N개의 요소에서 재귀 호출이 k번이라고 한다면 _k = log(N)_ 이라고 할 수 있고 이것을 N개의 요소만큼 반복한다.
- 따라서, 퀵 정렬의 평균적인 시간 복잡도는 **_O(NlogN)_** 라고 표현할 수 있다.
- 최악의 경우는 이미 정렬된 데이터의 마지막 원소, 즉 최댓값이나 최솟값을 피벗으로 하는 경우로 시간 복잡도는 **_O(N^2)_** 라고 표현할 수 있다.

## 계수 정렬 Counting Sort

- 계수 정렬은 특정한 조건이 부합할 때만 사용할 수 있는 매우 빠른 정렬 알고리즘으로 매우 간단하게 구현될 수 있다.
- 계수 정렬은 **데이터의 크기 범위가 제한되어 정수 형태로 표현할 수 있을 때만 사용**할 수 있다.
  - 데이터의 값이 무한한 범위를 가질 수 있다는 실수형 데이터가 주어지는 경우 계수 정렬은 사용하기 어렵다.
  - 일반적으로 가장 큰 데이터와 가장 작은 데이터의 차이가 1,000,000을 넘지 않을 때 효율적이다.
  - 예를 들어 0이상 100 이하인 성적 데이터를 정렬할 때 계수 정렬이 효과적이다.
- 계수 정렬을 이용할 때는 *모든 범위를 담을 수 있는 크기의 리스트를 선언*해야 한다.
  - 계수 정렬은 일반적으로 별도의 리스트를 선언하고 그 안에 정렬에 대한 정보를 담는다는 특징이 있다.
  - 데이터의 크기가 제한되어 있을 때에 한해서 데이터의 개수가 매우 많더라도 빠르게 동작한다.
- 이전까지는 두 수를 비교하는 **비교 정렬(Comparison Sort)** 인 것에 반해, 계수 정렬은 단 하나의 비교도 하지 않고 _정렬할 때 순서가 섞이지 않는_ **안정 정렬(Stable Sort)** 이다.

이 방법은 단 하나의 비교도 일어나지 않았습니다. 그리고 같은 숫자라도 정렬할 때 순서가 섞이지 않는 안정 정렬

### 계수 정렬 알고리즘

1. 먼저 가장 큰 데이터와 가장 작은 데이터의 범위가 모두 담길 수 있도록 하나의 리스트를 생성한다.
2. 처음에는 리스트의 모든 데이터가 0이 되도록 초기화 한다.
3. 마지막으로 *데이터를 하나씩 확인하며 데이터의 값과 동일한 인덱스의 데이터를 1씩 증가*시키면 계수 정렬이 완료된다.
4. 결과적으로 *리스트에는 각 데이터가 몇 번 등장했는지 그 횟수가 기록*되고 이 리스트에 *저장된 데이터 자체가 정렬된 형태 그 자체*라고 할 수 있다.

```python
# Assume all element >= 0
array = [7, 5, 9, 0, 3, 1, 6, 2, 9, 1, 4, 8, 0, 5, 2]

# Count array includes every element of the original array (Initialize with 0)
count = [0] * (max(array) + 1)

for i in range(len(array)):
    # Increase the number of frequency for each value
    count[array[i]] += 1 # 각 데이터의 해당하는 인덱스의 값 증가

# For all elements in the list
for i in range(len(count)):
    # For the number of each frequency
    for j in range(count[i]):
        # Print sorted values
        print(i, end = ' ')

>> 0 0 1 1 2 2 3 4 5 5 6 7 8 9 9
```

- 계수 정렬은 정렬 알고리즘과는 다르며, *동일한 값을 가지는 데이터가 여러 개 등장할 때 적합*하다.
  - 예를 들어 성적을 비교할 경우 100점을 맞은 학생이 여러 명일 수 있기 때문에 계수 정렬이 효과적이다.
- 반면에 앞서 설명한 퀵 정렬은 일반적인 경우에서 평균적으로 빠르게 동작하기 때문에 데이터의 특성을 파악하기 어렵다면 퀵 정렬을 이용하는게 유리하다.
- 즉, **계수 정렬은 데이터의 크기가 많이 중복되어 있을수록 유리**하며 항상 사용할 수는 없지만, 조건만 만족하다면 계수 정렬은 정렬해야 하는 데이터의 개수가 매우 많을 때에도 효과적으로 사용할 수 있다.

### 계수 정렬의 시간 복잡도

- 계수 정렬의 시간 복잡도는 **_O(N+K)_** 라고 표현 수 있다.
- 이 때 N은 리스트의 요소의 개수이고 K는 리스트의 가장 큰 값을 나타낸다.
- 따라서 리스트의 최댓값이 매우 큰 수라면 계수 정렬은 비효율적인 알고리즘이라는 사실을 알 수 있다.
