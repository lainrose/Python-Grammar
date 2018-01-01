## 패키지
- - -
패키지(Packages)는 도트(.)를 이용하여 파이썬 모듈을 계층적(디렉터리 구조)으로 관리할 수 있게 해준다.

game, sound, graphic, play는 디렉터리명이고 .py 확장자를 가지는 파일은 파이썬 모듈이다.

game 디렉터리가 이 패키지의 루트 디렉터리이고 sound, graphic, play는 서브 디렉터리이다.
> game/
>     __init__.py
>     sound/
>        __init__.py
>         echo.py
>         wav.py
>     graphic/
>         __init__.py
>         screen.py
>         render.py
>     play/
>         __init__.py
>         run.py
>         test.py

### 패키지 만들기
- - -
#### 패키지 기본 구성 요소 준비하기
1. C:/Python이라는 디렉터리 밑에 game 및 기타 서브 디렉터리들을 생성하고 .py 파일들을 다음과 같이 만들어 보자
(만약 C:/Python이라는 디렉터리가 없다면 먼저 생성하고 진행하자).
```python
C:/Python/game/__init__.py
C:/Python/game/sound/__init__.py
C:/Python/game/sound/echo.py
C:/Python/game/graphic/__init__.py
C:/Python/game/graphic/render.py
```
2. 각 디렉터리에 __init__.py 파일을 만들어 놓기만 하고 내용은 일단 비워 둔다.

3. echo.py 파일은 다음과 같이 만든다.
```python
# echo.py
def echo_test():
    print ("echo")
    ```
```
4. render.py 파일은 다음과 같이 만든다.
```python
# render.py
def render_test():
    print ("render")
    ```
```
5. 다음 예제들을 수행하기 전에 우리가 만든 game 패키지를 참조할 수 있도록 다음과 같이 도스 창에서 set 명령을 이용하여
PYTHONPATH 환경 변수에 C:/Python 디렉터리를 추가한다. 그리고 파이썬 인터프리터(Interactive shell)를 실행하자.
```python
C:\> set PYTHONPATH=C:/Python
C:\> python
Python 3.5.1 (v3.5.1:37a07cee5969, Dec 6 2015, 01:54:25) [MSC v.1900 64 bit (AM...
Type "help", "copyright", "credits" or "license" for more information.
>>>
```
#### 패키지 안의 함수 실행하기
첫 번째는 echo 모듈을 import하여 실행하는 방법으로, 다음과 같이 실행한다.
```python
>>> import game.sound.echo
>>> game.sound.echo.echo_test()
echo
```
두 번째는 echo 모듈이 있는 디렉터리까지를 from ... import하여 실행하는 방법이다.
```python
>>> from game.sound import echo
>>> echo.echo_test()
echo
```
세 번째는 echo 모듈의 echo_test 함수를 직접 import하여 실행하는 방법이다.
```python
>>> from game.sound.echo import echo_test
>>> echo_test()
echo
```
하지만 다음과 같이 echo_test 함수를 사용하는 것은 불가능하다.

import game을 수행하면 game 디렉터리의 모듈 또는 game 디렉터리의 __init__.py에 정의된 것들만 참조할 수 있다.
```python
>>> import game
>>> game.sound.echo.echo_test()
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
AttributeError: 'module' object has no attribute 'sound'
```
또 다음처럼 echo_test 함수를 사용하는 것도 불가능하다.

도트 연산자(.)를 사용해서 import a.b.c처럼 import할 때 가장 마지막 항목인 c는 반드시 모듈 또는 패키지여야만 한다.
```python
>>> import game.sound.echo.echo_test
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
ImportError: No module named echo_test
```
### **__ init __.py** 의 용도
- - -
**__ init__.py** 파일은 해당 디렉터리가 패키지의 일부임을 알려주는 역할을 한다.

만약 game, sound, graphic등 패키지에 포함된 디렉터리에 __init__.py 파일이 없다면 패키지로 인식되지 않는다.

### all의 용도
- - -
분명 game.sound 패키지에서 모든 것(*)을 import하였으므로 echo 모듈을 사용할 수 있어야 할 것 같은데
 echo라는 이름이 정의되지 않았다는 이름 오류(NameError)가 발생했다.
```python
>>> from game.sound import *
>>> echo.echo_test()
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
NameError: name 'echo' is not defined
```
이렇게 특정 디렉터리의 모듈을 *를 이용하여 import할 때에는 다음과 같이 해당 디렉터리의
__init__.py 파일에 __all__이라는 변수를 설정하고 import할 수 있는 모듈을 정의해 주어야 한다.

여기서 __all__이 의미하는 것은 sound 디렉터리에서 * 기호를 이용하여 import할 경우 이곳에 정의된 echo 모듈만 import된다는 의미이다.
```python
# C:/Python/game/sound/__init__.py
__all__ = ['echo']
```
### relative 패키지
- - -
```python
# render.py
from ..sound.echo import echo_test

def render_test():
    print ("render")
    echo_test()
```
> .. – 부모 디렉터리
> . – 현재 디렉터리
