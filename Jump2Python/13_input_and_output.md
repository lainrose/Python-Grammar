## 사용자 입력과 출력
- - -
### 사용자 입력
- - -
사용자가 입력한 값을 어떤 변수에 대입하고 싶을 때

#### input의 사용
input()은 입력되는 모든 것을 문자열로 취급한다.
```python
>>> a = raw_input()
Life is too short, you need python
>>> a
'Life is too short, you need python'
>>>
```
#### 프롬프트를 띄워서 사용자 입력 받기
```python
>>> number = raw_input("숫자를 입력하세요: ")
숫자를 입력하세요:
```

### print 자세히 알기
- - -
#### 큰따옴표(")로 둘러싸인 문자열은 + 연산과 동일하다
```python
>>> print("life" "is" "too short") # ①
lifeistoo short
>>> print("life"+"is"+"too short") # ②
lifeistoo short
```
#### 문자열 띄어쓰기는 콤마로 한다
```python
>>> print("life", "is", "too short")
life is too short
```
#### 한 줄에 결과값 출력하기
``` python
>>> for i in range(10):
...     print i,
...
0 1 2 3 4 5 6 7 8 9
```