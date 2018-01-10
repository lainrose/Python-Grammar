## 파이썬 알고리즘 풀면서 배운 유용한 문법
#### 입력받기
```python
>>> import sys
>>> sys.stdin.readline()
>>> ...
>>> input()
>>> ...
>>> raw_input()
>>> ...
```
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

>>> map(raw_input, ['']*input())
>>> 5
>>> 1
>>> 2
>>> 3
>>> 4
>>> 5
>>> [1, 2, 3, 4, 5]

>>> map(int,sys.stdin)

>>> [sys.stdin.readline() for _ in '-'*input()]
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
#### 숫자앞에 0붙여서 출력하기
```python
>>> a = [1,10,100]
>>> for i in a:
>>>     print '%02d'%(i)
>>> 01
>>> 10
>>> 100
```
#### dict 정렬
```python
>>> a = {2:1,1:2,3:4,7:1}
>>> print sorted(a.items(), key=lambda x:x[0])
>>> [(1,2),(2,1),(3,4),(7,1)]
```
#### dict를 tuple of list 변환 후 reduce
```python
reduce(lambda sum,(x,y):sum + x*y, a.items(),0)
```
#### sum()함수 내장
```python
>>> sum(1,2)
>>> 3
```
#### sorted 할 대상이 엄청 크지 않을경우
```python
>>> import sys
>>> print '\n'.join(sorted(map(str,sys.stdin)))
>>> print '\n'.join(sorted([sys.stdin.readline() for _ in '-'*input()]))
```
#### 정렬한 후에 카운팅값이 1개인지 2개이상인지 확인
```python
>>> 1%len(array)
# 개수가 2개이면 무조건 1뜨기 때문에 array[1]이고
# 개수가 1개이면 1%1 = 0되서 무조건 array[0]
```
#### 해당 이터레이블한 객체안에 원하는 요소가 모두있거나 그 중 1개라도 있는지 확인
```python
>>> items = 'a', 'b', 'c'
>>>if all(i in L for i in items):
>>>if any(i in L for i in items):
 ```python
