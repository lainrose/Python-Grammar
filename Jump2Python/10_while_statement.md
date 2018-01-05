## while문

### while문의 기본 구조
- - -
반복해서 문장을 수행해야 할 경우 while문을 사용한다. 그래서 while문을 반복문이라고도 부른다.
```python
while <조건문>:
    <수행할 문장1>
    <수행할 문장2>
    <수행할 문장3>
    ...
```
### while문 강제로 빠져나가기
- - -
```python
>>> coffee = 10
>>> money = 300
>>> while money:
...     print("돈을 받았으니 커피를 줍니다.")
...     coffee = coffee -1
...     print("남은 커피의 양은 %d개입니다." % coffee)
...     if not coffee:
...         print("커피가 다 떨어졌습니다. 판매를 중지합니다.")
...         break
...
```
if not coffee:라는 문장에서 not coffee가 참이 되므로 if문 다음의 문장인 "커피가 다 떨어졌습니다.
판매를 중지합니다."가 수행되고 break문이 호출되어 while문을 빠져나가게 된다.

### 조건에 맞지 않는 경우 맨 처음으로 돌아가기
- - -
```python
>>> a = 0
>>> while a < 10:
...     a = a+1
...     if a % 2 == 0: continue
...     print(a)
...
1
3
5
7
9
```
a가 짝수이면 continue 문장을 수행한다.
이 continue문은 while문의 맨 처음(조건문: a<10)으로 돌아가게 하는 명령어이다.

즉, while문을 빠져나가지 않고 while문의 맨 처음(조건문)으로 다시 돌아가게 만드는 명령어이다.

### 무한 루프
- - -
```python
while True:
    수행할 문장1
    수행할 문장2
    ...
```
