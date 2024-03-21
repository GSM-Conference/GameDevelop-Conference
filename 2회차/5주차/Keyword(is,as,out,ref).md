# Keyword(out와 ref, is와 as)

---

키워드는 프로그래밍 언어에서 미리 지정되어있는 **예약어**를 뜻한다

# out 키워드

out 키워드는 **메서드에서 값을 반환할 때 사용**된다

### 특징

- 메서드 안에서 반드시 out을 사용한 변수가 초기화 되야한다.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class KeywordExample : MonoBehaviour
{
    void Start()
    {
        int result;
        if(Add(10, 20, out result))
		        Debug.Log($"Add의 결과는 {result}"); // 출력 : Add의 결과는 30
    }

    bool Add(int a, int b, out int result)
    {
        result = a + b;
        return true; //예시를 들기 위해 true 반환
    }
}

```

# ref 키워드

ref 키워드는 말 그대로 **메서드에 변수를 참조할 때 사용**된다.

### 특징

- ref는 메서드로 **변수가 전달되기 전에 초기화**를 해줘야 한다.
- ref를 사용한 변수는 메서드 내에서 **변수 자체를 수정**할 수 있다.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class KeywordExample : MonoBehaviour
{
    void Start()
    {
        int number = 15;
        Add(10, ref number);
        Debug.Log($"AddTen의 결과는 {number}"); // 출력 : Add의 결과는 25
    }

    void Add(int a, ref int number)
    {
        number += a;
    }
}

```

## out과 ref의 차이점

- **out의 경우에는 메서드** 내에서 **ref의 경우에는 메서드로 전달되기 전에 초기화** 되야한다.
- **out은 메서드가 결과를 외부로 출력**할 때 사용되고 **ref는 변수의 데이터를 변경**할 때 사용된다.

# is 키워드

타입 캐스팅 후 결과에 따라 bool값을 리턴한다. (캐스팅 가능 true / 불가능 false)

값 타입이나 참조 타입 모두 사용 가능

```csharp
using UnityEngine;

public class KeywordExample : MonoBehaviour
{
    private void Start()
    {
        int i = 1;
        if (i is int)//출력 : i is int
            Debug.Log("i is int!");
        else
            Debug.Log("i is not int..");

        if(i is 2)//출력 : i is not 2.. 
            Debug.Log("i is 2!");
        else
            Debug.Log("i is not 2..");
    }

}
```

# as 키워드

타입 캐스팅 가능 여부에 따라 결과 혹은 null을 리턴한다. (가능 캐스팅 결과/ 불가능 null)

null 허용 타입 혹은 참조 타입만 가능

```csharp
using UnityEngine;

class testP
{ 
    //부모 클래스
}
class testC : testP
{ 
    //자식 클래스
}
public class KeywordExample : MonoBehaviour
{
    private void Start()
    {
        testP p1 = new testP();
        testC c1 = new testC();

        p1 = c1 as testP;

        testP p2 = new testP();
        testC c2 = new testC();

        c2 = p2 as testC;

        Debug.Log($"p1 : {p1}, c2 : {c2 == null}");//출력 p1 : testC, c2 : True
    }
}

```