## Chapter 1

Operating System으로써의 seL4

monolithic kernel에서 privileged mode로 작동하는 부분들을 user mode로 옮겨서 privileged mode에서 작동하는 코드를 최소한으로 줄인다.

privileged mode(kernel mode): 최상위 권한을 가지며 kernel code가 실행. system의 모든 memory와 hw에 대한 무제한적인 권한을 가진다. system resource관리, memory allocation, device control과 같은 중요한 작업을 수행한다. 안정성이 중요하다.

user mode: 제한된 권한을 가지며 application code가 실행된다. 할당된 memory 내부에서만 접근이 가능하며, kernel memory or HW에 접근이 불가능 하다. app 실행 중 오류 발생 시 나머지 system에 영향이 가지않도록 격리한다. HW or privileged mode가 필요할 경우 system call을 호출한다.

Hypervisor(Type1)로써의 seL4

linux같은  완벽한 기능을 갖춘 guest os를 실행할 수 있는 virtual machine을 지원한다. seL4의 communication channels하에 guest os와 그 application은 서로 통신 할 수 있으며 native application과도 통신이 가능하다

Type 1(Bare-metal): 물리적 Hw에 직접설치, Hw resource 직접 control

Type 2(Host): Host OS상에서 application 형태로 동작

seL4의 여러 특성들

- seL4는 formal, mathematical, machine-checked proof를 제공한다. 이는 올바르게 구성된 system에대해서 bug free를 의미하며 code level에서 검증된 세계 최초의 os이다.
- seL4 기반 system에서 confidentiality, integrity, availability에 대한 안전을 보장한다.
- Capability라는 seL4 system 내의 특정 자원에 대한 접근 권한을 세밀하게 제어할 수 있다. 이를 바탕으로 Principle of Least Privilege(POLA)에 따른 강력한 보안을 제공한다.
- seL4는 worst case execution time(WCET)에 대한 완전한 분석을 거친 OS이다. kernel이 제대로 설정이 되어있다면 task의 bound는 알 수 있다. 이는 hard real time system을 위한 전제조건이다.
- seL4는 신뢰도가 낮은 코드와 중요한 동작이 같은 플랫폼에서 동작이 보장되어야하는 mixed criticality real time systems(MCS)를 지원한다.
- 전통적으로 system들은 빠르거나 안전하거나 둘 중 하나였지만 seL4는 둘 다 가능하다.