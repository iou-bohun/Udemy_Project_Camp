# 오브젝트 풀링 
  사용 이유 
  1. Unity의 오브젝트를 새롭게 생성하고 파괴하는 과정에서 프레임 드랍이 발생한다.
  2. 메모리 파편화 현상이 발생한다.

## 오브젝트 풀링?
  * 오브젝트 풀링이란
    - 먼저 오브젝트를 담아둘 오브젝트 풀을 만들고. 이 풀에서 active되어있지 않은 오브젝트를 active해 사용하고, 만약 모든 오브젝트들이 활성화된 상태라면 오브젝트 풀에 새로 오브젝트를 만드는 것을 의미한다.

-----------------
## 구현 과정
  * 생성할 오브젝트 프리펩을 담고있는 GameObject 배열 생성
  * 오브젝트 프리펩에 1대1 대응되는 풀 List 생성
  * 리스트 초기화
  * 풀 안의 오브젝트의 활성상태 확인
    * 풀 안의 오브젝트중 active상태가 false인 오브젝트가 있는 경우 active
    * 풀 안의 오브젝트가 모두 사용중이라면 > 풀에 새로 오브젝트 생성
-----------------
## 코드 
  ```c#
public GameObject[] prefabs;
List<GameObject>[] pools;
```

배열과 리스트 생성

```c#
private void Awake()
{
    pools = new List<GameObject>[prefabs.Length];

    for(int index = 0; index <  pools.Length; index++)
    {
        pools[index] = new List<GameObject> ();
    }
}
```

리스트 초기화 

```c#
 GameObject select = null;
 foreach(GameObject item in pools[index])
 {
     if(!item.activeSelf)
     {
         select = item;
         select.SetActive(true);
         break;
     }
 }
```

foreach문을 통해 list안에 비활성화된 오브젝트가 있는지 찾는다.
비활성화된 오브젝트가 있을 경우 SetActive(true)를 통해 활성화.

```c#
if(select == null)
{
    select = Instantiate(prefabs[index],transform);
    pools[index].Add(select);
}
return select;
```

만약 모든 오브젝트가 활성화중인 경우 새로 오브젝트를 생성하고 list에 Add해준다. 

