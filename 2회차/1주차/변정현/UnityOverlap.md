## **Overlap | 일정 범위 충돌체를 감지**

---

### 2D

| https://docs.unity3d.com/ScriptReference/Physics2D.OverlapBox.html | 충돌체가 상자 영역 내에 있는지 확인합니다. |
| --- | --- |
| https://docs.unity3d.com/ScriptReference/Physics2D.OverlapBoxAll.html | 상자 영역에 속하는 모든 충돌체 목록을 가져옵니다. |
| https://docs.unity3d.com/ScriptReference/Physics2D.OverlapBoxNonAlloc.html | 상자 영역에 속하는 모든 충돌체 개수를가져옵니다. |

### 3D

| https://docs.unity3d.com/ScriptReference/Physics2D.OverlapBox.html | 접촉한 모든 콜라이더나 내부의 박스(box)와 함께 배열을 반환합니다. |
| --- | --- |
| https://docs.unity3d.com/ScriptReference/Physics2D.OverlapBoxNonAlloc.html | 접촉한 콜라이더의 개수를 반환합니다. |
| https://docs.unity3d.com/kr/530/ScriptReference/Physics.OverlapSphere.html | 접촉한 모든 콜라이더나 내부의 구체(sphere)와 함께 배열을 반환합니다. |
| https://docs.unity3d.com/kr/530/ScriptReference/Physics.OverlapSphereNonAlloc.html | 접촉한 콜라이더의 개수를 반환합니다. |

## 사용방법

---

```csharp
Collider2D Physics2D.OverlapBox(point, size, angle);
Collider2D Physics2D.OverlapBox(point, size, angle, layerMask);
```

point : OverlapBox의 원점이 시작되는 위치

size : OverlapBox의 범위

angle : OverlapBoxd의 범위 각도

layerMask : 특정 레이더 감지

### 예시

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class OverlapTest : MonoBehaviour
{
    public Vector2 size;
    public LayerMask isLayer;
    
    void Start()
    {
        Collider2D hit = Physics2D.OverlapBox(transform.position, size, 0, isLayer);
        Debug.Log(hit.name);
    }
    
    void OnDrawGizmos()
    {
        Gizmos.color = Color.red;
        Gizmos.DrawWireCube(transform.position, size);
    }
}
```

OnDrawGizmos는  OverlapBox의 영역을 시각적으로 보여줍니다!