# 좀비 서바이벌
![좀비게임](https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/5a7fe98d-2477-42d7-a30c-9c534b7428b3)

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
  클릭을 할 경우 CleanA(), CleanB()함수가 모두 동시에 실행된다.

## Navigation System
* 한 위치에서 다른 위치로의 경로를 계산하고 실시간으로 장애물을 피하며 이동하는 인공지능을 만드는 네이게이션 시스템
  * NavMesh : 에이전트가 걸어 다닐 수 있는 표면
  * NavMesh Agent : 네브메시 위에서 경로를 계산하고 이용하는 캐릭터 또는 컴포넌트
  * NavMesh Obstale : 에이전트의 경로를 막는 장애물
  * Off Mesh Link : 끊어진 네브메시 영역 사이를 잇는 연결지점(뛰어넘을 수 있는 울타리나 타고 올라갈수 있는 담벼락을 구현하는데 사용)

  ---------------
  본 후기는 유데미-스나이퍼팩토리 10주 완성 프로젝트캠프 학습 일지 후기로 작성되었습니다.

#프로젝트캠프 #프로젝트캠프후기 #유데미 #udemy #스나이퍼팩토리 #웅진씽크빅 #인사이드아웃 #IT개발캠프 #개발자부트캠프 #unity #유니티 #게임개발 #메타버스
  
