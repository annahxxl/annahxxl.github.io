---
layout: post
title: "[모두의 알고리즘] 셋째 마당: 탐색과 정렬"
subtitle: 책 "모두의 알고리즘"을 통한 학습 내용 정리 ✍
categories: Algorithm
tags: [모두의_알고리즘, 선택_정렬, 삽입_정렬, 병합_정렬, 퀵_정렬, 거품_정렬, 이분_탐색]
---

### [https://visualgo.net/en](https://visualgo.net/en)

- 애니메이션을 통한 데이터 구조 및 알고리즘을 시각화해서 보여주는 사이트입니다.
- 아래의 시각화 GIF들은 모두 해당 사이트에서 확인해 볼 수 있습니다 :)

### 정렬

#### 선택 정렬

1. 주어진 데이터 중 최솟값을 찾는다.
2. 최솟값을 주어진 데이터의 맨 앞에 위치한 값과 교체한다.
3. 맨 앞에 위치한 값을 제외한 나머지 데이터를 위 작업을 반복한다.

- 시간 복잡도: O(n**2)

![selection](https://user-images.githubusercontent.com/76666857/156442780-495d34c7-557d-48dc-8c26-deef5baf983a.gif)

#### 삽입 정렬

1. 두 번째 인덱스부터 시작한다.
2. 현재 인덱스(key)앞에 있는 데이터부터 key보다 작은 데이터(B)를 찾는다.
3. B가 존재한다면 key를 B 뒤에 삽입하고, 존재하지 않는다면 제일 작은 데이터이므로 맨 앞에 삽입한다.

- 시간 복잡도: O(n**2)

![insertion](https://user-images.githubusercontent.com/76666857/156444987-da3b256a-637a-49f8-9dad-66648259f619.gif)

#### 병합 정렬

1. 분할 정복을 이용한다.
2. 주어진 데이터를 비슷한 크기의 두 부분으로 나눈다.
3. 재귀 호출을 이용하여 위 작업을 반복한다.
4. 정렬된 부분 데이터들을 하나의 데이터로 합친다.

- 시간 복잡도: O(n*logn)

![merge](https://user-images.githubusercontent.com/76666857/156454159-4632d1c1-ee5e-4326-9152-745083e2bf73.gif)

#### 퀵 정렬

1. 기준점(pivot)을 정해서 기준점보다 작은 데이터는 왼쪽, 큰 데이터는 오른쪽으로 모은다.
2. 나누어진 왼쪽과 오른쪽을 재귀 호출을 이용하여 위 작업을 반복한다.
3. 정렬된 부분 데이터들을 하나의 데이터(왼쪽 + 기준점 + 오른쪽)로 합친다.

- 시간 복잡도: O(n*logn)

![quick](https://user-images.githubusercontent.com/76666857/156458755-a6a31ecd-f4eb-44a6-88c3-eca6db0f6c2f.gif)

#### 거품 정렬

1. 두 인접한 데이터를 비교한다.
2. 앞에 있는 데이터가 뒤에 있는 데이터보다 크면, 자리를 바꾼다.

- 시간 복잡도: O(n**2)

![bubble](https://user-images.githubusercontent.com/76666857/156458775-788f11ca-f96e-4992-ad7a-cf975c89997a.gif)

### 탐색

#### 이분 탐색

1. 정렬된 데이터를 기준으로 한다.
2. 중간 위치를 찾는다.
3. 찾는 값과 중간 위치 값을 비교한다.
4. 찾는 값이 중간 위치 값보다 작다면 중간 위치의 왼쪽을, 크다면 중간 위치의 오른쪽을 대상으로 다시 위 작업을 반복한다.
   
- 시간 복잡도: O(logn)

### 연습 문제

#### 7-1. 찾는 값이 나오는 모든 위치를 리스트로 돌려주는 탐색 알고리즘 만들기

```python
# O(n)
def solution(arr, x):
    result = []
    for index, value in enumerate(arr):
        if value == x:
            result.append(index)
    return result
```

#### 7-3. 아래와 같이 학생 번호와 이름이 리스트로 주어졌을 때 학생 번호를 입력하면 학생 번호에 해당하는 이름을 순차(선형) 탐색으로 찾아 돌려주는 함수 만들기

- 해당하는 학생 번호가 없다면 물음표(?) 돌려주기

```python
# 학생 번호, 학생 이름이 담긴 리스트
stu_no = [39, 14, 67, 105]
stu_name = ["Justin", "John", "Mike", "Summer"]
****
# 입력
num = int(input())

# O(n)
def solution(stu_no, stu_name, num):
    for index, value in enumerate(stu_no):
        if value == num:
            return stu_name[index]
    return "?"

# 출력
print(solution(stu_no, stu_name, num))
```

#### 8-1. 일반적인 선택 정렬 알고리즘을 사용해서 리스트 [2, 4, 5, 1, 3]을 정렬하는 과정을 적어보기

```python
# O(n**2)
def selection_sort(arr):
    n = len(arr)
    for i in range(0, n - 1): # 0 부터 n-2 까지 반복
        min_idx = i # i 번 위치부터 끝까지 자료 값 중 최솟값의 위치 저장
        for j in range(i + 1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i] # 찾은 최솟값을 i 번 위치로 이동
    return arr

# 출력
print(selection_sort([2, 4, 5, 1, 3]))
```

#### 8-2. 8-1번에서의 오름차순 정렬을 내림차순 정렬로 바꾸기

```python
# O(n**2)
def selection_sort(arr):
    n = len(arr)
    for i in range(0, n - 1):
        max_idx = i
        for j in range(i + 1, n):
            if arr[j] > arr[max_idx]:
                max_idx = j
        arr[i], arr[max_idx] = arr[max_idx], arr[i]
    return arr

# 출력
print(selection_sort([2, 4, 5, 1, 3]))
```

#### 9-1. 일반적인 삽입 정렬 알고리즘을 사용해서 리스트 [2, 4, 5, 1, 3]을 정렬하는 과정을 적어보기

```python
# O(n**2)
def insertion_sort(arr):
    n = len(arr)
    for i in range(1, n): # 1 부터 n-1 까지 반복
        key = arr[i] # 현재 i 번 위치에 있는 값 저장
        j = i - 1 # i 의 바로 왼쪽 위치 저장
        while (j >= 0) and (arr[j] > key): # key 값이 비교 값보다 클 때 동안 반복
            # 아직 key 값이 비교 값보다 작으므로
            arr[j + 1] = arr[j] # 삽입할 공간이 생기도록 값을 오른쪽으로 한 칸 이동
            j -= 1
        arr[j + 1] = key # 찾은 삽입 위치에 key 값 저장
    return arr

# 출력
print(insertion_sort([2, 4, 5, 1, 3]))
```

#### 9-2. 9-1번에서의 오름차순 정렬을 내림차순 정렬로 바꾸기

```python
# O(n**2)
def insertion_sort(arr):
    n = len(arr)
    for i in range(1, n):
        key = arr[i]
        j = i - 1
        while (j >= 0) and (arr[j] < key):
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr

# 출력
print(insertion_sort([2, 4, 5, 1, 3]))
```

#### 10-1. 일반적인 병합 정렬 알고리즘을 사용해서 리스트 [2, 4, 5, 1, 3]을 내림차순으로 정렬하는 과정을 적어보기

```python
# O(n*logn)
def merge_sort(arr):
    n = len(arr)

    # 정렬할 리스트의 자료 개수가 한 개 이하이면 정렬할 필요 없음 (재귀 종료 조건)
    if n <= 1:
        return arr

    # 두 그룹으로 나누는 기준
    mid = n // 2
    g1 = arr[:mid]
    g2 = arr[mid:]

    # 재귀 호출로 각각의 그룹 정렬
    merge_sort(g1)
    merge_sort(g2)

    # 두 그룹을 하나로 병합
    p1 = 0
    p2 = 0
    i = 0
    while (p1 < len(g1)) and (p2 < len(g2)):
        if g1[p1] > g2[p2]:
            arr[i] = g1[p1]
            p1 += 1
            i += 1
        else:
            arr[i] = g2[p2]
            p2 += 1
            i += 1
    
    # 아직 남아 있는 자료들을 최종 리스트 뒤쪽에 추가
    while p1 < len(g1):
        arr[i] = g1[p1]
        p1 += 1
        i += 1
    while p2 < len(g2):
        arr[i] = g2[p2]
        p2 += 1
        i += 1

    return arr

# 출력
print(merge_sort([2, 4, 5, 1, 3]))
```

#### 11-1. 수 많은 정렬 알고리즘 중 하나인 거품 정렬을 줄 서기로 비유한 과정을 읽고, 리스트 [2, 4, 5, 1, 3]을 정렬하는 과정을 적어보기

1. 일단 학생들을 아무렇게나 일렬로 줄을 세웁니다.
2. 선생님이 맨 앞에서부터 뒤로 이동하면서 이웃한 앞뒤 학생의 키를 서로 비교합니다. 앞에 있는 학생의 키가 바로 뒤에 있는 학생보다 크면 두 학생의 자리를 서로 바꿉니다.
3. 선생님은 계속 뒤로 이동하면서 이웃한 앞뒤 학생의 키를 비교해서 필요하면 앞뒤 학생의 위치를 서로 바꿉니다.
4. 모든 학생이 키 순서대로 줄을 설 때까지 이 과정을 반복합니다(줄의 끝까지 확인하는 동안 자리를 바꾼 적이 한 번도 없으면 모든 학생이 순서대로 줄을 선 것입니다).

```python
# O(n**2)
def bubble_sort(arr):
    n = len(arr)
    while True:
        changed = False # 자료를 앞뒤로 바꾸었는지 체크
        for i in range(0, n - 1):
            if arr[i] > arr[i + 1]:
                arr[i], arr[i + 1] = arr[i + 1], arr[i]
                changed = True
        if not changed: # 바뀐 적이 없다면 정렬이 완성된 것이므로 종료
            return arr

print(bubble_sort([2, 4, 5, 1, 3]))
```

#### 12-1. 다음 과정을 참고하여 재귀 호출을 사용한 이분 탐색 알고리즘 만들기

1. 주어진 탐색 대상이 비어 있다면 탐색할 필요가 없습니다(종료 조건).
2. 찾는 값과 주어진 탐색 대장의 중간 위치 값을 비교합니다.
3. 찾는 값과 중간 위치 값이 같다면 결과값으로 중간 위치 값을 돌려줍니다.
4. 찾는 값이 중간 위치 값보다 크다면 중간 위치의 오른쪽을 대상으로 이분 탐색 함수를 재귀 호출합니다.
5. 찾는 값이 중간 위치 값보다 작다면 중간 위치의 왼쪽을 대상으로 이분 탐색 함수를 재귀 호출합니다.
   
```python
# O(logn)
def binary_search(arr, target, start, end):
    # 남은 탐색 범위가 비었으면 종료 (재귀 종료 조건)
    if start > end:
        return -1
    
    mid = (start + end) // 2
    if target == arr[mid]:
        return mid
    elif target > arr[mid]:
        return binary_search(arr, target, mid + 1, end)
    else:
        return binary_search(arr, target, start, mid - 1)

    # 찾지 못했을 경우
    return -1

# 출력
arr = [1, 2, 3, 4, 5]
print(binary_search(arr, 4, 0, len(arr) - 1)) # 이분 탐색은 정렬된 리스트를 기준으로 한다.
```