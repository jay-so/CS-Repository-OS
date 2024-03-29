# 🏢 프로세스 관리_part1

---

## 👩🏻‍ 프로그램 실행 단계

---

- 프로그램을 실행하면, 해당 프로그램이 실행되어 **"프로세스"**가 됨

![1.png](..%2FImage%2F%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%20%EA%B4%80%EB%A6%AC_part1%2F1.png)

### 😶‍🌫 프로그램 실행 단계(가상 메모리)

- 프로그램이 실행될 때, 해당 프로그램만의 독자적인 주소 공간이 만들어짐

-> Virtual Memory(가상 메모리)

- 각각의 프로그램은 각각의 가상 메모리를 가짐
- 해당 프로그램을 실행하는데 꼭 필요한 메모리를 실제 메모리에 올라가게 되며, 나머지 부분은 스왑 영역으로 내려가 있게 됨

![2.png](..%2FImage%2F%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%20%EA%B4%80%EB%A6%AC_part1%2F2.png)

### 💪🏻 물리적 메모리

- 0번부터 하나의 메모리 주소로 매겨져서, 운영체제가 낮은 주소부터 높은 주소 순으로 찾음
- 가상 메모리 주소와 다른주소임
- 가상 메모리 주소에서 실제 메모리에 올려지기까지 "주소 변환"이라는 작업이 필요함

### 👓 가상 메모리 자세히 살펴보기
- Code, Data, Stack 영역들이 존재함
- Code: 실행 파일이 담겨져 있는 기계어가 담긴 코드, CPU에서 실행될 기계어가 담긴 영역
- Data: 데이터가 담긴 영역(전역변수)
- Stack: 데이터가 담긴 영역(지역 변수)


- 운영체제의 커널도 사실은 하나의 프로그램임
- 커널도 Code, Data, Stack으로 구성되어 있음 


![3.png](..%2FImage%2F%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%20%EA%B4%80%EB%A6%AC_part1%2F3.png)


### 😝 커널 주소 공간의 내용
- Code영역: 운영체제는 시스템 안에 있는 자원을 효율적으로 관리해 함
**-> 시스템을 효율적으로 관리하기 위한 코드가 담겨져 있음*
- 운영체제는 사용자 프로그램이 CPU에서 돌아가다가, 인터럽트가 발생되었을 때 및 특권명령(I/O작업)을 처리하는 시스템 콜 등을 위한 코드


- Data영역: 운영체제는 하드웨어 자원 및 프로세스를 관리하기 때문에 관리하기 위한 영역인 데이터 영역이 존재함 
- 프로세스를 관리하기 위한 **"PCB"** 라는 자료구조가 존재함


- Stack영역: 운영체제의 Stack은 특이한 구조를 가지고 있음
- 커널의 스택은 각 프로세스마다 별도로 가지고 있음 **(사용자 프로세스의 스택과의 차이점)**

![4.png](..%2FImage%2F%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%20%EA%B4%80%EB%A6%AC_part1%2F4.png)

### 🫡 사용자 프로그램이 사용하는 함수

함수(Function)
- 사용자 정의 함수
  - 자신의 프로그램에서 정의한 함수


- 라이브러리 함수
  - 자신의 프로그램에서 정의하지 않고 갖다 쓴 함수
  - 자신의 프로그램의 실행 파일에 포함되어 있음


- 커널 함수
  - 운영체제 프로그램의 함수
  - **커널 함수의 호출 = 시스템 콜**
  - **시스템 콜**
    - 사용자 프로그램이 운영체제의 서비스를 받기 위해 커널 함수를 호출하는 것

![5.png](..%2FImage%2F%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%20%EA%B4%80%EB%A6%AC_part1%2F5.png)

![6.png](..%2FImage%2F%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%20%EA%B4%80%EB%A6%AC_part1%2F6.png)


### 👩🏻‍🏫 프로그램의 실행(실행부터 종료까지)

- 사용자 모드, 커널 모드 번갈아가면서 실행됨
- 내가 정의한 코드 및 라이브러리를 통해 가져온 코드: 사용자 모드에서 CPU가 사용됨
- 운영체제에 정의된 커널의 함수를 사용할 때: 커널 모드에서 CPU가 사용됨

![7.png](..%2FImage%2F%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%20%EA%B4%80%EB%A6%AC_part1%2F7.png)

