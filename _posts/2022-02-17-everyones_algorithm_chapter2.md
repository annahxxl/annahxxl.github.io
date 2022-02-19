---
layout: post
title: "[모두의 알고리즘] 둘째마당: 재귀 호출"
subtitle: 책 "모두의 알고리즘"을 통한 학습 내용 정리 ✍
categories: Algorithm
tags: [모두의_알고리즘, 재귀, 유클리드, 하노이의_탑]
---

### 재귀 호출?

- 어떤 함수 안에서 자기 자신을 부르는 것을 말한다.
- 재귀 함수는 종료 조건이 함께 설계되어야 정상적으로 작동한다.
- 종료 조건 없이 재귀 호출을 한다면 호출에 필요한 메모리를 다 써버린 후 RecursionError나 Stack Overflow가 발생해 비정상적으로 종료된다.

### 유클리드 알고리즘

- 2개의 자연수 또는 정식의 최대공약수를 구하는 알고리즘 중 하나이다.
- a와 b의 최대공약수는 **_b_** 와 **_a를 b로 나눈 나머지_** 의 최대공약수와 같다.
- 어떤 수와 0의 최대공약수는 자기 자신이다.

```python
# gcd는 두 수의 최대공약수를 구하는 함수
gcd(60, 24) = gcd(24, 60 % 24) = gcd(24, 12) = gcd(12, 24 % 12) = gcd(12, 0) = 12
```

#### 유클리드 & 재귀 호출 구현 코드 (최대공약수 구하기)

- 일반적인 알고리즘으로 작성하면 다음과 같다.

```python
def gcd(a, b): # Greatest Common Divisor
  # 1. 두 수 중에서 작은값이 최대공약수 후보 중 가장 큰 값이므로 i에 저장한다.
  i = min(a, b)
  while True:
    # 2. i가 a와 b의 공통된 약수인지 확인한다.
    if a % i == 0 && b % i == 0:
      return i
    # 3. 아니라면 i를 -1 만큼 감소시킨다.
    i = i - 1
```

- 유클리드 알고리즘을 재귀 호출을 적용하여 최대공약수를 구하는 코드를 작성하면 다음과 같다.

```python
def gcd(a, b):
  if b == 0:
    return 0
  return gcd(b, a % b)
```

### 하노이의 탑 알고리즘

- [하노이의 탑](https://ko.wikipedia.org/wiki/%ED%95%98%EB%85%B8%EC%9D%B4%EC%9D%98_%ED%83%91)은 간단한 원반 옮기기 퍼즐이다.

#### 하노이의 탑 & 재귀 호출 구현 코드

- 원반 n개를 옮기는 과정을 구하는 코드를 작성하면 아래와 같다.

```python
def hanoi(n, from_pos, to_pos, aux_pos): # aux_pos는 보조 기둥 위치
  # 1. 원반이 1개면 3번째 기둥으로 옮긴다.
  if n == 1:
    print(from_pos, "→", to_pos)
    return
  # 2. 원반이 n개일 때 n-1개를 보조 기둥으로 옮긴다.
  hanoi(n - 1, from_pos, aux_pos, to_pos)
  # 3. 가장 큰 n번째 원반을 목적지로 옮긴다.
  print(from_pos, "→", to_pos)
  # 4. 보조 기둥에 있는 n-1개의 원반을 목적지로 옮긴다.
  hanoi(n - 1, aux_pos, to_pos, from_pos)
```

#### 하노이의 탑 알고리즘 시간 복잡도

하노이의 탑 구현 코드를 통해 값을 확인해보면

- 1층짜리 하노이의 탑: 원반을 1번 이동
- 2층짜리 하노이의 탑: 원반을 3번 이동
- 3층짜리 하노이의 탑: 원반을 7번 이동
- 4층짜리 하노이의 탑: 원반을 15번 이동
- 5층짜리 하노이의 탑: 원반을 31번 이동

1, 3, 7, 15, 31 ... 이런식으로 증가하고 있다.<br/>
원반 n개를 옮기려면 **_2 \*\* n - 1_** 번을 옮겨야 하므로
즉, 위 코드의 시간 복잡도는 **_O(2 \*\* n)_**이다.

### 연습 문제

#### 4-1. 연습 문제 1번의 1부터 n까지의 합 구하기를 재귀 호출로 만들기

```python
# 입력
n = int(input())

# O(n)
def solution(n):
  if n == 0:
    return 0
  return n + solution(n - 1)

# 출력
print(solution(n))
```

#### 4-2. 연습 문제 2번의 숫자 n개 중에서 최댓값 찾기를 재귀 호출로 만들기

```python
# 입력
nums = list(map(int, input().split()))

# O(n)
def solution(arr, n):
  if n == 1:
    return arr[0]
  maximum = solution(arr, n - 1) # n - 1번째까지의 최댓값 저장
  if maximum > a[n - 1]: # maximum과 n번째 값 비교
    return maximum
  else:
    return a[n - 1]

# 출력
print(solution(arr, len(arr)))
```

#### 5-1. 0과 1부터 시작하는 피보나치 수열이 0번째부터 시작한다고 가정할 때 n번째 피보나치 수를 구하는 알고리즘을 재귀 호출을 이용해서 구현하기

```python
# 입력
n = int(input())

# O(n)
def solution(n):
  if n <= 1:
    return n
  return solution(n - 1) + solution(n - 2)

# 출력
print(solution(n))
```
