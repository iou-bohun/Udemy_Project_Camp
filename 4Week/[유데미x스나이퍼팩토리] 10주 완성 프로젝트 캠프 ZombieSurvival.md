# 좀비 서바이벌
이미지
------------
### 인터페이스
  * 인터페이스란 외부와 통신하는 공개 통로이며, 통로의 규격이다.
### 코루틴
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
    
