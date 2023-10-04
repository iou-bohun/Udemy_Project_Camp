# SINGLETON
## 싱글톤 패턴이란?
  * 하나의 인스턴스만 생성하여 사용하는 디자인 패턴
#### 사용 이유
  * 메모리 낭비 방지
  * 여러 스크립트가 사용해야하는 변수나 기능이 있다면 접근의 편의 제공
  * 씬이 변경되어도 저장되는 데이터를 활용하기 위해
## 코드
 ``` c#
       public class GameManager : MonoBehaviour
{
    private static GameManager Instance = null;

    private void Awake()
    {
        if (Instance == null) 
            Instance = this;
        else if(Instance != this)
        {
            Destroy(this.gameObject);
        }
        DontDestroyOnLoad(gameObject); // 씬이 넘어가도 유지
    }

}
```

