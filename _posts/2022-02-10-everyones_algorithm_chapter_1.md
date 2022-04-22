---
layout: post
title: "[모두의 알고리즘] 첫째 마당: 알고리즘 기초"
subtitle: 책 "모두의 알고리즘"을 통한 학습 내용 정리 ✍
categories: Algorithm
tags: [모두의_알고리즘, BigO, List, Set]
---

### BigO?

- 알고리즘의 대략적인 성능을 수학적 표기법으로 알고리즘의 시간&공간 복잡도를 표현할 수 있다.
- 데이터나 사용자의 증가율에 따른 성능을 예측하는것이 목표이기 때문에
  상수와 같은 숫자들은 모두 제외된다.

> 💡 시간 복잡도 종류와 알고리즘 예시들은 [여기](https://www.youtube.com/watch?v=6Iq5iMCVsXA)에서 자세히 볼 수 있다.

### List vs Set

| 자료구조 | 순서 | 중복 | 추가   | 삭제    |
| -------- | ---- | ---- | ------ | ------- |
| List     | ⭕   | ⭕   | append | pop     |
| Set      | ✖    | ✖    | add    | discard |

> 💡 추가/삭제 메서드는 표에 작성된 것 외에도 다양하게 존재한다.

### 연습 문제

#### 1. 1부터 n까지 연속한 숫자의 제곱의 합을 구하는 프로그램을 for 반복문으로 만들기

```python
# 입력
n = int(input())

# O(n)
def solution1(n):
  total = 0
  for i in range(1, n + 1):
    total += (i ** 2)
  return total

# O(1)
def solution2(n):
  return n * (n + 1) * (2 * n + 1) // 6

# 출력
print(solution2(n))
```

#### 2. 숫자 n개를 리스트로 입력받아 최솟값을 구하는 프로그램 만들기

```python
# 입력
nums = list(map(int, input().split()))

# O(n)
def solution(arr):
    minimum = 0
    for i in arr:
        if i < minimum:
            minimum = i
    return minimum

# 출력
print(solution(nums))
```

#### 3. n명 중 두 명을 뽑아 짝을 짓는다고 할 때 짝을 지을 수 있는 모든 조합을 출력하는 알고리즘 만들기

```python
# 입력
people = list(input().split())

# O(n**2)
def solution(arr):
    n = len(arr)
    for i in range(0, n - 1):
        for j in range(i + 1, n):
            print('{0} - {1}'.format(arr[i], arr[j]))

# 출력
solution(people)
```
