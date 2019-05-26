## 문맥 교환 (Context Switching)

---

문맥 교환을 얘기하기전에 인터럽트(Interrupt)와 트랩(Trap)이 있다.

> **인터럽트(Interrupt)?**
> 현재 실행되는 프로세스와 별도로 외부에서 발생되는 여러 종류의 이벤트에 의해 발생한다.
>
> **트랩(Trap)?**
> 부적절한 파일 접근이나 현재 실행 중인 프로세스에 의해 발생되는 오류나 예외 상황 때문에 발생한다.

대부분의 운영체제에서는 프로세스 교환으로 **인터럽트**가 발생하지 않는다. 왜냐하면 **인터럽트** 처리 루틴을 실행한 후 현재 실행중인 프로세스가 재 실행될 수 있기 때문이다. 이와 달리 **트랩**은 시스템이 치명적인 오류인지 판단하여 치명적 오류이면, 프로세스를 종료하면서 프로세스 교환이 일어난다. **프로세스를 다른 프로세스로 교환하려면 이전 프로세스의 상태 레지스터 내용을 보관하고 다른 프로세스의 레지스터를 적재해야 하는데, 이런 일련의 과정을 문맥 교환(Context Switching)이라 한다.**