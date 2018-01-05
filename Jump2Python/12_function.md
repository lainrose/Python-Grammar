## 함수

### 파이썬 함수의 구조
- - -
```python
def 함수명(입력 인수):
    <수행할 문장1>
    <수행할 문장2>
    ...
```
```python
"""이 함수의 이름(함수명)은 sum이고 입력 인수로 2개의 값을 받으며 결과값은 2개의 입력값을 더한 값이다."""
def sum(a, b):
    return a + b
```
#### 일반적인 함수
```python
def sum(a, b):
    result = a + b
    return result
```
#### 입력값이 없는 함수
```python
>>> def say():
...     return 'Hi'
...
>>> print say()
Hi
```
#### 결과값이 없는 함수
```python
>>> def sum(a, b):
...     print("%d, %d의 합은 %d입니다." % (a, b, a+b))
...
>>> sum(3, 4)
3, 4의 합은 7입니다.
```
#### 입력값도 결과값도 없는 함수
```python
>>> def say():
...     print('Hi')
...
>>> say()
Hi
```
### 입력값이 몇 개가 될지 모를 때
- - -
```python
def 함수이름(*입력변수):
    <수행할 문장>
    ...
```
#### 여러 개의 입력값을 받는 함수 만들기
입력 변수명 앞에 *을 붙이면 입력값들을 전부 모아서 튜플로 만들어 준다.
```python
>>> def sum_many(*args):
...     sum = 0
...     for i in args:
...         sum = sum + i
...     return sum
...
>>>
```

### 함수의 결과값은 언제나 하나이다
- - -
```python
>>> def sum_and_mul(a,b):
...     return a+b, a*b
>>> result = sum_and_mul(3,4)
result = (7, 12)
```
sum_and_mul 함수의 결과값 a+b와 a*b는 튜플값 하나인 (a+b, a*b)로 돌려준다.

만약 이 하나의 튜플값을 2개의 결과값처럼 받고 싶다면 다음과 같이 함수를 호출하면 된다.
```python
>>> sum, mul = sum_and_mul(3, 4)
>>> sum
>>> 7
>>> mul
>>> 12
```
> return의 또 다른 쓰임새
>
> 어떤 특별한 상황이 되면 함수를 빠져나가고자 할 때는 return을 단독으로 써서 함수를 즉시 빠져나갈 수 있다.
```python
>>> def say_nick(nick):
...     if nick == "바보":
...         return
...     print("나의 별명은 %s 입니다." % nick)
...
>>> say_nick('야호')
나의 별명은 야호입니다.
>>> say_nick('바보')
>>>
```
### 입력 인수에 초깃값 미리 설정하기
- - -
```python
def say_myself(name, old, man=True):
    ...
```
#### 함수 입력 인수에 초깃값을 설정할 때 주의할 사항
초기화시키고 싶은 입력 변수는 항상 뒤쪽에 위치시키는 것을 잊지 말자.
```python
def say_myself(name, man=True, old):
"""에러"""
```
### 함수 안에서 선언된 변수의 효력 범위
- - -
def vartest(a)에서 입력 인수를 뜻하는 변수 a는 함수 안에서만 사용되는 변수이지 함수 밖의 변수 a가 아니다.
```python
# vartest.py
a = 1
def vartest(a):
    a = a +1

>>> vartest(1)
>>> 2
>>> print(a)
>>> 1
```
#### 함수 안에서 함수 밖의 변수를 변경하는 방법
##### 1. return 이용하기
```python
# vartest_return.py
a = 1
def vartest(a):
    a = a +1
    return a

a = vartest(a)
print(a)
```
##### 2. global 명령어 이용하기
```
# vartest_global.py
a = 1
def vartest():
    global a
    a = a+1

vartest()
print(a)
```