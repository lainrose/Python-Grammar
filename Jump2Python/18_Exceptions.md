## 예외처리
- - -
### 오류 예외 처리 기법
- - -
### try, except문
except문에서 **[ ]** 기호를 사용하는데, 이 기호는 괄호 안의 내용을 생략할 수 있다는 관례적인 표기법이다.
```python
try:
    ...
except [발생 오류[as 오류 메시지 변수]]:
    ...
```
1.try, except만 쓰는 방법

이 경우는 오류 종류에 상관없이 오류가 발생하기만 하면 except 블록을 수행한다.
```python
try:
    ...
except:
    ...
```
2.발생 오류만 포함한 except문

이 경우는 오류가 발생했을 때 except문에 미리 정해 놓은 오류 이름과 일치할 때만 except 블록을 수행한다는 뜻이다.
```python
try:
    ...
except 발생 오류:
    ...
```
이 경우는 오류가 발생했을 때 except문에 미리 정해 놓은 오류 이름과 일치할 때만 except 블록을 수행한다는 뜻이다.

3.발생 오류와 오류 메시지 변수까지 포함한 except문

이 경우는 두 번째 경우에서 오류 메시지의 내용까지 알고 싶을 때 사용하는 방법이다.
```python
try:
    ...
except 발생 오류 as 오류 메시지 변수:
    ...
```
예)
```python
try:
    4 / 0
except ZeroDivisionError as e:
    print(e)

>>> division by zero
```
#### try .. else
try문은 else절을 지원한다. else절은 예외가 발생하지 않은 경우에 실행되며 반드시 except절 바로 다음에 위치해야 한다.
```python
try:
    f = open('foo.txt', 'r')
except FileNotFoundError as e:
    print(str(e))
else:
    data = f.read()
    f.close()
```
#### try .. finally

try문에는 finally절을 사용할 수 있다. finally절은 try문 수행 도중 예외 발생 여부에 상관없이 항상 수행된다.
```python
f = open('foo.txt', 'w')
try:
    # 무언가를 수행한다.
finally:
    f.close()
```
#### 여러개의 오류처리하기
```python
try:
    ...
except 발생 오류1:
   ...
except 발생 오류2:
   ...
```
2개 이상의 오류를 동시에 처리하기 위해서는 위와같이 괄호를 이용하여 함께 묶어주어 처리하면 된다.
```python
try:
    # 무언가를 수행한다.
except (발생오류1, 발생오류2) as e:
    print(e)
```
### 오류 회피하기
- - -
```python
try:
    f = open("나없는파일", 'r')
except FileNotFoundError:
    pass
```
### 오류 일부러 발생시키기
파이썬은 raise라는 명령어를 이용해 오류를 강제로 발생시킬 수 있다.

예를 들어 Bird라는 클래스를 상속받는 자식 클래스는 반드시 fly라는 함수를 구현하도록 만들고
 싶은 경우(강제로 그렇게 하고 싶은 경우)가 있을 수 있다.
```python
 class Bird:
    def fly(self):
        raise NotImplementedError
```
(※ NotImplementedError는 파이썬 내장 오류로,
 꼭 작성해야 하는 부분이 구현되지 않았을 경우 일부러 오류를 발생시키고자 사용한다.)
```python
class Eagle(Bird):
    pass

eagle = Eagle()
eagle.fly()
```
```python
Traceback (most recent call last):
  File "...", line 33, in <module>
    eagle.fly()
  File "...", line 26, in fly
    raise NotImplementedError
NotImplementedError
```
NotImplementedError가 발생되지 않게 하려면 다음과 같이 Eagle 클래스에 fly 함수를 반드시 구현해야 한다.
```python
class Eagle(Bird):
    def fly(self):
        print("very fast")

eagle = Eagle()
eagle.fly()
```
### 오류 만들기
- - -
오류는 다음과 같이 파이썬 내장 클래스인 Exception클래스를 상속하여 만들 수 있다.
```python
class MyError(Exception):
    pass
```
```python
def say_nick(nick):
    if nick == '바보':
        raise MyError()
    print(nick)
```
```python
say_nick("천사")
say_nick("바보")
```
```python
천사
Traceback (most recent call last):
  File "...", line 11, in <module>
    say_nick("바보")
  File "...", line 7, in say_nick
    raise MyError()
__main__.MyError
```
**MyError**가 발생할 경우 예외처리기법을 이용하여 예외처리를 해 보도록 하자.
```python
try:
    say_nick("천사")
    say_nick("바보")
except MyError:
    print("허용되지 않는 별명입니다.")

>>> 천사
>>> 허용되지 않는 별명입니다.
```
```python
try:
    say_nick("천사")
    say_nick("바보")
except MyError as e:
    print(e)
```
실행 해 보면 print(e)로 출력한 오류메시지가 아무것도 출력되지 않는것을 확인 할 수 있다.

메시지가 보이게 하기 위해서는 오류 클래스에 다음과 같은 **__ str __** 메써드를 구현해야 한다
```python
class MyError(Exception):
    def __str__(self):
        return "허용되지 않는 별명입니다."
```
만약 에러 발생시점에 오류메시지를 전달하고 싶다면 다음과 같이 수정해야 한다.
```python
class MyError(Exception):
    def __init__(self, msg):
        self.msg = msg

    def __str__(self):
        return self.msg


def say_nick(nick):
    if nick == '바보':
        raise MyError("허용되지 않는 별명입니다.")
    print(nick)

try:
    say_nick("천사")
    say_nick("바보")
except MyError as e:
    print(e)
```