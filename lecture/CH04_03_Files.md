---
layout: default
---

# 4-3 Files
---

- 파이썬에서 파일을 다룰 때는 내장함수인 `open()` 을 활용함.



```python
open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)
```

- file : 파일 경로
- mode : 파일이 열리는 모드
    - 'r' : 읽기 모드 (default)
    - 'w' : 쓰기 모드, 새로운 파일로 생성.
    - 'a' : 쓰기 모드, 기존에 파일이 존재한다면 가장 마지막 부분부터 내용을 붙임.
    - 'b' : 바이너리 모드
    - 't' : 텍스트 모드 (default)

<br>

- 가장 많이 사용되는 방식
- `파일 객체 = open(파일 이름, mode)` 로 사용

## 1. 파일 생성


```python
f = open('test.txt', 'w')
f.close()
```

- close() 구문은 생략을 해도 무관.
- **But**, 파일 객체를 닫아주는 것이 좋음.

## 2. 파일에 쓰기


```python
f = open('test.txt', 'w')
f.write('First Line!')
f.close()
```


```python
f = open('test.txt', 'w')
for x in range(10):
    f.write('%d'%x)
    #f.write('%d\n'%x)
f.close()
```


```python
f = open('test.txt', 'a')
for x in range(10):
    #f.write('%d'%x)
    f.write('%d\n'%x)
f.close()
```

## 3. 파일 읽기

- `read`, `readline`, `readlines` 세 가지 방법.

#### (1) read
- 한번에 모든 내용을 읽음.
- 문자열로 반환.


```python
f = open('test.txt', 'r')
data = f.read()
print(data)
print(type(data))
f.close()
```

#### (2) readlines
- 한번에 모든 내용을 읽음.
- list로 반환.
- list 안에 요소들은 문자열.


```python
f = open('test.txt', 'r')
data = f.readlines()
print(data)
print(type(data))
f.close()
```

#### readline
- 한번에 한 line씩 읽음.
- 문자열로 반환.


```python
f = open('test.txt', 'r')
data = f.readline()
print(data)
print(type(data))
f.close()
```

#### 번외 

- close()를 써주기 귀찮다.....
- with 문을 사용해보자!


```python
with open('test.txt', 'r') as f:
    data = f.readlines()
print(data)
print(type(data))
```

[To Home](../index.md)  
[To Lecture List](../lecturelist.md)