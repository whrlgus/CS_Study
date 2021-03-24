# Longest Remaining Time First(LRTF) CPU Scheduling Algorithm

LJF 스케쥴링 알고리즘의 선점형 버전으로 가장 큰 remaining time을 찾아 수행한다. 특정 시간 간격 후에 이러한 프로세스를 찾아서 있으면 CPU time을 할당한다.

#### 절차

- Step-1: 처음에 arrival time의 오름차 순으로 프로세스를 정렬한다.
- Step-2: 가장 작은 arrival time과 가장 큰 burst time을 갖는 프로세스를 선택한다. 1unit을 수행하고 그 시간까지 도착한 프로세스가 있는지 검사한다.
- Step-3: 모든 프로세스를 수행할 때까지 처음 단계부터 반복한다.



**Example-1:** 프로세스 4개가 다음과 같은 도착시간 실행시간을 갖는다.

```
Process   Arrival time   Burst Time
P1            1 ms          2 ms
P2            2 ms          4 ms
P3            3 ms          6 ms
P4            4 ms          8 ms  
```

**Working:**

1. t = 1에 실행 가능한 프로세스는 P1 이므로 1ms를 수행한다.
2. t = 2에 실행 가능한 프로세스는 P1, P2 이다. **BT(P2) = 4**이고 **BT(P1) = 1** 이기 때문에 P2를 1ms동안 수행한다.
3. t =3에 실행 가능한 프로세스는 P1, P2, P3 이다. 마찬가지로 BT가 제일 큰 P3를 1ms 수행한다.
4. 이러한 방식으로 모든 프로세스가 종료될 때까지 반복한다.

**Note** 0에서 1동안은 실행가능한 프로세스가 없기 때문에 CPU가 idle 상태이다. 

Gantt 차트는 아래와 같다.

![](https://media.geeksforgeeks.org/wp-content/uploads/88888888.png)

최종 결과 테이블은 다음과 같다.

![](https://media.geeksforgeeks.org/wp-content/uploads/222223333.png)



**Example-2:** 아래와 같은 5개의 프로세스가 있다.

```
Process   Arrival time   Burst Time
P1            0 ms          2 ms
P2            0 ms          3 ms
P3            2 ms          2 ms
P4            3 ms          5 ms 
P5            4 ms          4 ms 
```

간트 차트와 결과 테이블을 다음과 같다.

![](https://media.geeksforgeeks.org/wp-content/uploads/GANT-3.png)

![](https://media.geeksforgeeks.org/wp-content/uploads/PRO2.png)

