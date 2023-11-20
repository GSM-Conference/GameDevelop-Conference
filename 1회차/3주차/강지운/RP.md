## 렌더링 파이프라인의 정의

렌더링 파이프라인은 씬에있는 정보들을 받아와 2D 그래픽으로 렌더링하는 과정이다.

## 렌더링 파이프라인의 작업

대체로 3가지 작업을 담당한다.

### 컬링

렌더링할 오브젝트와 렌더링하지않을 오브젝트를 구별하는작업,

화면밖의 오브젝트, 가려진 오브젝트등을 구별한뒤 계산에서 제외한다.

아래는 유니티 게임맵에서 카메라에 보이는부분만 렌더링한 모습이다.

![https://docs.unity3d.com/kr/current/uploads/Main/OcclusionFrustumCulling.jpg](https://docs.unity3d.com/kr/current/uploads/Main/OcclusionFrustumCulling.jpg)

### 렌더링

3D 공간상의 데이터를 2D그래픽으로 변환하는 단계

### 포스트 프로세싱

후처리 단계, 이미 렌더링된 결과물에 원하는 효과를 더함으로서 게임의 분위기를 연출하거나 렌더링 품질을 높이는등 여러가지 방법으로 활용할수있다.

![https://docs.unity3d.com/kr/2021.3/uploads/Main/PostProcessing-1.jpg](https://docs.unity3d.com/kr/2021.3/uploads/Main/PostProcessing-1.jpg)

# URP와 HDRP

URP와 HDRP는 유니티의 빌트인 SRP로서 지원되며,

각각 다른 용도에따라 사용된다.

## URP

유니티에 예전부터 존재하던 LWRP를계승한 렌더링 파이프라인으로, 최적화를 통해 여러가지 플랫폼에서 쉽고 간편하게 고사양 그래픽을 구현할 수 있다.

### 특징

- 쉬운 사용난이도
- 높은 범용성
- 커스텀기능을 에셋으로 해결할수있다.

![https://docs.unity3d.com/kr/2021.3/uploads/Main/urp-example.png](https://docs.unity3d.com/kr/2021.3/uploads/Main/urp-example.png)

## HDRP

AAA게임같은 고사양 게임의 그래픽을 구현하기위한 렌더링 파이프라인으로, 호환가능한 GPU를 필요로한다.

### 특징

- 높은 사용난이도
- 고사양 그래픽 구현가능
- 고사양 그래픽으로 인한 요구사양 상승

![https://docs.unity3d.com/kr/2021.3/uploads/Main/srp-hdr-example.png](https://docs.unity3d.com/kr/2021.3/uploads/Main/srp-hdr-example.png)

## URP와 HDRP의 차이점

- 요구 성능과 그래픽 수준에 따라 용도가 달라진다.
- URP가 커스텀기능을 비교적 많이 지원한다.