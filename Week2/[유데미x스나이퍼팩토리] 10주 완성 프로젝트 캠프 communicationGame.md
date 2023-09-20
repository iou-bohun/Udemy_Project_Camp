# 유니티짱을 이용한 미연시 

<img width="459" alt="스크린샷 2023-09-20 211010" src="https://github.com/iou-bohun/group6-Linear-Regression-Calculator/assets/56661597/310ac803-9ed5-44a1-a0a6-c9c6437da699">

------------
## 구현 내용
* 마우스를 이용한 카메라 제어
  1. [카메라_이동](#카메라_이동)
  2. [카메라 회전](#카메라_회전)
  3. [카메라 줌](#카메라_줌)
  4. [카메라_초기화](#카메라_초기화)
    

* 소리 출력
  1. [특정 조건에서의 음성 출력](#특정_조건에서의_음성_출력)

* 터치 인식
  1. [RayCast를 이용한 터치](#RayCast를_이용한_터치)

 * OnGui 사용
   1. [묵찌빠_게임](#묵찌빠_게임)
-------------
## 구현 과정
### 카메라_이동 
- 사용 함수
   GetMouseButton(n) // 마우스 입력처리
   
   n 0인경우 = 마우스 왼쪽 클릭
   
   n 1인경우 = 마우스 오른쪽 클릭
   
   n 2인경우 = 마우스 휠 클릭

  ``` c#
     if (Input.GetMouseButton(0)) 
     {
         transform.Translate(
             Input.GetAxis("Mouse X") / 10,
             Input.GetAxis("Mouse Y") / 10, 0);
     }
   }```

   
### 카메라_회전
```c#
 if (Input.GetMouseButton(1)) 
     {
         parent.transform.Rotate(
              -Input.GetAxis("Mouse Y") * 7,
              Input.GetAxis("Mouse X") * 7, 0);
     }
```

회전의 경우 회전의 기준점을 parent오브젝트로 해주어 자연스러운 회전을 구현하였다. 

<img width="75" alt="image" src="https://github.com/iou-bohun/group6-Linear-Regression-Calculator/assets/56661597/f6ca4f95-6698-4c6b-b536-dd198468b9e0">

### 카메라_줌
```C#
if (Input.GetAxis("Mouse ScrollWheel") != 0)
     {
         Camera.main.fieldOfView += -(20 * Input.GetAxis("Mouse ScrollWheel"));

         if (Camera.main.fieldOfView < 10)
             Camera.main.fieldOfView = 10;
         else if(Camera.main.fieldOfView>100)
             Camera.main.fieldOfView = 100;  
     }
```

- 이슈

  마우스 줌 인의 경우 플레이어에 일정 이상으로 가까워질 경우 상하좌우가 반젼되는 경우가 생겼다.
  그 문제를 해결하기 위해 줌인 아웃의 최대 최소값을 정해주었다.
  
  ```c#
  if (Camera.main.fieldOfView < 10)
             Camera.main.fieldOfView = 10;
         else if(Camera.main.fieldOfView>100)
             Camera.main.fieldOfView = 100;
  ```
  
### 카메라_초기화
```c#

     if (Input.GetMouseButton(2))
     {
         transform.position = defPosition;
         parent.transform.rotation = defRotation;
         Camera.main.fieldOfView = defZoom;
     }
```
-----------

### 특정_조건에서의_음성_출력
- AudioSource, AudioClip
  AudioSouce는 씬에서 오디오 클립을 재생하는데 사용된다.
  AudioClip은 재생될 사운드 클립에 대한 레퍼런스다.

  <img width="270" alt="image" src="https://github.com/iou-bohun/group6-Linear-Regression-Calculator/assets/56661597/c7086b03-e866-4c19-a871-66ce2244f15e">
  인스펙터 창에서의 AudioSouce와 AudioClip.
- 사용 함수
  PlayOnShot(AudioClip)
  
---------------

### RayCast를_이용한_터치
- 사용 함수
  Physics.RayCast(Ray,RayCastHit/레이가 반환하는 오브젝트/, 최대거리)
  ```c#
   Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
   RaycastHit hit;
  ```
  Ray의 경우 메인 카메라에서 발사되는 Ray를 이용하였다. Camera.main.ScreenPointToRay()
  Input.mousePosition을 통해 마우스 포지션으로 Ray를 발사하도록 하였다. 

  ```c#
   if(Physics.Raycast(ray, out hit, 100))
   {
     GameObject hitObj = hit.collider.gameObject;
  ```
  Ray가 오브젝트를 만나는 경우 out hit으로 반환하게 된다.
  이렇게 얻은 오브제트를 이용해 제어가 가능해진다.

---------------
  
### 묵찌빠_게임
```c#
tableResult[GOO, GOO] = DRAW;
tableResult[GOO, CHOKI] = WIN;
tableResult[GOO, PAR] = LOOSE;
tableResult[CHOKI, GOO] = LOOSE;
tableResult[CHOKI, CHOKI] = DRAW;
tableResult[CHOKI, PAR] = WIN;
tableResult[PAR, GOO] = WIN;
tableResult[PAR, CHOKI] = LOOSE;
tableResult[PAR, PAR] = DRAW;
```
위와 같이 가위바위보의 승무패 에 대한 2차원 테이블을 먼저 생성해준다. 

```c#
 unityHand = Random.Range(GOO, PAR + 1);
```
게임이 시작된 경우 유니티짱의 묵 찌 빠 를 랜덤으로 정해주고 
```c#
if (GUI.Button(rtBtnGoo, " 묵", guiBtnGoo))
{
    myHand = GOO;
    modeJanken++;
}
if (GUI.Button(rtBtnChoki, " 찌", guiBtnChoki))
{
    myHand = CHOKI;
    modeJanken++;
}
if (GUI.Button(rtBtnPar,"빠",guiBtnPar))
{
    myHand = PAR;
    modeJanken++;
}
```
내가 GUI조작을 통해 선택한 묵 찌 빠 를 myHand에 할당해준다. 
```c#
flagResult = tableResult[unityHand, myHand];
```
유니티짱과 내 선택에 해당한는 결과 태이블 값을 flagResult에 할당해 묵찌빠 게임을 구현하였다. 

