---
layout: default
---

# 03장 프로그램의 구조를 쌓는다! 제어문

## 3-3 ) for문
-----------------------------------------------------------------------

파이썬의 직관적인 특징을 가장 잘 대변해 주는 것이 바로 이 for문이다.  
while문과 비슷한 반복문인 for문은 매우 유용하고 문장 구조가 한눈에 쏙 들어온다는 장점이 있다.  

### (1) for문의 기본 구조
앞서 배운 while문은 조건이 참인 동안은 계속해서 반복 실행한다.  
조건이 거짓이 되는 순간 while문을 벗어난다.  
for문 또한 while문처럼 주어진 조건동안 반복 실행되는 것은 같으나,  
while문과 다른 점은 **초기값을 주고 이 값이 주어진 조건을 만족시키는 동안만 실행된다**는 점이다.


```python
for 변수 in 리스트(또는 튜플, 문자열):
    수행할 문장1
    수행할 문장2
    ...
```

리스트나 튜플, 문자열의 첫 번째 요소부터 마지막 요소까지 차례로 변수에 대입되어 "수행할 문장1", "수행할 문장2" 등이 수행된다.


```python
A = [1,2,3,4,5]
B = ('a','b','c')
C = '이제부터 for문 수업을 시작합니다!'

for a in C:
    print(a)
```

### for문 뒤에 'a'는 안 바꿔줘도 되는거야?
A,B,C에 있는 요소가 for문에 들어가기 전에 순서대로 a의 변수에 들어간다.  
따라서 **for문 내에서 반복 수행을 하는 것은 A,B,C가 아닌 a라는 변수가 수행하는 것이다.**  

-----  
### 이중 for문 (Nested for loops)
for loop 안에 for loop을 한 번 더 사용할 수 있다.


```python
items = ["aaa", 111, (4, 5), 2.01]
tests = [(4, 5), 3.14]

for key in tests:
    for item in items:
        if item == key:
            print(key, "was found")
            break
    else:
        print(key, "not found!")
```

### (2) 다양한 for문의 사용

* 리스트 안의 튜플값을 for문에서 사용하기 (List or Tuple assignment in for loop)


```python
a = [(1,2), (3,4), (5,6)]
for (first, last) in a:
    print(first + last)
```

--------------
## <Question 07>

> **「"총 5명의 학생이 시험을 보았는데 시험 점수가 60점이 넘으면 합격이고 그렇지 않으면 불합격이다. 합격인지 불합격인지 결과를 보여주시오."」**  

**Hint01)** for문을 사용한다.  
**Hint02)** for문은 조건을 값으로도 사용한다는 점을 기억한다.  



```python
marks = [90, 25, 67, 45, 80]  
```

-----

### (3) for문과 continue

**while문에서 살펴보았던 continue를 for문에서도 사용할 수 있다.**  
즉, for문 안의 문장을 수행하는 도중에 continue문을 만나면 for문의 처음으로 돌아가게 된다.

앞서 for문 응용 예제를 그대로 이용해서 60점 이상인 사람에게는 축하 메시지를 보내고 나머지 사람에게는 아무런 메시지도 전하지 않는 프로그램을 에디터를 이용해 작성해 보자.


```python
marks = [90, 25, 67, 45, 80]

number = 0 
for mark in marks: 
    number = number +1 
    if mark < 60:
        
    print("%d번 학생 축하합니다. 합격입니다. " % number)
```

-------------

### (4) for문과 range 함수

#### range()
range()는 숫자 리스트를 자동으로 만들어주는 함수이다.


```python
a= range(10)
b=[1,2,3,4,5,6,7,8,9,10]
a
```


```python
type(a)
```


```python
type(b)
```

range 함수로 만든 숫자 리스트의 내용을 확인하기 위해 for문을 사용해보자.


```python
for i in range(1,11):
    print(i)
```


```python
for b in a:
    print(b)
```

우리가 앞서 살펴보았던 60점 이상이면 합격이라는 문장을 출력하는 예제도 range 함수를 이용해서 바꿀 수 있다. 다음을 보자.


```python
marks = [90, 25, 67, 45, 80]

# marks 리스트의 길이를 가진 숫자 리스트를 생성함
# 생성된 숫자를 number에 넣어줌
for number in range(len(marks)):
    if marks[number] < 60: 
        continue
    print("%d번 학생 축하합니다. 합격입니다." % (number+1))
```

--------------
## <Question 08>
> **「"2단부터 9단까지 구구단을 출력하라."」**  

**Hint01)** for문을 2개 사용한다.  
**Hint02)** range함수를 사용한다.  
**Hint03)** 출력은 다음과 같이 나온다.  
  
  
2 4 6 8 10 12 14 16 18  
3 6 9 12 15 18 21 24 27  
4 8 12 16 20 24 28 32 36  
5 10 15 20 25 30 35 40 45  
6 12 18 24 30 36 42 48 54  
7 14 21 28 35 42 49 56 63  
8 16 24 32 40 48 56 64 72  
9 18 27 36 45 54 63 72 81  
  
  
여기서, 결과값을 출력할 때 다음줄로 넘기지 않고 그 줄에 계속해서 출력하기 위해선  
print문 마지막에 **end=" "**를 넣어준다.  
2단, 3단 등을 구분하기 위해 두 번째 for문이 끝나면 결과값을 다음 줄부터 출력한다.

-------------

### (5) 리스트 안에 for문 포함하기 : 리스트 내포 (List comprehension)
리스트 안에 for문을 포함하는 리스트 내포(List comprehension)를 이용하면 좀 더 편리하고 직관적인 프로그램을 만들 수 있다.  
* **List comprehension의 general format**


```python
[표현식 for 변수 in 반복자료형 if 조건]
```


```python
a = [1,2,3,4]
result = []
for num in a:
    result.append(num*3)

print(result)
```

위 예제는 a라는 리스트의 각 항목에 3을 곱한 결과를 result라는 리스트에 담는 예제이다.  
이것을 **List comprehension**을 이용하면 아래와 같이 간단히 해결할 수 있다.


```python
a = [1,2,3,4]
result = [num * 3 for num in a]
print(result)
```

앞서 배웠던 if문처럼 for문 또한 리스트 안에서 사용할 수 있다.    
  
만약 [1, 2, ,3, 4] 중에서 짝수인 2와 4에만 3을 곱하여 담고 싶다면 다음과 같이 **리스트 내포 안에 "if 조건문"** 을 사용할 수도 있다.


```python
a = [1,2,3,4]
result = [num * 3 for num in a if num % 2 == 0]
print(result)
```

조금 복잡하지만 for문을 2개 이상 사용하는 것도 가능하다.  
for문을 여러 개 사용할 때의 문법은 다음과 같다.


```python
[표현식 for 항목1 in 반복가능객체1 if 조건문1
        for 항목2 in 반복가능객체2 if 조건문2
        ...
        for 항목n in 반복가능객체n if 조건문n]
```

만약 구구단의 모든 결과를 리스트에 담고 싶다면 리스트 내포를 이용하여 아래와 같이 간단하게 구현할 수도 있다.


```python
result = [x*y for x in range(2,10)
              for y in range(1,10)]
print(result)
```

지금껏 우리는 프로그램의 흐름을 제어하는 if문, while문, for문에 대해서 알아보았다.  
아마도 여러분은 while문과 for문을 보면서 2가지가 아주 비슷하다는 느낌을 받았을 것이다.  
실제로 for문을 사용한 부분을 while문으로 바꿀 수 있는 경우도 많고, while문을 for문으로 바꾸어서 사용할 수 있는 경우도 많다.

[To Home](../index.md)  
[To Lecture List](../lecturelist.md)