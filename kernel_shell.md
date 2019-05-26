## 리눅스(Linux)의 커널(Kernel)과 쉘(Shell)

---



### 커널(Kernel) 이란?

* 리눅스에서 커널(Kernel)은 하드웨어를 직접 제어하는 역할을 한다.
* 리눅스 운영체제에서의 핵심으로서 프로세스(Process)관리, 메모리 관리, I/O 시스템 관리, 파일 시스템 관리 등을 수행한다. 



### 쉘(Shell) 이란?

* 쉘(Shell)은 커널(Kernel)에 명령을 주는 하나 이상의 쉘(Shell)로 구성되어 있다.
* 사용자(User)와 내부 커널(Kernel)사이의 인터페이스 역할을 한다. (명령어 해석기)
* 사용자(User)는 리눅스 OS와 상호작용을 하게 된다.
* 사용자



### 리눅스(Linux) OS의 구성 계층도

<img src="http://testingpool.com/wp-content/uploads/2015/09/UNIX-Architecture.png" width="750px" height="550px">



### 쉘(Shell)과 커널(Kernel)을 구분하는 이유는 무엇일까?

운영체제의 핵심은 커널(Kernel)이지만 사용자가 바로 커널(Kernel)을 제어하기는 매우 어렵다. (기계적인 부분이 많기 때문에..) 그래서 사용자가 내린 명령을 운영체제의 핵심인 커널(Kernel)이 이해할 수 있도록 번역해주는 프로그램이 필요했다. 이 번역장치에 해당하는게 쉘(Shell)이다. 그래서 우리가 운영체제라고 부르는 프로그램은 크게 커널(Kernel)과 쉘(Shell)로 구성 된다.



### 참고사이트

* [리눅스의 커널(Kernel)과 쉘(Shell)](http://studymake.blogspot.com/2015/05/kernel-shell.html)
* [리눅스 OS의 구성 계층도 이미지](http://testingpool.com/the-unix-architecture/)
* [리눅스#2 커널(Kernel)과 쉘(Shell)](https://hackingzone.tistory.com/5)