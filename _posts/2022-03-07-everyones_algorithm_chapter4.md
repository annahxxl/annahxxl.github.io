---
layout: post
title: "[모두의 알고리즘] 넷째 마당: 자료 구조"
subtitle: 책 "모두의 알고리즘"을 통한 학습 내용 정리 ✍
categories: Algorithm
tags: [모두의_알고리즘, 큐, 스택, 딕셔너리, 그래프]
---

### 큐(Queue)

- **F**irst **I**n **F**isrt **O**ut
- 자료 한 개를 집어넣는 동작을 enqueue, 꺼내는 동작을 deque라고 한다.
- 파이썬 프로그래밍일 경우, 큐를 리스트로 구현할 시 자료를 한 개 꺼낼 때 남은 자료를 모두 한 칸씩 당겨주는 처리가 필요하여 효율성이 떨어질 수 있다. 이는 collections 모듈에 있는 deque를 이용하여 개선할 수 있다.

### 스택(Stack)

- **L**ast **I**n **F**irst **O**ut
- 자료 한 개를 집어넣는 동작을 push, 꺼내는 동작을 pop이라고 한다.

### 딕셔너리(Dictionary)

- 정보를 찾는 기준이 되는 키(key)와 그 키에 연결된 값(value)의 대응 관계를 저장하는 자료 구조이다.

```python
dic = {'Justin': 13, 'John': 10, 'Mike': 8}
```

### 그래프(Graph)

- 정점(vertex)과 간선(edge)로 이루어져 있다.
- 정점에 연결된 정점들을 다시 큐에 추가하면서 그래프를 탐색하는 방법을 '너비 우선 탐색(Breadth First Search)'이라고 한다.

### 연습 문제

#### 13-1. 큐와 스택을 이용하지 않고 문장의 앞뒤를 차례로 비교하면서 각 문자가 같은지 확인하는 방법으로 회문인지 아닌지 판단하는 알고리즘 만들기

```python
# O(n)
def solution(s):
    i = 0
    j = len(s) - 1

    while i < j:
        if s[i].isalpha() == False:
            i += 1
        elif s[j].isalpha() == False:
            j -= 1
        elif s[i].upper() != s[j].upper():
            return False
        else:
            i += 1
            j -= 1
    
    return True

# 출력
print(solution('Wow')) # True
print(solution("Madam, I'm Adam.")) # True
print(solution('Madam, I am Adam.')) # False
```

#### 14-1. 학생 번호와 이름이 주어졌을 때 학생 번호를 입력하면 그 학생 번호에 해당하는 이름을 돌려주고, 해당하는 학생 번호가 없으면 물음표를 돌려주는 프로그램을 딕셔너리를 이용하여 작성해 보기

```python
students = {
    39: 'Justin',
    14: 'John',
    67: 'Mike',
    105: 'Summer'
}

def solution(students, target):
    if target in students:
        return students[target]
    else:
        return '?'

# 출력
print(solution(students, 105)) # Summer
print(solution(students, 777)) # ?
```

#### 15-1. 그래프 탐색 알고리즘을 이용하여 다음 그래프를 탐색하는 프로그램을 만들어 보기

- 시작 정점은 1이다.

```python
graph = {
    1: [2, 3],
    2: [1, 4, 5],
    3: [1],
    4: [2],
    5: [2]
}

def bfs(graph, start):
    q = []
    visited = set()

    q.append(start)
    visited.add(start)

    while q:
        node = q.pop(0)
        print(node)

        for x in graph[node]:
            if x not in visited:
                q.append(x)
                visitied.add(x)

bfs(graph, 1)
```