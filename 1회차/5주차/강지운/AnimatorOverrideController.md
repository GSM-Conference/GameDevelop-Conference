# 애니메이터 오버라이드 컨트롤러

## 역할

AnimatorOverrideController는 로직이 구현되어있는 AnimatorController를 참조해 사용되는 애니메이션을 다른 애니메이션에 대응시켜 동일한 로직의 여러가지 AnimatorController를 빠르게 만들수있다.

# 구조

**AnimatorOverrideController** 는 **RuntimeAnimatorController** 클래스를 상속한다.

## RuntimeAnimatorController

### 역할

- **Animator** 컴포넌트의 runTimeAnimatorController로서 참조되어 애니메이션 로직을 제공한다.
- **AnimatorOverrideController** 와 **AnimatorController** 의 부모클래스이다.

### 구성요소

- string name : 인스펙터상의 이름을 반환한다. (없으면 “”)
- AnimationClip[] animationClips : 컨트롤러에 포함된 애니메이션클립들을 반환한다.

## AnimatorController

### 역할

**Animator** 에서쓰일 로직을 구현하는 클래스이다.

### 특징

- 스크립트에서 AnimationClip을 바꿀수없다.

## AnimatorOverrideController

### 역할

runTimeAnimatorController 를 참조하여 사용되는 AnimationClip을 다른변수로 대체할수있다.

### 특징

- 로직구현을 **AnimatorController**에 의존한다.
- 오버라이드할 runTimeAnimatorController가 필수적이다.

### 구성요소

- int overridesCount{ get; } : 오버라이드한 클립의 개수를 반환한다.
- AnimationClip[] animationClips{ get; } : 오버라이드한 애니메이션들(오버라이드컨트롤러에 들어간)을 반환
- this[] : 이 클래스는 string으로 인덱싱이 가능하다, State의 이름으로 인덱싱하면 오버라이딩하는데 쓰인 AnimationClip을 반환한다.