---
marp: false
---

# 유니티 렌더링 파이프라인
> ## 🤔 **렌더링 파이프라인이란?**
씬의 오브젝트를 가져와 렌더링하는 일련의 작업.

유니티는 몇 가지 서로 다른 렌더링 파이프라인을 제공한다. <br>
개발 조기단계에서 프로젝트에 적절한 파이프라인을 선택하는 것이 중요하다.

---

> ## ⚙️ **작업**
- **컬링** : 렌더링 할 필요 없는 요소를 렌더링 과정에서 제외해 부하를 줄이는 작업<br>
![](https://mblogthumb-phinf.pstatic.net/MjAxOTA1MjZfMjgx/MDAxNTU4ODY0ODUxMzkz.45LbQdjY89xQz-o8N7LziOyjDuyt2gY58b0gzG9X9k0g.ASuY8Gx-QhgsF5DZc21dClWl-zVrM1OzY1YaIIXT6F8g.JPEG.canny708/untitled_hermet.jpg?type=w800)

- **렌더링** : 3D 모델을 계산하고 2D모니터 상에 그리는 작업<br>
![](https://blog.kakaocdn.net/dn/1TlJI/btroStscQ9E/hnDd4pmLkAgeGIGrDIPk0k/img.png)

- **포스트프로세싱** : 기존에 렌더링 된 작업물에 효과를 더하는 작업<br>
![](https://www.codeproject.com/KB/GDI/antialias/antialias.png)
![](https://docs.unity3d.com/Packages/com.unity.postprocessing@2.0/manual/images/screenshot-ao.jpg)


---

> ## **✨ 지원하는 파이프라인**
### 1. **BUILT-IN**
유니티 기본으로 설정되어있는 렌더링 파이프라인이다.
커스텀 확장은 SRP보다 기능이 제한적이다.
### 2. **SRP(Scriptable Render Pipeline)**
C# 스크립트를 통해 커스터마이징 할 수 있는 렌더링 파이프라인이다.
### 3. **URP(Universal Render Pipeline)**
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcjhSY5%2FbtqVyUjFWtx%2FPIUGkL388zqX7uucD6sBf1%2Fimg.png)
(유니티에서 URP를 사용해 개발한 Boat Attack)<br>
SRP의 경량화 버전. 뛰어난 성능과 향상된 그래픽 품질을 제공한다.<br>
기본 빌트인 렌더링 파이프라인보다 유연하고 확장성이 좋고,
플랫폼에 최적화된 그래픽을 제공한다.  <br>
기능으로는 셰이더 그래프와 VFX그래프를 지원한다.

### 4. **HDRP(High Definition Render Pipeline)**
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FNuMI8%2FbtqVnX3jIUS%2FYK3CUiqidZXBAqziFUQNTK%2Fimg.jpg)
SRP의 중량화 버전. GPU의 모든 자원을 활용하고 최적화 하여 매우 사실적인 그래픽을 제공한다. <br>
컴퓨트 셰이더 기술과 업샘플링 알고리즘 등의 최신 기술을 제공한다. <br>
특징으로는 고사양 하드웨어를 바탕으로 고성능을 발휘할 수 있다. <br>
HDRP를 사용해 개발한 게임의 예로는 메탈 헬싱어가 있다.