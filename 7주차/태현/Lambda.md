# C# 람다식(Lamda Expression)

## 람다
람다는 **무명함수**를 가리키는 말로 람다식 또는 람다표현식이라고 쓰기도 한다. <br>
람다의 특징은 메소드를 정의하지 않고, 함수 안에 직접 콜백함수를 정의 할 수 있는 편의성이 특징이다. <br>
무명함수 이외에도 한줄로 된 간단한 메소드를 정의할 때 사용할 수 있다.
#### | 사용법
`리턴타입 (매개변수 목록) => { ... }`

## 활용
C#에서는 람다 그 자체보다는 콜백 형태로 사용하기 위해서 델리게이트와 함께 쓰인다. <br>
람다를 저장하고 사용하기위해서는 크게 3가지 방법이 있다.

### 1. var
람다식을 선언과 동시에 변수에 저장시키는 가장 간편한 방법이다. 하지만 함수의 형태를 유추 할 수 없어 활용도가 낮다는 단점이 있다.

#### | 예시
```CSharp
var Add = (int a, int b) => { return a + b; }
Add(1, 2) // 결과 : 3
```

### 2. Func<>
Func는 var과 달리 리턴타입, 매개변수 목록을 설정할 수 있어 콜백의 형태를 정의해줄 수 있다. <br>
Func는 `Func<매개변수1, 매개변수2, ..., 리턴타입>`으로 정의되어있다.

#### | 예시
```CSharp
Func<int> Add = int (int a, int b) => { return a + b; }
Add(1, 2) // 결과 : 3

// 인수: 1개(int), 리턴: int64
Func<int, int64> Square = (int n) => return n*n; // 식 람다
Square(5) // 결과 : 5
```

### 3. Action<>
말 그대로 동작만 있는 함수. Func와 달리 리턴이 없는 함수만 넣을 수 있다. <br>
Action은 `Action<매개변수1, 매개변수2, ...>`으로 정의되어있다.

#### | 예시
```CSharp
Action SayHello = () => Console.WriteLine("Hello");
Action<string> SaySomething = (string message) => Console.WriteLine(message);
SayHello()
SaySomething("World!");
```