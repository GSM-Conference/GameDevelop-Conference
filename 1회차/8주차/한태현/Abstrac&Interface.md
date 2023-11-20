# 추상 클래스와 인터페이스

## 1. 추상 클래스
추상클래스는 **추상 메서드**를 구현하도록 유도시켜 **규격화** 하는 클래스이다. 추상 클래스를 상속받는 클래스는 모두 추상 클래스에 정의된 추상 메서드를 구현해야만 한다. <br>

### 선언
추상 클래스의 선언은 앞에 `abstract`를 붙여주고, 추상 메소드에도 `abstract`를 붙여주면 된다.

### 예시 코드
```cs
abstract class Animal
{
    // 자식 클래스에서 구현해야할 메소드
    public abstract void Speak();
}
class Cat :  Animal
{
    // 추상 메서드 구현
    public override void Speak()
    {
        Console.WriteLine("Meow");
    }
}

...

Animal cat = new Cat();
cat.Speak() // Meow
```
위 예시와 같이 추상클래스에 추상 메서드를 선언하고, 자식클래스에서 그것을 구현하는 방식으로 사용한다. <br> 
만약 추상메서드를 구현하지 않는다면 **컴파일 애러**가 난다.

<br>

---

<br>

## 2. 인터페이스
인터페이스는 각각의 기능별로 추상화 시켜놓은 추상메서드와 정적필드의 집합이다. 인터페이스의 멤버로는 추상메서드나 정적 필드만 있을 수 있다. 인터페이스의 네이밍은 `I-able`을 주로 사용한다.

### 선언
클래스 대신 `interface`를 사용해 선언한다.

### 예시 코드
```cs
interface IChargeable
{
    protected static int ChargeSpeed = 15;

    abstract void ChargeEnergy();
    abstract void UseEnergy();
}

class Laptop : IChargeable
{
    private int battery = 100;
    public void ChargeEnergy()
    {
        battery += IChargeable.ChargeSpeed;
    }

    public void UseEnergy()
    {
        battery -= 1;
    }
}
```
위와 같이 '충전할 수 있는`과 같이 특정 기능이 있는 인터페이스를 상속하여 모듈 형식으로 여러 개를 상속받을 수 있다. 추상클래스보다 추상화 정도가 강하다.

<br>

---

<br>

## 추상클래스와 인터페이스와 차이점
설계적 차이점으로는 추상클래스를 상속받은 클래스는 추상클래스 '이다`, 인터페이스를 상속받은 클래스는 인터페이스를 '할 수 있는' 이라는 논리의 차이점이 있다. <br>
모두 인터페이스를 상속받는다면 공통된 부분도 각각 모두 구현해줘야 하는 불편함이 있다. 하지만 추상클래스를 사용하면 공통된 부분을 재사용 할 수 있다.<br>
## 정리
기능을 분리한다면 인터페이스, 각각의 클래스끼리 공통된 부분이 있다면 추상클래스를 사용하면 된다.