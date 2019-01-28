---
layout: default
---

# 4-2 Input & Output
---

## 1. Input
- **input** 을 이용하여 사용자의 입력을 받을 수 있음.
- **String** 으로 취급한다는 것을 주의.


```python
a = input()
print(a)
print(type(a))
```


```python
a = input("마음대로 입력해보세요 : ")
print(a)
```


```python
a = int(input("숫자를 입력해보세요 : "))
print(a)
print(type(a))
```

## 2. Output
- **print** 를 이용하여 출력.


```python
x = 'test'
y = 99
z = ['hello', 'python']

print(x, y, z)
```

``` python
print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
```

[About **print**](https://docs.python.org/ko/3/library/functions.html#print)


```python
print(x, y, z, sep=', ')
```


```python
print(x, y, z, end='')
```


```python
print(x, y, z, file=open('test.txt', 'w'))
```


```python
for x in [1,2,3,4,5,6,7,8,9]:
    print(x, end=' ')
```


```python
for x in [1,2,3,4,5,6,7,8,9]:
    for y in [1,2,3,4,5,6,7,8,9]:
        print(x*y, end=' ')
    print()
```

[To Home](../index.md)  
[To Lecture List](../lecturelist.md)