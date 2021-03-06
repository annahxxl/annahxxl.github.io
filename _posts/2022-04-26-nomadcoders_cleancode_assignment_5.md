---
layout: post
title: "📚 노마드 개발자 북클럽 '클린코드' 3기 과제 #05"
subtitle: 🔖 3장. 함수
categories: TIL
tags: [Clean_Code, 코딩, 개발자, 노마드북클럽, 노개북]
---

### 💡 책에서 기억하고 싶은 내용을 적어보세요.

> **함수는 한 가지를 해야 한다. 그 한 가지를 잘 해야 한다. 그 한 가지만을 해야한다.** (p.44)

> 단순히 다른 표현이 아니라 의미 있는 이름으로 다른 함수를 추출할 수 있다면 그 함수는 여러 작업을 하는 셈이다. (p.45)

> 위에서 아래로 코드 읽기: **내려가기** 규칙 (p.46)

> 일반적으로 나는 switch 문을 단 한번만 참아준다. 다형적 객체를 생성하는 코드 안에서다. (p.49)

> 이름이 길어도 괜찮다. 겁먹을 필요없다. 길고 서술적인 이름이 짧고 어려운 이름보다 좋다. 길고 서술적인 이름이 길고 서술적인 주석보다 좋다. (p.49)

> 함수에서 이상적인 이수 개수는 0개(무항)다. 다음은 1개(단항)고, 다음은 2개(이항)다. 3개(삼항)은 가능한 피하는 편이 좋다. 4개 이상(다항)은 특별한 이유가 필요하다. 특별한 이유가 있어도 사용하면 안된다.

> **오류 코드보다 예외를 사용하라!** (p.57)

> Try/Catch 블록 뽑아내기 (p.58)

> 어쩌면 중복은 소프트웨어에서 모든 악의 근원이다. (p.60)

### 💭 오늘 읽은 소감은? 떠오르는 생각을 가볍게 적어보세요.

좋은 함수를 작성하는 방법에 관련하여 정말 자세히 전달해 주고 있다. 그래서 나는 또 반성해야 할 코드들이 스쳐지나 갔다..🥲<br> 그리고 항상 함수들을 올라가기/내려가기 방식 중 어떠한 방법으로 작성해야 할지 고민이었는데, 이 책에서 답을 얻을 수 있었다.<br>
추가로 오늘 내용 중 제일 인상 깊었던 점은 **_Try/Catch 블록 뽑아내기_** 부분이었는데, 오류 처리도 하나의 개별적인 동작이라는 것을 그동안 생각을 못 했었다.<br>그런데 정상 동작과 오류 처리 동작을 분리하여 각각 하나의 기능을 하는 함수로 뽑아내는 것을 보고 아차 싶었다! 오늘도 새로 배웠다.

### 🤔 궁금한 내용이 있거나, 잘 이해되지 않는 내용이 있다면 적어보세요.

- 추상화 수준 (p.45)
