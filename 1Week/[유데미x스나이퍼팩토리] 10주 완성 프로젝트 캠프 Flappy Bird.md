# Flappy Bird 실습
![image](https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/0e0f001e-fa29-4634-849a-cffb867b4f16)

출처 - https://www.forbes.com/sites/anthonykosner/2014/02/03/flappy-bird-and-the-power-of-simplicity-scaled/?sh=747c380f7339

## player 스크립트
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;

public class Player : MonoBehaviour
{
    Rigidbody rigid;

    public float jumpPower;
    public float speed;
    public int hp;

    private void Start()
    {
        rigid = GetComponent<Rigidbody>();  
    }
    private void Update()
    {
        if (Input.GetButtonDown("Jump"))
        {
            rigid.velocity = new Vector3(0, jumpPower, 0); // 플레이어의 점프 
        }
    }
    private void OnCollisionEnter(Collision collision) // 충돌 감지
    {
        if (collision.gameObject.tag == "Wall")
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name);
        }
    }
}
```

GetButtonDown("Jump") 함수를 이용해 키 입력을받는다. 
Jump 키워드의 경우   
<img width="450" alt="image" src="https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/c9f14f0a-7f7e-41d1-8e7f-52694d61ec3c">

Project Settings > input Manager > Jump 부분에 이미 정해져 있다.
Positive Button 의 값이 'space'로 이미 정해진것을 확인 할 수 있다. 

## 물체 충돌  
OnCollisionEnter(Collision collision)함수를 이용해 충돌을 감지한다. 
이 함수는 스크립트가 부착된 오브젝트와 이 외의 오브젝트와의 충돌을 감지하는데 사용된다. 
위의 경우 tag를 이용해 tag가 Wall인 물체와의 충돌만을 감지하게 하였다. 

## Scene Laod  
플레이어가 wall물체와 충돌할 경우 LoadScene을 호출해 씬을 재시작한다. 
SceneManager.GetActiveSvene().naem 을 이용해 현제 액티브된 씬의 이름을 가져온다. 
```c#
SceneManager.LoadScene("Game");
```
LoadScene의 인자값으로 씬의 이름을 직접 적어주어도 동일한 기능을 수행한다. 

### prefabs
생성된 오브젝트의 특성들과 성질을 기억하는 재사용이 가능한 오브젝트  

<img width="300" alt="image" src="https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/0157288b-e688-43bf-ba4e-dbe1980f2ec5">

## 장애물 재 소환

장애물 소환은 Spawner 오브젝트를 새로 생성해 스크립트를 추가해준다.
![image](https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/a896d87f-26b0-43ca-b745-dba61afd2d56)

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Spawner : MonoBehaviour
{
    public GameObject wallPrefab;
    public float spawntime = 1.5f;
    float term;
    public float range = 3;

    private void Start()
    {
        term = spawntime;
    }
    private void Update()
    {
        term += Time.deltaTime;
        if(term> spawntime)
        {
            Vector3 pos = transform.position;
            pos.y += Random.Range(-range, range);
            Instantiate(wallPrefab , pos, transform.rotation);
            term -=spawntime;
        }
    }
}
```
Instantiate함수를 이용해 오브젝트를 새로 생성해준다. 
Instantiate(프리펩,vector3,rotation)의 값을 인자로 가진다.


## 점수추가
<img width="326" alt="image" src="https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/4ebc883a-fecf-4ee7-93b7-ba32b347cb10">
점수를 표현해줄 TextMesh를 추가해준다.   

```c#
private void Start()
{
    rigid = GetComponent<Rigidbody>();
    textMesh = GameObject.Find(name :"Score").GetComponent<TextMesh>();
}
```
player의 스크립트에서 textMesh를 GameObject.Find를 이용해 textMesh를 찾아준다. 
```c#
public void addSocre(int s)
{
    score +=s;
    textMesh.text = "점수 : " + score;  
}
```
이를 이용해  점수를 추가해주는 addScore 함수를 만든다. 


## Try2
점프 파워 변경 로직

```c#
 public void boostJump()
 {
     if(transform.position.y <-2)
     {
         jumpPower = 7;
     }
     else
     {
         jumpPower = 5;
     }
```
플레이어의 y 값이 -2이하가 된 경우 점프 파워를 변경해준다. 

##  Try3
```c#
transform.Translate(Vector3.right * speed * Time.deltaTime);
```
플레이어가 앞으로 조금씩 이동하도록 변경해보았다.

## Try4
```c#
transform.localScale += Vector3.up*Time.deltaTime*0.1f;
```
플레이어의 x축 크기가 점점 증가하게 하였다. 
## Try5
```c#
public GameObject[] wallPrefab;
```
```c#
Instantiate(wallPrefab[randomRange],transform.position,transform.rotation);
```
<img width="350" alt="image" src="https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/6f47f4ba-2bd0-42bc-b091-c66a25ca2257">

여러 형태의 장애물 생성


<br/><br/><br/>
본 후기는 유데미-스나이퍼팩토리 10주 완성 프로젝트캠프 학습 일지 후기로 작성 되었습니다.
#프로젝트캠프 #프로젝트캠프후기 #유데미 #udemy #스나이퍼팩토리 #웅진씽크빅 #인사이드아웃 #IT개발캠프 #개발자부트캠프 #unity #유니티 #게임개발 #메타버스 
