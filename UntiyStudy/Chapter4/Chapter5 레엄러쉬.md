# 레엄러쉬
# 1. 게임 디자인
레엄러쉬란? <br>
타워 디펜스 게임이다.
타워 디펜스 요소
* 적을 막기 위한 건물 배치
* 방어용 물체(개체)
* 몰려오는 적들

## 요구사항
3D 그리드(격자구조)로 설정
시작점과 도착점을 지정하여 적들이 이동하는 경로 설정<br>

## 플레이어 경험
전술적, 전략적 경험<br>

## 핵심 구조
'제한'된 자원을 제공해 전략적으로 타워를 배치하여 목표를 달성하도록 유도

## 핵심 게임 반복구조(loop)
적들의 공격으로부터 가능한 길게 생존하기!!
금(라이프)가 다떨어지면 다시 시작!


# Grid Snapping
기존에는 드래그를 통해 object를 이동시켰으나 이제는 grid를 기준으로 일정한 방향으로 일정한 수치만큼 이동시킬 수 있다.
=> 즉 trnasform의 수치를 일일히 조정하여 일정한 위치, 간격을 설정하지 않아도 된다!!!

드디어! 이 기능이 나왔다!!! 
Edit메뉴-Grid and Snaps
=> 인 줄 알았지만 업데이트 되서 메뉴가 없어지고 그냥 오버레이 메뉴에서 자석, 격자 아이콘으로만 찾을 수 있다.

주의 자석모양아이콘(grid snapping)은 global 좌표로 설정하고, 이동커서(w)를 활성화 시켜야지만 활성화 시킬 수 있다.
https://forum.unity.com/threads/cant-find-grid-and-snap-settings-in-edit-tab.1286897/

## 추가로 알게 된 것
가운데를 누르면 y,z,x 중 두 좌표계 화살표가 색이 변하면서 해당 차원을 기준으로 2차원으로 이동시킬 수 있다.


# 2D 좌표 시스템
타워나 적을 배치시킬때 위치 확인이 쉽도록 효율적으로 2차원을 통해 타일의 위치를 표시할 것이다. 또한 그걸 text형태로 화면에 표시할 것이다.
전통적으로 (x,y)좌표 형태 사용 
* 주의!
 그러나 실제로는 3D이므로 transform의 z,x값 사용할 예정 Scene탭좌측 상단 좌표계 주의!
저번 챕터에서 사용한
TextMeshPro asset을 통해 표시

## TextMeshPro
package manager를 통해 설치
* TextMeshPro는 다른 UI와 달리, 다른 개체와 겹칠 때 투명해질 수 있다. 
**강의에는 불투명(오역)**
* Textmeshpro-Main setting-alignment 속성을 통해 부모 객체를 기준으로 정렬가능
(하단에 있어서 가려서 잘 안 보일 수 있다.)

## z-fighting or z-butter fighting
여러 오브젝트가 동일한 z좌표을 차지하려하여 렌더러(화면에 보여주는 장치)가 혼란을 겪어
오브젝트들이 서로 번갈아 가면서 보이는 현상
- 본 수업에서는 Text와 Cube가 해당한다.
* 해결책
1. 안 겹치도록 좌표 조정
2. TextMeshPro선택-shader-Distance Field Overlay 선택
=> text가 타 object에 의해 가려지지 않도록 설정

## 좌표 텍스트 자동 변경 script
타일의 좌표에 따라 좌표 텍스트가 변경되도록 하여 개발이 유용하도록 하기 위해
* [ExcuteAlways]
기존에는 play시에만 실행, 그러나 개발 도중에도 동작해야한다.<br>
작성하는 위치는 class 바로 위에 작성하여 준다.

* Application.isPlaying
play 실행 여부를 나타내는 변수
=> play 시에서 텍스트 함수 실행 X

* using TMpro
TextMeshPro에 접근 가능하도록 설정

### 발생한 문제 해결
주의!
vscode C# extension이 업데이트 되면서 관련 unity package도 업데이트 해줘야 했다.
package manager에서 visual studio editor (code말고!)를 lock을 해제하고 최신버전으로 업데이트 했다.!!!
출처 : https://github.com/microsoft/vscode-dotnettools/issues/271
고마워요 ㅠㅠ

# 적 추가
* 적의 이동경로를 콘솔에 출력해보자!
타일의 2차원 좌표를 받아올 매개체로서  WayPoint Script를 tile에 추가(태그를 매개체로 사용 가능하다.)
* 현재는 좌표를 받아오는 매개체 역할 이지만, 추후에는 다른 역할을 하도록 script수정 예정
타일 위 적을 움직이게 하기 위해서 EnemyMover Script 작성
## List vs Array
Array와 List는 둘 다 여러 개체를 담는 형태의 자료구조를 말한다.
Array는 크기가 고정되어 있고 List는 가변적이다.
그 대신 Array는 속도가 빠르고, List는 길이에 따라 차이가 있다.

* Code
List<type>() 로 List를 표현할 수 있다.
type은 List내부에 들어가는 데이터의 자료형을 말한다.
Ex) List<WayPoint>

### ?의문점
강의에서 enemyMover script 의 inspecter [Serialized] 필드에 tile object를 드래그 하니까 script 컴포넌트가 list의 속성으로 들어갔다.
좌표 값을 받아오기 위해서 코드에서는 wayPoint.name을 통해 불러왔는데 잘 이해가 되지 않았다.
wayPoint 코드에는 name이라는 변수가 없었는데? script는 기본적으로 장착된 object의 이름을 가지고 있는건가?  그럼 script의 저 type은 머지???
아니면 serialized 에 일부로 tile object전체를 가져온건가???



# 적의 위치를 매초 지정한 경로로 따라 움직이자!
* 기존 Invoke 사용하여 함수 지연 , 단점 : 문자열 참조
* 변경 StartCoroutine 사용, 메소드 참조 가능

## Coroutine
Coroutine은 실행을 중단하고 다른 작업을 진행하게 해주는 메소드이다.
StartCoroutine(function f)을 통해 실행한다.
이때 f는 Enumerator를 반환하고 yield return 문이 작성된 메소드여야 한다.
* yield return new WaitForsecond(1f)를 통해 1초 동안 다른 작업을 하고 돌아오게 한다.
* Enumerator란 컴퓨터가 셀 수 있는 가상의 객체이다.(?)
* yield의 의미는 양보하다. 즉, 현재 함수에서 다른 함수로 양보한다는 의미가 담긴 것 같다.
### Invoke vs Coroutine
Invoke의 경우 단순히 시간을 지연하기 때문에 지연되는 동안 해당 스크립트는 다른 작업을 하지 않는다(?)
Coroutine의 특징은 다른 함수로 진행하다가 다시 Coroutine함수로 돌아올 수 있다.
* +a  
Invoke의 경우 대상 gameobject가 비활성화 되도 작동한다.
Coroutine의 경우 비활성화 되면 작동안한다.

# 에셋 임포트
## 중첩 프리팹 수정
타 에셋의 프리팹을 가져와 기존에 프리팹의 자식으로 추가한 경우
해당 에셋또한 프리팹이기에 기존 프리팹 화면에서는 수정할 수가 없다. 
프리팹인 상태로 수정사항 반영을 위해서는 본 에셋 프리팹에서 수정해야 한다. 그러나 이 경우 원 프리팹이 변경된다.
그래서 우클릭-프리팹-unpack을 통해서 해당 에셋이 프리팹이 아니게 만들어서 수정한다.
## 변형 프리팹 (prepab variant)
부모 프리팹의 특성을 유지하면서 일부 속성만 변경시킨 자식 프리팹.
따라서, 부모 프리팹의 변경사항 발생시 변형 프리팹도 적용받는다. <br>
<b>단! 이 때 변경된 일부 속성의 경우 부모에서 변경이 일어나도 적용되지 않는다.</b>
* 자식 프리팹의 변경사항 확인 방법
자식 프리팹의 인스펙터 창을 보면 좌측에 얇게 파란색으로 표시가 되어 있다 

* 부모 프리팹 확인 방법
Inspecter 창에서 prepab창을 통해 확인

# 적의 이동을 부드럽게 하기
현재는 매초 지정된 좌표로 순간이동하고 있다.<br>
우리는 부드럽게 이동하길 원한다.<br>
그러나 좌표와 좌표 사이에 어떻게 이동할지 모른다.
선형보간법을 통해서 좌표를 추정한다. 
유니티에서는 선형보간법 함수 Vector3.LERP()를 제공한다.<br>
* Vector3.LERP(시작좌표, 도착좌표, travelpercent)<br>
travelpercent=> 이동 정도를 나타내는 0~1사이의 값<br>
1=도착, 0.5=중간, 0=시작
* transform.Lookat(vector3)
object가 vector3 좌표를 바라보게 한다.
강의에서는 각 이동할 위치를 바라보게 한다.
* Serialized Field의 범위 지정
[Serialized] [range(min,max)] speed;

## 선형보간법이란?
단순히 말해서 점과 점 사이를 잇는 선을 긋는 방법이다.<br>
(1,4) (2,7) => y=3x+1

# 타워 배치
## 타워 배치를 위한 User Input 받기
타워 배치를 위해서 유저가 타일에 클릭햇을 때 event를 받는 방법에 대해 알아보자
1. 클릭 범위를 인지하기 위해서 colider를 설정
클릭을 인식하는 함수 onMouse가 Colider가 있는 개체에서만 동작하기 때문이다.
2. 클릭시 Instaniate(?) 함수를 이용해서 타워 인스턴스를 생성

## 타워 방향 조절을 위한 script

이전 적 방향조절과 동일하게 Lookat(transform)함수를 사용
Findbyobjecttype을 통해서 적을 찾고 대상의 transform을 lookat함수에 적용

## 무기 발사를 위한 particle system
particle이 카메라 방향으로 향하지 않도록 Renderer-Alignment =velocity로 설정
shape를 꺼서 일직선으로 나가도록 설정 등등.....
충돌을 위한 coliision 설정을 해주고..


## 무기 적중 시 event 관련 script 작성 EnemyHealth
OnCollisionParticle 메소드를 사용하여 충돌 시 Hitpoint를 낮추고 0이 도달하면 파괴된다.
* 단 이 때 particleSystem에서 collision-collision message send를 체크해야지만 onCollisionParticle 메소드가 호출된다.

# 기존 좌표 텍스트를 켜고 끌 수 있도록 디버깅 설정하기
이를 위해서는 기존 script들의 객체에 접근할 필요가 있다.
public으로 지정하는 방법을 사용하는 것은 모든 스크립트에서 접근할 수 있기에 위험하다<br>
보다 안전한 방법
1. 변수 대신 메소드를 통해 값을 얻게 한다.(직접 수정 방지)
2. property라는 개념을 사용한다.
property 또한 1번과 유사하지만, 함수는 아니고 변수처럼 접근하되, 내부는 get, set이라고 사전에 정의된 함수를 사용하는 것이 다르다.
그리고 property의 이름은 대문자로 시작하여야 한다.
1번 2번의 차이를 잘 모르겠지만, 1번을 간단하게 하는 것이 2번이라고 생각한다.



# 경로 찾기
적을 play 동안 인스턴스화 하여 생성할 것이므로 자동으로 경로를 찾아야 한다.<br>
경로의 기준은 뭘까? 기존의 Isplacable은 타워를 배치한 자리와 헷갈리므로 다른 기준이 필요<br>
=>  Tag를 통해 구분하자
FindGameObjectWithTag를 통해 Path를 불러오자

## 오류
FindGameObjectsWithTag위계 그대로 불러오지 않아서 막 지멋대로 돌아다니고 난리가 났다.
그래서 일단 리팩토링 파트로 가서 제대로 된 코드로 수정함

## ObjectPool
계속 Object를 생성하고 지우는 것은 컴퓨터에 부담을 심하게 준다.<br>
그래서 Object를 Destory하는 것이 아니라 비활성화 하여 다시 사용하는 방법이 필요
이 때 Object들을 보관하는 가상의 장소를 ObjectPool이라고 한다.

* OnEnable
awake, start , update와 같이 Unity event 발생 구조 중 하나 인다.
object가 활성화 될 때 호출되는 메소드이다.

* for vs foreach
```
for(int i=0; i<10; i++){
    //함수...
}
```
```
        foreach(Transform child in parent.transform){
            WayPoint wayPoint = child.GetComponent<WayPoint>();
            if(wayPoint != null){
                path.Add(wayPoint);
            }
        }
```
foreach는 배열/리스트의 내용을 하나씩 꺼내는 역할
for은 foreach보다 세부적인 반복이 가능하다.
Ex) 1,3,5번째만 실행 


# 타워가 가까운 적 겨냥 하도록 수정
TargetLocator Script를 수정한다.
기존의 EnemyMover 대신 Enemy script(빈 스크립트)를 통해 적을 식별한다.

* Vector3.Distance(vector3, vector3) 두 벡터의 거리를 계산한다.
* 두 변수를 통해 비교하여 가장 가까운 변수를 알아낸다.
* 일종의 bubble sort, selection sort와 유사해 보인다.(?) 어쨋든 일종의 알고리즘 같은 거 같다.

## 타워의 범위를 벗어난 적 쏘지 않기
distance와 range를 비교해서 distance가 큰 경우 particle system의 emission을 체크 해제 한다.

### ? 궁금증
왜 play나 stop은 안되지?
