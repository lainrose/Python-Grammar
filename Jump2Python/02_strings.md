## 02. 문자열 자료형

문자열(String)이란 문자, 단어 등으로 구성된 문자들의 집합을 의미한다.
```python
"Life is too short, You need Python"
"a"
"123"
```

### 문자열 만드는 방법
- - -
##### 1. 큰따옴표로 양쪽 둘러싸기
```python
"Hello World"
```
##### 2. 작은따옴표로 양쪽 둘러싸기
```python
'Python is fun'
```
##### 3. 큰따옴표 3개를 연속으로 써서 양쪽 둘러싸기
```python
"""Life is too short, You need python"""
```
##### 4. 작은따옴표 3개를 연속으로 써서 양쪽 둘러싸기
```python
'''Life is too short, You need python'''
```
단순함이 자랑인 파이썬이 문자열을 만드는 방법은 왜 4가지나 있는지 알아보자.

### 문자열 안에 작은따옴표나 큰따옴표를 포함시키고 싶을 때
- - -
문자열을 만들어 주는 주인공은 작은따옴표(')와 큰따옴표(")이다.
그런데 문자열 안에도 작은따옴표와 큰따옴표가 들어 있어야 할 경우가 있다.
이때는 좀 더 특별한 기술이 필요하다.

##### 1. 문자열에 작은따옴표 (') 포함시키기
```python
Python's favorite food is perl
```
위와 같은 문자열을 food라는 변수에 저장하고 싶다고 가정하자.
문자열 중 Python's에 작은따옴표(')가 포함되어 있다.

이럴 때는 다음과 같이 문자열을 큰따옴표(")로 둘러싸야 한다.
큰따옴표 안에 들어 있는 작은따옴표는 문자열을 나타내기 위한 기호로 인식되지 않는다.
```python
>>> food = "Python's favorite food is perl"
>>> food
"Python's favorite food is perl"
```
##### 2. 문자열에 큰따옴표 (") 포함시키기
```python
>>> say = '"Python is very easy." he says.'
>>> say
'"Python is very easy." he says.'
```
##### 3. \(백슬래시)를 이용해서 작은따옴표(')와 큰따옴표(")를 문자열에 포함시키기
작은따옴표(')나 큰따옴표(")를 문자열에 포함시키는 또 다른 방법은 \(백슬래시)를 이용하는 것이다.
즉, 백슬래시(\)를 작은따옴표(')나 큰따옴표(") 앞에 삽입하면 \(백슬래시) 뒤의 작은따옴표(')나 큰따옴표(")는 문자열을
둘러싸는 기호의 의미가 아니라 문자 ('), (") 그 자체를 뜻하게 된다.
```python
>>> food = 'Python\'s favorite food is perl'
>>> say = "\"Python is very easy.\" he says."
```

### 여러 줄인 문자열을 변수에 대입하는 방법
- - -
##### 1. 줄을 바꾸기 위한 이스케이프 코드 \n 삽입하기
```python
>>> multiline = "Life is too short\nYou need python"
```
위의 예처럼 줄바꿈 문자인 \n을 삽입하는 방법이 있지만 읽기에 불편하고 줄이 길어지는 단점이 있다.

##### 2. 연속된 작은따옴표 3개(''') 또는 큰따옴표 3개(""") 사용
위 1번의 단점을 극복하기 위해 파이썬에서는 다음과 같이 작은따옴표 3개(''') 또는 큰따옴표 3개(""")를 이용한다.
```python
>>> multiline="""
... Life is too short
... You need python
... """
>>> print multiline
Life is too short
You need python
```

### 문자열 연산
- - -
파이썬에서는 문자열을 더하거나 곱할 수 있다.

##### 1. 문자열 더해서 연결하기
```python
>>> head = "Python"
>>> tail = " is fun!"
>>> head + tail
'Python is fun!'
```

##### 2. 문자열 곱하기
```python
>>> a = "python "
>>> a * 2
'python python '
```

##### 3. 문자열 곱하기 응용
```python
# 소스
print "=" * 50
print "Hello Python"
print "=" * 50

# 실행결과
==================================================
My Program
==================================================
```

### 문자열 인덱싱과 슬라이싱
- - -
##### 문자열 인덱싱
```python
>>> a = "Life is too short, You need Python"
>>> a[3]
'e'
>>> a[-1]
'n'
>>> a[-0]
'L'
```
문자열을 뒤에서부터 읽기 위해서 마이너스(-) 기호를 붙인다.
뒤에서부터 첫 번째 문자를 표시할 때도 0부터 세어 "a[-0]이라고 해야 하지 않을까?"라는 의문이 들 수도 있겠지만,
0과 -0은 똑같은 것이기 때문에 a[-0]은 a[0]과 똑같은 값을 보여 준다.

##### 문자열 슬라이싱
```python
>>> a = "Life is too short, You need Python"
>>> a[0:3]
'Lif'
```
주의할 점으로는, 슬라이싱은 0 <= a < 3 을 만족하기 때문에, Lif가 된다. 즉 뒤의 숫자 자리에서 -1한 위치까지 슬라이싱 하게된다.

### 문자열을 슬라이싱하는 방법
- - -
```python
# a[시작 번호:끝 번호]에서 끝 번호 부분을 생략하면 시작 번호부터 그 문자열의 끝까지 뽑아낸다.
>>> a[19:]
'You need Python'

# a[시작 번호:끝 번호]에서 시작 번호를 생략하면 문자열의 처음부터 끝 번호까지 뽑아낸다.
>>> a[:17]
'Life is too short'

# a[시작 번호:끝 번호]에서 시작 번호와 끝 번호를 생략하면 문자열의 처음부터 끝까지를 뽑아낸다.
>>> a[:]
'Life is too short, You need Python'

# 슬라이싱에서도 인덱싱과 마찬가지로 마이너스(-) 기호를 사용할 수 있다.
>>> a[19:-7]
'You need'

### 슬라이싱으로 문자열 나누기
```python
>>> a = "20010331Rainy"
>>> year = a[:4]
>>> day = a[4:8]
>>> weather = a[8:]
>>> year
'2001'
>>> day
'0331'
>>> weather
'Rainy'
```

> "Pithon"이라는 문자열을 "Python"으로 바꾸려면?
```python
>>> a = "Pithon"
>>> a[1]
'i'
>>> a[1] = 'y'
```
위는  에러가 발생한다. 왜냐하면 문자열의 요소값은 바꿀 수 있는 값이 아니기 때문이다.
(문자열, 튜플 등 의 자료형은 그 요소값을 변경할 수 없다. 그래서 immutable한 자료형이라고도 부른다).

다음과 같이 슬라이싱을 이용하면 'Pithon'이라는 문자열을 'P' 부분과 'thon' 부분으로 나눌 수 있기 때문에 그 사이에
'y'라는 문자를 추가하여 'Python'이라는 새로운 문자열을 만들 수 있다.
```python
>>> a = "Pithon"
>>> a[:1]
'P'
>>> a[2:]
'thon'
>>> a[:1] + 'y' + a[2:]
'Python'
```

### 문자열 관련 함수
- - -
#### 문자 개수 세기(count)
```python
>>> a = "hobby"
>>> a.count('b')
2
```
#### 위치 알려주기1(find)
```python
>>> a = "Python is best choice"
>>> a.find('b')
10
>>> a.find('k')
-1
```
문자열 중 문자 b가 처음으로 나온 위치를 반환한다. 만약 찾는 문자나 문자열이 존재하지 않는다면 -1을 반환한다.

#### 위치 알려주기2(index)
```python
>>> a = "Life is too short"
>>> a.index('t')
8
>>> a.index('k')
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
ValueError: substring not found
```
문자열 중 문자 t가 맨 처음으로 나온 위치를 반환한다. 만약 찾는 문자나 문자열이 존재하지 않는다면 오류를 발생시킨다.
앞의 find 함수와 다른 점은 문자열 안에 존재하지 않는 문자를 찾으면 오류가 발생한다는 점이다.

#### 문자열 삽입(join)
```python
>>> a= ","
>>> a.join('abcd')
'a,b,c,d'
```
abcd라는 문자열의 각각의 문자 사이에 변수 a의 값인 ','를 삽입한다.

#### 소문자를 대문자로 바꾸기(upper)
```python
>>> a = "hi"
>>> a.upper()
'HI'
```

#### 대문자를 소문자로 바꾸기(lower)
```python
>>> a = "HI"
>>> a.lower()
'hi'
```

#### 왼쪽 공백 지우기(lstrip)
```python
>>> a = " hi "
>>> a.lstrip()
'hi '
```

#### 오른쪽 공백 지우기(rstrip)
```python
>>> a= " hi "
>>> a.rstrip()
' hi'
```

#### 양쪽 공백 지우기(strip)
```python
>>> a = " hi "
>>> a.strip()
'hi'
```

#### 문자열 바꾸기(replace)
```python
>>> a = "Life is too short"
>>> a.replace("Life", "Your leg")
'Your leg is too short'
```

#### 문자열 나누기(split)
```python
>>> a = "Life is too short"
>>> a.split()
['Life', 'is', 'too', 'short']
>>> a = "a:b:c:d"
>>> a.split(':')
['a', 'b', 'c', 'd']
```
__a.split()__ 처럼 괄호 안에 아무런 값도 넣어 주지 않으면 공백(스페이스, 탭, 엔터등)을 기준으로 문자열을 나누어 준다.