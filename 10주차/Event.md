# C# event

## 이벤트
클래스나 객체에서 특정 상황이 발생할 때 이벤트를 보내 알릴 수 있다. <br>
이벤트를 보내거나 발생시키는 클래스를 `게시자`라고 하고 이벤트를 받거나 처리하는 클래스를 `구독자`라고 한다.
보통 비동기 프로그래밍에서 콜백을 호출하고 완료통지 할때나 GUI프로그래밍에서 이벤트를 처리할 때 사용된다.

게시자는 이벤트가 발생했을 때 어떻게 처리할 지 `EventHandler`를 통해 정해준다. <br>
EventHandler는 (sender, args)형태의 델리게이트이고, 제네릭을 사용하여 인자 클래스를 바꿀 수 있다. <br>
만약 구독자에서 이벤트를 추가하고 싶다면 `+=`연산자를 사용하면 된다. <br> 추가할 수 있는 함수는 여러개가 될 수 있고, `-=`를 사용하여 제거 할 수 있다.

## 예제
```csharp
class Button
{
    public event EventHandler OnClick;
        
    public void Click()
    {
        OnClick?.Invoke(this, EventArgs.Empty);
    }
}
class Program
{
    static void Main(string[] args)
    {
        Button button = new Button();
        button.OnClick += (object sender, EventArgs args) => {
            Console.WriteLine("Hello World!");
        };
        button.Click(); // 결과 : Hello World!
    }
}
```
`event` 키워드가 없어도 작동은 할 수 있다. 하지만 그냥 EventHandler 변수라고 하는것보단, 이벤트라고 명시해 줌으로써 이 변수가 콜백으로 호출되는 이벤트라고 알려 줄 수 있다.

명시해주지 않은 경우 <br>
![](https://github.com/GSM-Conference/GameDevelop-Conference/assets/63224377/f24135c1-aa82-41c5-9974-013ad7be36ad)

명시해준 경우 <br>
![](https://github.com/GSM-Conference/GameDevelop-Conference/assets/63224377/d2b498c5-30b7-4c1c-b234-6c8e77f2262c)