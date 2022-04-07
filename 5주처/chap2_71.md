## Nonleaf (swap(함수를 호출하는))
> - 즉 nonleaf는 함수안에 또다른 함수가 있는, leaf형태가 아닌 것으로 봐도 무방함.
> ## C언어세서 버블정렬
> >![image](https://user-images.githubusercontent.com/84065357/162174985-29b8510d-6114-4afd-baa9-127da922fc36.png)
> > ## Procedure Body
> >![image](https://user-images.githubusercontent.com/84065357/162177546-0183c20e-e615-4b99-a55a-2f57c84d6b41.png)
> > ## FUll Procedure
> >![image](https://user-images.githubusercontent.com/84065357/162177607-baa2d818-1426-481f-9084-5ee37620b188.png)

## 컴파일러 최적화의 효과
> ![image](https://user-images.githubusercontent.com/84065357/162177883-a8aea4f2-9106-459c-8821-29840e82d291.png)
> - Relative Performance : 상대적인 성능
> - Instruction count
> > - 아무 최적화도 안하면 IC값이 매우 큼
> - Clock Cycles 
> > - 아무 최족화도 안하면 CC값이 매우 큼
> - CPI
> > - 큰 CC와 IC 값 -> CPI값의 저하.

## 언어와 알고리즘에 따른 차이
> ![image](https://user-images.githubusercontent.com/84065357/162178225-3db09c99-03b5-43e0-846e-e53254263d91.png)

## 여기서 배울 수 있는 점
> ### IC,CPI값은 성능을 평가하는데 좋은 지표는 아님(모든것을 생각해야함)
> ### 컴파일러 최적화는 알고리즘에 민감하다
> ### Java/JIT 코드 같은 경우는 JVM보다 빠르다
> > - C코드에 비견할 만함
> ### 최적화를 잘해도 알고리즘이 좋지않으면 성능은 안나옴
## 배열과 포인터
> ## Array 인덱싱
> > - 원소(데이터형)의 크기만큼 index를 곱해줘야함
> > - 그리고 그 값을 배열의 기본주소에 더해줘야함
> ## 포인터 
> - 메모리주소와 직접적으로 일치함
> > - 인덱싱하는데 복잡학을 피할 수있다.
> ## 예제
> > ![image](https://user-images.githubusercontent.com/84065357/162180621-2ed279d4-7bef-4bd8-aae4-036e72c7450b.png)
> ## 배열과 포인터의 비교
> > ### 포인터는 Shift 연산자를 많이 쓸 필요가 없다 (시간감소.)
> > ### 배열은 Shift 연산자가 루프 안에 있어야함
> > > - i 값 증가
> > ### 컴파일러는 포인터를 수동으로 사용한다.(간단한 경우)
> > > - 유도 변수 제거(i)
> > > - 명확하고 안전하게 프로그램을 만든다.
