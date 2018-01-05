## 내장 함수

### abs
- - -
abs(x)는 어떤 숫자를 입력으로 받았을 때, 그 숫자의 절대값을 돌려주는 함수이다.
```python
>>> abs(3)
3
>>> abs(-3)
3
>>> abs(-1.2)
1.2
```
### all
- - -
all(x)은 반복 가능한(iterable) 자료형 x를 입력 인수로 받으며, 이 x가 모두 참이면 True, 거짓이 하나라도 있 으면 False를 리턴한다.

(※ 반복 가능한 자료형이란 for문으로 그 값을 출력할 수 있는 것을 의미한다. 리스트, 튜플, 문자열, 딕셔너리, 집합 등이 있다.)
```python
>>> all([1, 2, 3])
True

>>> all([1, 2, 3, 0])
False
```
### any
- - -
any(x)는 x 중 하나라도 참이 있을 경우 True를 리턴하고, x가 모두 거짓일 경우에만 False를 리턴한다. all(x)의 반대 경우라고 할 수 있다.
```python
>>> any([1, 2, 3, 0])
True
>>> any([0, ""])
False
```
### chr
- - -
chr(i)는 아스키(ASCII) 코드값을 입력으로 받아 그 코드에 해당하는 문자를 출력하는 함수이다.
```python
>>> chr(97)
'a'
>>> chr(48)
'0'
```
### dir
- - -
dir은 객체가 자체적으로 가지고 있는 변수나 함수를 보여 준다.
```python
>>> dir([1, 2, 3])
['append', 'count', 'extend', 'index', 'insert', 'pop',...]
>>> dir({'1':'a'})
['clear', 'copy', 'get', 'has_key', 'items', 'keys',...]
```
### divmod
- - -
divmod(a, b)는 2개의 숫자를 입력으로 받는다. 그리고 a를 b로 나눈 몫과 나머지를 튜플 형태로 리턴하는 함수이다.
```python
>>> divmod(7, 3)
(2, 1)
>>> divmod(1.3, 0.2)
(6.0, 0.099999999999999978)
```
### enumerate
- - -
이 함수는 순서가 있는 자료형(리스트, 튜플, 문자열)을 입력으로 받아 인덱스 값을 포함하는 enumerate 객체를 리턴한다.
```python
>>> for i, name in enumerate(['body', 'foo', 'bar']):
...     print i, name
...
0 body
1 foo
2 bar
```
### eval
- - -
eval(expression)은 실행 가능한 문자열(1+2, 'hi' + 'a' 같은 것)을 입력으로 받아 문자열을 실행한 결과값을 리턴하는 함수이다.
```python
>>> myStr = '{name: "webisfree", domain: "dotcom"}'
>>> myDict = eval(myStr)
>>>
>>> print myStr['name']
```
### filter
filter 함수는 첫 번째 인수로 함수 이름을, 두 번째 인수로 그 함수에 차례로 들어갈 반복 가능한 자료형을 받는다.

그리고 두 번째 인수인 반복 가능한 자료형 요소들이 첫 번째 인수인 함수에 입력되었을 때 리턴값이 참인 것만 묶어서(걸러내서) 돌려준다.
```python
#filter1.py
def positive(x):
    return x > 0

print(list(filter(positive, [1, -3, 2, 0, -5, 6])))
```
### raw_input
- - -
input([prompt])은 사용자 입력을 받는 함수이다.
```python>>> a = input()
hi
>>> a
'hi'
>>> b = input("Enter: ")
Enter: hi
```
### lambda
- - -
함수를 한줄로 간결하게 만들 때 사용한다.

lambda 인수1, 인수2, ... : 인수를 이용한 표현식
```python>>> sum = lambda a, b: a+b
>>> sum(3,4)
7
```
```python
>>> myList = [lambda a,b:a+b, lambda a,b:a*b]
>>> myList
[at 0x811eb2c>, at 0x811eb64>]
```
```python
>>> myList[0]
at 0x811eb2c>
>>> myList[0](3,4)
7
```
```python
>>> myList[1](3,4)
12
```
### len
- - -
len(s)은 입력값 s의 길이(요소의 전체 개수)를 리턴하는 함수이다.
```python
>>> len("python")
6
>>> len([1,2,3])
3
>>> len((1, 'a'))
2
```
### list
- - -
list(s)는 반복 가능한 자료형 s를 입력받아 리스트로 만들어 리턴하는 함수이다.
```python
>>> list("python")
['p', 'y', 't', 'h', 'o', 'n']
>>> list((1,2,3))
[1, 2, 3]
```
### map
- - -
map(f, iterable)은 함수(f)와 반복 가능한(iterable) 자료형을 입력으로 받는다.

map은 입력받은 자료형의 각 요소가 함수 f에 의해 수행된 결과를 묶어서 리턴하는 함수이다.
```python
>>> def two_times(x): return x*2
...
>>> list(map(two_times, [1, 2, 3, 4]))
[2, 4, 6, 8]
```
lambda로 더 간결하게...
```python
>>> list(map(lambda a: a*2, [1, 2, 3, 4]))
[2, 4, 6, 8]
```
### ord
- - -
ord(c)는 문자의 아스키 코드값을 리턴하는 함수이다.

(※ ord 함수는 chr 함수와 반대이다.)
```python
>>> ord('a')
97
>>> ord('0')
48
```
### pow
- - -
pow(x, y)는 x의 y 제곱한 결과값을 리턴하는 함수이다.
```python
>>> pow(2, 4)
16
>>> pow(3, 3)
27
```
### sorted
- - -
sorted(iterable) 함수는 입력값을 정렬한 후 그 결과를 리스트로 리턴하는 함수이다.
```python
>>> sorted([3, 1, 2])
[1, 2, 3]
>>> sorted(['a', 'c', 'b'])
['a', 'b', 'c']
>>> sorted("zero")
['e', 'o', 'r', 'z']
>>> sorted((3, 2, 1))
[1, 2, 3]
```
리스트 자료형에도 sort라는 함수가 있다.
 하지만 리스트 자료형의 sort 함수는 리스트 객체 그 자체를 정렬만 할 뿐 정렬된 결과를 리턴하지는 않는다.

### zip
- - -
zip(iterable*)은 동일한 개수로 이루어진 자료형을 묶어 주는 역할을 하는 함수이다.
```python
>>> list(zip([1, 2, 3], [4, 5, 6]))
[(1, 4), (2, 5), (3, 6)]
>>> list(zip([1, 2, 3], [4, 5, 6], [7, 8, 9]))
[(1, 4, 7), (2, 5, 8), (3, 6, 9)]
>>> list(zip("abc", "def"))
[('a', 'd'), ('b', 'e'), ('c', 'f')]
```