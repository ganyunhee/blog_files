---
title: "[AI웹개발 취업캠프/정보통신산업진흥원(NIPA)] Day 12"
date: 2023-08-01
descripton: "Day 12 in AI+웹개발 취업캠프"
tags:
    - diary
---


## Python - 외부 라이브러리 사용

- 외부 라이브러리 (e.g. numpy, scipy, jupyter 등)을 사용하기 위해 라이브러리를 먼저 설치해야 한다.
- 라이브러리를 설치하려면 패키지 매니저 (e.g. pip, npm 등)을 사용해야 한다.

## `__init.py__` 에 대해

- 파이썬 패키지의 파일 구조를 보면 생성자(constructor) 코드가 들어간 `__init__.py` 라는 파일이 이미 만들어짐.

```
usr > local > lib > python3.11 > site-packages > numpy > __init__.py
```

- 라이브러리를 설치할 때 같이 다운받게 되는 생성자 파일이다.

##  numpy

```python
arr = np.array([1,2,3])
arr
# result : array([1, 2, 3])
```

- 메소드 같은데 객체이다. 메소드처럼 쓰지만 배열 객체를 생성하게 된다.

```python
type(arr)
# result : numpy.ndarray
```

- `arr`의 타입을 보면  `numpy.ndarray` 타입을 가지고 있다고 볼 수가 있다.
- 즉, 파이썬의 표준 라이브러리를 안 쓰고 `numpy`의 라이브러리를 통해 array를 만들었다.

```python
arr = [1, 2, 3]
type(arr)
# list

arr = np.array([1, 2, 3])
type(arr)
# numpy.ndarray
```

- numpy array는 파이썬의 list와 표기가 거의 유사해서  비슷하다고 생각할 수 있지만, 형식이 아예 다르다.
	- python으로 만든 list와 numpy로 만든 array 객체를 각자 정의와 다루는 방식이 다르다. 즉, 서로 아예 다른 객체이다.

## 라이브러리 API 안 외우는 이유

- API가 너무 많기 때문에 다 외우기가 어렵다.
- 외워보려고 해도 numpy와 같은 라이브러리는 numpy를 만든 자의 마음대로 만든 것이니 그 만든 자만큼 능숙하게 사용할 수 없다.
- 라이브러리를 가져올 때 통째로 사용할 필요가 없으니 사용할 것들을 가지고 기능을 충분히 이해해서 사용하면 된다.

## 모든 것들을 코드로 만들 수 없음

- 각 언어는 한계가 있고 JavaScript나 Python만 가지고 다 만들 수 있는 것이 아니다.
- 어떤 언어를 사용해서 어떤 feature를 만들 수 있는지 없는지 스스로 판단하고 추가로 다른 언어 또는 라이브러리를 사용할지 잘 결정해야 한다.
	- e.g. array 생성하고 관리할 때  numpy 사용, image를 편집하고 코드에서 많이 다룰 때 opencv 사용
## numpy array

- 사용하는  이유 : 파이썬의 list와 같은 자료구조를 사용해서 만들면 오래 걸릴 수 있는 array를 쉽게 numpy를 통해 만들 수 있음

```python
arr1 = np.array([1, 2, 3, 4, 5]) # 1 dimension 
arr2 = np.array([[1, 2, 3], [4, 5, 6], [7,8,9]]) # two dimension
```

1D array [arr1] : (x) or (rows) --> (5)
2D array [arr2] : (x, y) or (rows, columns) --> (3, 3)

## numpy random

```python
np.random.rand
```

<br>

## 과제 > pandas 연습 + csv 파일 데이터 가져오기

source: https://github.com/ganyunhee/ai_webdev/tree/main/python/0801_pandas

<br>



<br><br><br><br>

#### ——————————————————————————
본 후기는 정보통신산업진흥원(NIPA)에서 주관하는 <AI 서비스 완성! AI+웹개발 취업캠프 - 프론트엔드&백엔드> 과정 학습/프로젝트/과제 기록으로 작성 되었습니다.
#정보통신산업진흥원 #NIPA #AI교육 #프로젝트 #유데미 #IT개발캠프 #개발자부트캠프 #프론트엔드 #백엔드 #AI웹개발취업캠프 #취업캠프 #개발취업캠프 
