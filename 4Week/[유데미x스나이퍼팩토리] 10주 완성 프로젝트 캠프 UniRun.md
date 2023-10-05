# 유니 런
![UniRun](https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/30814281-eff1-477f-bfe2-e2fc90e2f90a)

### 새로 배운 내용
 # SINGLETON
## 싱글톤 패턴이란?
  * 하나의 인스턴스만 생성하여 사용하는 디자인 패턴
#### 사용 이유
  * 메모리 낭비 방지
  * 여러 스크립트가 사용해야하는 변수나 기능이 있다면 접근의 편의 제공
  * 씬이 변경되어도 저장되는 데이터를 활용하기 위해
## 코드
 * 싱글톤의 간단한 예제 코드이다.
 ``` c#
public class GameManager : MonoBehaviour
{
    private static GameManager instance = null; 
    public static GameManager Instance 
    {
        get
        {
            if (null == instance)
                return null;
            else
                return instance;
        }
    }

    private void Awake()
    {
        if (instance == null)
            instance = this;
        else if(instance != this)
        {
            Destroy(this.gameObject);
        }
        DontDestroyOnLoad(gameObject);
    }

}
```
## 사용에제
 * 이 게임에서 GameManager 스크립트에 사용되었다.
 * 게임 캐랙터가 사망했을 때 게임 오버를 실행하는 메소드를 구현하는데 사용(게임오버UI를 로드하는데 사용됨)
 * ``` c#
    private void Die() {
     // 사망 처리
     animator.SetTrigger("Die");
     playerAudio.clip = deathClip;
     playerAudio.Play();
     playerRigidbody.velocity = Vector2.zero;
     isDead = true;
     GameManager.instance.OnPlayerDead();
   }
   ```
   GamemaManager.Instance.OnplayerDead()와 같이 사용.

   
----------
본 후기는 유데미-스나이퍼팩토리 10주 완성 프로젝트캠프 학습 일지 후기로 작성되었습니다.

#프로젝트캠프 #프로젝트캠프후기 #유데미 #udemy #스나이퍼팩토리 #웅진씽크빅 #인사이드아웃 #IT개발캠프 #개발자부트캠프 #unity #유니티 #게임개발 #메타버스
