# 🏢 운영체제 개요 - Part1

---

## 📞 운영체제란 무엇인가?

---

- **컴퓨터 하드웨어 바로 위에 설치되어 사용자 및 다른 모든 소프트웨어와 하드웨어를 연결하는 계층**

-> 사용자가 컴퓨터 하드웨어를 몰라도 소프트웨어를 사용할 수 있게 하는 것이 목적임

![1.png](..%2FImage%2F%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C%20%EA%B0%9C%EC%9A%94_part1%2F1.png)

<br/>

## 🎯 운영 체제의 목적

---

1. 컴퓨터 시스템을 **편리하게 사용할 수 있는 환경을 제공함**

- 운영체제는 동시 사용자/ 프로그램들이 각각 독자적 컴퓨터에서 수행되는 것 같은 환상을 제공함(프로그램 입장에서는 혼자서 컴퓨터를 사용하는듯한 현상)
- 하드웨어를 직접 다루는 복잡한 부분을 운영체제가 대행함

![2.png](..%2FImage%2F%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C%20%EA%B0%9C%EC%9A%94_part1%2F2.png)


2. 컴퓨터 시스템의 **자원을 효율적으로 관리함**

- 컴퓨터 자원 = CPU, 메모리, I/O 장치
  - CPU, 메모리, I/O 장치 등의 효율적 관리
  - 메모리 = CPU의 작업 공간
  => 운영체제가 각 프로그램마다 적절히 메모리 공간을 분배함

- 주어진 자원으로 최대한의 성능을 내도록 => 효율성
- 특정 사용자/ 프로그램의 지나친 불이익이 발생하지 않도록 => 형평성
- 사용자 및 운영체제 자신의 보호

![3.png](..%2FImage%2F%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C%20%EA%B0%9C%EC%9A%94_part1%2F3.png)

<br/>

## 🤖 컴퓨터 시스템의 구조

---

- 좌측: 컴퓨터 내부 디바이스
- 우측: 컴퓨터 외부 디바이스
  - 하드 디스크 = 외부 디바이스로 볼 수 있으며, I/O 디바이스로 입력과 출력이 가능한 장치로 봄
![4.png](..%2FImage%2F%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C%20%EA%B0%9C%EC%9A%94_part1%2F4.png)

<br/>

## 📅 운영체제의 기능

---

- 운영체제는 컴퓨터가 실행되면 메모리에 올라가게 되어, 컴퓨터가 종료될 때까지 유지됨
- 커널 = 컴퓨터가 실행하는 동안 메모리 공간에 존재함
- 메모리 = CPU의 작업 공간
  - 매순간 CPU는 메모리의 내용을 읽어서 실행함
- CPU는 디스크나 외부 I/O 장치를 직접 접근할 수 없음
=> 프로그램이 실행되다가 만약 CPU가 **디스크의 내용이 필요하다면, I/O 컨트롤러를 통해 해당 내용을 읽어옴**

1. **CPU 스케줄링:** 어떤 프로그램에서 CPU 사용권을 줄지, 얼마동안 줄지 결정하는 스케줄링
2. **메모리 관리:** 한정된 메모리를 쪼개서 각 프로그램에게 할당함
3. **디스크 스케줄링:** 디스크에 들어온 요청에 대한 순서 처리를 할지 결정함
   - 프로그램 A,B,C로 부터 디스크의 내용을 읽어들어올 때, 디스크의 내용을 어떻게 읽으면 효율적인지 계산을 함
4. **인터럽트, 캐싱:** 빠른 CPU와 느린 I/O 장치간 속도 차를 극복하는 방법을 제시함
   - 캐싱: 메모리와 디스크에서도 속도 차이가 있기 때문에, 똑같은 데이터를 읽을 경우 디스크에서 읽어오는 것이 아닌 메모리 공간에 복사본으로 존재하여 해당 방법을 해결함
   - 인터럽트: 프로그램의 I/O 작업이 있을 때, I/O 컨트롤러에게 해당 내용을 위임하고 CPU는 당장 다른 프로그램을 실행하고, I/O 컨트롤러를 통해 디스크에게 모두 읽어왔을 때 CPU에게 인터럽트를 걸어 알려줌
   - CPU는 매 프로그램이 끝날때마다, 인터럽트를 체킹함
   - 인터럽트 요청이 오면, CPU는 무조건 운영체제에게 넘어가고 인터럽트를 체킹하고 다음 CPU 스케줄링에 실행될 수 있도록 함
![5.png](..%2FImage%2F%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C%20%EA%B0%9C%EC%9A%94_part1%2F5.png)

<br/>

## 🧑🏻‍🎨 프로세스의 상태

---

- 프로세스 = 실행중인 프로그램
- CPU는 1개이며, 나머지 프로그램이 CPU를 사용하고 싶을때, CPU 큐를 만들어서 해당 작업들을 줄 세워둠

-> CPU 스케줄링 = 운영체제가 해당 스케줄링을 관리함

- CPU 스케줄링에 의해 해당 내용을 모두 끝낼때까지 CPU를 점유하는 것이 아닌, 해당 순간동안 CPU를 쓰게하고, 이후에 CPU 큐 맨 뒤에 두는 형식으로 다음 작업이 CPU를 쓰게 하는 방식으로 프로그램이 실행됨
- CPU에서 실행되는 프로그램이 디스크에 잇는 파일을 읽어와야 하는 경우, CPU에서 디스크로 옮기게 되고, 디스크 입출력 큐에 대기하도록 하고 다음 프로그램을 실행하도록함

-> 만약 디스크 입/출력 과정이 끝나면, 디스크 입출력 큐에서 해당 내용을 빼서 CPU 큐에 대기하도록 함
=> 키보드 입출력 큐도 동일한 방식으로 작동함(웹 서핑 작업 등)
- Interactive Application = CPU와 I/O를 반복하여 사람과 인터액티브하는 프로그램 
- Scientific Application = I/O작업 없이 CPU만 작업하는 프로그램
![6.png](..%2FImage%2F%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C%20%EA%B0%9C%EC%9A%94_part1%2F6.png)

<br/>

## 📖 Reference

---

[KOCW 반효경 교수님 - 운영제체](http://www.kocw.net/home/cview.do?cid=4b9cd4c7178db077)

[운영체제와 정보기술의 원리 - 반효경 교수님](https://www.aladin.co.kr/shop/wproduct.aspx?ISBN=K762639583&start=pnaver_02)