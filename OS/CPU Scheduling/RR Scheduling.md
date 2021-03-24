# Program for Rround Robin scheduling

[링크](https://www.geeksforgeeks.org/program-round-robin-scheduling-set-1/)

Round Robin은 각 프로세스가 순환형태로 고정된 time slot을 부여받는 스케쥴링 알고리즘이다.

- 단순하고, 구현하기 쉬우며, 모든 프로세스가 공평하게 CPU를 공유하므로 starvation-free이다.
- CPU 스케쥴링의 핵심으로 가장 많이 사용되는 기술이다.
- 프로세스에는 기껏해야 하나의 고정 slice만 할당되는 선점형알고리즘이다.
- 단점으로는 문맥교환으로 인한 오버헤드이다.

| SERIAL NO. | ADVANTAGES                                                   | DISADVANTAGES                                                |
| :--------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 1.         | CPU를 공평하게 공유한다.                                     | Waiting time과 response time이 길다.                         |
| 2.         | 새로운 프로세스는 대기큐의 끝에 추가된다.                    | 처리량(throughput)이 적다.                                   |
| 3.         | Time-sharing을 사용하여 각 작업(job)에 slot이나 quantum을 부여한다. | 문맥교환이 존재한다.                                         |
| 4.         | 특정 time quantum이 다른 작업들에 할당된다.                  | 간트 차트가 커질 수 있다.(예를 들어, 큰 스케쥴링에 1ms의 quantum을 사용하는 경우) |
| 5.         | 각 프로세스는 특정 quantum time 이후에 다시 스케쥴링 된다.   | 작은 quantum에 대해 시간이 많이 소요된다.                    |



![](https://media.geeksforgeeks.org/wp-content/uploads/round-robin-1.jpg)



도착 시간이 0이고 quantum이 2일 때 다음 프로세스들의 평균 WT와 TAT를 구한 것이다. 주의해야 할 부분은 프로세스의 remaining time이 퀀텀 시간 보다 작다면, 프로세스 종료 후 idle 시간을 갖지 않고 바로 다음 프로세스를 수행한다는 점이다. 

![](https://i.imgur.com/3NEruAG.jpg)