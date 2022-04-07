## 32 비트 상수
> - 대부분의 상수는 작은 크기다
> - 16-비트의 크기로도 충분하나 가끔 32-비트 크기를 필요로하는 상수가 있다
> ## 연산
> > ## lui rt, constant
> > > - 16-bit 상수를 rt의 좌측 16비트에 복사한다.
> > > - rt의 오른쪽 16비트를 0으로 바꾼다.
## Branch Addressing
> ## 브랜치 명령
> > - Opcode, 두 개의 레지스터, 타겟 어드레스(어디로 움직일 지를 알려줌)
> - 대부분의 branch의 target은 branch의 주변에 있다.
> > - 앞쪽이나 뒤쪽으로 갈 수 있다.
> > - ![image](https://user-images.githubusercontent.com/84065357/162168851-c4aa31ea-b41f-4a6d-ada8-1dc211c8ad07.png)
> > - PC-relative addressing(프로그램 카운터에 상대적인 주소)
> > > - ### 타겟 어드레스 = PC + offset * 4
> > > - PC already incremented by 4 by this time 
> > > > - PC는 이미 4만큼 증가해 있는 상태(이미 Branch 다음의 명령을 가리키고 있음.).
## Jump Addressing
> - ### Jump(j와 jal)의 타겟은 텍스트 세그먼트에서 어디든지 될 수있다.
> > - ![image](https://user-images.githubusercontent.com/84065357/162169625-3fba99c5-834f-42bb-960c-8c52c1689921.png)
> > - FULL address를 인코딩함. (절대적 주소)
> > - ### 타겟 어드레스 = PC : (address안에 있는 값 * 4)
## 타겟 어드레싱 예제
> ![image](https://user-images.githubusercontent.com/84065357/162170120-53a3d6e5-ff0d-452b-a758-b3f14ed823da.png)

## 멀리 있는곳으로 Branching 하는 경우
> ### Branch target이 16비트 offset보다 멀리 떨어져 있을 경우
> - ![image](https://user-images.githubusercontent.com/84065357/162170749-1e7ce07b-b245-4902-bb27-04a6051726f2.png)
## Addressing 요약
> ![image](https://user-images.githubusercontent.com/84065357/162170966-c0a93329-c4a0-40d0-a397-9a39ce04b882.png)

## 동기화
> - 메모리의 한 영역을 공유하는 두개의 프로세서
> > - P1은 쓰고, P2는 읽는다
> > - P1과 P2가 동기화하지않을때에는 Data race 발생
> > > - 결과값이 접근의 순서에 따라 달라짐.
> - 하드웨어 서포트가 필요하다
> > ### Atomic read/write memory operation
> > > - 메모리를 읽거나 쓰는 작업을 할때, 다른 프로세스의 개입을 최소화 시켜야함.
> > ### no other access to the location allowed between the read and write 
> > > - 즉, 다른 접근을 막는것임
> - Single instruction을 이용해서 다양한 일을 할 수있음.
> > - 한계가 있어 instruction의 Atomic pair를 이용한다.
> ## 예제
> > ![image](https://user-images.githubusercontent.com/84065357/162171889-6c7c40b5-a1ad-497c-a1cb-3041fdfd64e2.png)
> > - Load linked = ll rt, offset(rs) -> rs에서 얼마나 떨어져있는지에관한 offset을 얻어서 rt에 저장
> > - Store conditional = sc, offset(rs) -> rt에 저장되어있는 데이터를, offset(rs)에 다시 저장.
> > > - ll 이라는 instruction을 이용해 데이터를 load한 후 원하는 operation을 한 후  해당하는 위치에 데이터를 저장을 할때
> > > > - 성공적으로 저장하면 rt에 1저장
> > > > - 실패하면(데이터가 의도한것과 다르다면.) rt에 0 저장.

## 어셈블러 슈도 instruction
> ### 대부분의 어셈블러 명령들은 기계 명령과 일대일 대응관계를 가지고있음.
> ## Pseudoinstructions : 어셈블러의 상상력의 산물?
> ![image](https://user-images.githubusercontent.com/84065357/162173602-3e2c4cd2-1e12-4674-b4b8-290c5db2fc18.png)

## C Sort 예제
> ![image](https://user-images.githubusercontent.com/84065357/162173874-1a7dd52b-4d9c-434a-ba78-32a9f205f1a8.png)
> ![image](https://user-images.githubusercontent.com/84065357/162174086-89571d30-fffb-4fc9-a5a0-71d2fad1f650.png)
 
