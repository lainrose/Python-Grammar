## 파일 읽고 쓰기
- - -
### 파일 생성하기
- - -
파일 객체 = open(파일 이름, 파일 열기 모드)
```python
f = open("새파일.txt", 'w')
f.close()
```
> 파일열기모드	설명
>
> r	읽기모드 - 파일을 읽기만 할 때 사용
>
> w	쓰기모드 - 파일에 내용을 쓸 때 사용
>
> a	추가모드 - 파일의 마지막에 새로운 내용을 추가 시킬 때 사용
```python
f = open("C:/Python/새파일.txt", 'w')
f.close()
```
### 파일을 쓰기 모드로 열어 출력값 적기
- - -
print 대신 파일 객체 f의 write 함수를 이용한다.
```python
# writedata.py
f = open("C:/Python/새파일.txt", 'w')
for i in range(1, 11):
    data = "%d번째 줄입니다.\n" % i
    f.write(data)
f.close()
```
### 프로그램의 외부에 저장된 파일을 읽는 여러 가지 방법
- - -
#### readline() 함수 이용하기
```python
# readline.py
f = open("C:/Python/새파일.txt", 'r')
line = f.readline()
print(line)
f.close()
```
만약 모든 라인을 읽어서 화면에 출력하고 싶다면 다음과 같이 작성하면 된다.

readline()은 더 이상 읽을 라인이 없을 경우 None을 출력한다
```python
# readline_all.py
f = open("C:/Python/새파일.txt", 'r')
while True:
    line = f.readline()
    if not line: break
    print(line)
f.close()
```
#### readlines() 함수 이용하기
readlines() 함수는 파일의 모든 라인을 읽어서 각각의 줄을 요소로 갖는 리스트로 리턴
```python
f = open("C:/Python/새파일.txt", 'r')
lines = f.readlines()
for line in lines:
    print(line)
f.close()
```
#### read() 함수 이용하기
read()는 파일의 내용 전체를 문자열로 리턴
```python
f = open("C:/Python/새파일.txt", 'r')
data = f.read()
print(data)
f.close()
```
### 파일에 새로운 내용 추가하기
파일을 추가 모드('a')로 열면 된다.
```python
# adddata.py
f = open("C:/Python/새파일.txt",'a')
for i in range(11, 20):
    data = "%d번째 줄입니다.\n" % i
    f.write(data)
f.close()
```
### with문과 함께 사용하기
with문을 이용하면 with 블록을 벗어나는 순간 열린 파일 객체 f가 자동으로 close되어 편리하다.
```python
with open("foo.txt", "w") as f:
    f.write("Life is too short, you need python")
```
