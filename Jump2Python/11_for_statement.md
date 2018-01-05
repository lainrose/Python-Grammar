## for문

### for문의 기본 구조
- - -
```python
for 변수 in 리스트(또는 튜플, 문자열):
    수행할 문장1
    수행할 문장2
    ...
```
### 예제를 이용한 for문 이해하기
- - -
#### 전형적인 for문
```python
>>> test_list = ['one', 'two', 'three']
>>> for i in test_list:
...     print(i)
...
one
two
three
```
#### 다양한 for문의 사용
```python
>>> a = [(1,2), (3,4), (5,6)]
>>> for (first, last) in a:
...     print(first + last)
...
3
7
11
```
위의 예는 a 리스트의 요소값이 튜플이기 때문에 각각의 요소들이 자동으로 (first, last)라는 변수에 대입된다.
### for문과 continue
- - -
```python
# marks2.py
marks = [90, 25, 67, 45, 80]

number = 0
for mark in marks:
    number = number +1
    if mark < 60: continue
    print("%d번 학생 축하합니다. 합격입니다. " % number)
```
### for와 함께 자주 사용하는 range함수
- - -
 range(숫자 개수), range(시작 숫자, 끝 숫자),  range(시작 숫자, 끝 숫자, 숫자 간격)
```python
>>> a = range(10)
>>> a
[0, 1, 2, 3, 4 ,5 ,6 ,7 ,8, 9]
```
### for와 range를 이용한 구구단
- - -
```python
>>> for i in range(2,10):
...     for j in range(1, 10):
...         print i*j,
...     print('')
...
2 4 6 8 10 12 14 16 18
3 6 9 12 15 18 21 24 27
4 8 12 16 20 24 28 32 36
5 10 15 20 25 30 35 40 45
6 12 18 24 30 36 42 48 54
7 14 21 28 35 42 49 56 63
8 16 24 32 40 48 56 64 72
9 18 27 36 45 54 63 72 81
```
### 리스트 안에 for문 포함하기
- - -
리스트 안에 for문을 포함하는 리스트 내포(List comprehension)를 이용하면 좀 더 편리하고 직관적이다.
```python
>>> a = [1,2,3,4]
>>> result = []
>>> for num in a:
...     result.append(num*3)
...
>>> print(result)
[3, 6, 9, 12]
```
```python
>>> result = [num * 3 for num in a]
>>> print(result)
[3, 6, 9, 12]
```
```python
[표현식 for 항목 in 반복가능객체 if 조건]
>>> result = [num * 3 for num in a if num % 2 == 0]
>>> print(result)
[6, 12]
```
```python
[표현식 for 항목1 in 반복가능객체1 if 조건1
        for 항목2 in 반복가능객체2 if 조건2
        ...
        for 항목n in 반복가능객체n if 조건n]
```
```python
"""list comprehension 구구단"""
>>> result = [x*y for x in range(2,10)
...               for y in range(1,10)]
>>> print(result)
```
