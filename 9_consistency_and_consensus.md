분산시스템에서 실패를 다루는 가장 좋은 방법은 그냥 전체가 실패하게 두는 것이다.
하지만 이렇게 할 수 없다면 에러를 핸들링할 방법을 찾아야한다.

실패를 다루는 가장 좋은 방법은 일반적으로 사용할 수 있는 목적의 추상화(공통적으로 사용할 수 있는 시스템)를 하는 것이다.


분산시스템에서 가장 중요한 추상화의 하나는 consensus이다. 모든 노드가 특정한 이슈에 대해 합의하는 것을 의미한다.

Consistency Guarantees
=
대부분의 replicated databases는 eventual consistency를 제공한다.
하지만 이러한 일관성은 '언제'를 보장하지 않기 때문에 약한 Guarantees를 가지고 있다. 

분산시스템의 consistency model과 데이터베이스의 transaction isolation levels은 유사성이 있다.

차이점은 트랜잭션은 race condition을 대비하기 위한 용도라면 분산시스템의 consistency model은 레플리카들 사이의 상태를 일관적으로 맞취주는 것에 초점을 맞춘다는 것이다.

Linearizability
=
분산시스템에서 서로 다른 데이터에 동시에 접근한다면 다른 데이터를 볼 수도 있다. 이런 replication lag를 극복하기 위해 마치 하나의 데이터 소스가 있는 것처럼 보이게하는 linearizability(강한 일관성)를 고려할 수 있다. linearizability를 간단히 설명하면, 변경사항에 대한 즉각적인 보장이다.


Linearizability와 Serializability는 비슷하지만 차이가 있다. Serializability는 트랜잭션과 보다 관련이 있다.
Serializability는 하나의 오브젝트와 관련이 있고, Linearizability는 여러 오브젝트의 관계성에 관련이 있다.

Locking and leader election
=
single-leader replication 시스템은 split brain 현상이 발생하지 않도록 해야한다. 이를 보장하는 하나의 방법은 락이다. 시작할 때 모든 노드들이 락을 얻으려고 경쟁하고, 가장 먼저 획득한 노드를 리더로 선출한다. 이때, Linearizability 개념이 중요하다. 모든 노드가 동의하지 않는다면(합의 알고리즘: consensus) 락은 소용없다.

Constraints and uniqueness guarantees
=
소프트한경우, unsync를 감수하고 이후 보상해주는 방식이 있다. 하지만 엄격한 관리를 위해서는 Linearizability 개념이 중요하다.

Cross-channel timing dependencies
=
Linearizability 개념이 중요하다.


The Cost of Linearizability
=
Linearizability와 성능은 트레이드-오프 관계이다.

Ordering Guarantees
=
Linearizability가 마치 하나의 카피를 가지고 있는 것처럼 행동한다는 것은, 잘 정리된 순서보장 매커니즘이 있다는 것이다.

ordering, linearizability, consensus 사이에는 깊은 상관관계가 있다.
linearizability는 causality를 함축한다.

Ordering and Causality
=
대략 인과관계과 순서의  연관관계..

The causal order is not a total order
=
인과적 순서는 특정한 두 요소를 골랐을 때, 반드시 둘 사이의 대소관계가 있다는 total order와는 다른 개념이다. 예를 들어 {a, b}와 {b, c} 사이에 어떤 것이 크다고 단정할 수 없는 것과 같다. 왜냐하면 동시적 문제에서는 서로 다른 두 이벤트의 순서를 확정하기 어렵기 때문이다.

causal order와 total order를 모두 만족할 때, 동시성 시의 인과관계 문제를 해결할 수 있다. (e.g: using Lamport timestamps) 

Total Order Broadcast
=
linearizability와 유사하지만 비동기, 언제에 대한 보장이 없다는 차이가 있다.

Distributed Transactions and Consensus
=

