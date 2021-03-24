# CPU Scheduling in Operating System

[링크](https://www.geeksforgeeks.org/cpu-scheduling-in-operating-systems/)

작업(work)을 제시간에 끝내기 위해 프로세스 스케쥴링을 한다. 다음은 한 프로세스와 연관된 여러 time이다.

- Arrival Time: 대기 큐에 프로세스가 도착한 시각
- Completion Time: 프로세스가 수행을 완료한 시각
- Burst Time: CPU 수행을 위해 프로세스에 요구되는 시간
- Turn Around Time(총처리 시간): Completion Time(완료 시각)과 Arrival Time(도착 시각)의 차
- Waiting Time: Turn Around Time과 Burst Time의 차



### 스케쥴링이 필요한 이유?

일반적인 프로세스는 I/O time과 CPU time을 포함한다. MS-DOS와 같은 단일 프로그래밍 시스템에서는 프로세스가 I/O를 기다리는 시간에 CPU는 아무 작업을 하지 않는다. 다중 프로그래밍 시스템에서는 하나의 프로세스가 I/O를 기다릴 때 다른 프로세스가 CPU를 사용할 수 있으며, 이는 프로세스 스케쥴링에 의해 가능해진다.



### 프로세스 스케쥴링 알고리즘의 목적

- CPU를 최대한 활용하는 것
- CPU를 공평하게 할당하는 것
- 최대 처리량(단위 시간동안 완료가능한 프로세스의 수)
- 최소 turnaround 시간
- 최소 대기 시간
- 최소 응답 시간



### 다양한 스케쥴링 알고리즘

**First Come First Serve(FCFS):** 프로세스의 도착 시간에 따라 스케쥴을 정하는 단순한 알고리즘이다. 즉, CPU를 요청한 프로세스에 CPU가 먼저 할당된다. FCFS는 FIFO 큐를 사용하여 구현한다. 프로세스가 대기 큐에 들어오면, 해당하는 PCB는 큐의 tail에 연결된다. CPU가 free 상태라면, 큐의 head에 있는 프로세스에 할당된다. 그리고 실행중인 프로세스는 큐에서 제거된다. FCFS는 비선점(non-preemptive) 스케쥴링 알고리즘이다.

**Shortest Job First(SJF):** 짧은 burst time을 가진 프로세스가 먼저 스케쥴 된다. 만약 두 프로세스가 동일한 burst time을 가지고 있다면 FCFS방식이 적용된다. 비선점 방식이다.

**Longest Job First(LJF):** SJF 스케쥴링 알고리즘과 유사하다. 하지만, 긴 burst time의 프로세스에 우선권을 부여한다. 비선점형으로 완료되기 전까지 interrupt 할 수 없다.

**Shortest Remaining Time First(SRTF):** SJF 알고리즘의 선점형으로 shortest remaining time에 의해 스케쥴된다.

**Longest Remaining Time First(LRTF):** LJF 알고리즘의 선점형으로 가장 큰 burst time 이 남은 프로세스에 우선도를 부여한다.

**Round Robin Scheduling:** 각 프로세스는 순환형태로 고정된 시간(Time Quantum/Time Slice)을 할당받는다. 이 알고리즘은 Time-sharing 시스템을 위해 고안되었다. 대기 큐를 원형 큐로 다뤄진다. CPU 스케쥴러는 대기큐를 돌면서 각 프로세스에 1-time quantum의 시간을 할당한다. 대기큐는 FIFO로 구현하며 새로운 프로세스는 큐의 tail에 추가된다. CPU 스케쥴러는 대기큐의 첫번째 프로세스를 택하여 1-time quantum 이후에 인터럽트를 위한 타이머를 설정한다. 그리고 다음 둘 중 하나의 절차가 수행된다.

- 프로세스는 1-time quantum 보다 작은 CPU burst를 가질 수 있다. 이 경우, 프로세스는 자발적으로 CPU를 release한다. 
- 만약, 현재 진행 중인 프로세스의 CPU burst가 1-time quantum 보다 큰 경우, 타이머에 의해 시스템을 인터럽트한다. context switch가 일어나며, 프로세스는 대기큐의 tail에 추가된다.

그리고 스케쥴러는 대기 큐의 다음 프로세스를 수행한다.

**Priority Based scheduling(Non-Preemptive):** 프로세스들을 우선순위에 따라 스케쥴되며, 같은 우선순위라면 도착시간 기준으로 판단한다. 기아현상이 발생할 수 있다.

**Highest Response Ratio Next(HRRN):** 높은 response ratio를 가진 프로세스가 실행되며 starvation을 피할 수 있다.

```
Response Ratio = (WT + BT) / BT
```

**Multilevel Queue Scheduling:** 프로세스의 priority에 따라, 다른 큐에 배치한다. 일반적으로 높은 priority는 top level 큐에 위치시킨다. top level 큐의 모든 프로세스를 완료한 이후에야 낮은 level의 큐에 있는 프로세스를 수행한다. starvation이 발생할 수 있다.

**Multi level Feedback Queue Scheduling: **프로세스가 큐 사이에서 이동할 수 있다. 아이디어는 프로세스의 CPU burst의 특징에 따라 분리하는 것이다. 만약 프로세스가 많은 CPU time을 사용한다면, lower-priority 큐로 이동된다.



**Some useful facts about Scheduling Algorithm:**

1. FCFS는 첫 job이 많은 CPU time이 필요한 경우 긴 WT를 유발하게 된다.
2. SJF와 SRTF 은 기아 현상을 유발할 수 있다. 
3. RR의 time quantum이 매우 크다면, 이는 FCFS처럼 동작한다.
4. SJF는 평균 WT이 가장 작다. 





