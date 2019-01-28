---
layout: default
---

# About Python <!-- omit in toc -->
---
## Contents <!-- omit in toc -->

  - [Python?](#python)
  - [Why we use Python?](#why-we-use-python)
  - [Who uses Python?](#who-uses-python)
  - [What can we do?](#what-can-we-do)
  - [The Downside?](#the-downside)
---

### Python?

**인터프리터** 언어 중 하나. [나무위키](https://namu.wiki/w/%EC%9D%B8%ED%84%B0%ED%94%84%EB%A6%AC%ED%84%B0) , [Wikipedia](https://ko.wikipedia.org/wiki/%EC%9D%B8%ED%84%B0%ED%94%84%EB%A6%AC%ED%84%B0)  
귀도 반 로섬(Guido van Rossum)이 1989년에 크리스마스 주에 연구실에서 **심심해서** 만들었다고 함..
> 인터프리터 언어?
> - 컴파일러와 대조적으로 line 단위로 실행되는 언어.
> - 스크립트(script) 언어라고도 불림. 



[Python의 철학](https://www.python.org/dev/peps/pep-0020/)
    - Beautiful is better than ugly.
    - Explicit is better than implicit.
    - Simple is better than complex.
    - Complex is better than complicated.
    - Readability counts.
    - ....

### Why we use Python?
- **인터프리터 언어**
    - line 단위 실행 -> 결과 -> 수정의 절차를 가짐.
    
- **Cross-flatform**
    - 윈도우, 리눅스, 맥OS 등 다양한 운영체제에서 실행이 가능.
    
- **동적 타이핑**
    - C, C++ 에서 처럼 타입이나 크기에 대한 선언을 요구하지 않음.

    ``` c
    // Using C
    int *array = new int[3];
    array[0] = 1;
    array[1] = 3;
    array[2] = 5;
    ```

    ``` python
    # Using Python
    array = [1,3,5]
    ```
    
    
- **단순한 문법**
  - "Hello, World" 출력 예시.
    ``` c
    // Using C
    #include <stdio.h>
    int main(){
        printf("Hello, World!");
        return 0;
    }
    ```

    ``` python
    # Using Python
    print("Hello, World!")
    ```
    

- **많은 자료**
    - `Python` 사용자가 증가하면서 참고할 자료도 매우 많아짐.
    - 다양한 라이브러리가 있고 설치도 쉬움.
      - `numpy`, `matplotlib`, `pandas`, `Pillow`, `scikit-image`, ...


- **확장성**
    - C, C++등 다른 언어로 만든 프로그램을 쉽게 접근해서 파이썬에서 사용이 가능.
    
    
- **개발 기간 단축**
    - 물론 사람마다의 개인차는 있지만 다른 언어에 비해 처음부터 배우고 개발하는데 시간이 적게 드는 편.  


### Who uses Python?
[파이썬 사용현황](https://ko.wikipedia.org/wiki/%ED%8C%8C%EC%9D%B4%EC%8D%AC#%EC%82%AC%EC%9A%A9_%ED%98%84%ED%99%A9)
- Google
- Yahoo
- NASA
- 카카오
- Dropbox
- ...

### What can we do?
[List of Python software](https://en.wikipedia.org/wiki/List_of_Python_software)
- Systems Programming
- GUI
- [Game](https://www.youtube.com/watch?v=zPlJ-ma32T0)
- [Image Processing](https://opencv-python-tutroals.readthedocs.io/en/latest/_images/face.jpg)
- [Robot control](https://pythonprogramming.net/robotics-raspberry-pi-tutorial-gopigo-introduction/)
- ...

### The Downside?
-  **느.리.다.**
    - C 또는 C++ 같은 완전한 컴파일 및 저수준 언어만큼 항상 빠르게 실행되지는 않는다.


[To Home](../index.md)  
[To Lecture List](../lecturelist.md)