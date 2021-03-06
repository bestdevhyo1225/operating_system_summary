## [운영체제] 프로세스(Process)와 스레드(Thread)

---



### 프로세스 (Process)

프로세스에 대한 다양한 정의 중 가장 일반적인 것은 **'실행 중인 프로그램'** 이다.

> **실행 중인 프로그램?** 
> 디스크에 저장되어 있던 실행 가능한 프로그램이 메모리에 적재되어 운영체제의 제어를 받는 상태이다.

즉, 해당 프로세스가 사용하고 있는 메모리 영역(자신의 주소 공간)이 존재함을 의미한다.



### 프로세스 (Process) 특징

* 기본적으로 프로세스당 최소 1개의 메인 스레드를 가진다.
* 각 프로세스는 별도의 주소 공간에서 실행 된다.
* 한 프로세스는 다른 프로세스의 변수나 자료구조에 접근할 수 없다. 즉, 다른 프로세스 메모리에 접근할 수 없다. (독립적)
* 한 프로세스가 다른 프로세스의 자원을 접근하려면 프로세스 간의 통신(IPC, Inter-Process Communication)을 사용해야 한다.



### 프로세스 (Process) 주소 공간 구조

<img src="http://1.bp.blogspot.com/-tqy_yWzqWas/VMUJhhPADJI/AAAAAAAAABE/vN3AFzFtb-8/s1600/process_memory_organization.png" width="700px" height="500px">

* **실행 스택 (Stack)**
    * 호출된 프로시저(함수)의 복귀 주소와 지역 변수처럼 일시적인 데이터를 저장하는 영역이다. 

* **실행 힙 (Heap)**
    * 프로그램 실행 중 시스템 호출을 통해 사용되다가 해지되는 등 자유자재로 사용할 수 있다. 

* **데이터 (정적 변수)**
    * 전역 또는 정적 변수를 저장하는 영역이다.

* **텍스트 (코드)**
    * 프로세서가 실행하는 코드를 저장하는 영역이다.



---



### 스레드 (Thread)

**프로세스 내에서 실행되는 여러 흐름의 단위**이며, 프로세스가 할당받은 자원을 이용하는 실행의 단위이다. (작업의 흐름, 코드의 흐름)



### 스레드 (Thread) 특징

* 스레드는 프로세스 내에서 각각 Stack 영역과 레지스터 영역을 따로 할당 받는다.
* Stack 영역을 제외한 Heap, Data, Code 영역은 공유한다.



### 스레드 (Thread) 주소 공간 구조

<img src="https://gmlwjd9405.github.io/images/os-process-and-thread/thread.png" width="700px" height="400px">



---



### 정리

* 프로세스 (Process) 란? 운영체제로 부터 자원을 할당받는 작업의 단위!"
* 스레드 (Thread) 란? 프로세스가 할당받은 자원을 이용하는 실행의 단위!"



---



### 멀티 프로세스와 멀티 스레드의 차이

우선 멀티 프로세스와 멀티 스레드의 공통점은 **동시에 두 가지 이상의 루틴을 실행할 수 있는 역할**을 하는 것이다.

* **멀티 프로세스**
    여러개의 프로세스는 독립적인 메모리(Code, Data, Heap, Stack)를 가지고 있고, 프로세스 간의 통신을 하려면 IPC(Inter Process Communication)를 통해야 한다.
    
    <img src="https://t1.daumcdn.net/cfile/tistory/230A334B5822F74D08" width="500px" height="400px">

* **멀티 스레드**
    하나의 프로세스 안에 여러개의 스레드가 존재한다. 각 스레드는 Stack영역을 제외한 Code, Data, Heap영역을 공유한다.
    
    <img src="https://t1.daumcdn.net/cfile/tistory/217D00505822F78905" width="500px" height="300px">



### 멀티 프로세스 대신 멀티 스레드를 사용하는 이유?

우선 결론부터 말하자면, 여러개의 프로그램을 실행하는 것보다 하나의 프로그램에서 여러 작업을 해결하는게 효율적이기 때문이다.

* **자원의 효율성 증대**
    1. 멀티 스레드로 실행할 경우, 프로세스를 생성하여 자원을 할당하는 시스템 콜이 줄어들어 자원을 효율적으로 관리할 수 있다.
    2. 스레드는 프로세스내의 메모리를 공유하기 때문에 스레드 간 데이터를 주고 받는 것이 간단해진다.

* **처리비용 및 응답시간 단축**
    1. 프로세스 간의 통신(IPC)보다 스레드 간의 통신의 비용이 적으므로 작업들 간의 비용 부담이 줄어든다.
    2. 프로세스 간의 전환 속도보다 스레드 간의 전환 속도가 빠르다.

* **멀티 스레드에서 주의할 점!**
    1. **동기화 문제**
    2. 스레드 간의 자원 공유는 전역 변수를 이용하므로 함께 사용할 때 충돌이 발생할 수 있다.



---



### 참고사이트
* [프로세스 주소 공간 구조 이미지](https://www.google.com/search?biw=1680&bih=971&tbm=isch&sa=1&ei=TarjXOLTDsyC-QbkpLTACA&q=%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4+%EA%B5%AC%EC%A1%B0&oq=%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4+%EA%B5%AC%EC%A1%B0&gs_l=img.3..0l2j0i8i30l2.60150.60496..60627...1.0..1.93.425.5......0....1..gws-wiz-img.......0i5i30.Nn5o7CX6p-k#imgrc=FUUSEizc7i_EpM:)
* [스레드 주소 공간 구조 이미지](https://www.google.com/search?q=%EC%8A%A4%EB%A0%88%EB%93%9C+%EC%A3%BC%EC%86%8C+%EA%B3%B5%EA%B0%84+%EA%B5%AC%EC%A1%B0&source=lnms&tbm=isch&sa=X&ved=0ahUKEwjiq5Kxn6ziAhWRE4gKHQERA7cQ_AUIDigB&biw=1680&bih=971#imgrc=y4W_QzmPRsYKjM:)
* [멀티 프로세스와 멀티 스레드](https://you9010.tistory.com/136)
