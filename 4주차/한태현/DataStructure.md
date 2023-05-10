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

## 이외의 자료구조
- LinkedList
- SortedList

### SortedList
List에 추가로 Key값이 들어있다. 요소를 추가할 때 키값을 기준으로 정렬한다. <br>
해시맵과 유사하다.
```CSharp
var ranking = new SortedList<int, string>;
...
DisplayWiner(ranking[1]);
```