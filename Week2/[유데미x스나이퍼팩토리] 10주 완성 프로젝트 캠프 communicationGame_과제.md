# CommunicationGame DevLog

# 유니티짱 미연시 UGUI로 바꿔보기

기존 GUYStyle을 이용해 작업했던것을 UGUI로 바꾸기!

------------
# UGUI
  UGUI는 Unity에서 사용하는 GUI시스템을 의미한다. 

#구현 과정

  <img width="378" alt="image" src="https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/36341423-06e8-4aba-839a-df9c142a76c1">
  
  먼저 button 오브젝트르 생성해주었다.

  버튼의 스프라이트를 변경하기 위해 Button 오브젝트의 Image 인스팩터에서 바로 변경을 하려고 했으나 이미지의 유형이 맞지 않아 변경을 할 수 없었다. 
  
  <img width="320" alt="image" src="https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/19326a74-3118-47f8-814e-7d75e513b4b1">
  
  따라서 기존 default로 되어있던 teture Type를 Sprite(2D and UI)로 변경해 주었다. 

  버튼은 일반이미지 / 호버링 했을때의 이미지 / 클릭시의 이미지를 다르게 해주었다. 
  
  버튼 인스펙터의 Button 에서 Transition속성을 이용해 쉽게 처리할 수 있었다. 
  
  <img width="304" alt="image" src="https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/a68d3c5e-fc02-4017-84de-7091441c727d">
  

  기존에 유니티짱에 포함되어있던 가위바위보 로직을 사용하기 위해 Janken스크립트에 Button 을 퍼블릭으로 선언해 주었다. 
  
  <img width="145" alt="image" src="https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/19449373-06c6-4978-8186-2f848f0fec92">![Uploading image.png…]()

  하지만 이 과정에서 문제가 생겼다. 
  
  <img width="313" alt="image" src="https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/9e7de049-2959-413d-a599-482739276b20">

  이와같이 Button 오브젝트가 들어가지 않고, Button스크립트가 할단된 것이다. 
  
  문제를 해결하기 위해 함께 캠프를 진행하고 있는 다른분에게 문제에 애해서 이야기 해보며 해결을 하였다. 
  
  스크립트의 이름이 Button 이기에 문제가 생긴것이었다. 
  
  스크립트를 삭제하니 Button이 정상적으로 할당되는것을 확인 할 수 있었다. 
  

  <img width="308" alt="image" src="https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/79b12e95-d99b-4535-9e9a-bc65f5ce987a">

  ```public void OnClickJANEKN()```
  ```public void OnClickGoo()```
  ```public void OnClickCHOKI()```
  ```public void OnClickPA```
  
  위 함수를 이용해 버튼제어를 해주었다. 
  
  각각 버튼을 눌렀을때 작동하는 로직을 포함하는 함수들이다. 
  
  <img width="312" alt="image" src="https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/a90ec556-c42a-41e0-ac70-bbfdcaad329e">

  위 함수들을 알맞은 버튼에 할당해 가위바위보 로직을 완성하였다. 

  ![가위바위보UGUI](https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/7664036b-2342-44b8-a2fd-38175bdecd85)

  -----------------------------------------
  <br/><br/><br/>
  #프로젝트캠프 #프로젝트캠프후기 #유데미 #udemy #스나이퍼팩토리 #웅진씽크빅 #인사이드아웃 #IT개발캠프 #개발자부트캠프 #unity #유니티 #게임개발 #메타버스
  
  

