# Introduction of Deadlock in Operating System

OS에서 한 프로세스는 요청(request)-사용(use)-방출(release) 방식으로 자원을 사용한다.

**Deadlock**은 각 프로세스가 하나의 자원을 들고있고, 다른 프로세스가 들고 있는 자원을 기다리면서 일련의 프로세스가 block되는 현상이다. 아래 그림의 예시와 같이, Process 1이 Resouce 1을 들고 있고 Resource 2를 기다리는데, 이 Resource 2는 Process 2가 들고 있으며 Resource1이 사용가능해 질 때까지 놓지 않는다.

![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2015/06/deadlock.png)

Deadlock은 다음 네가지 상황이 동시에 발생할 때 유발된다.

- **Mutual Exclusion:** 공유 불가한 하나 이상의 자원이 있다. (한 시점에 하나의 프로세스만 사용할 수 있다.)
- **Hold and Wait:** 한 프로세스가 적어도 하나의 자원을 가지고 있고 다른 자원을 기다린다.
- **No Preemption:** 한 자원이 그 자원을 가지고 있는 프로세스에서 놓지 않는 이상 다른 프로세스가 취할 수 없다.
- **Circular Wait:** 일련의 프로세스가 순환 형태로 서로를 기다린다.



#### Method for handling deadlock

다음 세가지 방법으로 교착상태를 처리할 수 있다.

1. Deadlock prevention or avoidance: 시스템이 교착상태가 되지 않도록 하는 방식이다. 
2. Deadlock detection and recovery: 교착상태가 발생하면 선점을 하여 해결한다.
3. Ignore the problem altogether: 교착상태가 드물게 발생한다면, 시스템을 reboot한다. Windows와 Unix가 취하는 방식이다.