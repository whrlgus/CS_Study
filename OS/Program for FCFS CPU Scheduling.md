# Program for FCFS CPU Scheduling

~~코드 말고 시간 계산이 어떻게 되는지만 알아보자.~~

[Set1](https://www.geeksforgeeks.org/program-for-fcfs-cpu-scheduling-set-1/)

n개의 프로세스와 각각의 burst time이 주어진다. FCFS 스케쥴링 알고리즘을 이용하여 평균 waiting time과 평균 turn around time을 구하자.

FIFO 혹은 FCFS는 가장 단순한 스케쥴링 알고리즘이다. FIFO는 단순히 프로세스가 대기큐에 도착한 순서대로 줄을 짓는다. 따라서, 처음에 들어온 프로세스가 처음으로 수행되며 다음 프로세스는 이전 프로세스가 완료된 이후에 수행된다.

모든 프로세스의 토착 시간은 0으로 가정한다.

#### How to compute below times in Round Robin using a program?

1. Completion Time: 프로세스가 수행을 마친 시각
2. Turn Around Time: 완료시각과 도착시각의 차이
3. Waiting Time: turn around time과 burst time의 차이

도착 시간은 0으로 가정하였기 때문에, 각 프로세스의 turn around time과 completion time은 동일하다.

![](https://media.geeksforgeeks.org/wp-content/uploads/FCFS.png)

burst time에 해당하는 duration으로 P1, P2, P3의 대기 시간을 계산하여 평균을 내보면 average waiting time은 17이 나온다.

각각의 turn around time은 24, 27, 31 이고, average turn around time은 (24 + 27 + 31) / 3 = 27.333 이다.

#### Important Points

1. 비선점
2. 평균 대기 시간은 최선이 아니다.
3. 자원을 병렬적으로 활용하지 못한다: **Convoy effect** 



[Set2](https://www.geeksforgeeks.org/program-for-fcfs-cpu-scheduling-set-2-processes-with-different-arrival-times/)

| Process | Burst Time | Arrival Time | Waiting Time | Turn-Around Time | Completion Time |
| :-----: | :--------: | :----------: | :----------: | :--------------: | :-------------: |
|    1    |     5      |      0       |      0       |        5         |        5        |
|    2    |     9      |      3       |      2       |        11        |       14        |
|    3    |     6      |      6       |      8       |        14        |       20        |

```
average waiting time은 (0 + 2 + 8) / 3 = 3.333
average turn around time은 (5 + 11 + 14) / 3 = 10
```

