# 유니티 생명주기란?

유니티 생명주기란 이벤트 함수의 실행 순서를 뜻한다

## 첫 씬 로드

---

Awake()

프리펩이 인스턴스화 된 직후에 호출된다

*오브젝트가 비활성 상태라면 활성화 될때까지 호출되지 않는다

*자주 애용

OnEnable()

오브젝트 활성화 직후 호출된다

## 에디터

---

Reset()

오브젝트에 처음 연결하거 Reset커맨드를 사용할 때

스크립트의 프로퍼티(property)를 초기화할때 호출된다

OnValidate()

스크립트의 프로퍼티가 설정될 때마다 호출된다

## 첫프레임 업데이트 전

---

Start()

스크립트 인스턴스가 활성화된 경우에만 첫 번째 프레임 업데이트 전에 호출된다

## 업데이트 순

---

FixedUpdate()

일정한 속도로 업데이트 가끔 프레임보다 여러번 호출된다

*자주 애용

Update()

프레임당 한번씩 호출된다

LateUpdate()

Update()가 끝난 후 프레임당 한번씩 호출된다

OnTrigger,OnCollision

트리거나 콜리전이 일어날때 호출된

## 삭제

---

OnDisable()

오브젝트 비활성화시 호출된다

OnDestroy()

오브젝트 생존기간의 마지막 프레임이 업데이트 된 후 호출된다

OnApplicationQuit()

응용프로그램 종료 전에 모든 오브젝트에서 호출된다.

`Initialization & Editor` Reset()→Awake()→OnEnable()→Start()→

`Physics & GameLogic` FixedUpdate()→OnTrigger,OnCollision→Update()→LateUpdate()→

`Decommissioning` OnDisable()→OnDestroy()→OnApplication()