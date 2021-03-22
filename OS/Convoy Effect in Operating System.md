# Convoy Effect in Operating Systems

Convoy Effect는 FCFS 알고리즘과 연관된 것으로, 몇몇의 느린 프로세스에 의해서 Operating System 전체가 느려지는 현상이다.

![](https://media.geeksforgeeks.org/wp-content/uploads/222-2.png)

FCFS는 비선점 알고리즘으로 한 프로세스에 CPU time이 할당되면, 다른 프로세스는 현재 프로세스가 끝난 이후에 CPU time을 얻을 수 있다. FCFS의 이러한 속성이 Convoy Effect라는 상황을 야기하게 된다.

다음 상황을 가정해보자. 대기 큐에 하나의 CPU intensive(large burst time) 프로세스와 burst time은 상대적으로 작지만 IO bound(IO operation이 자주 필요한)인 프로세스 여러 개가 있다.

프로세스 수행 단계는 다음과 같다.

- I/O bound 프로세스들은 처음으로 CPU time을 할당 받는다. CPU intensive가 작기 때문에, 빠르게 수행되어 I/O 큐로 들어간다.
- 이제, CPU intensive 프로세스에 CPU time이 할당된다. burst time이 크기 때문에 완료되기 까지 시간이 오래걸린다.
- CPU intensive 프로세스가 수행되는 도중에, I/O bound 프로세스들은 I/O 작업을 마치고 대기큐로 들어온다.
- 그러나, I/O bound 프로세스들은 CPU intensive 프로세스가 끝나지 않았기 때문에 기다려야 한다. **따라서, I/O 장치들을 idle상태로 만들게 된다.**
- CPU intensive 프로세스가 끝나면, I/O 큐로 보내져서 I/O 장치에 접근할 수 있다.
- 그동안, I/O bound 프로세스들은 CPU time을 얻어 수행된 후 다시 I/O 큐로 들어간다.
- 그러나, CPU intensive 프로세스가 아직 I/O 장치에 접근중이므로 대기해야한다. **결과적으로, CPU를 idle 상태로 만든다.**

그러므로 Convoy Effect는, 하나의 느린 프로세스가 전체의 성능을 느리게 만들며, CPU time과 다른 장치의 낭비를 야기한다.

**Convoy Effect를 피하기 위해서는 Round Robin 알고리즘과 같은 선점형 스케쥴링을 사용해야 한다. 작은 프로세스는 CPU time을 기다릴 필요가 없고 실행을 빠르게 만들며 idle 상태에 놓이는 자원이 줄어든다.**