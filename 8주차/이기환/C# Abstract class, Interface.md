# C# Abstract class, Interface

# 추상 클래스 (Abstract class)

추상 클래스란 하나 이상의 추상 메서드를 가지는 클래스이다. abstract 키워드를 사용한다.

## 추상 클래스의 특징

- new 연산자로 인스턴스를 생성할 수 없다.
- 자식 클래스의 상속을 통해서만 구현 가능하다.
- 추상 메서드와 추상 프로퍼티를 가질 수 있다.

## 추상 메서드의 특징

- abstract 키워드를 사용한다.
- 암시적으론 가상(virtual) 메서드이기에 구현 시 override 키워드를 사용해야 한다.
- 추상 클래스에서만 선언할 수 있다.
- 선언 시 static, virtual 키워드는 사용할 수 없다.
- 메서드 본문이 존재하지 않는다.
- 자식 클래스가 추상 클래스가 아니라면 무조건 구현해야 한다.

## 추상 클래스 구현 예시

추상 클래스 구현 예시로는 Monster 추상 클래스를 생성한 뒤 자식 클래스에서 상속받아 메서드를 구현하는 기능을 구현하였다.

```csharp
using UnityEngine;

public abstract class Monster : MonoBehaviour // 추상 클래스 구현
{
    protected int atk;

    protected abstract int Atk { get; set; } // 추상 프로퍼티 구현

    protected abstract void Attack(int atk); // 추상 메서드 구현
}

class Zombie : Monster
{
    protected override int Atk { get => atk; set => atk = value; }
    protected override void Attack() => Debug.Log("Bite, Damage : " + Atk);
    protected override void Move() => Debug.Log("Walk");
}

class WildBoar : Monster
{
    int rushAtk;
    protected override int Atk { get => atk + rushAtk; set => atk = value; }
    protected override void Attack()
    {
        Debug.Log("Rush, Damage : " + Atk);
        rushAtk = 0;
    }
    protected override void Move()
    {
        Debug.Log("Run");
        rushAtk++;
    }
}
```

# 인터페이스

인터페이스란 추상 클래스와 비슷하게 상속받은 클래스가 인터페이스에 선언된 멤버를 구현하게 할 때 사용하는 키워드이다. 추상 클래스와 다르게 다중상속이 가능하다.

## 인터페이스 특징

- 메소드, 프로퍼티, 인덱서, 이벤트만 선언할 수 있다.
- 추상 클래스 처럼 구현부가 없다.
- 추상 클래스 처럼 인스턴스를 생성할 수 없다.
- 무조건 public으로 선언된다.
- 선언된 모든 메서드는 가상 메서드로 간주되기에 virtual, override 키워드를 사용하지 않는다.

## 인터페이스 구현 예시

인터페이스 구현 예시로는 IAttackable와 IWeapon 인터페이스를 생성한 뒤 각 클래스에서 인터페이스의 메서드를 구현하는 기능을 구현하였다.

```csharp
using UnityEditor;
using UnityEngine;

public interface IAttackable
{
    void Attack();
    void SpecialAttack();
}

public interface IWeapon
{
    void SetWeapon(string weaponName);
}

class Zombie : MonoBehaviour, IAttackable
{
    public void Attack() => Debug.Log("Bite");
    public void SpecialAttack() => Debug.Log("Infection Bite");
}

class Player : MonoBehaviour, IAttackable, IWeapon
{
    string weapon;
    public void Attack() => Debug.Log(weapon + " Attack");
    public void SpecialAttack() => Debug.Log(weapon + " Rush");
    public void SetWeapon(string weaponName) => weapon = weaponName;
}
```

# 추상 클래스와 인터페이스의 사용

- 추상 클래스는 기본적으로 클래스이며 상속, 확장하여 사용하기 때문에 공통된 필드, 메서드를 가지는 경우 사용한다.
- 인터페이스는 내부 멤버의 선언만을 제공하며 다중상속이 가능하기에 객체의 여러 동일한 사용방법과 동작을 보장해야 하는 경우 사용한다.

# 추상 클래스와 인터페이스를 공부하면서

- 알던거 나와서 너무 편하다