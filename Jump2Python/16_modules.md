## 모듈

모듈이란 함수나 변수 또는 클래스 들을 모아 놓은 파일이다.
### 모듈 만들고 불러 보기
- - -
import 모듈이름
```python
# mod1.py
def sum(a, b):
    return a + b
```
```python
>>> import mod1
>>> print mod1.sum(3,4)
````
#### 모듈 함수를 사용하는 또 다른 방법
from 모듈이름 import 모듈함수
```python
>>> from mod1 import sum
>>> sum(3, 4)
7
```
##### sum 함수와 safe_sum 함수를 둘 다 사용하기
```python
from mod1 import sum, safe_sum
```
```python
from mod1 import *
```
### if __name__ == "__main__": 의 의미
- - -
```python
# mod1.py
def sum(a, b):
    return a+b

def safe_sum(a, b):
    if type(a) != type(b):
        print("더할수 있는 것이 아닙니다.")
        return
    else:
        result = sum(a, b)
    return result

print(safe_sum('a', 1))
print(safe_sum(1, 4))
print(sum(10, 10.4))
```
엉뚱하게도 import mod1을 수행하는 순간 mod1.py가 실행이 되어 결과값을 출력한다.
```python
>>> import mod1
더할 수 있는 것이 아닙니다.
None
5
20.4
```
이러한 문제를 방지하려면
__name__ == "__main__"이 참이 되어 if문 다음 문장들이 수행된다.

반대로 대화형 인터프리터나 다른 파일에서 이 모듈을 불러서 사용할 때는 __name__ == "__main__"이 거짓이 되어 if문 다음 문장들이 수행되지 않는다.
```python
if __name__ == "__main__":
    print(safe_sum('a', 1))
    print(safe_sum(1, 4))
    print(sum(10, 10.4))
```
### 클래스나 변수 등을 포함한 모듈
- - -
```python
# mod2.py
PI = 3.141592

class Math:
    def solv(self, r):
        return PI * (r ** 2)

def sum(a, b):
    return a+b

if __name__ == "__main__":
    print(PI)
    a = Math()
    print(a.solv(2))
    print(sum(PI , 4.4))
```
#### 모듈에 포함된 변수, 클래스, 함수 사용하기
```python
>>> import mod2
>>> print(mod2.PI)
3.141592
>>> a = mod2.Math()
>>> print(a.solv(2))
12.566368
```