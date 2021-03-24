# Difference between Deadlock and Starvation in OS

[링크](https://www.geeksforgeeks.org/difference-between-deadlock-and-starvation-in-os/)

### Deadlock

데드락은 각 프로세스가 자원을 가지고 있고 각자가 들고 있는 서로 다른 자원을 기다리는 현상에서 발생한다. 데드락이 발생하는 필수 상황은 **Mutual Exclusion**, **Hold and Wait**, **No Preemption** 그리고 **Circular Wait**이다. 

### Starvation

starvation은 높은 우선순위의 프로세스가 계속 실행되어 낮은 우선도를 가진 프로세스가 영원히 block되는 현상이다. 이 문제는 Aging으로 해결한다. Aging에서는 오래 기다린 프로세스의 우선도가 점점 증가한다.

| S.NO | Deadlock                                                     | Starvation                                                   |
| :--- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 1.   | 모든 프로세스가 서로 다른 프로세스가 끝나길 기다리며 아무도 실행되지 않는다. | 높은 우선도의 프로세스만 계속 실행되어 낮은 우선도의 프로세스는 블락된다. |
| 2.   | 자원들이 프로세스에의해 블락된다.                            | 자원은 계속적으로 높은 우선도의 프로세스에 의해 사용된다.    |
| 3.   | 필요조건은 **상호배제, 점유와 대기, 비선점, 환형대기**이다.  | 프로세스에 우선도가 할당된다.                                |
| 4.   | 환형대기라고도 한다.                                         | Also know as lived lock                                      |
| 5.   | 필요조건을 회피하는 방법으로 방지할 수 있다.                 | Aging으로 방지할 수 있다.                                    |

