## *args and **kwargs
대부분 *args와 **kwargs는 함수를 정의 할 때 사용됩니다.

가변인수라 부르며 이는, 어떤 함수를 호출할 때 입력받을 인자가 일정하지 않을 때 사용됩니다.

*args는 인자들을 tuple형태로 받고,

**kwargs는 인자들을 dict(key : value) 형태로 받아옵니다.

###  *args의 사용법
- - -


반드시 *args와 **kwargs 라는 이름으로 사용할 필요는 없습니다.
*만 사용하면므로 *var, **vars로 사용해도됩니다.

*args는 **키워드 되지않은** 가변 갯수의 인자들을 함수에 보낼 때 사용합니다.

스크립트
```python
def test_var_args(f_arg, *argv):
    print ("첫 번째 인자:", f_arg)
    for arg in argv:
        print ("*argv의 다른 인자", arg)

tast_var_args('야숩', 'python', '달걀', 'test')
```
결과
```python
첫번째 인자: 야숩
*argv의 다른 인자: python
*argv의 다른 인자: 달걀
*argv의 다른 인자: test
```

### **kwargs의 사용법
- - -
**kwargs는 **키워드**된 가변 갯수의 인자들을 함수에 보낼 때 사용합니다.
**kwargs는 함수가 **이름이 지정된 인자**를 처리할 때 사용해야합니다.

### 언제 쓸 수 있는가?
- - -
#### 오버로딩
```java
# java code
class Calc{
    //add1
    public int add(int a, int b){
        return a+b;
    }

    //add2
    public int add(int a, int b, int c){
        return a+b+c;
    }

    //add3
    public int add(int a, int b, int c, int d){
        return a+b+c+d;
    }

    //add....
}
```
```python
# python code
def add(*params):
    result = 0
    for p in params:
        result += p
    return result
    ```
```
### 어떻게 쓸 수 있는가?
- - -
```python
def args1(*args):
    print('args :',args)

def args2(**kwargs):
    print('kwargs :',kwargs)

def args3(*args, **kwargs):
    print(args)
    print(kwargs)

args1(1,2,3) # args : (1,2,3)
args2(name='daseul', addr='incheon') # kwargs : {'name':'daseul', 'addr'='incheon'}
args3(1,2,c=3,d=4)
#(1, 2)
#{'c': 3, 'd': 4}
```