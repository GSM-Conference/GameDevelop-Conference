# C# 비동기 프로그래밍

> ## 동기와 비동기
![](https://wikidocs.net/images/page/168327/concurrency-Page-4.drawio_1.png) <br>

### 비동기
비동기(Asynchronous) 함수는 함수를 호출하면 즉시 반환되고, 완료되면 콜백을 호출하는 방식의 함수입니다.<br>
주로 멀티스레드를 통해 이루어집니다. <br>

### 동기
그 반대로 동기(Synchronous) 함수는 함수를 호출하면 반환될때까지 대기하는 방식의 함수입니다. <br>

### 코루틴
추가로 코루틴이 있습니다. 코루틴도 비동기 방식으로 작업하지만, 멀티스레드가 아니라 시분할을 통해 이루어집니다.
<br> 그 장점으로 데이터레이스나 데드락, 컨텍스트 스위칭의 비용을 줄일 수 있습니다.

### 차이점
동기는 직렬적으로 처리하고, 비동기는 병렬적으로 처리한다는 것이 차이점입니다.<br>
만약 싱글스레드라면 비동기는 시분할로 인해 성능이 느려질 수 있습니다.

<br>

---

<br>    

> ## C#에서의 비동기 프로그래밍

### Async/Await
`async`와 `await` 키워드는 비동기 프로그래밍에서 사용하는 키워드 입니다. <br>
- async 키워드 <br>
    `await`가 있는 함수를 사용할 수 있게 비동기 방식으로 바꿔주는 함수입니다. <br> 
    사용법 : `public async void Run() { await ...; }`
- await 키워드 <br>
    `async`함수 내에서 비동기 함수가 완료될때까지 대기하는 키워드입니다. <br>
    사용법 : `await Task.Delay(100);`

#### 사용 예
```Csharp
static void Main(string[] args)
{
    SomethingWork(); // 대기하지 않고 진행된다.
    for(int i = 0; i < 10; ++i)
    {
        Console.WriteLine("Main is working.");
        Thread.Sleep(100); // 100ms(0.1초)동안 대기
    }
    // 결과 : 대략 5번 찍었을 때 Something work.가 출력된다.
}

static async void SomethingWork()
{
    await Task.Delay(500);
    Console.WriteLine("Something work.");
}

```

### Unity 코루틴
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTNWacm-JA9tT5lk8L4j3oGSFKZyeHplyuDpg&usqp=CAU) <br>
유니티에서 `IEnumerator`와 `StartCoroutine`을 통해 코루틴을 사용할 수 있도록 제공해줍니다.<br>
사용법으로는 `yield`를 통해 지정된 시간동안 주 스레드에게 실행권을 반환해 딜레이를 주는 방식을 사용합니다.