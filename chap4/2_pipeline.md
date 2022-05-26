## MIPSS PipeLine
> ### 하나의 instruction을 분해
> > # ![image](https://user-images.githubusercontent.com/84065357/170497314-b28b6d03-59a0-4e05-98cb-8768a9b805d3.png)
> > - 무조건 암기
> > - IF,ID,EX,MEM,WB
> > - 한 사이클마다 한 Stage씩\
> # ![image](https://user-images.githubusercontent.com/84065357/170503303-73f7fdae-91c0-433a-ad68-1e8f76a5ab17.png)
> > - stage당 차지시간이 균형이 맞지않으면 엄청 큰 효율은 안나올 수도 있다. ㅇㅇ

## Hazard 위험
> - 다음 사이클에서 다음 명령을 시작하는것을 방해하는 상황
> ## 1. 구조 Hazard
> > - 필요한 자원이 이미 사용중임
> > - 자원 사용시 충돌
> > ### 하나의 메모리를 사용하는 MIPS 파이프라인에서 
> > > - Load/store는 데이터 접근을 요구함
> > - 따라서 파이프라인 데이터패스는 분리된 명령이나 데이터 메모리를 요구함
> > > - 아니면 캐시
> ## 2. Data Hazard
> > - 이전 명령의 결과를 이용해서 현재의 명령을 수행할때 발생하는 문제
> > # ![image](https://user-images.githubusercontent.com/84065357/170509919-d16b369b-d68a-487c-9011-18ac6d890f7e.png)
> > - WB(write)를 안했는데 불러버리면 이상한 데이터가 올수 있다
> > - 세번 쉬기는 시간이 아깝다
> > - WB의 시간과 ID의 시간은 EX에 비해 상대적으로 짧음
> > - 따라서 WB를 앞에다 ID를 뒤에다 붙여버리면 같은 Cycle내에서 침범없이 수행 가능.
> > - 즉, 저장 reg와 읽기 reg가 겹치면 안됨.
> > > ## Forwarding
> > > # ![image](https://user-images.githubusercontent.com/84065357/170511453-4a7d25f5-fba5-46fb-baec-313dcec39548.png)
> > > > - 연산이 끝나면 바로 가져오자..
> > ## Load-Use Data Hazard
> > > # ![image](https://user-images.githubusercontent.com/84065357/170511910-cc2d2b8a-78f5-4511-b998-0f966a51ad6f.png)
> > > - forwarding이 항상 stall을 피할 수 있는것은 아님
> > > - bubble을 발생 시켜야하는 경우가 생김.
> > ## Stall을 피하는 코드 스케줄링.
> > > # ![image](https://user-images.githubusercontent.com/84065357/170512441-91442d0a-ff01-4c2f-923f-769cbd4ca40e.png)
> > > - load한 뒤에 바로 사용이  되면 bubble 발생
> > > - 사이클 낭비 방지 위해 lw add의 레지스터가 겹치지 않도록함
> ## 3. Control Hazard
> > - Branch는 제어의 흐름을 결정함
> > - Branch수행 후의 명령은 Branch의 결과에 따라 다름
> > > - IF단계부터 문제가 됨
> > > - 파이프라인은 항상 올바른 명령을 접근할 수 없음
> > - MIPS에서
> > > - 레지스터 사이에 있는 값들을 비교한 후(ALU), 파이프라인을 할지 말지 빨리 결정
> > > - ID 단계에서 진행(추가적인 하드웨어 요구)
> > # ![image](https://user-images.githubusercontent.com/84065357/170513687-88db484d-df74-4606-898a-cea508bded97.png)
> > > - ID 후에 바로 IF들어감.
## Branch Prediction
> - 예측이 잘못됐을 경우에만 Stall 발생.
> - Branch가 받아들여지지 않았다고 생각
> - Branch가 받아들여지지 않음 -> 딜레이 x 
> > # ![image](https://user-images.githubusercontent.com/84065357/170514793-e7591cc3-09ef-433a-b5fb-1540d08f72a1.png)
> - Branch가 받아 들여졌을 때
> > # ![image](https://user-images.githubusercontent.com/84065357/170514819-5f9e84ce-3bed-4978-b761-69eceb2b9305.png)
> > - IF했던것을 버리고(lw) or부터 IF 다시 함.

## 더욱 현실적인 Branch Prediction
> # ![image](https://user-images.githubusercontent.com/84065357/170515136-243fecd6-a64d-4d51-b349-a9e3efd4e0ab.png)
> ## 정적
> > - 전형적인 Branch 경우 
> ## 동적
> > - 실제 Branch의 동작을 예측
> > > -과거의 Branch의 동작을 모두 기록
> > 즉, 과거의 동작을 계속할 거라고 예측
> > > - 틀리면, 다시 IF 할때까지 stall

## MIPS 파이프라인 DataPath
> # ![image](https://user-images.githubusercontent.com/84065357/170515711-eb8470cc-f8b1-452a-9099-f3feebbdbec6.png)
> > - 5개의 stage로 나눔
> > - 오른쪽에서 왼쪽 방향의 Flow는 hazard를 야기시킬 수 있다.(MEM, WB)
## 파이프라인 레지스터
> # ![image](https://user-images.githubusercontent.com/84065357/170516491-edf80c26-da45-4c06-9693-5fe938298583.png)
> - stage(한 클럭당 한 stage)사이에 Register가 필요함
> > - 이전 사이클에 발생한 정보들을 일시적으로 저장시키기 위해
> ## IF for Load,Store,...
> > # ![image](https://user-images.githubusercontent.com/84065357/170516795-f1672183-605c-401c-84e9-28d7cacf736b.png)
> ## ID for Load,Store,...
> > # ![image](https://user-images.githubusercontent.com/84065357/170516997-762c5e98-6bbe-4ff5-b1bd-07b6c2a27835.png)
> ## EX for Load,Store
> > # ![image](https://user-images.githubusercontent.com/84065357/170517096-609a089a-b115-46ec-911c-571dec4cb42f.png)
> ## MEM for Load
> > # ![image](https://user-images.githubusercontent.com/84065357/170517208-5c226595-1e6d-435e-a191-1c7beb1d7f77.png)
> ## WB for Load
> > # ![image](https://user-images.githubusercontent.com/84065357/170517310-1786519c-2c6f-493d-a9cb-97d7958f9ee6.png)
> > - 데이터를 저장하려는 레지스터는 다른 IF에의해 다름
> > - 문제 발생
> > ## 수정
> > # ![image](https://user-images.githubusercontent.com/84065357/170517766-e9e27e56-af00-47b5-a513-dbd26ea96c6b.png)
> > > - Write Register를 계속 저장시켜놓음.

## multi-Cycle 파이프라인 다이어그램
> # ![image](https://user-images.githubusercontent.com/84065357/170518230-0ebdb47d-53fa-49af-9f93-c7d401a475db.png)
## 파이브라인과 Control 신호
> # ![image](https://user-images.githubusercontent.com/84065357/170519071-2654b3f1-1b8b-4bf6-9723-0d16aa6e0bbc.png)
> > - 각 사이클마다 다른 명령 수행중 -> 신호 유지를 위함.
> > # ![image](https://user-images.githubusercontent.com/84065357/170519349-0e9da039-64fc-4a42-a4e5-9e339df3dd7a.png)
> > > - ID/EX등의 레지스터에 값이 바뀌는것은 Clock이 바뀔때

## ALU 명령에서의 Data Hazard
> # ![image](https://user-images.githubusercontent.com/84065357/170521214-6c184329-d86f-4018-bd67-eb0683bc8acb.png)
> - Forwarding을 이용해 해결 가능
> > - 언제 Forwarding할지를 알 수 있을까?
> > # ![image](https://user-images.githubusercontent.com/84065357/170521416-90922adc-bd40-407f-b303-8f55bd79033a.png)
> > - IM: instruction memory 
> > - DM: data memory
> > > - And or 만 Forwarding 하는 이유 : Reg에 저장하기 전에 Reg값을 불러오기 때문에 ALU에서 연산이 끝난 후의 값을 바로 forwarding해야 올바른 값이 들어감
> > > - Add,sw는 Reg를 살펴보면 시간이 짧기 때문에 사이클 내부에서 일찍 저장 시킴(sub)
> > > - 따라서 read해올 당시에 올바른 값이 저장되어 있음. 

## Forwarding 할 필요를 찾는 것
> # ![image](https://user-images.githubusercontent.com/84065357/170522461-c30d6092-bb9e-4a1d-983d-1eef876de544.png)
> > - 파이프 라인을 따라서 Reg num이 전달되어야함.
> ### Data hazard 발생 경우=forwarding을 해줘야할 경우
> > - 1.a EX/MEM.rd = ID/EX.RS  // Add $1,$2,$3 , ADD $4,$1,$6 rd==rs
> > - 1.b EX/MEM.rd = ID/EX.RT
> > > - EX/MEM 파이프라인 Reg에서의 forwarding이 필요함.
> > - 2.a MEM/WB.rd = ID/EX.RS
> > - 2.b MEM/WB.rd = ID/EX.RT
> > > - MEM/WB 파이프라인 Reg에서의 forwarding 필요
> > - EX/MEM.RegWrite, MEM/WB.RegWrite가 활성화 되었을때만 forwarding 해야함
> > - EX/MEM,MEM/WB Rd가 $zero가 아닌경우 forwarding
## Forwarding Path
> # ![image](https://user-images.githubusercontent.com/84065357/170525406-c7981bb6-827d-4080-b113-67dccd87ef93.png)
> ## 조건
> > # ![image](https://user-images.githubusercontent.com/84065357/170525537-be90d801-f5fe-475c-843a-020341b518d2.png)
## Double Data Hazard
> # ![image](https://user-images.githubusercontent.com/84065357/170525917-324b5238-05a5-497d-9c7f-06b2156a75bb.png)
> > - 가장 마지막(add $1 $1 $3에서의 rd를 forwarding해줌)
> > - 첫번째꺼는 하면 안됨.
> # ![image](https://user-images.githubusercontent.com/84065357/170527220-668c2542-c9f6-48f4-8f29-f6911d8716c1.png)
## DataPath with Forwarding
> # ![image](https://user-images.githubusercontent.com/84065357/170527159-e7fa9996-2274-4123-a14a-a625b55ebdf6.png)
