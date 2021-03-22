# Difference between Arrival Time and Burst Time in CPU Scheduling

[링크](https://www.geeksforgeeks.org/difference-between-arrival-time-and-burst-time-in-cpu-scheduling/)

CPU 스케쥴링 알고리즘은 작업 수행에 CPU time과 IO time이 필요하다. CPU time은 절차(process)를 수행하는데 걸리는 시간이고, IO time은 그 절차의 I/O 작업(operation)에 필요한 시간이다.

여러 프로세스를 수행하기 위해서 FCFS, Shortest Job First와 같은 다양한 알고리즘이 있으며, Arrival Time, Burst Time, Waiting Time과 같은 time frame 값에 따라 최적화하기 위해 선택해야하는 알고리즘이 달라진다.

##### 1. Arrival Time(AT)

Arrival time(도착 시각)은 프로세스가 수행을 위해 대기큐에 도착한 시점이다. CPU/IO time과 독립적으로 단지 그 작업(job)을 수행할 수 있게 됐음을 나타내는 time frame(시간 구간)이다. Arrival Time은 Completion Time과 Turn Around Time의 차로 계산된다.

```
Arrival Time (AT) = Completion Time (CT) - Turn Around Time (TAT)
```

##### 2. Burst Time(BT)

Burst Time은 프로세스 수행에 소요되는 시간을 말한다. CPU time에 해당(IO time과는 관련 없음)하며 Execution time 혹은 running time이라고도 한다. 이 time frame 동안에 프로세스는 Running state에서 Complettion State로 상태 전이한다. Burst time은 Completion Time과 Waiting Time의 차로 계산된다.

```
Burst Time (BT) = Completion Time (CT) - Waiting Time (WT)
```



아래 표는 세 개의 프로세스 P1, P2, P3의 Arrival Time과 Burst Time을 나타내었다. 세 개의 프로세스 수행을 위해 단일 CPU를 사용한다.

| Processes | Arrival Time (in ms) | Burst Time (in ms) |
| :-------- | :------------------- | :----------------- |
| P1        | 0                    | 3                  |
| P2        | 4                    | 2                  |
| P3        | 6                    | 4                  |



FCFS 스케쥴링에 의해 프로세스를 수행한다면, 프로세스의 도착 시간이 각 Burst time동안 수행되는 실행 순서를 결정하게 된다. 

![](https://media.geeksforgeeks.org/wp-content/uploads/20200430201323/Untitled-Diagram-68.jpg)

P2가 4ms에 도착하고 P1은 수행에 3ms가 필요하기 때문에, CPU는 1ms를 대기한다. 이시간은 idle time으로 어떠한 프로세스도 수행하지 않는다.

다음 표는 Arrival Time과 Burst Time의 핵심 차이점을 나타낸다.

| Arrival Time                              | Burst Time                               |
| :---------------------------------------- | :--------------------------------------- |
| 큐에서 프로세스의 entry point를 표시한다. | 큐에서 프로세스의 exit point를 표시한다. |
| 프로세스 수행 전에 계산된다.              | 프로세스 수행 후에 계산된다.             |
| CPU의 Ready State와 연관이 있다.          | CPU의 Running State와 연관이 있다.       |