---
layout: default
---

# 4-1 함수(Function)
---

## 1. 함수란 무엇이고 왜 사용하는가?
<img src='./figures/box_function.png' width="150" height="160" title="함수 상자">
<br>
<img src='./figures/math_function.png' width="190" height="80" title="수학에서 함수">  
    
    - 프로그램에서 한 번 이상 실행할 수 있도록 여러 문을 그룹화하는 장치.
    - 프로그램을 절차적으로 분해.
    - 코드가 실행될 때마다 다른 입력값을 받을 수 있음.
    - 코드의 재사용성을 높이고 코드 중복성을 최소화.  


```python
# 입력 a, b를 받아 각각 제곱이 짝수인지 판별하는 프로그램
a = 4
b = 2

result_a = (a**2)%2 
result_b = (b**2)%2

if (result_a or result_b) == 0:
    print("둘 다 짝수입니다 !")
else:
    print("하나 이상이 홀수입니다 !")
result = result_a or result_b
```


```python
# 입력 a, b를 받아 각각 제곱이 짝수인지 판별하는 프로그램
def func_1(val):
    return (val**2)%2

def func_2(val1, val2):
    if (result_a or result_b) == 0:
        print("둘 다 짝수입니다 !")
    else:
        print("하나 이상이 홀수입니다 !")
    return (result_a or result_b)


a = 4
b = 2

result_a = func_1(a)
result_b = func_1(b)

reult = func_2(result_a, result_b)
```

## 2. 함수만들기 (def)

- **def**
    - 함수 객체를 만들고 함수 이름을 할당.
    - 들여쓰기가 매우 중요.

### (1) 기본적인 포맷
``` python
def 함수이름(입력값1, 입력값2, ... 입력값N):
  수행 코드
  ...
  수행 코드
  return 결과값
```


```python
def add(a, b):
    c = a + b
    return c

# a, b에 순서대로 4, 6이 지정됨.
result = add(4, 6)
print(result)


result = add(a = 4, b = 6)
print(result)

# 순서가 바뀌어도 b, a에 각각 지정했기 때문에 순서에 상관하지 않음.
result = add(b = 6, a = 4)
print(result)
```


```python
def add(a, b):
    return a + b

result = add(4, 6)
print(result)
```


```python
# Sequence 는 + 시 concatenation! CH02_built-in_types 참고하세요!

print(add([2,3,4], [2,3,1]))

print(add('Python', 'MMMIL'))

print(add((2,3,1), (1,2,1)))
```

### (2) 입력값이 없는 경우
``` python
def 함수이름():
    수행 코드
    ...
    수행 코드
```


```python
def greet():
    print("Hello, Python!")

greet()
```

### (3) 결과값이 없는 경우
``` python
def 함수이름(입력값1, 입력값2, ... 입력값N):
    수행 코드
    ...
    수행 코드
```


```python
def greet_name(name):
    print("Hello, " + name)
    
greet_name("Jerry")
```

### (4) 제어문이 있는 경우
``` python
def 함수이름(입력값1, 입력값2, ... 입력값N):
    수행 코드
    ...
    수행 코드
    for 값 in Sequence:
        if 조건 1:
            수행 코드
            ...
            return 결과값 1
        elif 조건 2 :
            수행 코드
            ...
            return 결과값 2
        else :
            수행 코드
            ...
            return 결과값 3

```


```python
def intersect(val1, val2):
    result = []
    for x in val1:
        if x in val2:
            result.append(x)
    return result

print(intersect("SPAM", "SCAM"))
print(intersect("SPAM", ["S","C","A","M"]))
```

### (5) 출력값이 여러 개인 경우
``` python
def 함수이름(입력값1, 입력값2, ... 입력값N):
    수행 코드
    ...
    수행 코드
    return 결과값 1, 결과값 2, ...결과값 N

```


```python
def compute(a, b):
    result_1 = a + b
    result_2 = a * b
    return result_1, result_2

# 결과값이 여러 개일때 호출하면 N개의 출력값이 tuple로 반환!
print(compute(3, 4))

# Unpacking
# 다음과 같이 선언하면 a 에는 3, b 에는 7이 됨.
a, b = compute(3, 4)
print(a)
print(b)
```

## 3. Global & Local

``` python
a = 43

def add(x, y):
    a = x + y
    print(a)
    return a

print(a)
print(add(2, 4))
print(a)

```


```python
a = 43

def add(x, y):
    a = x + y
    print(a)
    return a

print(a)
print(add(2, 4))
print(a)
```


```python
a = 43

def add(x, y):
    global a
    a = x + y
    print(a)
    return a

print(a)
print(add(2, 4))
print(a)
```


```python
def test():
    val = 5
    print(val)
test()
print(val)
```


```python
def test():
    global val
    val = 5
    print(val)
test()
print(val)
```

## 4. 매개변수

### (1) * args
- N 개의 매개변수를 받음.
- * 을 이용.
- *val, *python 등과 같이 *이름이라고 마음대로 선언해도 됨.
- 보통은 arguments의 약자로 *args 로 사용.
- tuple로 반환.


```python
def test(*args):
    return args

a = test(1, 2, 5, 3, 6)
print(type(a))
```


```python
def test(*val):
    return val

a = test(1, 2, 5, 3, 6)
print(type(a))
```


```python
def sum_all(*args):
    result = 0
    for x in args:
        result += x
    return result

result = sum_all(8,1,5)
print(result)

result = sum_all(1,2,3,4,5,6,7)
print(result)
```

### (2) **kwargs
- N개의 매개변수를 받음.
- ** 을 이용.
- **val, **python 등과 같이 **이름이라고 마음대로 선언해도 됨.
- 보통은 keyword arguments 의 약자로 **kwargs 로 사용.
- dictionary로 반환.


```python
def test(**kwargs):
    return kwargs

a = test(name="python", ver="3.6.8")
print(type(a))
print(a)
```


```python
def addormat(**kwargs):
    if kwargs['op'] == 'add':
        result = 0
        for x in kwargs['val']:
            result += x
        return result

    elif kwargs['op'] == 'mul':
        result = 1
        for x in kwargs['val']:
            result *= x
        return result
    
print(addormat(op='mul', val=[2,6,3]))

print(addormat(op='add', val=[2,6,3]))
```

### Tip. Docstring
- 함수에 대한 설명.
``` python
a = [1,2,3]
a.append()
```


```python
def make_docstring():
    """
    This Function is testing about docstring.
    """
    pass
```


```python
make_docstring()
```

## 5. 함수만들기 (lambda)
- lambda 표현식은 block을 이용한 statements가 아님.
- 가벼운, 짧은 함수 만들때 이용.
- lambda만 사용할 수 있고 def 안에 중첩하여 사용할 수 있음.

```python
lambda 매개변수1, 매개변수2, ... : 매개변수를 이용한 표현식
```


```python
def add_def(x, y):
    return x+y

add = lambda x, y: x+y

```


```python
print(add_def(1, 2))
print(add(1, 2))
```

[To Home](../index.md)  
[To Lecture List](../lecturelist.md)