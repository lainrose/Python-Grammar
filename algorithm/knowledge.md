## 파이썬 알고리즘 풀면서 배운 유용한 문법
#### print, 은 공백이 생기는데 공백없이 출력하는 방법
```python
>>> import sys
>>> sys.stdout.write()
```
#### list를 for문으로 안돌고 print하는 방법
```python
>>> print '\n'.join(list)
```
#### 여러줄 입력값 for문 없이 받기
```python
>>> [input() for i in range input()]

>>> map(input(), ['']*input())
>>> 5
>>> 1
>>> 2
>>> 3
>>> 4
>>> 5
>>> [1, 2, 3, 4, 5]
```
#### 정렬하기
##### 오름차순 정렬
```python
>>> sorted(list)
```
##### 길이 정렬
```python
>>> sorted(list, key = len)
```
#### 길이, 오름차순 정렬
```python
>>> sorted(list, lambda x:(len(x),x))

>>> sorted(sorted(list), key=len)
```
#### 거꾸로 정렬
```python
>>> sorted(list, reverse=True)

>>> sorted(list)[::-1]
```
#### 지능형 리스트
```python
>>> [i for i in list if 조건...]
```
#### 치환
해당 문자열에서 바꿀문자가 여러개일경우 전부 바꿔준다.
```python
>>> str.replace('바꿀문자','바뀔문자')
```
#### 여러줄에 명령문 쓰기
;를 붙여주면 이어서 쓸 수 있다.
#### 함수 이름 치환해서 쓰기
```python
>>> s = sorted
>>> s(list)
```
