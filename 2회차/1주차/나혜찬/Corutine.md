

# 코루틴이란?

<aside>
💡 유니티 프로그래밍에서 사용되는 문법 중 하나로, 시간의 경과에 따른 명령을 표현하기 좋은 방식이다.

</aside>

# 코루틴의 구성

<aside>
💡 IEnumerator라는 반환타입을 가지고 중간에는 yield return이 들어가야한다.

### yield return

- yield return null;
    
    다음 프레임에 실행
    
- yield return new WaitForSeconds(float sec);
    
    sec만큼의 시간 후에 실행
    
- yield return new WaitForSecondsRealtime(float sec);

sec만큼의 실제시간 후에 실행

- yield break

해당 키워드를 만나면 코루틴을 빠져나오게 됨

</aside>

```csharp
IEnumerator CoroutineName()
    {
        yield return null;
    }
```

# 코루틴의 실행

<aside>
💡 StartCoroutine() 메서드를 사용하여 실행할 수 있다.

</aside>

```csharp
     	StartCoroutine(Test());  //인자를 넣는것도 가능하다
        StartCoroutine("Test");
```

# 

# 코루틴의 정지

<aside>
💡 StopCoroutine() 메서드를 사용하여 실행할 수 있다.

</aside>

```csharp
     	StopCoroutine(Test());
        StopCoroutine("Test");
```

# 코루틴 예제

```csharp
public class CoroutineTest : MonoBehaviour
{
    int second = 0;
    void Start()
    {
        StartCoroutine(Test());
    }

    IEnumerator Test()
    {
        while (true)
        {
            Debug.Log(second++ +"초");
            yield return new WaitForSeconds(1);
        }
    }
}
```