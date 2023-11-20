

# Rect Transform

- anchor(닻)
    
    ![](./Anchor1.png)
    
    4개의 삼각형이 각각 UI의 꼭짓점을 가리키는데
    
- anchor 공식
    
    닻과 부모(팔레트)에 비례 해서 닻을 조정해서 UI크기를 맞춘다
    
    ![](https://prod-files-secure.s3.us-west-2.amazonaws.com/25999f0d-b80e-4b64-b81f-57225ccda5a7/040f4c7e-b7ea-4ae3-93f6-18199d470ea3/Untitled.png)
    
- Rect transform
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/25999f0d-b80e-4b64-b81f-57225ccda5a7/b9e913f7-79eb-45e0-95dd-9bfaf9d9a061/Untitled.png)
    

Rect transform은 일반 오브젝트와는 다르게 UI에만 있는 transform인데 UI의 위치와 크기. Anchors ,pivot(중심점)들을 사용 할 수 있다

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/25999f0d-b80e-4b64-b81f-57225ccda5a7/311777e8-d1ac-4e2a-b524-394e4675f155/Untitled.png)

*RectTransform객체를 만들어서 GetComponent해서 사용한 예

anchoredPosition : UI의 위치 

pivot : pivot의 위치

sizeDelta : UI의 크기
