# Program for Shortest Job First CPU Scheduling

~~코드 말고 시간 계산이 어떻게 되는지만 알아보자.~~

[Set1](https://www.geeksforgeeks.org/program-for-shortest-job-first-or-sjf-cpu-scheduling-set-1-non-preemptive/)

SJF(또는 SJN,Shortest Job Next) 스케쥴링 정책은 다음 수행할 프로세스로 실행 시간이 더 작은 것을 선택한다. 비선점형의 알고리즘이다.

- SJF은 모든 스케쥴링 알고리즘 중에 average waiting time이 가장 작다는 이점이 있다.
- Greedy 알고리즘이다.
- 짧은 프로세스가 계속해서 도착한다면 **기아 현상**이 유발될 수 있다. 이는 ageing의 개념으로 해결한다.
- 실제로 OS가 burst time을 알 수 없고 정렬할 수 없기 때문에 실현 불가능한 방식이다. 실행시간은 예측할 수 없지만, 이전 실행 시간의 가중치 평균(weighted average)와 같은 작업(job)의 실행 시간을 예측하는데 몇몇 방식을 사용할 수 있다. SJF는 정확한 실행 시간을 측정할 수 있는 특별한 환경에서만 사용할 수 있다.

#### Algorithm

1. 도착 시간에 따라 모든 프로세스를 정렬한다.
2. 최소 도착시간과 최소 burst time을 가지는 프로세스를 선택한다.
3. 프로세스 완료 후, 이전 프로세스 완료전까지 생성된 프로세스 pool중에서 가장 작은 burst time을 갖는 프로세스를 선택한다.

![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200303163658/SJF.jpg)



| Process ID | Arrival Time | Burst Time | Waiting Time | Turnaround Time |
| :--------: | :----------: | :--------: | :----------: | :-------------: |
|     1      |      2       |     3      |      4       |        7        |
|     2      |      0       |     4      |      0       |        4        |
|     3      |      4       |     2      |      0       |        2        |
|     4      |      5       |     4      |      4       |        8        |



[Set2](https://www.geeksforgeeks.org/program-for-shortest-job-first-sjf-scheduling-set-2-preemptive/)

Shortest Remaining Time First(SRTF)는 SJF의 선점형 방식이다. 완료까지 남은 시간이 가장 작은 프로세스가 선택되는 알고리즘이다. 정의에 따라 현재 수행중인 프로세스는 남은 시간이 가장 짧고, 이 시간은 실행되면서 줄어들기 때문에 프로세스는 완료될 때까지 혹은, 더 짧은 시간을 갖는 프로세스가 추가될 때까지 실행된다.

#### 장점

- 짧은 프로세스들은 매우 빠르게 처리된다.
- 프로세스가 완료되거나 새로운 프로세스가 추가될 때 결정하기 때문에 오버헤드가 적다.
- 새 프로세스가 추가되면 알고리즘은 현재 진행중인 프로세스하고만 비교하면 된다.

#### 단점

- SJF처럼 프로세스 기아 현상이 발생할 수 있다.
- 짧은 프로세스가 계속 추가되면 긴 프로세스는 영원히 미뤄질 수 있다.

| Process | Burst time | Arrival time | Waiting time | Turn around time |
| :-----: | :--------: | :----------: | :----------: | :--------------: |
|    1    |     6      |      1       |      3       |        9         |
|    2    |     8      |      1       |      16      |        24        |
|    3    |     7      |      2       |      8       |        15        |
|    4    |     3      |      3       |      0       |        3         |

