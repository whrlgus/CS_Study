# Program for Priority CPU Scheduling

[set1](https://www.geeksforgeeks.org/program-for-priority-cpu-scheduling-set-1/)

priority 스케쥴링은 배치 시스템에서 가장 일반적인 스케쥴링 알고리즘 중 하나이다. 각 프로세스는 우선순위를 부여받는다. 가장 높은 우선순위 부터 실행되며 같은 우선순위라면 시간 순으로 실행된다. 우선순위는 메모리 요구조건, 시간 요구조건 혹은 다른 요구 조건에 의해 결정될 수 있다.

Note: 주요한 문제점은 무한 blocking 혹은 starvation이다. 낮은 우선도를 갖는 프로세스의 기아 현상은 aging 방식으로 해결한다.

# Priority CPU Scheduling with different arrival time

[set2](https://www.geeksforgeeks.org/priority-cpu-scheduling-with-different-arrival-time-set-2/)

각 프로세스는 도착 순으로 실행되며, 우선순위를 비교하고 프로세스 번호를 비교하여 실행 순서를 정한다.

다섯 개의 프로세스에 대한 정보가 있고, 그 아래 간트 차트와 같이 실행된다.

![](https://media.geeksforgeeks.org/wp-content/uploads/opSystemScheduling.png)

![](https://media.geeksforgeeks.org/wp-content/uploads/gantchart2.jpg)

FCFS 방식에서 같은 AT의 프로세스에 대해서 priority, process name으로 정렬을 하네... 