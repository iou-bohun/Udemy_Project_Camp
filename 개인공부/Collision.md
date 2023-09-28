# 물체 충돌처리 
----------------
사용 이유 
  1. 물체간 충돌을 처리할 때 사용한다.

## CollisionEnter 일반 충돌
  * CollisionEnter 의 경우 일반적인 콜라이더를 가진 두 게임 오브젝트가 충돌할 때 실행한다.
  * 충돌한 두 콜라이더는 서로 통과하지 않고 밀어낸다.
  * = 오브젝트간 물리적 연산 실행
    * ```OnCollisionEnter(Collision collision)```: 충돌한 순간
    * ```OnCollisionStay(Collision collision)```: 충돌하는 동안 
    * ```OnCollisionExit(Collision collision)```: 충돌했다가 분리되는 순간
## TriggerEnter 트리거 충돌 
  * 충돌한 두 게임 오브젝트의 콜라이더 중 최소 하나가 트리거 콜라이더라면 자동으로 실행한다.
  * 충돌한 두 게임 오브젝트가 서로 통과한다.
  * = 오브젝트간 물리적 연산 X
    * ```OnTriggerEnter(Collision other)```: 충돌한 순간
    * ```OnTreiggerStay(Collision other)```: 충돌하는 순간
    * ```OnTriggerExit(Collision other)```: 충돌했다가 분리되는 순간

## 특정 물체와의 충돌만 필요할 때 
  * tag 를 이용한다.
      ``` OnTriggerEnter(Collider other) ```의 경우
     ``` other.tag == " 특정 물체의 태그 " ``` 와 같은 방법으로 처리할 수 있다.
    
      
