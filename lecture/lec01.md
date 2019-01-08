---
layout: default
---

# About Python  <!-- omit in toc -->
---
## Contents  <!-- omit in toc -->
- [Python?](#python)
- [Why Python?](#why-python)
- [Who Uses Python?](#who-uses-python)
- [What Can I Do?](#what-can-i-do)
- [The Downside?](#the-downside)

### Python?

1991년 발표된 **인터프리터** 언어. [나무위키](https://namu.wiki/w/%EC%9D%B8%ED%84%B0%ED%94%84%EB%A6%AC%ED%84%B0){: target="_blank" } , [Wikipedia](https://ko.wikipedia.org/wiki/%EC%9D%B8%ED%84%B0%ED%94%84%EB%A6%AC%ED%84%B0){: target="_blank" }
> 인터프리터 언어?
> - 컴파일러와 대조적으로 line 단위로 실행되는 언어.
> - 스크립트(script) 언어라고도 불림. 

귀도 반 로섬(Guido van Rossum)이 크리스마스 주에 연구실에서 **심심해서** 만들었다고 함..

[Python의 철학](https://www.python.org/dev/peps/pep-0020/){: target="_blank" }

### Why Python?
- **단순한 문법**
  - 코드를 봤을때 읽기 쉽게 설계.
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
  - 동적 타이핑
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

- **많은 자료**
    - `Python` 사용자가 증가하면서 참고할 자료도 매우 많아짐.
    - 다양한 라이브러리가 있고 설치도 쉬움.
      - `numpy`, `matplotlib`, `pandas`, `Pillow`, `scikit-image`, ...

- **빠른 속도**
    - 언어 자체의 실행 속도가 빠르다는 것이 아니라 개발 속도가 빠르다는 것.
    - 물론 사람마다의 개인차는 있지만 다른 언어에 비해 처음부터 배우고 개발하는데 시간이 적게 드는 편.  


### Who Uses Python?
- Google
- Yahoo
- NASA
- 카카오
- Dropbox
- ...


### What Can I Do?
- Systems Programming
- GUI
- [Game](https://www.youtube.com/watch?v=zPlJ-ma32T0){: target="_blank" }
- [Image Processing](https://opencv-python-tutroals.readthedocs.io/en/latest/_images/face.jpg){: target="_blank" }
- [Robot control](https://pythonprogramming.net/robotics-raspberry-pi-tutorial-gopigo-introduction/){: target="_blank" }
- ...

### The Downside?
-  C 또는 C++ 같은 완전한 컴파일 및 저수준 언어만큼 항상 빠르게 실행되지는 않는다.

[Back to Home](../index.md)

[Back to Lecture list](../lecturelist.md)