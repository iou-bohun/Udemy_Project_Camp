# Keep(현제 만족하는 부분)
  타이머 기능
  개별 탕후루의 Prefab화 
  탕후루의 스택기능 

# Problem
  준비 완료된 과일의 수에 따라서 랜덤으로 과일을 선택하는 기능
  * 현제 과일을 랜덤으로 선택하는 기능 구현 되어있지만 과일의 보관 수가 0이 되더라도 그 과일을 선택하게 된다.

# Try
  준비 완료된 과일들을 Dictionary형태로 저장을 하고있는데 이 부분에서 문제가 발생하고있는거 같다. 이 부분의 수정이 필요하다고 판단된다. 

### 생각하고있는 문제 코드 부분 
``` c#
public void SelectRandomFruit()
{
    foreach(var fruit in fruitCounts.Keys )
    {
        if (fruitCounts[fruit] > 0)
        {
            avaliableFruits.Add(fruit);
        }
    }
    if(avaliableFruits.Count > 0)
    {
        int randomIndex = Random.Range(0, avaliableFruits.Count);
        selectedFruit = avaliableFruits[randomIndex];
        fruitCounts[selectedFruit]--;
        Debug.Log(selectedFruit + "남은 개수 : " + fruitCounts[selectedFruit]);
    }
    else
    {
        Debug.Log("과일 없음");
    }
}
```

### 수정 내용
  SelectRandomFruit()의 첫 줄에 avaliableFruits.Clear()부분을 추가해 해결해주었다. 

--------------
#프로젝트캠프 #프로젝트캠프후기 #유데미 #udemy #스나이퍼팩토리 #웅진씽크빅 #인사이드아웃 #IT개발캠프 #개발자부트캠프 #unity #유니티 #게임개발 #메타버스 
