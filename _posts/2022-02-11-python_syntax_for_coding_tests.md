---
layout: post
title: "[파이썬 알고리즘 문제풀이] 섹션 1: 코딩 테스트를 위한 파이썬 문법 간단 정리"
subtitle: 강의 "파이썬 알고리즘 문제풀이"를 통한 학습 내용 정리 ✍
categories: Algorithm
tags: [파이썬_알고리즘_문제풀이, Python]
---

## 출력

```python
a, b = 10, 20

print(a) # 10

print(a, b) # 10 20 30

print('a', a) # a 10

print(a, b, sep=', ') # 10, 20

print(a, end='!') # 10!

print('{0} + {1} = {2}'.format(a, b, a + b)) # 10 + 20 = 30
```

## 입력

```python
# 기본 입력
a = input('숫자를 입력하세요 : ') # 입력받은 값은 항상 문자열

print(a) # a


# 띄어쓰기로 구분하여 여러개 입력
a, b = input('숫자를 입력하세요 : ').split()

print(a, b) # 1, 2

print(a + b) # 12
```

## 형 변환

```python
a = '10'


# 숫자 형 변환
a = int(a)

print(a + 5) # 15


# 문자 형 변환
a = str(a)

print(a + '5') # 105


# 여러 개 입력 시 모두 숫자로 형 변환
a, b = map(int, input().split())

print(a, b) # a b


# 여러 개 입력 후 list로 받기
arr = list(input().split())

print(arr) # [a, b]


#여러 개 입력 후 숫자로 형 변환 하여 list로 받기
arr = list(map(int, input().split()))

print(arr) # [1, 2]
```

## 연산자

```python
a, b = 6, 4

print(a + b) # 10

print(a - b) # 2

print(a * b) # 24

print(a ** b) # 1296

print(a % b) # 2

print(a / b) # 1.5

print(a // b) # 1
```

## 조건문

```python
a = 93

if a == 100:
    print('만점')
elif a >= 90:
    print('A')
elif a >= 80:
    print('B')
elif a >=70:
    print('C')
elif a >=60:
    print('D')
else:
    print(F)
```

## 반복문

### range (범위 지정)

```python
# range
arr = list(range(10))
print(arr) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

arr = list(range(1, 11))
print(arr) # [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

arr = list(range(10, 0 ,-1))
print(arr) # [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
```

### for

```python
arr = []

for i in range(10):
    arr.append(i)
print(arr) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### for-else

```python
arr = []

for i in range(10):
    arr.append(i)
else: # 반복문이 break에 의해 종료되지 않고 정상적으로 반복문이 종료된다면 실행
    print(arr) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### while

```python
arr = []

i = 1

while i < 10:
    arr.append(i)
    i += 1

print(arr) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### continue/break (키워드)

| 키워드   | 설명                                                           |
| -------- | -------------------------------------------------------------- |
| continue | continue 키워드 아래에 있는 문장들을 건너뛰고 다음 반복을 시작 |
| break    | 더 이상 반복하지 않고 현재 반복문을 종료                       |

```python
# continue
arr = []

for i in range(10):
    if i % 2 == 0:
        continue
    arr.append(i)

print(arr) # [1, 3, 5, 7, 9]


# break
arr = []

for i in range(10):
    if i == 5:
        break
    arr.append(i)

print(arr) # [0, 1, 2, 3, 4]
```

## 문자열

| 메서드 | 설명                                                           |
| ------ | -------------------------------------------------------------- |
| upper  | 문자열을 대문자로 변환하기                                     |
| lower  | 문자열을 소문자로 변환하기                                     |
| find   | 해당하는 문자열이 처음으로 나오는 index 구하기 (대소문자 구별) |
| count  | 해당하는 문자열의 개수 구하기 (대소문자 구별)                  |
| len    | 문자열 길이 구하기                                             |
| ord    | 문자를 ASCII 코드로 변환하기                                   |
| chr    | ASCII 코드를 문자로 변환하기                                   |
| slice  | 문자열 자르기                                                  |

### upper

```python
print('It is string'.upper()) # IT IS STRING
```

### lower

```python
print('It is string'.lower()) # it is string
```

### find

```python
print('It is string'.find('t')) # 1
```

### count

```python
print('It is string'.count('t')) # 2
```

### slice

```python
print('It is string'[:2]) # It

print('It is string'[6:]) # string
```

### len

```python
print(len('It is string')) # 12
```

### ord

```python
print(ord('E')) # 69
```

### chr

```python
print(chr(69)) # E
```

## 리스트

|메서드|설명|
|append|맨 뒤에 값 추가하기|
|insert|특정 위치에 값 추가하기|
|pop|값 삭제하기|
|remove|특정 값 삭제하기|
|index|값 찾기|
|sum|리스트의 합 구하기|
|max|리스트의 최댓값 구하기|
|min|리스트의 최솟값 구하기|
|sort|리스트 정렬하기 (반환 X)|
|sorted|정렬한 리스트를 새로운 결과로 반환하기|
|clear|리스트 비우기|
|enumerate|(index, value) 튜플로 변환하기|
|all|반복 가능한 자료형의 모든 요소가 참이면 True|
|any|반복 가능한 자료형의 요소가 하나라도 참이면 True|

### 리스트 생성

```python
# 1차원 리스트
a = []
b = [1, 2, 3]
c = list() # []
d = list(range(1, 4)) # [1, 2, 3]
e = [i for i in range(1, 4)] # [1, 2, 3]
f = [0] * 3 # [0, 0, 0]


# 2차원 리스트
a = [[1, 2, 3] for _ in range(3)]

b = [1, 2, 3]
c = [b for _ in range(3)]

print(a) # [[1, 2, 3], [1, 2, 3], [1, 2, 3]]
print(c) # [[1, 2, 3], [1, 2, 3], [1, 2, 3]]
```

### 리스트 합치기

```python
a = [1, 2, 3]
b = [4, 5, 6]

print(a + b) # [1, 2, 3, 4, 5, 6]
```

### append

```python
a = [1, 2]

a.append(3)

print(a) # [1, 2, 3]
```

### insert

```python
a = [1, 2, 3]

a.insert(0, 0)

print(a) # [0, 1, 2, 3]
```

### pop

```python
a = [1, 2, 3]

a.pop()

print(a) # [1, 2]

a.pop(0)

print(a) # [2]

print(a.pop()) # 2
```

### remove

```python
a = [1, 2, 3]

a.remove(2)

print(a) # [1, 3]
```

### index

```python
a = [1, 2, 3]

print(a.index(3)) # 2
```

### sum

```python
a = [1, 2, 3]

print(sum(a)) # 6
```

### max

```python
a = [3, 1, 2]

print(max(a)) # 3
```

### min

```python
a = [3, 1, 2]

print(min(a)) # 1
```

### sort

```python
a = [3, 1, 2]

# 오름차순
a.sort()

print(a) # [1, 2, 3]

# 내림차순
a.sort(reverse=True)

print(a) # [3, 2, 1]
```

### sorted

```python
a = [3, 1, 2]

# 오름차순
print(sorted(a)) # [1, 2, 3]

# 내림차순
print(sorted(a), reverse=True) # [3, 2, 1]

```

### clear

```python
a = [1, 2, 3]

a.clear()

print(a) # []
```

### enumerate

```python
a = [1, 2, 3]

for i in enumerate(a):
    print(i) # (0, 1) ... (2, 3)
    print(i[0], i[1]) # 0 1 ... 2 3

for index, value in enumerate(a):
    print(index, value) # 0 1 ... 2 3
```

### all

```python
a = [1, 2, 3]

if all(x > 0 for x in a):
    rint('YES') # YES
else:
    print('NO')

if all(x > 2 for x in a):
    print('YES')
else:
    print('NO') # NO
```

### any

```python
a = [1, 2, 3]

if any(x > 2 for x in a):
    print('YES') # YES
else:
    print('NO')
```

## 함수

```python
def add(a, b):
    return a + b

print(add(1, 3)) # 4
```

## 람다식

```python
add = lambda x : x + 2

print(add(1))

a = [1, 2, 3]

print(list(map(add, a))) # [3, 4, 5]

print(list(map(lambda x : x + 2, a))) # [3, 4, 5]
```

### 람다식을 이용한 튜플 정렬하기

```python
a = [(1, 2), (4, 3)]


# 첫 번째 원소로 오름차순 정렬
a.sort(key = lambda x : x[0])

print(a) # [(1, 2), (4, 3)]


# 첫 번째 원소로 내림차순 정렬
a.sort(key = lambda x : -x[0])

print(a) # [(4, 3), (1, 2)]


# 두 번째 원소로 오름차순 정렬
a.sort(key = lambda x : x[1])

print(a) # [(1, 2), (4, 3)]


# 두 번째 원소로 내림차순 정렬
a.sort(key = lambda x : -x[1])

print(a) # [(4, 3), (1, 2)]
```
