## 클래스
- - -
```python
class Calculator:
    def __init__(self):
        self.result = 0

    def adder(self, num):
        self.result += num
        return self.result
```
파이썬 메서드의 첫번째 파라미터명은 관례적으로 self라는 이름을 사용한다.

호출 시 호출한 객체 자신이 전달되기 때문에 self("self"는 자기자신이라는 뜻을 가진 영어단어이다.)라는 이름을 사용하게 된 것이다.

물론 self말고 다른 이름을 사용해도 상관은 없다.
### 클래스와 객체
- - -
```python
>>> class Cookie:
>>>    pass
""" (※ pass는 아무것도 수행하지 않는 문법이다. 임시로 코드를 작성할 때 주로 사용한다.)"""
>>> a = Cookie()
>>> b = Cookie()
```
> 객체와 인스턴스의 차이
>
> 클래스에 의해서 만들어진 객체를 인스턴스라고도 한다.
> 그렇다면 객체와 인스턴스의 차이는 무엇일까? 이렇게 생각해 보자.
>
> a = Cookie() 이렇게 만들어진 a는 객체이다.
> 그리고 a라는 객체는 Cookie의 인스턴스이다.
>
> 즉, 인스턴스라는 말은 특정 객체(a)가 어떤 클래스(Cookie)의 객체인지를 관계 위주로 설명할 때 사용된다.
>
> 즉, "a는 인스턴스" 보다는 "a는 객체"라는 표현이 어울리며,
> "a는 Cookie의 객체" 보다는 "a는 Cookie의 인스턴스"라는 표현이 훨씬 잘 어울린다.

### 생성자 (Constructor)
- - -
생성자(Constructor)란 객체가 생성될 때 자동으로 호출되는 메서드를 의미한다.

파이썬 메서드명으로 __init__ 을 사용하면 이 메서드는 생성자가 된다.
```python
>>> class FourCal:
...     def __init__(self, first, second):
...         self.first = first
...         self.second = second
```
### 클래스의 상속
- - -
어떤 클래스를 만들 때 다른 클래스의 기능을 물려받을 수 있게 만드는 것이다.

class 클래스명(상속할 클래스명)
```python
>>> class MoreFourCal(FourCal):
...     pass
...
>>>
```
#### 메서드 오버라이딩
- - -
SafeFourCal 클래스는 FourCal클래스에 있는 div라는 메서드를 동일한 이름으로 다시 작성하였다.

이렇게 부모 클래스(상속한 클래스)에 있는 메서드를 동일한 이름으로 다시 만드는 것을 메서드 오버라이딩(Overriding, 덮어쓰기)이라고 한다.

이렇게 메서드를 오버라이딩하면 부모 클래스의 메서드 대신 오버라이딩한 메서드가 호출된다.
```python
>>> class FourCal(self):
...     def div(self):
...         pass
```
```python
>>> class SafeFourCal(FourCal):
...     def div(self):
...         pass
```