# 리스트(List)

배열과 유사한 기본적인 선형자료구조

## 개념

리스트는 배열과 유사한 형태를 가지지만 가변적인 길이를 가진다.

## 배열리스트

리스트를 구현할때 배열을 사용하는 리스트이다.

유니티에서는 List<T> 클래스를통해 사용할수있다.

### 특징

- 메모리의 물리적위치가 연속적이다.
- 원소 추가나 삭제시 나머지원소의 위치를 조정해줘야하기때문에 오래걸린다.

### 사용예시

[관찰자 패턴](https://www.notion.so/f5d04f2e80d14f8d85ec2c267f76409a) : 발행자가 관찰자를 저장할때 활용한다.

## 연결리스트

리스트를 구현할때 원소들을 서로 연결시키는 리스트이다.

유니티에서는 LinkedList<T> 클래스를통해 사용할수있다.

### 특징

- 메모리의 물리적위치가 서로 떨어져있을수있다.
- 원소의 추가나 삭제시 참조몇개만 바꾸면되기때문에 빠르다.
- 원소참조시 참조를 여러번해야되기때문에 느리다.

### 사용이유

원소의 추가나 삭제가 자주일어날경우 배열리스트보다 더빠르다.

# 스택(Stack)

선입후출의 형태를 가지는 선형자료구조

유니티에서는 Stack<T> 클래스를통해 사용할수있다.

## 형태

![https://blog.kakaocdn.net/dn/bcgR9A/btqSX70PCTe/dMSMQoJcZhDpq4sRRpu3A0/img.png](https://blog.kakaocdn.net/dn/bcgR9A/btqSX70PCTe/dMSMQoJcZhDpq4sRRpu3A0/img.png)

Push : 스택에 정보를 삽입함

Top : 가장 마지막에 Push된 정보

Peek : Top의 정보를 확인함(삭제되지 않음)

Pop : Top의 정보를 가져옴

## 특징

- foreach로 순회할시 Top부터 순서대로 나온다.
- 비어있는 스택에 Peek나 Pop을 실행하면 에러가 발생한다.

## 사용이유

뒤로가기등을 구현할수있다.

아래는 간단하게 이동과 뒤로가기를 구현한 예시이다.

```jsx
public class Character : MonoBehaviour
{
    Stack<Vector3> positionLogs;

    public void Move(Vector3 power)
    {
        positionLogs.Push(transform.position);
        transform.position += power;
    }

    public void Undo()
    {
        if (positionLogs.Count == 0) return;
        transform.position = (positionLogs.Pop());
    }
}
```

# 큐(Queue)

선입선출의 형태를 가지는 선형자료구조

유니티에서는 Queue<T> 클래스를통해 구현할수있다.

## 형태

[https://t1.daumcdn.net/cfile/tistory/9929C0495C932BB115](https://t1.daumcdn.net/cfile/tistory/9929C0495C932BB115)

Enqueue : 큐에 데이터를 삽입하는 함수

Rear : 가장나중에 Enqueue된 데이터의 자리

Front : 가장먼저 Enqueue된 데이터의 자리

Dequeue : Front를 가져오는함수

## 특징

- foreach로 순회할시 Front부터 순서대로 나온다.
- 비어있는 큐에 Deque를 실행하면 에러가 발생한다.

## 사용이유

- 버퍼를 구현하는데 쓰인다.

# 딕셔너리(Dictionary)

Key와 Value로 이루어진 자료구조

유니티에서는 Dictionary<TKey, TValue> 클래스로 구현할수있다.

## 형태

![https://velog.velcdn.com/images%2Ffalling_star3%2Fpost%2F31116191-e4b8-48ac-b709-b02a15f442b7%2F444.JPG](https://velog.velcdn.com/images%2Ffalling_star3%2Fpost%2F31116191-e4b8-48ac-b709-b02a15f442b7%2F444.JPG)

딕셔너리는 한 인덱스에 Key와 Value가 대응되어 들어있는 자료구조이다.

## 특징

- 인덱싱을할때 int를 요구하지않고 Key를 통해 Value를 구할수있다.

## 사용이유

- 특정정보를 가지고있으면 관련된정보를 제공해줄수있다.
- 가독성이 좋아진다.

아래는 몬스터의 이름을 넣으면 그몬스터의 정보를 반환해주는 클래스를 구현한예시이다.

```jsx
class MonsterBook
{
    static Dictionary<string, string> information = new Dictionary<string, string>()
    {
        {"멍멍이","I love you"},
        {"요정","맛있겠다~"},
        {"작은 새","흰머리오목눈이" },
        {"해골","666"}
    };

    public static string GetInformation(string name)
    {
        if (!information.ContainsKey(name)) return "-";
        return information[name];
    }
}
```

# 해시셋(HashSet)

List<T>와 유사하지만 중복된값을 허용하지않는 자료구조이다.

유니티에서는 HashSet<T> 클래스로 구현할수있다.

## 특징

- 정보를 순서대로 저장하지않는다.(인덱싱불가능)
- 원소를 삽입할때 bool Add(T item); 함수를 사용한다.

## 사용이유

- 원소의 중복을 방지하기위해

# C# 자료구조의 인터페이스 상속여부

|  | List | LinkedList | Stack | Queue | Dictionary | HashSet |
| --- | --- | --- | --- | --- | --- | --- |
| ICollection<T> |            O |            O |            X |            X |            O |            O |
| ISerialzable |            X |            O |            X |            X |            O |            O |
| IDeserializationCallback |            X |            O |            X |            X |            O |            O |

### 공통적으로 상속하는 인터페이스

- ICollection
- IEnumerable
- IEnumerable<T>
- IReadOnlyCollection<T>

## 인터페이스의 역할