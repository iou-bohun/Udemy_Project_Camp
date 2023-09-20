# 유니티짱을 이용한 미연시 

<img width="459" alt="스크린샷 2023-09-20 211010" src="https://github.com/iou-bohun/group6-Linear-Regression-Calculator/assets/56661597/310ac803-9ed5-44a1-a0a6-c9c6437da699">

------------
## 구현 내용
* 마우스를 이용한 카메라 제어
  1. [카메라_이동](#카메라_이동)
  2. [카메라 회전](#카메라_회전)
  3. [카메라 줌](#카메라_줌)

* 소리 출력
  1. [특정 조건에서의 음성 출력](#특정_조건에서의_음성_출력)

* 터치 인식
  1. [RayCast를 이용한 터치](#RayCast를_이용한_터치)

 * OnGui 사용
   1. [묵찌파_게임](#묵찌빠_게임)
-------------
## 구현 과정
#### 카메라_이동 
- 사용 함수
   GetMouseButton(n) // 마우스 입력처리
   
   n 0인경우 = 마우스 왼쪽 클릭
   
   n 1인경우 = 마우스 오른쪽 클릭
   
   n 2인경우 = 마우스 휠 클릭

- 구현 코드
  ``` c#
   void CameraMove()
   {
     if (Input.GetMouseButton(0)) 
     {
         transform.Translate(
             Input.GetAxis("Mouse X") / 10,
             Input.GetAxis("Mouse Y") / 10, 0);
     }
     if (Input.GetMouseButton(1)) 
     {
         parent.transform.Rotate(
              -Input.GetAxis("Mouse Y") * 7,
              Input.GetAxis("Mouse X") * 7, 0);
     }
     if (Input.GetAxis("Mouse ScrollWheel") != 0)
     {
         Camera.main.fieldOfView += -(20 * Input.GetAxis("Mouse ScrollWheel"));

         if (Camera.main.fieldOfView < 10)
             Camera.main.fieldOfView = 10;
         else if(Camera.main.fieldOfView>100)
             Camera.main.fieldOfView = 100;  
     }
     if (Input.GetMouseButton(2))
     {
         transform.position = defPosition;
         parent.transform.rotation = defRotation;
         Camera.main.fieldOfView = defZoom;
     }
   }
 ```
   
#### 카메라_회전
#### 카메라_줌
#### 특정_조건에서의_음성_출력
#### RayCast를_이용한_터치
#### 묵찌빠_게임
