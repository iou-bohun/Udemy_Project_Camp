# 물체 충돌처리 
----------------
사용 이유 
  1. 물체간 충돌을 처리할 때 사용한다.

## CollisionEnter 일반 충돌
  * CollisionEnter 의 경우 일반적인 콜라이더를 가진 두 게임 오브젝트가 충돌할 때 실행한다.
  * 충돌한 두 콜라이더는 서로 통과하지 않고 밀어낸다.
    * ```C# OnCollisionEnter(Collision collision)```: 충돌한 순간
    * ```C# OnCollisionStay(Collision collision)```: 충돌하는 동안 
    * ```C# OnCollisionExit(Collision collision)```: 충돌했다가 분리되는 순간
## TriggerEnter 트리거 충돌 
  * 충돌한 두 게임 오브젝트의 콜라이더 중 최소 하나가 트리거 콜라이더라면 자동으로 실행한다.
  * 충돌한 두 게임 오브젝트가 서로 통과한다.
    * ```C# OnTriggerEnter(Collision collision)```: 충돌한 순간
    * ```C# OnTreiggerStay(Collision collision)```: 충돌하는 순간
    * ```C# OnTriggerExit(Collision collision)```: 충돌했다가 분리되는 순간
