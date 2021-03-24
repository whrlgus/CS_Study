# Highest Response Ratio Next(HRRN) CPU Scheduling

Response ratio((WT+BT) / BT)가 가장 큰 프로세스가 먼저 수행되며, 비선점형이며 완료될 때까지 계속 수행된다. 

다음 5개의 프로세스가 있다.

![](https://media.geeksforgeeks.org/wp-content/uploads/Scheduling-Example.jpg)

HRRN 방식으로 수행된 간트 차트이다.

![](https://media.geeksforgeeks.org/wp-content/uploads/Gantt-Chart.jpg)

**Explanation**

- t = 0 에 하나의 프로세스만 가능하며 A가 수행된다.
- t = 3 에 마찬가지 이유로 B가 수행된다.
- t = 9 에는 세 개의 프로세스가 가능하다. C, D, E 각각의 WT는 5, 3, 1이다. Response Ratio는 (5 + 4) / 4 = 2.25, (3 + 5) / 5 = 1.6, (1 + 2) / 2 = 1.5이다.
- 따라서 response ratio가 가장 높은 C가 수행된다.
- t = 13 에는 D, E가 가능하며 각각의 Response ratio는 (7 + 5) / 5 = 2.4, (5 + 2) / 2 = 3.5 이다. 
- 따라서 E가 먼저 수행되며, 마지막으로 D가 수행된다.



