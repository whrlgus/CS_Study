# Multilevel Queue(MLQ) CPU Scheduling

[링크](https://www.geeksforgeeks.org/multilevel-queue-mlq-cpu-scheduling/)

대기 큐에 존재하는 프로세스가 다른 종류로 구분되어 각 종류에 해당하는 스케쥴링이 필요할 수 있다. 예를 들어, 일반적인 분류로 foreground(interactive) 프로세스와 background(batch) 프로세스가 있다. 이 두 클래스는 다른 스케쥴링이 필요하다. 이러한 경우에 MLQ가 사용된다. 

다음 그림은 대기 큐가 세개로 나뉘어 각각 system, interactive, batch 프로세스를 담는다. 각 큐는 서로 다른 스케쥴링 알고리즘을 선택할 수 있다. 예를 들어, 큐 1,2는 Round Robin 이고, 3은 FCFS 일 수 있다.

![](https://media.geeksforgeeks.org/wp-content/uploads/multilevel-queue-schedueling-1-300x217.png)



**Scheduling among the queues:** 다음 두가지 방식으로 큐에 담긴 프로세스를 스케쥴링 할 수 있다.

1. **Fixed priority preemptive scheduling method -** 각 큐는 우순선위가 있다. 큐 1 > 큐 2 > 큐 3 의 우선순위가 있다면, batch queue인 큐 3은 1, 2 큐가 빌 때까지 실행되지 않는다. 큐 3의 프로세스가 수행중에 큐 1, 2로 프로세스가 들어온다면 해당 프로세스에 의헤 CPU가 선점된다.
2. **Time slicing -** 큐 각각이 특정 양의 CPU time을 가지고 각각의 스케쥴링 알고리즘을 수행한다. 예를 들어, 큐 1은 50%, 2와 3은 30%, 20%의 CPU time을 점유할 수 있다.