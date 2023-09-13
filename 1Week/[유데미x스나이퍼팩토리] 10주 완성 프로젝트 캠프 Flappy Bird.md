### Flappy Bird 실습
![image](https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/0e0f001e-fa29-4634-849a-cffb867b4f16)

출처 - https://www.forbes.com/sites/anthonykosner/2014/02/03/flappy-bird-and-the-power-of-simplicity-scaled/?sh=747c380f7339

#### player 스크립트

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
            rigid.velocity = new Vector3(0, jumpPower, 0);
        }
    }
    private void OnCollisionEnter(Collision collision)
    {
        if (collision.gameObject.tag == "Wall")
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name);
        }
    }
}


#### prefabs
생성된 오브젝트의 특성들과 성질을 기억하는 재사용이 가능한 오브젝트  

<img width="300" alt="image" src="https://github.com/iou-bohun/Udemy_Project_Camp/assets/56661597/0157288b-e688-43bf-ba4e-dbe1980f2ec5">

본 후기는 유데미-스나이퍼팩토리 10주 완성 프로젝트캠프 학습 일지 후기로 작성 되었습니다.
#프로젝트캠프 #프로젝트캠프후기 #유데미 #udemy #스나이퍼팩토리 #웅진씽크빅 #인사이드아웃 #IT개발캠프 #개발자부트캠프 #unity #유니티 #게임개발 #메타버스 
