---
layout: post
title: '[Python] collections 모듈 - 효율적인 데이터 구조'
date: 2024-06-15 22:30:00
categories: [Python]
tags: [namedtuple, deque, Counter, defaultdict, ChainMap]
toc: true
image:
  path: assets/img/for_post/240615-t.jpg
img_path: /assets/img/for_post/
description: 리스트의 스택(Stack) 및 큐(Queue)로의 활용, 딕셔너리의 순서 및 기본값 처리 등을 보완하여 더 강력하고 유연한 데이터 구조를 제공하는 collections 모듈을 알아보자.
---

파이썬은 리스트, 튜플, 딕셔너리 등의 기본 자료형을 제공하지만, 특정 상황에서는 비효율적이거나, 원하는 기능을 완벽히 지원하지 못하는 경우가 있다. 

> 리스트의 스택(Stack) 및 큐(Queue)로의 활용, 딕셔너리의 순서 및 기본값 처리 등을 보완하여 더 강력하고 유연한 데이터 구조를 제공하는 `collections` 모듈을 알아보자.
{: .prompt-info}

---
## collections

`collections` 모듈은 기본 자료형의 확장된 버전을 포함하고 있고, 이를 통해 코드를 더 직관적이고, 효율적으로 작성할 수 있도록 돕는다.

`collections` 모듈의 주요 컴포넌트를 하나씩 알아보자.

---
### 1. namedtuple

> 이름이 있는 필드가 있는 튜플
{: .prompt-tip}

**`namedtuple`**은 **이름을 지정하지 못하는 튜플의 단점을 보완**하고자 구현되었으며, 데이터의 구조에 의미를 부여하고 싶을 때 활용한다.

또한, 기존 튜플을 그대로 상속받으므로 불변성 등 튜플이 가진 장점들이 모두 유지된다.

~~~python
from collections import namedtuple

# 사용 예시: 2D 좌표를 표현할 때
Point = namedtuple('Point', ['x', 'y'])

p = Point(10, 20)
print(f"X 좌표: {p.x}, Y 좌표: {p.y}")
# 출력: X 좌표: 10, Y 좌표: 20

# 불변성 확인: p.x = 30  # 오류 발생
~~~

위 예시에서는 좌표를 나타내는 튜플을 생성하여 더 직관적인 코드를 구현할 수 있다.

---
### 2. deque

> 양쪽 끝에서 빠르게 요소를 추가/제거할 수 있는 큐
{: .prompt-tip}

기존 리스트는 한쪽 끝에서 삽입, 삭제를 수행할 수 있는데, **양쪽 끝에서는 처리가 어렵다는 문제점을 극복**하고자 **`deque`**가 구현되었다.

따라서, 양쪽 끝에서 O(1)의 시간 복잡도로 삽입, 삭제를 처리할 수 있다.

삽입과 삭제가 빈번히 일어나는 큐(Queue)나 스택(Stack), 또는 슬라이딩 윈도우와 같은 알고리즘을 구현할 때 유용하다.

~~~python
from collections import deque

# 최대 길이 지정 가능
d = deque(maxlen=10)

# 요소 추가 및 제거
d.append("A") # ["A"]
d.append("B") # ["A", "B"]
d.appendleft("C") # ["C", "A", "B"]
d.pop() # "B", ["C", "A"]
d.popleft() # "C", ["A"]
d.extend(["D", "E", "F"]) # ["A", "D", "E", "F"]
d.popleft() # ["D", "E", "F"]
d.clear() # []
d.extendleft([1,2,3,4,5]) # [5, 4, 3, 2, 1]
d.rotate(2) # [2, 1, 5, 4, 3]
d.rotate(-1) # [1, 5, 4, 3, 2]
d.reverse() # [2, 3, 4, 5, 1]
d.remove(1) # [2, 3, 4, 5]
d.index(4) # 2
~~~

---
### 3. Counter

> 요소의 개수를 셀 수 있는 딕셔너리
{: .prompt-tip}

**`Counter`**는 **객체의 빈도를 쉽게 셀 수 있는 딕셔너리**로, 데이터의 빈도수 계산에 최적화되어 있다.

자주 발생하는 요소를 찾고자 할 때, **특히 텍스트 분석에서 단어 빈도를 계산할 때** 많이 활용된다.

~~~python
from collections import Counter

a = "aaaabbcccd"
counter = Counter(a) # Counter({'a': 4, 'c': 3, 'b': 2, 'd': 1})
print(counter.most_common(2)) # [{'a': 4, 'c': 3}]
print(counter["a"]) # 4 
~~~

---
### 4. defaultdict

> 기본값을 자동으로 생성하는 딕셔너리
{: .prompt-tip}

기존 딕셔너리는 존재하지 않는 키를 참조할 때 'KeyError'가 발생한다.

**`defaultdict`**는 **키가 존재하지 않을 때 기본값을 자동으로 설정할 수 있으며**, 다중 값을 처리하는 딕셔너리를 구성하거나, 코드에서 키를 확인하고 처리하는 과정을 생략할 때 활용된다.

~~~python
from collections import defaultdict

# 사용 예시: 학생별 과목 성적 관리
grades = defaultdict(list)
grades['Alice'].append(85)
grades['Bob'].append(90)
grades['Alice'].append(95)

print("성적:", grades)
# 출력: defaultdict(<class 'list'>, {'Alice': [85, 95], 'Bob': [90]})
~~~

위 예시에서의 학생별 성적 관리 딕셔너리에서 키가 존재하지 않을 때 자동으로 리스트가 생성되어 편리하게 성적을 관리할 수 있다.

---
### 5. ChainMap

> 여러 딕셔너리를 하나의 맵으로 다룰 수 있는 구조
{: .prompt-tip}

**`ChainMap`**은 **여러 딕셔너리를 논리적으로 병합하여 하나의 맵처럼 다룰 수 있는 구조**를 제공한다.

서로 다른 딕셔너리의 값을 통합적으로 접근할 때, 기본값과 사용자 정의 값을 함께 처리할 때 주로 활용된다.

~~~python
from collections import ChainMap

# 사용 예시: 기본 설정과 사용자 설정 병합
default_config = {'theme': 'light', 'show_logs': True}
user_config = {'theme': 'dark'}

config = ChainMap(user_config, default_config)
print("최종 설정:", config['theme'])  # 사용자 설정이 우선
print("로그 표시 여부:", config['show_logs'])  # 기본 설정 사용
~~~

위 예시에서는 기본 설정과 사용자 설정을 병합하여 최종 설정을 관리하도록 사용되며, 사용자 설정이 우선되도록 설정된다.

---
### Reference

1. [파이썬 공식 문서 - collections](https://docs.python.org/ko/3/library/collections.html)
2. [Advanced Python 유튜브 - collections](https://youtu.be/UdcPhnNjSEw?si=nC6QQHzVCzhZDdcL)
