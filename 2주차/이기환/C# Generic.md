# C# Generic

제네릭은 데이터 타입을 확정하지 않고 그것을 사용할 시점에 타입을 정의하는 것을 말한다.

일반적으로 비슷한 형식의 메소드나 클래스, 인터페이스를 만들때 데이터 타입 때문에 여러번 구현해야할 때 제네릭을 사용하면 여러개를 만들 필요없이 하나의 메소드나 클래스, 인터페이스로 정의가 가능하다. 제네릭을 선언할땐 주로 Type의 T로 선언한다.

## 예시 (제네릭 메서드)

### 일반적인 메서드의 문제점

```csharp
public void Print(int value)
{
	Debug.Log(value);
}

public void Print(float value)
{
	Debug.Log(value);
}
...
```

위의 코드에서 오버로딩을 통해 매개변수를 Debug.Log로 출력하는 메서드 Print() 를 구현했다. 만약 int, float 타입 뿐 아니라 string, bool 등의 다른 타입들의 메서드도 구현해야 할 때 내부 구조가 같음에도 매개변수가 다르기 때문에 여러 메서드를 생성해야 하는 일이 발생한다. 이러한 경우 제네릭을 사용하여 코드를 줄일 수 있다.

### 제네릭 메서드

```csharp
public void Print<T>(T value)
{
	Debug.Log(value);
}
```

이렇게 하면 하나의 메서드로 여러 타입을 받을 수 있다. 코드를 살펴보면 <T>는 형식 매개변수로 메서드를 호출할 때 T 대신 원하는 형식을 넣어 사용할 수 있다. T 대신 키워드를 작성할 경우 컴파일 에러가 발생하니 주의 해야한다.

`Print<int>(10);` 

`Print<string>("debug");`

메서드 호출은 이런식으로 할 수 있다.

### 제네릭 메서드의 매개변수와 형식 매개변수

`void Print<T>(T value1, T value2) {…}` 

`void Print<T, Y>(T value1, Y value2) {…}`

이 외에도 이런 식으로 여러개의 매개변수나 형식 매개변수를 가질 수 있다.

### 제네릭 형식의 반환타입을 사용한 메서드

```csharp
public T Return<T>(T value)
{
	return value;
}
```

또는 이런 식으로 반환타입 또한 제네릭 형식을 사용하여 메서드를 구현할 수도 있다.

### 제네릭 메서드 호출 시 <> 생략

`Print<int>(10); ⇒ Print(10);`

이런 식으로 <>를 생략하고 제네릭 메서드를 호출할 경우 컴파일러가 매개변수의 타입을 유추해 해당 메서드의 형식 매개변수를 유추한 타입으로 치환한다.

### 유니티에서 사용되는 제네릭 메서드

유니티에서 많이 사용되는 대표적인 제네릭 메서드로 GetComponent 메서드가 있다. 유니티에서 각 컴포넌트에 접근할 때 GetComponentRigidbody, GetComponentTransform 등 각각의 메서드로 접근하기 힘들기 때문에 GetComponent<T> 로 해결할 수 있다.

## 그 외 내장된 제네릭 클래스 기능

`using System.Collections.Generic` 로 네임스페이스 선언을 해주면 여러 제네릭 클래스 기능을 사용할 수 있다.

### 예시

- ArrayList<T>
- LinkedList<T>
- List<T>
- Stack<T>
- Queue<T>

## 직접 제네릭을 사용한 경험

메서드나 클래스 등에 직접 제네릭을 적용한 경험은 없지만 List<T> 기능을 지방기능대회에서 랭킹시스템을 구현할 때 사용했었다. 닉네임과 점수를 저장하고 있는 Rank 클래스를 생성한 뒤

`public List<Rank> ranking = new List<Rank>();`

으로 Rank 클래스를 리스트 형태로 관리하여 랭킹 시스템을 구현한 적 있다.