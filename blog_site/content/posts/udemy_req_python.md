---
title: "[AI웹개발 취업캠프/정보통신산업진흥원(NIPA)] Udemy - Python"
date: 2023-08-06
descripton: "A journal on the 코딩 초보자를 위한 파이썬(Python) 입문(Beginner) Udemy Class"
tags:
    - diary
math: true
---

<br><br>

---
# CONTENTS SUMMARY
- [INTRODUCTION](#introduction)
- [리스트, 튜플, 세트, 사전](#리스트-튜플-세트-사전)
- [if, elif, else](#if-elif-else)
- [다양한 입출력 방법](#다양한-입출력-방법)
- [강의 외에 추가로 알게 된 내용](#강의-외에-추가로-알게-된-내용)
- [함수와 lambda](#함수와-lambda)
---

<br><br>

# INTRODUCTION
---
> `Udemy 필수 강의 : 코딩 초보자를 위한 파이썬(Python) 입문(Beginner)`

3주차부터 유데미 강의를 필수로 수강하기 시작했습니다.

이미 파이썬을 어느 정도 사용했기 때문에 기초 내용보다는 자료구조 학습과 유데미 강사님의 코딩 방식에 더 집중하여 학습했습니다.

<br>

# 리스트, 튜플, 세트, 사전
---
<br>

## List vs. Tuple vs. Set

- List `'[]'`
    - 순서 있는(ordered) 요소의 집합이니 index로 각 원소를 접근 가능함
    - 원소를 변경할 수 있음(mutable). 즉, 원소 추가, 삭제 등이 가능함.
- Tuple `'()'`
    - 순서 있지만(ordered) 변경할 수 없는(immutable) 요소의 집합 (즉, 원소 추가 또는 삭제가 불가능)
- Set `'{}'` or `set()`
    - 순서 없는(unordered) 요소의 집합
    - 중복값을 하나로 취급함. 즉, unique elements만 가짐

<br><br><br>

## List (리스트)

### append와 insert의 차이
- `list.append(item)`
    - parameter 1개 - list 끝에 추가할 원소를 추가함
- `list.insert(index, item)`
    - parameter 2개 - 하나는 list에 추가할 원소(item)이고, 다른 하나는 그 원소를 리스트 안에서 어디 넣을지(index)를 가지고 list에 원소를 추가함

즉, append와 insert의 가장 큰 차이는 append의 경우 위치 알려줄 필요 없이 원소를 list 끝에 추가하고, insert의 경우 list 안에 넣을 위치를 알려주며 그 해당 위치에 원소를 추가합니다.

### pop과 remove의 차이
- `list.pop(index)`
    - 인덱스를 가지고 그 해당 인덱스에 있는 원소를 삭제함
    - 삭제한 원소를 return하고 
    - 인덱스를 주지 않으면 default로 리스트의 마지막 원소를 삭제함
- `list.remove(item)`
    - 어떤 변수를 가지고 리스트에서 가장 먼저 동일하게 나오는 원소를 삭제함
    - 값을 return하지 않고 리스트를 직접 변경함
    - item을 넘겨주지 않으면 ValueError가 발생됨

### Other List Functions
- `list.extend()`
- `list.clear()`
- `list.count()`
- `list.sort()`

<br><br><br>

## Tuple (튜플)

Tuple 안에 들어 있는 원소들은 immutable 즉 변경할 수 없으니, 값을 다시 할당하거나 삭제할 수 없습니다.

```python
tuple1 = 2, 4, 6, 8
tuple2 = ('W', 'X', 'Y', 'Z')

tuple1[1] = 3
tuple2[2] = 'A'

# <결과>
# TypeError: 'tuple' object does not support item assignment
```

단, Tuple은 indexing, slicing, addition, multiplication 등 다양한 operation을 할 수 있습니다. Indexing과 Slicing은 리스트와 비슷하고 Addition과 Multiplication은 아래와 같이 할 수 있습니다.

### Tuple Addition

튜플과 튜플을 더하면 문자열 간의 concatenation 방식에서 두 가지 문자열의 문자들을 가지고 하나의 문자열로 합치는 것과 비슷하게 두 가지 튜플들의 원소들을 모두 가지고 하나의 튜플을 만들 수 있습니다.

```python
tuple1 = 2, 4, 6, 8
tuple2 = ('W', 'X', 'Y', 'Z')

new_tuple = tuple1 + tuple2
print(new_tuple)

# <결과>
# (2, 4, 6, 8, 'W', 'X', 'Y', 'Z')
```

### Tuple Multiplication

튜플을 숫자와 곱하면 튜플을 안의 모든 원소들을 순서를 유지하면서 각 원소를 반복할 수 있습니다. 즉, 똑같은 튜플 하나를 가지고 몇번 복제하여 하나의 튜플로 저장할 수 있습니다.

```python
print(tuple1*3)

# <결과>
# (2, 4, 6, 8, 2, 4, 6, 8, 2, 4, 6, 8)
```

<br><br><br>

## Set (세트)

```python
set1 = set([1,2,3,4])
set2 = set([3,4,5,6])
```

위 코드에서 선언된 set 2개를 가지고 교집합(Intersection), 합집합(Union), 차집합(Difference)을 다음과 같이 구하는 방법을 배웠습니다.

- 교집합 (Intersection)
    ```python
    print(set1 | set2) # '|'(OR) 연산자 사용
    print(set1.union(set2)) # union 함수 사용
    ```

- 합집합 (Union)
    ```python
    print(set1 - set2) # `-` 연산자 사용
    print(set1.difference(set2)) # difference 함수 사용
    ```

- 차집합 (Difference)
    ```python
    print(set1 & set2) # '&'(AND) 연산자 사용
    print(set1.intersection(set2)) # intersection 함수 사용
    ```

### Set Functions
- set.add()
- set.remove()
- set.update()

<br><br><br>

## Dictionary (사전)

### fromkeys 함수

```python
list1 = ['a','b','c','d']
tuple1 = 1,2,3,4

dictionary1 = {}.fromkeys(list1)
dictionary2 = {}.fromkeys(list1, 1)
dictionary3 = {}.fromkeys(tuple1)
dictionary4 = {}.fromkeys(tuple1, 1)

# <결과>
# {'a': None, 'b': None, 'c': None, 'd': None}
# {'a': 1, 'b': 1, 'c': 1, 'd': 1}
# {1: None, 2: None, 3: None, 4: None}
# {1: 1, 2: 1, 3: 1, 4: 1}
```

### pop과 popitem의 차이

- `dictionary.pop(item)` -- 주어진 item과 동일한 원소를 삭제함
- `dictionary.popitem()` -- 마지막 키와 값을 tuple로 보여주고 삭제함

```python
my_dict = {'a': 1, 'b': 2, 'c': 3}

# dictionary.pop(item)
value_of_b = my_dict.pop('b')
print(value_of_b)  # 2
print(my_dict)     # {'a': 1, 'c': 3}

# dictionary.popitem()
last_item = my_dict.popitem()
print(last_item)   # ('c', 3)
print(my_dict)     # {'a': 1}
```

NOTE. Python 3.7부터 popitem()은 원소들의 insert한 순서에 따라 마지막으로 추가된 원소를 제거하고 return하지만, 이전 버전에서 popitem()은 어느 원소를 무작위로 뽑아 제거했습니다.


### loop를 활용한 응용

```python
# 모든 값을 출력
for k in dic.keys():
     print("key : " + k)

# 모든 키의 값을 출력
for v in dic.values() :
     print("value : " + str(v))

# 모든 원소를 츨력
for k,v in dic.items():
     print("key : "+k )
     print("value : " + str(v))
```

<br><br><br>

# if, elif, else
---
<br>

해결하고자 하는 문제에 따라 조건이 많을 수 있는데 이런 경우에는 nested if문이나 하나의 if문과 함께 많은 elif문을 퉁해 다양한 조건을 정의할 수 두 가지 방식이 있는 것을 배웠습니다.

<br><br><br>

# 다양한 입출력 방법
---
<br>

## separator, end

print함수 안에서 코마(,)로 나눈 변수들 간에 공백을 삽입하게 되는 것이 기본이지만, 공백 대신에 `separator`를 다른 문자나 문자열로 설정이 가능한 것을 알게 되었습니다.

즉, separator를 따로 설정하지 않으면 default로 다음과 같이 사용되지만,

```python
print("A", "B", sep=" ")
print("A", "B", sep=None)
# A B
```

아래 예시와 같이 문자들간의 공백을 없애거나 숫자 사이에 코마(,)를 넣어 출력할 때 사용할 수 있습니다.

```python
chars = ["one", "two"]
print(chars[0], chars[1], sep="")

# <결과>
# onetwo
```

```python
nums = ["1", "20", "300"]
print(nums[0], nums[1], nums[2], sep=", ")

# <결과>
# 1, 20, 300
```

다음 코드는 문자열과 숫자의 다양한 parameter 조합의 예입니다.

```python
# 문자열
print("List", "Tuple", "Set", sep=" VS ")
# 숫자
print(1, 2, sep=" and ")
# 문자열 + 숫자
print("A", 1, "B", 2, sep="-")

# <결과>
# List VS Tuple VS Set
# 1 and 2
# A-1-B-2
```

NOTE. separator는 코마(,)를 기준으로 parameter를 나누기 때문에 플러스(+)를 사용할 때 separator가 출력되지 않습니다.

```python
print("Hello " + "Where", "are", "you", sep=".")

# <결과>
# Hello Where.are.you
```

`end`는 print함수의 parameter를 모두 출력한 다음에 맨 끝에 문자나 문자열을 넣을 수 있게 해줍니다.

```python
print("What do you want? " + "Apple", "Orange", "Strawberry", sep = " or ", end = "?")

# <결과>
# What do you want? Apple or Orange or Strawberry? 
```

단, end를 사용하면 자동으로 개행 문자 `\n`를 추가하지 않으니 다음과 같은 출력 결과가 나타날 수 있습니다.

```python
print("What do you want? " + "Apple", "Orange", "Strawberry", sep = " or ", end = "?")
print("A", "B", sep=" or ", end="?")
```

따라서, 한 라인이 출력 끝나고 다음 라인이 newline으로 출력되길 바라면 앞에 출력될 라인 end 값에 `\n`을 추가해야 합니다.

```python
print("What do you want? " + "Apple", "Orange", "Strawberry", sep = " or ", end = "?\n")
print("A", "B", sep=" or ", end="?")

# <결과>
# What do you want? Apple or Orange or Strawberry?
# A or B?
```

NOTE. separator와 end는 반드시 숫자가 아닌 문자나 문자열이어야 합니다. 만약 `sep=1` 이나 `end=1`와 같이 코드를 작성하면 다음 에러가 발생합니다.

```python
print("A", "B", sep=1)
# 또는
print("A", "B", sep=" or ", end=1)

# <결과>
# TypeError: end must be None or a string, not int
```

<br><br><br>

## ljust(), rjust()

`ljust()`와 `rjust()`는 왼쪽 정렬과 오른쪽 졍렬을 해주는 함수들입니다.
- `ljust(n)`의 경우 왼쪽 정렬하기 위해 문자열 오른쪽에서 빈칸을 n만큼 추가하고,
- `rjust(n)`의 경우 오른쪽 정렬하기 위해 문자열 왼쪽에서 빈칸을 n만큼 추가합니다

```python
menu = {"Hamburger" : 5000, "Soda" : 1000, "Fries" : 2000}
for item, price in menu.items():
    print(item.ljust(10), str(price).rjust(10))

# <결과>
# Hamburger        5000
# Soda             1000
# Fries            2000
```

<br><br><br>

## zfill()

`zfill(n)` 함수는 문자열 앞에 0을 n만큼 넣어주니, 대기번호 등을 나타내기에 사용될 수 있는 함수입니다.

```python
for num in range(0, 6):
    print("Queue # ", str(num).zfill(5))

# <결과>
# Queue #  00000
# Queue #  00001
# Queue #  00002
# Queue #  00003
# Queue #  00004
# Queue #  00005
```

<br><br><br>

## format

- `{:,}` -- 숫자 3자리마다 코마(,)를 출력해줌
- `{:+,}` -- 양수와 음수에 따라 +/-를 표시하고 3자리마다 코다(,)를 출력해줌
- `{: >n}` -- n만큼 index 차지하여 오른쪽 정렬하여 출력함
- `{: <n}` -- n만큼 index 차지하여 왼쪽 정렬하여 출력함
- `{:+>n}` -- 양수와 음수에 따라 +/-를 표시해서 n만큼 index 차지하고 오른쪽 정렬하여 출력함
- `{:+<n}` -- 양수와 음수에 따라 +/-를 표시해서 n만큼 index 차지하고 왼쪽 정렬하여 출력함
- `{:c>n}` -- c 문자로 공백을 채우면 n만큼 index 차지하고 오른쪽 정렬하여 출력함
- `{:c<n}` -- c 문자로 공백을 채우면서 n만큼 index 차지하고 왼쪽 정렬하여 출력함

```python
print("Salary: {:,} USD" .format(1000000))
print("Property: {:+,} USD" .format(-1000000))
print("{:>5}" .format(10)) # 10이 2자리이니 왼쪽에서 3칸 공백 추가
print("{:<5}" .format(10)) # 10이 2자리이니 오른쪽에서 3칸 공백 추가
print("{:+>5}" .format(10))
print("{:+<5}" .format(10))
print("{:*>5}" .format(10))
print("{:-<5}" .format(10))

# <결과>
# Salary: 1,000,000 USD
# Property: -1,000,000 USD
#   10
# 10   
# ***10
# 10---
```

<br><br><br>

# 함수와 lambda
---
<br>

아래 코드를 보면 함수와 lambda는 비슷한 결과를 나타냅니다.

```python
# 함수
def add(a,b):
    return a+b

print(add(2, 4))

# <결과> 6
```

```python
# lambda
add_lambda = lambda a, b : a+b
print(add_lambda(2, 4))

# <결과> 6
```

lambda는 함수와 비슷한 역할을 inline으로 할 수 있습니다.
단, 파이썬은 함수와 lambda를 서로 다르게 다루고 있습니다.

다른 자료구조와 함께 어떻게 사용하는지 살펴보자면,
다음과 같이 lambda는 list에 직접 추가할 수 있고, 함수는 리스트에 직접 추가할 수 없는 것을 확인할 수 있습니다.

```python
list1 = [lambda a,b :a+b, lambda a,b : a/b]
print(list1[0](2, 4))
print(list1[1](2, 4))

# <결과>
# 6
# 0.5
```

위 코드와 같이 두 가지의 lambda 함수를 list 하나에 같이 넣고 언제든지 접근하여 호출할 수 있는 것을 배웠습니다.

<br><br><br>

# 강의 외에 추가로 알게 된 내용
---
<br>

Python의 공식문서 내용을 좀 더 살펴본 후 새로 알아보게 된 것들을 아래와 같이 정리해봤습니다.

<br>

## Variable Type Annotations / Type Hints

파이썬에서 변수를 선언할 때 변수의 타입은 주어지는 값에 따라 설정됩니다. 즉, 문자열을 받아 선언됐으면 string 타입이고, 정수를 받아 선언됐으면 integer 타입 등처럼 변수의 타입은 assign 받는 값에 따라 정해집니다.

변수를 선언한 다음 타입을 바꾸려면 `float()`, `int()`, `str()` 함수를 사용합니다.

```python
# 정수로 선어
value = 100
# 문자열로 타입 변환
print(str(value))
```

하지만 2015년에 Python 3.5부터는 Variable Type Annotation 또는 Type Hint라는 기능이 추가되었으며 변수를 선언하는 동시에 타입 지정(type annotation)이 가능해졌습니다.

```python
value: float = 12.312345
```

파이썬의 특징 중 하나는 변수의 타입을 지정할 필요없이 코드를 실행만 하면 런타임 중에 변수들이 자동으로 타입이 결정(Type Inference)이 되는 것입니다. 영문으로 글을 작성하듯이 코드의 가독성(readability)이 좋지만, 변수의 타입에 의한 에러가 발생할 때 각 변수의 type을 확인하는 것이 번거롭고  

코드의 작동 흐름을 더 쉽게 이해할 수 있도록 가독성을 높일 수 있고, 다른 언어를 사용하는 개발자와 함께 협업하여 여러 인터페이스를 통합(integration)시킬 때 좋은 기능인 것 같습니다.

NOTE. 좀만 더 테스트해봤더니 처음에 어떤 타입으로 선언했든 상관없이 실행 중간에도 타입이 지정된 변수에다 새로운 값이 할당되면 그 값의 타입에 따라 변수의 타입이 변환됩니다. 또한, 원래처럼 `float()`, `int()`, `str()` 함수를 통해 타입을 변경할 수 있습니다. 

```python
value : float = 3.14159
print(value)
print(type(value))

value = 10
print(value)
print(type(value))

# <결과>
# 3.14159
# <class 'float'>
# 10
# <class 'int'>
```

그러니 Type Annotation은 코드 실행 동안 변수의 타입을 변경할 수 없게 만드는 기능이 아니라 단순히 코드의 가독성을 높이기 위해 변수에 지정한 타입을 알리는 힌트(type hint)를 알리는 기능이라고 알게 되었습니다.

<br>

References
- Official Python Documentation. https://peps.python.org/pep-0526/
- 동적타핑(Dynamic Typing), 정적타이핑(Static Typing). https://seongonion.tistory.com/16


<br><br><br>

## Exponential Scientific Notation

파이썬에서 너무 크거나 작은 숫자를 "과학적 기수법/표기법"으로 표현하는 방식이 있습니다.

아래 코드와 같이 `1.2 x 10^6` 만큼 큰 숫자를 나타낼 때 사용하기가 편리한 것 같습니다.

```python
value = 1.2e6
print(value)

# <결과>
# 1200000.0
```




<br><br><br><br>

#### ——————————————————————————
본 후기는 정보통신산업진흥원(NIPA)에서 주관하는 <AI 서비스 완성! AI+웹개발 취업캠프 - 프론트엔드&백엔드> 과정 학습/프로젝트/과제 기록으로 작성 되었습니다.
#정보통신산업진흥원 #NIPA #AI교육 #프로젝트 #유데미 #IT개발캠프 #개발자부트캠프 #프론트엔드 #백엔드 #AI웹개발취업캠프 #취업캠프 #개발취업캠프