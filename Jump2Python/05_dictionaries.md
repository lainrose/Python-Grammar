## 05. 딕셔너리 자료형

### 딕셔너리의 생성 방법
- - -
{Key1:Value1, Key2:Value2, Key3:Value3 ...}

Key와 Value의 쌍 여러 개가 {과 }로 둘러싸여 있다.
각각의 요소는 Key : Value 형태로 이루어져 있고 쉼표(,) 로 구분되어 있다.

(※ Key에는 변하지 않는 값을 사용하고, Value에는 변하는 값과 변하지 않는 값 모두 사용할 수 있다.)

```python
>>> a = {'name': 'pey', 'phone': '0119993323', 'birth': '1118'}
>>> a = {1: 'hi'}
>>> a = { 'a': [1,2,3]}
```

### 딕셔너리 쌍 추가, 삭제하기
- - -
딕셔너리는 순서를 따지지 않는다는 사실을 기억하자.

#### 1. 딕셔너리 쌍 추가하기
```python
>>> a = {1: 'a'}
>>> a[2] = 'b'
>>> a
{2: 'b', 1: 'a'}
>>> a['name'] = 'pey'
{'name':'pey', 2: 'b', 1: 'a'}
>>> a[3] = [1,2,3]
{'name': 'pey', 3: [1, 2, 3], 2: 'b', 1: 'a'}
```

#### 2. 딕셔너리 요소 삭제하기
```python
>>> del a[1]
>>> a
{'name': 'pey', 3: [1, 2, 3], 2: 'b'}
```


### 딕셔너리를 사용하는 방법
- - -
#### 딕셔너리에서 Key 사용해 Value 얻기
```python
>>> grade = {'pey': 10, 'julliet': 99}
>>> grade['pey']
10
>>> grade['julliet']
99
```

### 딕셔너리 만들 때 주의할 사항
- - -
- 먼저 딕셔너리에서 Key는 고유한 값이므로 중복되는 Key 값을 설정해 놓으면 하나를 제외한 나머지 것들이
모두 무시된다는 점을 주의해야 한다.
```python
>>> a = {1:'a', 1:'b'}
>>> a
{1: 'b'}
```

- Key에 리스트는 쓸 수 없다는 것이다. 하지만 튜플은 Key로 쓸 수 있다.
딕셔너리의 Key로 쓸 수 있느냐 없느냐는 Key가 변하는 값인지 변하지 않는 값인지에 달려 있다.
```python
>>> a = {[1,2] : 'hi'}
Traceback (most recent call last):
File "", line 1, in ?
TypeError: unhashable type
```

### 딕셔너리 관련 함수
- - -
#### Key 리스트 만들기(keys)
```python
>>> a = {'name': 'pey', 'phone': '0119993323', 'birth': '1118'}
>>> a.keys()
dict_keys(['name', 'phone', 'birth'])
```
#### Value 리스트 만들기(values)
```python
>>> a.values()
dict_values(['pey', '0119993323', '1118'])
```
#### Key, Value 쌍 얻기(items)
```python
>>> a.items()
dict_items([('name', 'pey'), ('phone', '0119993323'), ('birth', '1118')])
```
#### Key: Value 쌍 모두 지우기(clear)
```python
>>> a.clear()
>>> a
{}
```
#### Key로 Value얻기(get)
```python
>>> a = {'name':'pey', 'phone':'0119993323', 'birth': '1118'}
>>> a.get('name')
'pey'
>>> a.get('phone')
'0119993323'
```
다만, 다음 예제에서 볼 수 있듯이 a['nokey']처럼 존재하지 않는 키(nokey)로 값을 가져오려고 할 경우
a['nokey']는 Key 오류를 발생시키고 a.get('nokey')는 None을 리턴한다는 차이가 있다.

어떤것을 사용할지는 본인의 선택이다.
```python
>>> a.get('nokey')
>>> a['nokey']
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
KeyError: 'nokey'
```

딕셔너리 안에 찾으려는 key 값이 없을 경우 미리 정해 둔 디폴트 값을 대신 가져오게 하고 싶을 때에는
get(x, '디폴트 값')을 사용하면 편리하다.
```python
>>> a.get('foo', 'bar')
'bar'
```

#### 해당 Key가 딕셔너리 안에 있는지 조사하기(in)
```python
>>> a = {'name':'pey', 'phone':'0119993323', 'birth': '1118'}
>>> 'name' in a
True
>>> 'email' in a
False
```