## Branch
> - 브랜치(branch) 또는 분기
> - 컴퓨터가 다른 명령 시퀀스의 실행을 시작하도록 지시함으로써 순서대로 명령의 기본 실행 지시로부터 벗어날 수 있게 하는 컴퓨터 프로그램의 한 명령
> - ![image](https://user-images.githubusercontent.com/84065357/162143425-6cec2578-566f-4651-a07f-3eda0204c253.png)

## Basic Blocks
> -  엔트리 외에는 들어오는 분기가 없고, 출구 외에는 나가는 분기가 없는 직선 코드열.
> - 컴파일러는 최적화를 위해 Basic block을 파악한다.
> - 성능이 좋은 프로세서는 Basic Block의 실행을 가속시킬 수 있다.
## 추가적인 조건 연산자.
> ![image](https://user-images.githubusercontent.com/84065357/162142769-5426689d-ed8c-48fc-b9e7-81af1b842583.png)
## Branch Insturction Design
> - 왜 조건연산자에는 blt, bge 등이 없을까?
> - 하드웨어에서 <,>=과 같은 연산자는 =,!=보다 느림.
> > - Branch와 결합하면 명령당 더 많은 작업이 필요하므로 더 느린 클럭이 필요합니다.
> > - 모든 지시에 불이익 발생!
## Signed와 Unsigned
> ![image](https://user-images.githubusercontent.com/84065357/162143953-d8c1de55-1f14-43e4-be99-3d2855b9a95e.png)
## 프로시져 호출
> ### 단계
> > 1. 레지스터에 매개변수를 위치시킨다
> > 2. 제어를 Procedure에게 옮긴다
> > 3. 프로시저를 위한 저장공간 확보
> > 4. 프로시져의 연산들을 수행
> > 5. 호출자에 레지스터에 결과를 저장
> > 6. 호출했던곳으로 돌아가기.
## 레지스터 사용
> ![image](https://user-images.githubusercontent.com/84065357/162144417-6b36edd8-02d9-40ca-bd38-a60abbcdf66b.png)
## 프로시저 호출 명령어
> ## 프로시저 호출: jump와 link
> > ### jal procedureLabel
> > > - $ra에 입력된 다음 명령의 주소
> > > - 그 주소로 이동
> ## 프로시저 리턴: jump register
> > ### jr $ra
> > > - $ra를 프로그램 카운터에 복사
> > > - case/switch와 같은 계산된 점프에도 사용가능
## Leaf Procedure Example
> ![image](https://user-images.githubusercontent.com/84065357/162145510-e557381f-5657-4fc2-a659-82a7891e8690.png)
> ![image](https://user-images.githubusercontent.com/84065357/162145541-d5f4c3cd-02aa-4108-ab5f-8f954baf2663.png)
> > - f는 $0에 있기때문에 stack에다가 저장 시켜줘야함.
> > - 어차피 f밖에 없기때문에 stack pointer에다가 -4시켜줘서 stack의 head에다 넣어줌
> > - 그리고 $v0에 값을 저장한 후, $s0을 stack에다가 복원시키고 나서, stack pointer도 다시 복원 시킴.
## Non-leaf Procedures
> ### 다른 프로세스를 호출하는 프로세스
> - 중첩 호출에 대하여, 호출자는 stack에 저장해야함.
> > - 주소반환
> > - 호출후에 필요한 매개변수나 임시 변수
> - 호출 후에 stack으로부터 복원한다.
> ## 예시
> > ![image](https://user-images.githubusercontent.com/84065357/162148308-376b8f3b-5745-4df5-9ecb-66f24504215c.png)
> > ![image](https://user-images.githubusercontent.com/84065357/162148353-2eff2917-b6d3-43bb-b224-e5137d62f4f5.png)
## Stack에서의 Local data
> ![image](https://user-images.githubusercontent.com/84065357/162151871-e988314b-4a89-4eb6-854c-0d2ce5654fbd.png)
> - 피호출자에 의해 할당된 로컬 데이터
> > - C 자동 변수 등..
> - Procedure fram(활성화 레코드)
> > - stack 저장공간을 관리하기위해 컴파일러에의해 사용됨.
## 메모리 레이아웃
> - Text: Program code
> - 정적 data : 전역변수
> > - ex) C의 정적 변수, 상수 배열, 스트링
> > - $gp(정적데이터의 글로벌 포인터(reg 28): 이 세그먼트에 ±offset을 허용하는 주소를 지정하기 위해 초기화됨
> - 동적 data : heap 영역
> > - C의 malloc, Java의 new
> - Stack: 자동적인 저장소
## 문자 데이터
> - Byte 단위로 인코딩된 문자 집합
> > - ASCII : 128개의 문자
> > - Latin-1 : 256개의 문자
> - Unicode : 32-bit 문자집합
> > - 세계의 대부분의 알파벳과 기호
> > - UTF-8, UTF-16 : 가변 길이 인코딩
## Byte/Halfowrd 연산자
> - 비트단위 작업 연산자 사용 가능
> - MIPS byte/halfword load/store
> ![image](https://user-images.githubusercontent.com/84065357/162153757-8bdb4ca9-b9c8-46c4-9335-9953981a588c.png)
> ## 문자열 복사 예제
> > ![image](https://user-images.githubusercontent.com/84065357/162153955-3340f674-7cad-4185-8bf2-5a02cbb07ffb.png)
> > ![image](https://user-images.githubusercontent.com/84065357/162155457-2a17d219-5e6d-4e1b-9c3c-b4537c87ebf9.png)

