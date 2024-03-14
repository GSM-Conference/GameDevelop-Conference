# Abstract Class(추상 클래스)

<aside>
💡 abstract는 class 혹은 Method앞에 붙어 현재 붙어있는 class 혹은 Method가 추상인지를 나타낸다. 여기서 추상이란 현재 class의 Method에서 코드의 불완전함이 있음을 말한다. 그리고 이러한 불완전함은 abstract가 붙지않은 class에서 구현을 해주어야한다. 또한 추상클래스로 객체생성할 수 있다.

</aside>

```csharp
abstract class AbstractClass 
{
	public abstract testMethod();
}

class NonAbstractClass : TestClass 
{
	public override void testMethod()
	{
		Debug.Log("구현");
	}
} 
```

# Interface

<aside>
💡 Interface는 구성요소들의 구현부가 존재하지 않고 선언부로만 되어있는 클래스이다. 따라서 Interface는 구현을 위한 클래스라고 할 수 있다. 그리고 Interface는 다중상속을 가능하게 해준다. 하지만  Interface로는 객체 생성을 할 수 없다. 또한 Interface를 구현할 때에는 명시적 구현과 암시적 구현으로 나눠지는데 암시적 구현은 그냥 일반적으로 Class에서 구현하는것이고 명시적 구현은 구할때 Method의 이름 앞에 Interface의 이름을 넣는다. 이러한 명시적 구현의 특징은 Class내부의 멤버와 이름이 같아도 충돌 하지 않는다

</aside>

```csharp
**interface IInterface1
{
    void test1();
}

interface IInterface2
{
    void test2();

}

class ImplementClass : IInterface1, IInterface2
{
    public void test1()
    {
        Debug.Log("암시적 구현!");
    }

    void IInterface2.test2()
    {
        Debug.Log("명시적 구현!");
    }

    void Start()
    {
        test1();

        IInterface2 interface2 = new ImplementClass();
        interface2.test2();
    }
}**
```