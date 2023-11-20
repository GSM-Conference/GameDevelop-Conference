# **자료구조**


## 유니티에서 자주쓰이는 자료구조
- Stack
- Queue
- Dictionary
- List

### Stack
Last In First Out(LIFO)로 마지막에 넣은 데이터가 먼저 나온다. <br>
*ex. 디펜스게임에서 마지막 적만 공격하는 터렛)*
```CSharp
// 공격범위 트리거에 걸리면,
OnTriggerEnter2D(Collision2D collision)
{
    targets.Push(collision.gameObject);
}

//공격 메소드
Attack()
{   
    if(targets.Count > 0)
    {
        // 스택의 맨 위 요소를 가져옵니다.
        GameObject target = targets.Peek();
        ...
    }
}
```

### Queue
First In First Out(FIFO)로 처음에 넣은 데이터가 먼저 나온다. <br>
*ex. 디펜스게임에서 맨 앞 적만 공격하는 터렛)*
```CSharp
// 공격범위 트리거에 걸리면,
OnTriggerEnter2D(Collision2D collision)
{
    targets.Push(collision.gameObject);
}

//공격 메소드
void Attack()
{   
    if(targets.Count > 0)
    {
        // 큐의 맨 앞 요소를 가져온다.
        GameObject target = targets.Peek();
        ...
    }
}
```

### Dictionary
Key-Value페어로 되어있는 해쉬맵기반의 자료구조다. <br>
해쉬맵: 키값을 해싱해서 값의 접근속도가 O(1)이 되는 자료구조이다. <br>
*ex.유저명을 통한 데이터접근)*
```CSharp
/*                              유저명    데이터   */
var scoreBoard = new Dictionary<string, UserData>();
... 
scoreBoard["index"].점수;
scoreBoard["KGEW"].비밀번호
// TryGetValue사용
// if(scoreBoard.TryGetValue("rkdwldns", out data)) { ... }
```

### List
배열에서 확장된 형태의 자료구조 입니다. 여러가지 함수를 지원합니다.
```CSharp
var itemList = new List<Item>;

// 포션 사용
void UsePortion()
{
    // 리스트에서 힐포션을 찾아 제거합니다.
    itemList.Remove(itemList.Find(i => i.name == "Heal"))
    ...
}
```

### 이외의 자료구조(Deque)
Double-Ended Queue로, 한 방향으로만 삽입, 삭제가 되는것과 달리 양방향으로 가능하다.
```CSharp
// 정의
public class Deque<T>
{
    public T PopBack() {...}
    public T PopFront() {...}
    public void PushBack() {...}
    public void PushFront() {...}
}
```
*ex.디펜스게임에서 범위에 나갔다가 들어온 적이 있다면 먼저 공격)*
```CSharp
OnTriggerEnter2D(Collision2D collision)
{
    if(collision.GetComponent<Enemy>().IsEntered)
    {
        deque.PushFront(collision.gameObject);
    }
    else
    {
        deque.PushBack(collision.gameObject);
    }
}
```