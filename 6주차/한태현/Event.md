# **UnityAction와 UnityEvent**

## UnityAction
이벤트 프로그래밍에서
델리게이트 대신에 사용되는 클래스이다. 사용방법은 C#의 Action과 같다. <br>
### 사용법
```CSharp
// 기존의 델리게이트 방식

delegate void f(); // 델리게이트 형식 정의
f f1; // 델리게이트 객체 생성

void Start()
{
    f1 = printHello();    // 함수 대입
    f1();    // 함수 호출
}

void printHello()
{
    Debug.Log("Hello");
}
...

// UnityAction을 사용

UnityAction action;

void Start()
{
    action = printHello();
    action();
}

```
### C# Action과의 차이점
둘이 사용하는 방식은 똑같지만, 유니티이벤트가 메모리 할당량이 낮다. 하지만 속도가 상대적으로 느리다.

---

## UnityEvent
유니티에서 사용하는 이벤트 객체이다. 특정 상황에서 이벤트나 함수를 호출하고 싶을 때 사용된다.<br>
public, SerializedField로 선언시 에디터 인스펙터에서 수정할 수 있다.
Invoke호출 시 등록된 이벤트 핸들러(콜백함수 = UnityAction)를 호출한다. <br>
유니티이벤트를 사용한 예로는 유니티UI의 Button에 선언된 OnClick이 있다.
![](https://answers.unity.com/storage/temp/45113-button.jpg) <br>
### 사용법
```CSharp
// 이벤트 객체
UnityEvent OnDead;

void Start()
{
    OnDead = new UnityEvent();

    // 콜백 등록
    OnDead.AddListener(Func1);
    OnDead.AddListener(Func2);

    // 콜백 삭제
    OnDead.RemoveListener(Func2);
}

OnTriggerEnter2D(Collision2D collision)
{
    OnDead.Invoke();
}

void Func1()
{
    Debug.Log("Hi");
}

void Func2()
{
    Debug.Log("Hello");
}

```
---
