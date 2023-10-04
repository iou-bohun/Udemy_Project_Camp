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

