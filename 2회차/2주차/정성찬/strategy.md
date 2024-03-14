# 전략 패턴

## 전략 패턴이란?

전략을 쉽게 바꿀 수 있도록 해주는 디자인 패턴이다

### 전략 패턴을 사용하면 유지보수가 좋다는 장점이 있습니다

## 사용 예시

ex) switch문으로 새로운 것을 추가 해줄 때마다 case를 추가해주면서 유지보수가 좋지않은 코드

![](./Ex1.png)

ex) 전략 패턴 사용 코드

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class WeaponController : MonoBehaviour
{
    IWeapon weapon;
    public Weapon lastWeapon;
    public void Init(IWeapon weapon)
    {
        this.weapon = weapon;
    }

    private void Start()
    {
        if( weapon == null )
            gameObject.AddComponent<Default>();
    }

    private void Update()
    {
        if (Input.GetKeyDown(KeyCode.A))
        {
            weapon.Attack();
        }

        if (Input.GetKeyDown(KeyCode.D))
        {
            Destroy(lastWeapon);
            gameObject.AddComponent<Sword>();
        }
    }
}
``````


```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;


public interface IWeapon
{
    public void Attack();
}
public abstract class Weapon : MonoBehaviour
{
    public abstract void SetWeapon();
}

```
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Default : Weapon, IWeapon
{
    public void Attack()
    {
        Debug.Log("태권도 얍!얍!얍!"); //Attack의 내용을 다르게 만든다
    }
    void Start()
    {
        SetWeapon();
    }

    public override void SetWeapon()
    {
        GetComponent<WeaponController>().lastWeapon = this;
        GetComponent<WeaponController>().Init(this);
    }
}

```
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Sword : Weapon, IWeapon
{
    void Start()
    {
        SetWeapon();    
    }
    public void Attack()
    {
        Debug.Log("검도 얍!얍!얍!");   //Attack의 내용을 다르게 만든다
    }

    public override void SetWeapon()
    {
        GetComponent<WeaponController>().lastWeapon = this;
        GetComponent<WeaponController>().Init(this);
    }
}

```