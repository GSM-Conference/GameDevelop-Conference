# 제네릭

### 개념

제네릭은 사용할 자료형을 외부에서 지정할 수 있는 기법이다.

c#에서 제네릭을 사용가능한 구조의 목록은 다음과같다.

- 클래스
- 인터페이스
- 구조체
- 메서드(익명함수 포함)

## 공통 사용법

제네릭은 이름뒤에 꺽쇠를 붙여 사용하며, 아래의 코드와같이 타입을 여러개 받거나,

타입을 제한할 수 있다.

```csharp
class Util<T> { }           //기본 형태
class Util<T1,T2> { }       //타입을 여러개 받을수도 있다.
class Util<T> where T : Parent { }    //T의 타입을 Parent를 상속한 타입으로 제한
class Util<T> where T : class { }     //T의 타입을 클래스로 제한
class Util<T> where T : struct { }    //T의 타입을 구조체로 제
class Util<T1, T2> where T1 : Parent where T2 : Parent { }   //다중 제한도 가능하다.
```

또한 제네릭도 매개변수처럼 오버라이드가 가능하다.

### 제네릭의 사용예시

```csharp
//제네릭 클래스
class Class<T> {}

//제네릭 구조체
struct Struct<T> {}

//제네릭 인터페이스
interface Interface<T> {}

//제네릭 메서드
void Function<T>() {}

//제네릭 대리자
delegate TResult Func<out TResult>();
```

유니티에서 제공해주는 기능들도 제네릭을 사용하는경우가 있다.

- List<T>
- T Getcomponent<T>()
- delegate TResult Func<TResult>()
- 등등…

## 제네릭의 사용이유

- 여러가지 타입을 지원함으로서 재사용성을 늘린다.
- 캐스팅횟수를 줄일수있다.

# 내 사용경험

## 자바 프로젝트

C#은 아니지만 자바프로젝트때 GetComponent함수를 구현하면서 쓴적이있다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c223246e-9ea3-4af3-b62a-3fbbacff1137/Untitled.png)

## 유니티 자료형

제네릭을 직접정의해본적은 아직 없지만, 여러가지 유니티 기본제공기능에서 응용해보았다.