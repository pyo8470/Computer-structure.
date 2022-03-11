# Computer-structure.

# 1주차
중간 30 기말 30 과제 20 퀴즈 10

# 1과제 : 자기 PC사양 조사

## 성능에 영향을 미치는 것
> 1. 알고리즘
> > - 연산횟수를 정함
> 2. 언어, 컴파일러, 아키텍처
> > - cpu 내부에서 돌아가는 연산의 횟수가 달라짐
> > - 예를들어 자바와 C의 연산횟수가 태생적으로 다를 수 있음.
> 3. 프로세서와 메모리 시스템
> > - 연산이 얼마나 빠르게 동작하는지 정함
> 4. I/O 시스템 (운영체제 포함)
> > - I/O 연산이 얼마나 빠르게 일어나는지 정함.

## 7개의 성능 향상 아이디어
> 1. 디자인 단순화를 위해 추상화 사용
> > - 수억, 수천만개를 동시에 디자인할 수 없기에 블럭단위로 쪼개서 디자인 한다던지..
> 2. 흔한 케이스를 빠르게 하자
> 3. 병렬 처리, 파이프, 예상
> > - 병렬 처리는 물리적 한계 때문에 상당히 중요해짐.
> 4. 메모리 계층구조를 이용
> 5. 중복성 ↑ -> 신뢰성 ↑

# 2주차
## 프로그램 코드의 레벨
> ### 1. 하이레벨 
> > - 추상적인 수준으로 구현 가능
> > - 생산성과 유동성(다른 기기에 대한 이식성), 
> ### 2. 어셈블리
> > - 명령에 대한 문자적 표현
> > - ex) MUL,DIV,SUB 등
> ### 3. 하드웨어
> > - 이진수
> > 암호화된 명령과 데이터
## 터치스크린
> - 저항 타입, Capacitive 타입
> - 요즘은 모두 Capacitive (동시 터치 가능)
## LCD 스크린
> - pixel 단위
> - 프레임 버퍼(어떤 것을 display 할지 담고있는) 메모리 보유

## 추상화
> - 복잡도 다루는데 도움을 줌
> - ISA(명령집합 아키텍처)(용어 암기.)
> > - 하드웨어/소프트웨어 인터페이스
> - 어플리케이션 이진 인터페이스
> > - ISA + 시스템 소프트웨어 인터페이스

## 반도체
> - 실리콘으로 제작
> - 특성변화를 위한 재료를 추가
> > - 도체, 절연체, Switch(조건에 따라 전기가 통하거나 안 통함)
## IC(Inergrated Circuit Cost)
> - Cost per die= Cost per wafer/(Dies per wafer * Yield) - 암기
> - Dies per wafe .= Wafer area/Die area - 암기
> - Yield=1/(1+(Defects per area * Die area/2))^2
## Performace
> - Response time
> > - 하나의 task를 처리할 때 걸리는 시간
> - Throughput
> > - 단위시간 내에 완료된 일의 총량
## Relative Performance
> ### Performance=1/Execution Time
> - X가 Y보다 n배 빠르다
> > - Performance Ex/Performance Ey = Execution Time Y / Execution Time X = n
> ### Excution Time의 측정
> - #### Elapsed time (경과 시간)
> > - Total response time(모든 상황을 고려한)
> > > - Processing,I/O,OS overhead,idle time (상황)
> > - 시스템 성능을 결정함.
> - #### CPU time
> > - 지정된 작업을 처리하는 데 걸리는 시간
> > > - Discounts I/O time, other jobs' shares
> > - 사용자 CPU time과 시스템 CPU time을 구성.
> > - 프로그램마다 CPU 및 시스템 성능에 따라 다른 영향을 받습니다.
## CPU Clocking
![image](https://user-images.githubusercontent.com/84065357/157788486-5057cd5f-ada4-4534-acc0-903e48daa30e.png)
> - 디지털 하드웨어의 연산은 일정하게 유지되는 clock에 영향을 받음
> - Clock period : 한 클락 사이클의 길이
> - Clock frequency(rate) : 초당 사이클 수. 
> ### Cpu time = Cpu Clock Cycle * Clock Cycle time
> ### - = CPU Clock Cycles/Clock rate
> - 성능 향상법
> > - clock 사이클을 줄인다.
> > - clock rate 증가
> > - 하드웨어 디자이너는 사이클 
> ### Instruction count and CPI(cycles per instruction)
> - Instruction count = 프로그램,ISA,컴파일러에 의해 결정
> - Instruction에 따라 CPI 값도 달라짐
> - 하지만 일단 동일하다고 가정함.
