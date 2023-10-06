# 좀비 서바이벌
이미지
------------
## 인터페이스
  * 인터페이스란 외부와 통신하는 공개 통로이며, 통로의 규격이다.
## 코루틴
  * 함수를 딜레이를 주고 실행하고자 할때 사용하였다.
  * ``` c#
     // 발사 이펙트와 소리를 재생하고 총알 궤적을 그린다
     private IEnumerator ShotEffect(Vector3 hitPosition) {
     muzzleFlashEffect.Play();
     shellEjectEffect.Play();
     gunAudioPlayer.PlayOneShot(shotClip);
     bulletLineRenderer.SetPosition(0, fireTransform.position);
     bulletLineRenderer.SetPosition(1, hitPosition);
     // 라인 렌더러를 활성화하여 총알 궤적을 그린다
     bulletLineRenderer.enabled = true;
     // 0.03초 동안 잠시 처리를 대기
     yield return new WaitForSeconds(0.03f);
     // 라인 렌더러를 비활성화하여 총알 궤적을 지운다
     bulletLineRenderer.enabled = false;
     }
    ```
    yield return new WaitForSeconds(0.03f)를 통해 그 아래의 코드가 0.03초 뒤에 실행되도록 한다.

## IK(역운동학)
 * 애니메이션은 스켈레톤의 조인트 각도를 미리 정해진 값으로 회전하여 만드는데.
 * 역 운동학 = 자식 조인트의 위치를 먼저 결저하고 부모 조인트가 거기에 맞춰서 변형된다.
 * 반대로는 FK(순 운동학)가 있다.

## Action타입
* 입력과 출력이 없는 메서드를 가리킬 수 있는 델리게이트.
* 델리게이트는 '대리자' 로 번역되며 메서드를 값으로 할당받을 수 있는 타입이다.
  ###  코드
  ```
    Action onClean;

  private void Start()
  {
      onClean += CleanA;
      onClean += CleanB;
  }
  private void Update()
  {
      if (Input.GetMouseButtonDown(0))
      {
          onClean();
      }
  }
  void CleanA()
  {
      Debug.Log("A 클린");
  }
  void CleanB()
  {
      Debug.Log("B 클린");
  }
  ```
  클릭을 할 경우 ClennA(), CleanB()함수가 모두 동시에 실행된다.
  
