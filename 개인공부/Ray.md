# Ray
* 한 지점에서 뻗어나가는 무한의 선을 의미한다.
* 방향을 나타내는 direction과 레이가 나아가는 시작점인 origin을 변수로 가진다.
* 생성은 다음과 같이 이루어진다.

  ```Ray ray = new Ray(transform.posotion, transform.forward)```

## Physics.Raycast?
* bool True if the ray intersects with a collider, Ohterwise false
* 레이가 다른 콜라이더와 상호작용 하는 경우 True를, 이 외에는 false를 반환한다.
* RaycastHit을 이용해 상효작용 하는 물체의 정보를 가져올 수 있다. 
  * ## RaycastHit?
  * Structure used to get information back from a raycast.
  * rigidbody, transform, collider와 같은 정보를 활용 할 수 있게 해준다.
     ``` c#
    if(Physics.Raycast(transform.position, transform.forward,out hit, 10 ))
    {
      Debug.Log(hit.distance);
     }
    ```
   <img width="154" alt="image" src="https://github.com/iou-bohun/group6-Linear-Regression-Calculator/assets/56661597/5c419f61-dca4-430d-b19b-63447ea23d0a"><img width="113" alt="image" src="https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/8658973b-9266-4667-8739-71aaf04ba52b"> 
  이와 같이 물체간의 거리를 구할 수 있다.
* 선별적으로 콜라이더를 무시하거나 충돌하기 위해 LayerMask가 활용된다. 
