# C# 고급문법 **제네릭**이란?

## ***의미***
> **제네릭**이란 클래스, 인터페이스, 메소드를 개별적으로 다시 작성하지 않아도 여러 자료형으로 사용할 수 있도록 해주는 문법이다. 

## ***사용법***
> 클래스, 인터페이스, 메소드에 <T<T>>와 같은 타입 파라미터(Type parameter)를 붙여 구현한다.

## **NET 제네릭** 클래스들
> System.Collections.Generic 네임스페이스는 모두 제네릭 타입이다.
+ (예시) **List<T<T>>, Dictionary<T<T>>, LinkedList<T<T>>**

## **제네릭 타입 제약**

    // T는 Value 타입
    class MyClass<T> where T : struct 

    // T는 Reference 타입
    class MyClass<T> where T : class
 
    // T는 디폴트 생성자를 가져야 함
    class MyClass<T> where T : new() 

    // T는 MyBase의 파생클래스이어야 함
    class MyClass<T> where T : MyBase

    // T는 IComparable 인터페이스를 가져야 함
    class MyClass<T> where T : IComparable

    // 좀 더 복잡한 제약들
    class EmployeeList<T> where T : Employee,
       IEmployee, IComparable<T>, new()
    {
    }

    // 복수 타입 파라미터 제약
    class MyClass<T, U> 
        where T : class 
        where U : struct
    {
    }

## **장점**
> 클래스나 메소드 내부에서 사용되는 **객체의 타입 안정성**을 높일 수 있습니다

> 반환값에 대한 **타입 변환** 및 **타입 검사**에 들어가는 노력을 줄일 수 있습니다.

## **사용 예시**
>유니티에서 컴포넌트를 넣어줄때 GetComponent<RigidBody<RigidBody>>() 

>Dictionary<key, value>, List<T<T>>