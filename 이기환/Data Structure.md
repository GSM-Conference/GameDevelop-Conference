# Stack

스택은 마지막에 들어온 데이터를 먼저 처리하는 후입선출(LIFO, Last In First Out) 형태의 자료구조 이다. 주로 최근에 입력된 데이터를 순서대로 처리할 때 사용한다.

### 대표적인 기능

- Push : 스택의 가장 위에 데이터 요소를 추가한다.
- Pop : 스택의 가장 위에 있는 데이터 요소를 참조한 뒤 삭제한다.
- Peek : 스택의 가장 위에 있는 데이터 요소를 참조한다.

### 예시

스택은 게임 상태를 되돌릴 때 사용할 수 있다. 혼자서 플레이하는 바둑, 오목, 체스, 스파이더 카드게임 등에서 게임을 이전 상태로 되돌리기 위해 스택을 사용할 수 있다.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class StackExample : MonoBehaviour
{
    Stack<GameStatus> gameStatus = new Stack<GameStatus>();
		//게임상태를 저장하는 GameStatus 클래스를 관리하는 스택을 선언한다.
		GameStatus currentStatus;
		//현재 게임상태를 저장하는 변수를 선언한다.

		public void AddGameStatus(GameStatus addGS)
		{
				gameStatus.add(addGS);
				currentStatus = gameStatus.peek();
		} //게임상태를 스택을 추가한 뒤 현재 게임상태를 변경한다.

		public void RevertGameStatus()
		{
				gameStatus.pop();
				currentStatus = gameStatus.peek();
		} //게임상태를 취소한 뒤 현재 게임상태를 되돌린다.
}
```

---

# Queue

큐는 처음 들어온 데이터를 순서대로 처리하는 선입선출(FIFO, First In First Out) 형태의 자료구조 이다. 주로 입력된 데이터를 순서대로 처리할 때 사용한다.

### 대표적인 기능

- EnQueue : 큐의 마지막 부분의 데이터 요소를 추가한다.
- DeQueue : 큐의 시작 부분의 데이터 요소를 참조한 뒤 삭제한다.
- Peek : 큐의 시작 부분의 데이터 요소를 참조한다.

### 예시

클로시 로얄의 덱 순환 방식을 예시로 들 수 있다. 현재 사용할 수 있는 4개의 카드 이 외에 카드를 사용했을 때 새로 들어올 대기중인 카드가 큐로 이루어져있다. 현재 카드 하나를 사용하면 대기 카드 큐의 시작 부분에 있는 카드가 새로 들어오고 사용한 카드는 대기 카드 큐의 마지막 부분에 추가되는 방식이다.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class QueueExample : MonoBehaviour
{
    Queue<Card> waitingCards = new Queue<Card>();
		//카드의 정보를 저장하는 Card 클래스를 관리하는 대기중인 카드 큐를 선언한다.
		List<Card> currentCards = new List<Card>();
		//현재 사용가능한 카드를 관리하는 리스트 선언.

		public void UseCard(Card useCard)
		{
				currentCards.Remove(useCard); //현재 가지고 있는 카드 중 사용한 카드를 삭제한다.
				currentCards.Add(waitingCards.DeQueue()); //대기 카드의 맨 앞 카드를 현재 카드에 추가한다.
				waitingCards.EnQueue(useCard); //대기 카드 맨 뒤에 사용한 카드를 추가한다.
		}
}
```

---

# Dictionary

딕셔너리는 인덱스 번호 대신 사용하는 Key와 값을 다루는 Value를 같이 사용하는 자료구조 이다. Key를 참조하여 Value를 얻기 때문에 숫자, 문자열 등을 Key로 사용할 수 있다. 다만 중복된 Key는 사용할 수 없다.

### 대표적인 기능

- Add(TKey, TValue) : 딕셔너리에 지정한 키와 값을 가진 데이터 요소를 추가한다.
- Remove(TKey) : 딕셔너리에 지정한 키값을 가진 데이터 요소를 제거한다.
- TryGetValue(TKey, out TValue) : 딕셔너리에서 지정한 키값을 가진 데이터 요소를 TValue에 반환한다.

### 예시

게임 난이도나 상태를 불러올 때 딕셔너리를 사용할 수 있다. 예를 들어 게임 난이도에 따라 체력, 공격력, 적 대미지 등이 바뀔때 이러한 정보를 저장하는 게임 난이도 클래스를 관리하는 딕셔너리를 생성해 게임 난이도 시스템을 구현할 수 있다.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class DictionaryExample : MonoBehaviour
{
		Dictionary<int, GameDifInfo> gameDifInfo = new Dictionary<int, GameDifInfo>;
		//게임 난이도를 Value로 저장하는 딕셔너리를 선언한다.
		GameDifInfo curGameDif;
		//현재 게임난이도를 저장하는 변수를 선언한다.

		public void SetGameDif(int difLevel) => TryGetValue(difLevel, out curGameDif);
		//설정할 게임난이도 값을 Key값으로 가진 게임난이도를 현재 게임난이도에 반환한다.
}
```

---

# List

일반적인 배열과 다르게 동적으로 크기 조절이 가능한 기본적인 자료 구조이다. 인덱스 번호를 통해 데이터 요소에 접근할 수 있고, 배열에 크기에  크게 신경쓰지 않아도 되며 여러 기능을 지원한다.

### 대표적인 기능

- Add(T) : 리스트의 마지막 부분에 데이터 요소를 추가한다.
- Remove(T) : 리스트에서 먼저 확인되는 T값을 가진 데이터 요소를 삭제한다.
- Insert(int index, T) : 리스트의 index번째 인덱스에 T값을 가진 데이터 요소를 추가한다.

### 예시

지방기능경기대회 과제에서 랭킹 시스템을 구현할 때 사용하였다. 닉네임과 점수를 가지고 있는 Rank 클래스를 만든 뒤 `List<Rank> ranking = new List<Rank>();` 를 통해 Rank 클래스를 관리하는 리스트 ranking을 만들어 랭킹 시스템을 구현하였다.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ListExample : MonoBehaviour
{
		List<Rank> ranking = new List<Rank>();
		//닉네임과 점수를 저장하는 Rank 클래스를 관리하는 리스트를 선언한다.

		public void AddRank(Rank rankInfo)
		{
				ranking.Add(rankInfo); //ranking 리스트에 새 Rank 클래스를 추가한다.

				for (int i = ranking.Count; i > 0; i--)
				{
						if (ranking[i].score > ranking[i-1].score
						{
								Rank temp = ranking[i];
								ranking[i] = ranking[i-1];
								ranking[i-1] = temp;
						}
				}
				// for문을 실행해 점수순으로 ranking 리스트를 정렬한다.
		}
}
```

---

# LinkedList

연결 리스트는 데이터를 가지고 있는 노드들을 연결하여 만든 자료구조로 각 노드들은 데이터와, 이전/ 다음 노드들의 포인터를 가지고 있다.

### 대표적인 예시

- AddAfter(LinkedListNode<T>, LinkedListNode<T>) : 연결 리스트에 지정한 노드 다음에 새 노드를 생성한다.
- AddBefore(LinkedListNode<T>, LinkedListNode<T>) : 연결 리스트에 지정한 노드 이전에 새 노드를 생성한다.
- AddFirst(LinkedListNode<T>) : 연결 리스트의 가장 앞에 새 노드를 생성한다.
- AddLast(LinkedListNode<T>) : 연결 리스트의 가장 뒤에 새 노드를 생성한다.

### 예시

연결 리스트는 몬스터의 행동 패턴 등을 구현할 때 사용할 수 있다. 예를 들어 몬스터의 행동을 정찰, 추격, 공격으로 나눈뒤 조건에 따라 행동이 바뀔 때 연결 리스트를 통해 몬스터 행동 패턴을 구현할 수 있다.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class LinkedListExample : MonoBehaviour
{
		LinkedList<MonsterBhv> MonsterBhvs = new LinkedList<MonsterBhv>();
		//몬스터의 행동들을 저장하는 MonsterBhv를 관리하는 연결리스트를 선언한다.
		MonsterBhv curMonsterBhv;
		//현재 몬스터의 행동을 저장하는 변수를 선언한다.

		public void ChangeNextBhv()
		{
				curMonsterBhv = MonsterBhvs.Find(curMonsterBhv).Next.Value;
				//MonsterBhvs 연결리스트에서 현재 행동의 다음 행동을 현재 행동으로 설정한다.
		}

		public void ChangePrevBhv()
		{
				curMonsterBhv = MonsterBhvs.Find(curMonsterBhv).Previous.Value;
				//MonsterBhvs 연결리스트에서 현재 행동의 이전 행동을 현재 행동으로 설정한다.
		}
}
```