---
layout: default
---

# 1. Numpy 란?

### Numpy 는 C언어로 구현된 파이썬 라이브러리로써, 고성능의 수치계산을 위해 제장되었습니다.

### Numpy는 Numerical Python의 줄임말이기도 한 Numpy는 벡터 및 행렬 연산에 있어서 매우 편리한 기능을 제공합니다. 

### numpy에서는 기본적으로 array라는 단위로 데이터를 관리하며 이에 대해 연산을 수행합니다. 

관례상 Scipy와 PyData를 사용하는 대부분의 사용자는 Numpy를 별칭(alias)인 np를 사용해 import 한다.



```python
import numpy as np
```


import는 파이썬에서 라이브러리를 읽기 위해 사용하는 명령어이다.

Numpy는 외부라이브러리로 본래 파이썬을 다운받을 때 존재하지 않는 라이브러리이다. 그래서 이 모듈을 가져오기 위해서 import를 사용한다.





 

 

 ## ndarray 다차원 배열 객체
 
 ---
 

ndarray는 같은 종류의 데이터를 담을 수 있는 포괄적인 다차원 배열이다. ndarray의 모든 원소는 같은 자료형이어야만 한다.


- shape : 모든 배열은 각 차원의 크기를 알려주는 튜플, 차원의 구조를 볼 때 사용 (행, 렬)로 표시됨.
 


- dtype : 배열에 저장된 자료를 알려주는 객체

 

 


```python
import numpy as np

a = np.array([1, 2, 3])  # rank가 1인 배열 생성
a.dtype
```




    dtype('int64')




```python
a.shape  
```




    (3,)




```python
b = np.array([[1,2,3],[4,5,6]])
type(b)
```




    numpy.ndarray




```python
b.shape
```




    (2, 3)



 ## **1. 1 배열 생성 함수** ###





**np.array()**


- 순서가 있는 객체(주로 리스트)를  넘겨받아 데이터가 들어있는 새로운 NumPy 배열 생성



다차원 배열 생성시 배열의 길이가 동일해야 함.



다차원 배열은 일종의 매트릭스와도 비슷하다.



순서가 있는 배열은 벡터(;크기와 방향을 가진 양; 수와 순서쌍으로 구성)와도 비슷해보임




 - np.array.ndim : 차원 수 (행)


**np.zeros , np.ones**


 - 각각 0과 1이 들어있는 배열을 생성한다.

 - 다차원 배열을 생성하려면 (행,열)로된 튜플을 넘기면 된다.





```python
np.zeros((3,4))
```




    array([[0., 0., 0., 0.],
           [0., 0., 0., 0.],
           [0., 0., 0., 0.]])



 
**np.empty**
 - 초기화가 없는 값으로 배열을 반환함



**np.arange(n)**


- 배열 버전의 range 함수, 자료형을 명시하지 않으면 float64임.









<img src="https://raw.githubusercontent.com/kkkjerry/python_camp/master/lecture/figures/ndarray.PNG">

## **2. Numpy 배열의 기초 (배열 슬라이싱 : 하위 배열에 접근하기)** ###

1차원 배열


```python
x = np.arange(10)
x
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
x[:5]
```




    array([0, 1, 2, 3, 4])




```python
x[5:]
```




    array([5, 6, 7, 8, 9])




```python
x[4:7]
```




    array([4, 5, 6])




```python
x[::2]
```




    array([0, 2, 4, 6, 8])




```python
x[1::2]
```




    array([1, 3, 5, 7, 9])




```python
x[::-1]
```




    array([9, 8, 7, 6, 5, 4, 3, 2, 1, 0])




```python
x[5::-2]
```




    array([5, 3, 1])



 

 

### **실습 문제** ###


```python
a=np.arange(13)
a
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12])



- 10부터 3 간격으로 요소를 거꾸로 나열해보자.

답변 ↓


```python
print(a[-3::-3])
```

    [10  7  4  1]


 

## **3. Numpy 배열의 기초 (배열 인덱싱 : 단일 요소에 접근하기)** ###

- 배열 인덱싱은 개별 배열 요소값을 가져오고 설정할 수 있습니다.

- square bracket 안에 원하는 인덱스 값을 지정할 수 있습니다.

- 배열의 끝에서 부터 인덱싱할려면 음수 인덱스를 사용하면 됩니다. 


```python
x1 = np.random.randint(10, size=((3,4)))
x1
```




    array([[9, 3, 4, 9],
           [6, 6, 7, 8],
           [6, 2, 1, 5]])




```python
x1[0,0]
```




    9




```python
x1[0,0] =12
x1
```




    array([[12,  3,  4,  9],
           [ 6,  6,  7,  8],
           [ 6,  2,  1,  5]])



 

 

다차원 배열에서는 콤마로 구분된 인덱스 튜플을 이용해 배열 항목에 접근할 수 있습니다.

인덱스 표기법을 사용해 값을 수정할 수도 있습니다.


```python
x2 = np.random.randint(10,size=(3,4))
x2
```




    array([[6, 4, 4, 3],
           [0, 0, 8, 8],
           [1, 4, 0, 2]])



 


```python
x2[:2,:3]
```




    array([[6, 4, 4],
           [0, 0, 8]])



 

 

## **4. 배열의 재구조화** ##

* 초기 배열의 구조가 형상이 변경된 구조의 규모와 일치해야 한다.


```python
grid = np.arange(1,10).reshape((3,3))
grid
```




    array([[1, 2, 3],
           [4, 5, 6],
           [7, 8, 9]])




```python
grid.reshape((1,9))
```




    array([[1, 2, 3, 4, 5, 6, 7, 8, 9]])




```python
grid.reshape((3,2))
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-24-df39b94ccfc8> in <module>
    ----> 1 grid.reshape((3,2))
    

    ValueError: cannot reshape array of size 9 into shape (3,2)


 

 

 

 

 ## 배열 연결 및 분할
 
 
 ### 배열 연결
 
 - Numpy에서는 주로 np.concatenate, np.vstack, np.hstack 루틴을 이용해 두 배열을 결합하거나 연결합니다. 
 


```python
x = np.array([1,2,3])
y = np.array([3,2,1])
np.concatenate([x,y])
```




    array([1, 2, 3, 3, 2, 1])



  

  

한번에 두 개 이상의 배열을 연결할 수도 있다.



```python
z=[99,99,99]
print(np.concatenate([x,y,z]))
```

    [ 1  2  3  3  2  1 99 99 99]


 

 ### np.concatenate는 2차원 배열에서도 사용할 수 있다.
 
 

 


```python
grid = np.array([[1, 2, 3],[4, 5, 6]])
```


```python
np.concatenate([grid, grid])
```




    array([[1, 2, 3],
           [4, 5, 6],
           [1, 2, 3],
           [4, 5, 6]])




```python
np.concatenate([grid, grid], axis=1)
```




    array([[1, 2, 3, 1, 2, 3],
           [4, 5, 6, 4, 5, 6]])



 

 

 

 

 

 

## **5. Numpy 배열 연산 : 유니버설 함수** ##
 
 

* 파이썬의 기본 구현에서 몇 가지 연산은 느리게 수행됩니다. 이는 부분적으로 파이썬이 동적인 인터프리터 언어이기 때문입니다. 


* 파이썬은 수많은 작은 연산이 반복되는 상황에서 확연히 느립니다.


 
 
 
 **cf) 인터프리터 언어란?**
 
 
- 소스코드를 바로 실행하는 컴퓨터 프로그램 또는 환경
- 인터프리터는 소스코드를 한줄 한줄 읽어들이면서 실행하는 프로그램
- **번역과 실행이 동시에 이루어집니다.**(별도의 실행파일이 존재하지 않습니다.)
- **자바스크립트, HTML, SQL, python,등**



**cf) 컴파일 언어란?**


- 소스코드에서 목적코드로 옮기는 것을 말합니다. 
- **번역과 실행이 따로 이루어집니다.**
- 긴 코드를 작성 해놓은 후 한번의 실행으로 해당 코드를 컴파일 과정을 거쳐 CPU에서 차례차례 실행이 되는 언어
- **C, C++, JAVA, C#등**



- NumPy는 정적 타입 체계를 가진 컴파일된 루틴에 편리한 인터페이스를 제공하는데 이를 벡터화 연산이라고 한다. 



- NumPy에서 벡터화 연산은 **NumPy 배열의 값에 반복된 연산을 빠르게 수행하는 것을 주목적으로 하는 ufuncs를 통해 구현된다.**



- 유니버설 함수는 매우 유연해서 두 배열 간의 연산도 가능하다.





 



```python
np.arange(5)/np.arange(1,6)
```




    array([0.        , 0.5       , 0.66666667, 0.75      , 0.8       ])



 

 

 

 #### 배열 산술 연산- NumPy ufuncs는 파이썬의 기본 산술 연산자를 사용한다. 


```python
x= np.arange(4)
print("x=",x)
print("x+5=",x+5)
print("x-5=",x-5)
print("x*2=",x*2)
print("x/2=",x/2)
print("x//2=",x//2) # 바닥 나눗셈( 나머지는 버림)
```

    x= [0 1 2 3]
    x+5= [5 6 7 8]
    x-5= [-5 -4 -3 -2]
    x*2= [0 2 4 6]
    x/2= [0.  0.5 1.  1.5]
    x//2= [0 0 1 1]


### 산술 연산은 사용상 편의를 위해 Numpy에 내장된 특정 함수로 감싼 것이다. 


```python
np.add(x,5)
```




    array([5, 6, 7, 8])



### 절댓값 함수에 대응하는 NumPy ufunc는 np.absolute로, np.abs라는 별칭으로도 사용가능하다.

복소수 데이터도 처리할 수 있으며, 이경우에는 절댓값은 크기를 반환한다.




```python
x=np.array([-2,-1,0,1,2])
np.abs(x)
```




    array([2, 1, 0, 1, 2])




```python
np.absolute(x)
```




    array([2, 1, 0, 1, 2])




```python
x=np.array([3-4j, 4-3j, 2+0j, 0+1j])
np.abs(x)
```




    array([5., 5., 2., 1.])



### 삼각함수  - 데이터에서 가장 유용한 함수 중 일부는 삼각함수이다. 



```python
theta = np.linspace( 0, np.pi, 3)

print("theta = ", theta)
print(" sin(theta)= ", np.sin(theta))
print(" cos(theta)= ", np.cos(theta))
print(" tan(theta)= ", np.tan(theta))

```

    theta =  [0.         1.57079633 3.14159265]
     sin(theta)=  [0.0000000e+00 1.0000000e+00 1.2246468e-16]
     cos(theta)=  [ 1.000000e+00  6.123234e-17 -1.000000e+00]
     tan(theta)=  [ 0.00000000e+00  1.63312394e+16 -1.22464680e-16]


### 지수와 로그


```python
x=[1,2,3]
print("x = ",x)
print("e^x = ", np.exp(x) )
print("2^x =", np.exp2(x))
print("3^x =", np.power(3, x))
```

    x =  [1, 2, 3]
    e^x =  [ 2.71828183  7.3890561  20.08553692]
    2^x = [2. 4. 8.]
    3^x = [ 3  9 27]



```python
x = [1, 2, 4, 10]
print("x =", x)
print("ln(x) =", np.log(x))
print("log2(x) =", np.log2(x))
print("log10(x) =", np.log10(x))
```

    x = [1, 2, 4, 10]
    ln(x) = [0.         0.69314718 1.38629436 2.30258509]
    log2(x) = [0.         1.         2.         3.32192809]
    log10(x) = [0.         0.30103    0.60205999 1.        ]


## 출력지정

* 대규모 연산인 경우, 연산 결과를 저장할 배열을 지정하는 것이 유용할 대가 있다. 임시배열을 생성하지 않고 지정한 배열을 이용해 원하는 메모리 위치에 직접 연산 결과를 쓸 수 있다. 


* 모든 ufuncs 에서 함수의 out 인수를 사용해 출력을 지정할 수 있다.


```python
x = np.arange(5)
y = np.empty(5)
np.multiply(x, 10, out=y)
print(y)
```

    [ 0. 10. 20. 30. 40.]



```python
y = np.zeros(10)
np.multiply(2, x, out=y[::2])
print(y)
```

    [0. 0. 2. 0. 4. 0. 6. 0. 8. 0.]


## 집계




* 배열을 특정 연산으로 축소하고자 한다면 reduce 메서드를 사용하면 됩니다. 


* reduce 메서드는 결과가 하나만 남을 때까지 해당 연산을 배열 요소에 반복해서 적용합니다.




```python
x = np.arange(1, 6)
np.add.reduce(x)
```




    15




```python
np.multiply.reduce(x)
```




    120



* 계산의 중간 결과를 모두 저장하고 싶다면 reduce 대신 accumulate 를 사용하면 됩니다. 


```python
x = np.arange(1, 6)
np.add.accumulate(x)
```




    array([ 1,  3,  6, 10, 15])




```python
np.multiply.accumulate(x)
```




    array([  1,   2,   6,  24, 120])



## 6. 브로드 캐스팅

느린 파이썬 루프를 제거하기 위해 연산을 벡터화 하는 NumPy의 유니버설 함수 사용법을 했었다. 


벡터화 연산의 또 다른 방법은 NumPy의 브로드 캐스팅 기능을 사용하는 것이다.



### 브로드캐스팅은 단지 다른 크기의 배열에 유니버설 함수(덧셈, 뺄셈, 곱셈 등)를 적용하기 위한 규칙의 집합이다.



```python
a = np.array([1,2,3])
b=np.array([1,2])

a+b
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-45-cc3620bbd4ac> in <module>
          2 b=np.array([1,2])
          3 
    ----> 4 a+b
    

    ValueError: operands could not be broadcast together with shapes (3,) (2,) 


<img src="https://raw.githubusercontent.com/kkkjerry/python_camp/master/lecture/figures/broadcasting.PNG">

브로드캐스팅은 어떤 조건만 만족한다면 모양이 다른 배열끼리의 연산도 가능하게 해주며 모양이 부족한 부분은 확장하여 연산을 수행할 수 있도록 한다.


확장 또는 전파한다는 의미로 Broadcasting을 설명하는 가장 간단한 예는 배열과 스칼라 값을 계산하는 것이다.

- 스칼라는 일반 상수를 생각하면 된다.




   
 

위의 그림에서는 첫 번째 그림에 해당하는 것으로 0, 1, 2라는 NumPy로 생성한 배열에 스칼라 5를 합한 결과가 5, 6, 7이라는 것을 알 수 있다. 일반적인 파이썬 리스트를 사용하면 for문을 이용해야 같은 결과를 얻을 수 있지만, NumPy에서는 브로드캐스팅의 개념 덕분에 5가 0이외에 1과 2의 원소 부분에도 전파(broadcast)되어 계산되어 간단하게 합 연산을 수행하는 것만으로 같은 결과를 얻을 수 있었다. 


두 번째 그림은 배열 간의 계산으로 배열의 차원이 확대된 케이스이다. 두 번째 그림은 3x3 배열에 1x3 배열을 합 연산한 경우이다. 각 행에 동일한 계산을 전파한 것을 볼 수 있다. 

 세번째 그림은 브로드캐스팅의 확장성 측면을 극명하게 보여주는 케이스이다. 3x1 배열과 1x3 배열의 합을 했는데 두 번째에서는 한쪽의 더 낮은 차원의 배열에서만 아래(0번 축) 방향으로 broadcast한 것에 반해 양 쪽 배열에서 broadcast한 것을 확인할 수 있다.

  **브로드캐스팅이 일어날 수 있는 조건은 다음과 같다.**
  
      • 규칙 1 : 두 배열의 차원 수가 다른 경우 치수가 더 작은 배열의 모양에 선행 (왼쪽)면이있는 모양이 채워집니다.



      • 규칙 2 : 두 배열의 모양이 임의의 차원에서 일치하지 않으면 해당 차원의 모양이 1 인 배열이 다른 모양과 일치하도록 늘어납니다.



      • 규칙 3 : 크기가 어느 정도라도 크기가 일치하지 않고 둘 다 1과 같으면 오류가 발생합니다.


```python
a = np.array([1,2,3])
b=np.array([1,2])

a+b
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-46-cc3620bbd4ac> in <module>
          2 b=np.array([1,2])
          3 
    ----> 4 a+b
    

    ValueError: operands could not be broadcast together with shapes (3,) (2,) 



```python
b.shape=(2,1)

a+b
```




    array([[2, 3, 4],
           [3, 4, 5]])




```python
np.ones((3,1))
```




    array([[1.],
           [1.],
           [1.]])




```python
np.arange(3)
```




    array([0, 1, 2])




```python
np.ones((3,3))+np.arange(3)
```




    array([[1., 2., 3.],
           [1., 2., 3.],
           [1., 2., 3.]])



## 비교, 마스크, 부울 로직



<img src="https://raw.githubusercontent.com/kkkjerry/python_camp/master/lecture/figures/dd.PNG">

### Numpy는 요소단위의 유니버셜 함수로 비교연산자도 구현한다.

* 이 비교 연산자의 결과는 항상 부울 타입의 배열입니다.



```python
rng = np.random.RandomState(0)
x = rng.randint(10, size=(3, 4))
x
```




    array([[5, 0, 3, 3],
           [7, 9, 3, 5],
           [2, 4, 7, 6]])




```python
x < 6
```




    array([[ True,  True,  True,  True],
           [False, False,  True,  True],
           [ True,  True, False, False]])




```python
# 8보다 큰 값이 하나라도 있는가
np.any(x > 8)
```




    True




```python
#0보다 작은 값이 하나라도 있는가?
np.any(x < 0)
```




    False




```python
#모든 값이 10보다 작은가
np.all(x<10)
```




    True




```python
#모든 값이 6과 같은가?
np.all(x==6)
```




    False



## 값 중 하나라도 참이 있는지나 모든 값이 참인지 빠르게 확인하고 싶을때 np.any() 나 np.all()을 사용하면 된다.

* np.all 과 np.any는 특정 축을 따라 사용할 수도 있습니다,


```python
# 각 행의 모든 값이 8보다 작은가
np.all(x < 8, axis=1)
```




    array([ True, False,  True])



axis =0 세로 열,


axis =1 가로 행


## 마스크로서의 부울 배열

* 부울 배열을 마스크로 사용해 데이터 자체의 특정 부분 집합을 선택할 수 있습니다.

* 부울 배열을 인덱스로 사용해서 조건에 맞는 값을 선택할 수 있습니다. 이를 마스킹 연산이라고 합니다.


```python
x
```




    array([[5, 0, 3, 3],
           [7, 9, 3, 5],
           [2, 4, 7, 6]])




```python
x < 5
```




    array([[False,  True,  True,  True],
           [False, False,  True, False],
           [ True,  True, False, False]])




```python
x[x < 5]
```




    array([0, 3, 3, 3, 2, 4])



### 반환된 값은 이 조건에 맞는 모든 값, 마스크 배열이 True인 위치에 있는 모든 값으로 채워져서 출력이 됩니다.


## 팬시인덱싱

### 팬시인덱싱은 정수 리스트를 이용해서 여러 개를 동시에 선택하는 방식입니다. 


```python
import numpy as np
rand = np.random.RandomState(42)
x = rand.randint(100, size=10)
print(x)
```

    [51 92 14 71 60 20 82 86 74 74]



```python
[x[3], x[7], x[2]]
```




    [71, 86, 14]



세 개의 다른 요소에 접근하고자 할 때, 다음과 같이 할 수 있습니다.



```python
ind = [3, 7, 4]
x[ind]
```




    array([71, 86, 60])



인덱스의 단일 리스트나 배열을 전달해서 팬시인덱싱을 할 수도 있습니다.


```python
X = np.arange(12)
X
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11])




```python
i =  np.array([2,4,6,8,10])
X[i]=0
print(X)
```

    [ 0  1  0  3  0  5  0  7  0  9  0 11]


# Pandas

## Pandas는 파이썬에서 사용하는 데이터 분석, 데이터 처리 등을 쉽게 하기 위해 만들어진 라이브 러리 입니다.



* 테이블을 수정하고 조작하는 다양한 기능 제공


* SQL, 엑셀파일, CSV 파일과 데이터 베이스의 데이터를 읽어들임

## 1. Pandas 자료구조

### Pandas는 Series, DataFrame 두 자료 구조가 가장 중요합니다.

## 1-1 Series

### 1차원 배열 같은 구조입니다. 


```python
import pandas as pd
```

### Series 정의하기


```python
obj = pd.Series([4,1,2,3])
obj
```




    0    4
    1    1
    2    2
    3    3
    dtype: int64



### Series의 값만 확인하기


```python
obj.values
```




    array([4, 1, 2, 3])



### Series의 인덱스만 확인하기


```python
obj.index
```




    RangeIndex(start=0, stop=4, step=1)



### Series의 자료형 확인하기


```python
obj.dtypes
```




    dtype('int64')



### 인덱스를 변경할수도 있습니다.


```python
obj2=pd.Series([20,21,25,4],index=['a','b','c','d'])
obj2
```




    a    20
    b    21
    c    25
    d     4
    dtype: int64



### dictionary 자료형을 Series data로 만들 수 있습니다.

### dictionary의 key가 Series의 index가 됩니다.




```python
data = {'Hong':27,'Yang':25,'Kim':27}
obj3=pd.Series(data)
obj3
```




    Hong    27
    Yang    25
    Kim     27
    dtype: int64



자료들의 이름을 지정해 줄수도 있다.



```python
obj3.name = 'Lab'
```


```python
obj3
```




    Hong    27
    Yang    25
    Kim     27
    Name: Lab, dtype: int64




```python
obj3.index.name = "NAMES"
```


```python
obj3
```




    NAMES
    Hong    27
    Yang    25
    Kim     27
    Name: Lab, dtype: int64



## Series를 사용하는 이유는 values 와 index 속성으로 접근할 수 있습니다.


```python
obj3[:'Yang']
```




    NAMES
    Hong    27
    Yang    25
    Name: Lab, dtype: int64




```python
obj3[0:3]
```




    NAMES
    Hong    27
    Yang    25
    Kim     27
    Name: Lab, dtype: int64




```python
population_dict = {'California': 38332521,'Texas': 26448193,'New York': 19651127,'Florida': 19552860,'Illinois': 12882135}

population = pd.Series(population_dict)
population
```




    California    38332521
    Texas         26448193
    New York      19651127
    Florida       19552860
    Illinois      12882135
    dtype: int64



### 원하는 인덱스만 지정해서 값을 출력할 수 도 있습니다.


```python
 pd.Series(population_dict,index=['Texas','Florida'])
```




    Texas      26448193
    Florida    19552860
    dtype: int64



## Pandas DataFrame 객체

## Series가 유연한 인덱스를 가지는 1차원 배열이라면 

## DataFrame은 유연한 행 인덱스와 유연한 열 이름을 가진 2차원 배열이라고 볼수 있습니다.


```python
population_dict = {'California': 38332521,'Texas': 26448193,'New York': 19651127,'Florida': 19552860,'Illinois': 12882135}

area_dict = {'California': 423967, 'Texas': 695662, 'New York': 141297,'Florida': 170312, 'Illinois': 149995}
area =pd.Series(area_dict)
```


```python
area
```




    California    423967
    Texas         695662
    New York      141297
    Florida       170312
    Illinois      149995
    dtype: int64




```python
states = pd.DataFrame({'population': population,'area': area})
states
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>population</th>
      <th>area</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>California</th>
      <td>38332521</td>
      <td>423967</td>
    </tr>
    <tr>
      <th>Texas</th>
      <td>26448193</td>
      <td>695662</td>
    </tr>
    <tr>
      <th>New York</th>
      <td>19651127</td>
      <td>141297</td>
    </tr>
    <tr>
      <th>Florida</th>
      <td>19552860</td>
      <td>170312</td>
    </tr>
    <tr>
      <th>Illinois</th>
      <td>12882135</td>
      <td>149995</td>
    </tr>
  </tbody>
</table>
</div>




```python
states.index
```




    Index(['California', 'Texas', 'New York', 'Florida', 'Illinois'], dtype='object')




```python
states.columns
```




    Index(['population', 'area'], dtype='object')



## DataFrame은 열 이름을 열데이터로 이뤄진 Series로 매핑합니다.

 


```python
states['area']
```




    California    423967
    Texas         695662
    New York      141297
    Florida       170312
    Illinois      149995
    Name: area, dtype: int64



### 위에서 보는거와 같이 열 이름을 넣었을 때 DataFrame형식이 아닌 Series 형태로 나오는 것을 확인할 수 있습니다.


```python
pd.DataFrame(population,columns=['area'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>area</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>California</th>
      <td>38332521</td>
    </tr>
    <tr>
      <th>Texas</th>
      <td>26448193</td>
    </tr>
    <tr>
      <th>New York</th>
      <td>19651127</td>
    </tr>
    <tr>
      <th>Florida</th>
      <td>19552860</td>
    </tr>
    <tr>
      <th>Illinois</th>
      <td>12882135</td>
    </tr>
  </tbody>
</table>
</div>



## Series와 마찬가지로 DataFrame의 index와 columns에 이름을 붙일 수 있습니다


```python
data={"name":["용기","재은","태진","재열"],"Year":[1993,1995,1992,1993],"number":[1,2,3,4]}
df=pd.DataFrame(data)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>Year</th>
      <th>number</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>용기</td>
      <td>1993</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>재은</td>
      <td>1995</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>태진</td>
      <td>1992</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>재열</td>
      <td>1993</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.index.name ="Num"
df.columns.name = "Info"
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Info</th>
      <th>name</th>
      <th>Year</th>
      <th>number</th>
    </tr>
    <tr>
      <th>Num</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>용기</td>
      <td>1993</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>재은</td>
      <td>1995</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>태진</td>
      <td>1992</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>재열</td>
      <td>1993</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>



### 딕셔너리에서 정의한 키값을 인자로 columns에 직접 넣어 columns의 순서를 새롭게 정의할 수 있으며, 키값이 미리 존재하지 않는 이름을 columns 인자의 성분으로 넣는다면, 그 columns 은 NaN으로 표시됩니다. 

(NaN은 Not a Number를 의미하며, 해당하는 값이 없다는 뜻입니다.)


```python
df2=pd.DataFrame(data,columns=["Year","name","number","project"])
```


```python
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>name</th>
      <th>number</th>
      <th>project</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1993</td>
      <td>용기</td>
      <td>1</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1995</td>
      <td>재은</td>
      <td>2</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1992</td>
      <td>태진</td>
      <td>3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1993</td>
      <td>재열</td>
      <td>4</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



## DataFrame에서 열을 선택(인덱싱)하여 조작하기


### 하나의 열을 가져오는 방법은 2가지이다.

DataFrame 변수["칼럼명"]
1. df["컬럼이름"]



2. df.컬럼이름

DataFrame에서 하나의 열을 가져온 결과는 Series의 모양을 하고 있다


```python
df2["name"]
```




    0    용기
    1    재은
    2    태진
    3    재열
    Name: name, dtype: object




```python
df2.name
```




    0    용기
    1    재은
    2    태진
    3    재열
    Name: name, dtype: object





### 2개 이상의 열을 가져오는 방법은 df[["컬럼이름1","컬럼이름2"]]의 방법으로 가져온다.


```python
df2[["Year","name"]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1993</td>
      <td>용기</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1995</td>
      <td>재은</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1992</td>
      <td>태진</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1993</td>
      <td>재열</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>name</th>
      <th>number</th>
      <th>project</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1993</td>
      <td>용기</td>
      <td>1</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1995</td>
      <td>재은</td>
      <td>2</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1992</td>
      <td>태진</td>
      <td>3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1993</td>
      <td>재열</td>
      <td>4</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



### 선택된 열의 모든 성분에 값을 대입할 수도 있습니다.


```python
df2["project"]="Ai"
```


```python
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>name</th>
      <th>number</th>
      <th>project</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1993</td>
      <td>용기</td>
      <td>1</td>
      <td>Ai</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1995</td>
      <td>재은</td>
      <td>2</td>
      <td>Ai</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1992</td>
      <td>태진</td>
      <td>3</td>
      <td>Ai</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1993</td>
      <td>재열</td>
      <td>4</td>
      <td>Ai</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2["project"]=["Ai","Ai","Ai","PET"]
```


```python
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>name</th>
      <th>number</th>
      <th>project</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1993</td>
      <td>용기</td>
      <td>1</td>
      <td>Ai</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1995</td>
      <td>재은</td>
      <td>2</td>
      <td>Ai</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1992</td>
      <td>태진</td>
      <td>3</td>
      <td>Ai</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1993</td>
      <td>재열</td>
      <td>4</td>
      <td>PET</td>
    </tr>
  </tbody>
</table>
</div>



### 새로운 열을 생성과 동시에 대입할 수도 있습니다.


```python
df2["grade"]=["4학년","대학원생","대학원생","대학원생"]
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>name</th>
      <th>number</th>
      <th>project</th>
      <th>grade</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1993</td>
      <td>용기</td>
      <td>1</td>
      <td>Ai</td>
      <td>4학년</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1995</td>
      <td>재은</td>
      <td>2</td>
      <td>Ai</td>
      <td>대학원생</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1992</td>
      <td>태진</td>
      <td>3</td>
      <td>Ai</td>
      <td>대학원생</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1993</td>
      <td>재열</td>
      <td>4</td>
      <td>PET</td>
      <td>대학원생</td>
    </tr>
  </tbody>
</table>
</div>



### DataFrame의 하나의 열을 선택했을 때 Series로 제공된다는 점에서 착안하여, 새로운 열을 입력할 때도, 리스트가 아닌 Series를 대입해 줄 수도 있습니다. 


```python
add=pd.Series([1,2,3,4],index=[3,2,1,0])
df2["등수"]=add
```


```python
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>name</th>
      <th>number</th>
      <th>project</th>
      <th>grade</th>
      <th>등수</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1993</td>
      <td>용기</td>
      <td>1</td>
      <td>Ai</td>
      <td>4학년</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1995</td>
      <td>재은</td>
      <td>2</td>
      <td>Ai</td>
      <td>대학원생</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1992</td>
      <td>태진</td>
      <td>3</td>
      <td>Ai</td>
      <td>대학원생</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1993</td>
      <td>재열</td>
      <td>4</td>
      <td>PET</td>
      <td>대학원생</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



### Series를 만들어서 대입하는 이유는, Series를 정의할 때, 기존의 행 index와 동일한 이름으로 주면, 맞춰서 끼어들어가는 특징을 이용할 수 있기 때문입니다.

## 행과 열 바꾸기

* T를 이용해 열과 행을 바꿔 줄수 있습니다.


```python
df2.T
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Year</th>
      <td>1993</td>
      <td>1995</td>
      <td>1992</td>
      <td>1993</td>
    </tr>
    <tr>
      <th>name</th>
      <td>용기</td>
      <td>재은</td>
      <td>태진</td>
      <td>재열</td>
    </tr>
    <tr>
      <th>number</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
      <td>4</td>
    </tr>
    <tr>
      <th>project</th>
      <td>Ai</td>
      <td>Ai</td>
      <td>Ai</td>
      <td>PET</td>
    </tr>
    <tr>
      <th>grade</th>
      <td>4학년</td>
      <td>대학원생</td>
      <td>대학원생</td>
      <td>대학원생</td>
    </tr>
    <tr>
      <th>등수</th>
      <td>4</td>
      <td>3</td>
      <td>2</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
score ={"수학":[30,90],"영어":[60,100]}
df3= pd.DataFrame(score,index=["철수","영희"])
df3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>수학</th>
      <th>영어</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>철수</th>
      <td>30</td>
      <td>60</td>
    </tr>
    <tr>
      <th>영희</th>
      <td>90</td>
      <td>100</td>
    </tr>
  </tbody>
</table>
</div>




```python
df3.T
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>철수</th>
      <th>영희</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>수학</th>
      <td>30</td>
      <td>90</td>
    </tr>
    <tr>
      <th>영어</th>
      <td>60</td>
      <td>100</td>
    </tr>
  </tbody>
</table>
</div>

[To Home](../index.md)  
[To Lecture List](../lecturelist.md)
