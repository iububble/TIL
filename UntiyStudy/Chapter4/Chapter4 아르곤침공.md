# 주요 특징
### Camera Rail
카메라가 일정경로로 이동하게 하는 것
Cinemachine 사용

### Player movement
수평 수직으로 이동하되 실제 비행기를 운전하는 느낌처럼

### shooting
총알을 발사해서 적에게 데미지를 주도록

### Health
적에게 체력을 주어서 이것이 떨어지면 죽도록
한방에 죽지 않도록

### Score
게임의 목표 적을 죽이면 증가



# Terrain
상하 일부분의 높낮이를 조절할 수 있는 개체

3dObject-terrain으로 생성가능하다.

```question 
왜 영상에서는 좌측 하단 모서리에 x,y,z축 화살표가 생기는 내꺼는 중앙에 생길까?
```

## Inspecter
### Terrain
Set Height-> Terrain의 높이 지정
Raise or lower -> 수동으로 Terrain의 높낮이 조절

단 이 때 기본 Terrain에서 움푹 패이게 할 수는 없기에

Terrain 의 Height를 높게 하여 지평선을 만들고
해당 지평선을 깍는 식으로 설정한다.

## 추가적인 Terrain tool package manager 
설치를 통한 기능확장 가능

## Bump Map, Height Map, Normal Map\
### Bump Map이란?
2D 이미지에 들어있는 3D를 나타내기 위한 빛의 정보<br>
또는 3D비주얼의 레이어의 분류(?)


```
question
3D 비주얼의 레이어의 분류(?)가 무슨말인가....
```
### Height Map이란?
Bump Map의 하위 개념으로<br>
2D에 3D 정보를 담기위한 방법중 하나로 흑백을 이용한 고저차 표현방식이다.

### Normal Map이란?
Bump Map의 하위 개념으로<br>
2D에 3D 정보를 담기위한 방법중 하나로 RGB 컬러를 이용한 고저차 표현방식이다.


### Terrain Texture
Terrain의 질감을 표현할 수 있는 속성이다.
Inspecter>Terrain>Paint Texture> Layers에서 설정할 수 있다.

거기서 첫 레이어의 텍스쳐는 Terrian 전체에 적용
그리고 두번째 부터 레이어의 텍스쳐는 브러쉬를 통하여 Terrain에 칠해줄 수 있다.

### Tree add
Inspecter>Terrain>Paint Tree 메뉴 사용

### Timeline
* 시간대를 기준으로 실행할 수 있는 애니메이션 제작 기법이다.
* Scrit이외에 자동으로 animation을 만들수 있는 방법이다.
* 게임 안에서 애니메이션을 토대로 미리 정해진 행동을 만들어 준다.

Timeline 창에서 자물쇠 버튼을 클릭하면
타 객체를 클릭하더라도 변경되지 않고 현재 객체의 타임라인을 그대로 볼 수 있다.

## 사용법
1. [Window]-[Sequencing]-[Timeline]을 통해 창 생성
2. [window]-[animation]창 필요
3. Object를 선택한 상태에서 Timeline 창에서 Create 버튼을 통해 Director 객체 생성
4. Timeline 창에 animation 추가
5. animation 칸에 움직일 object를 할당
6. animation 칸의 붉은색 원 버튼을 눌러서 움직임을 기록한다.
7. 그리고 하얀색 타임라인 위의 선택자(?)를 클릭하여 시간을 선택

```
선택자 저걸 선택하는 것이 너무 어렵다.
애니메이션 항목 생성 후 하얀색 타임바가 고정이 되어서 움직이지 않는다. 그리고 새로운 타임바가 클릭하면 나타나는데 

문제 해결!!!!
타임라인 창의 상단 메뉴 중에서 [▷] 버튼을 클릭하면
범위로 지정해서 재생할 수 있게 되기 때문에
강의에서 처럼 단일 슬라이더로 관리가 불가능하게 된다.
toggle형태라서  꺼줘야 한다.
```

8. 해당 시간대의 오브젝트 위치를 지정한 뒤 살짝 움직여서 키 플레임을 생성한다.
* Insecter 창에서 position항목에서-우클릭-add key frame을 선택할 수 있다.


### animation 편집하기
타임라인에 animation 클릭하여 우 클릭해서 animation창에서 열기 선택
드래그를 통해 범위를 지정해서 줄였다 늘렀다 가능
frame key 추가도 가능


## Unity 새로운 Input System
### User Input Binding  유저의 입력을 받는 방법 설정

script의 Serializefield를 통해서 Inspecter에서 InputAction 개체를 설정할 수 있다.
<br>
Add up&down&left&right composite 메뉴를 통해
2D에서의 상하좌우 이동을 입력을 더하고
Inspecter에서 설정할 수 있다.

## Local Position
너무 힘들었다....
우주선의 상위 객체에 position 넣어넣고 왜 안되는지 심히 궁금했다.
이유는 모르겠으나 localposition이라 함은 자식객체에만 적용이 되는 요소인듯 하다.
localpositon이 생기려면 기준이 있어야 하는데 아마 그 기준이 부모객체의 위치가 기준인듯하다.
그래서 부모객체의 localpositon은 자기자신이니까 동일해서 아마 global postion과 같은 값이 나온게 아닐까 싶다. 하....

### Mathf.Clamp(value, min, max)
변수의 범위를 제한하는 함수

### Quaternion.Euler(pitch, yaw, roll)
목표로 하는 회전 값을 넣어주면 해당 회전을 시켜준다.

왜 이런게 필요하다냐?
x,y,z축을 중심으로 회전할 때 회전 순서를 잘 맞춰야지만 서로 영향을 주지 않고 해당 수치로 회전시킬 수 있다.

pitch=> x축을 중심으로 회전정도를 나타내는 값<br>
yaw=> y축을 중심으로 회전정도를 나타내는 값<br>
roll => z축을 중심으로 회전정도를 나타내는 값<br>
```
```

```
#PlyaerControl.cs 파일

사용자가 비행선을 이동시킬 때, 조금의 회전도 함께 시켜서 움직일려고 한다.
float pitch = transform.localPosition.y * -positionPitchFacotor;
(중략)
위 코드는 사용자입력에 따른 변화하는 y좌표에 따라서 우주선의 위치에 따라 회전을 시키기 위해서이다.
localposition을 쓴 이유는 1차적으로는 이동을 localposition기준으로 하기 때문이다.

아래 코드에 의해서 사용자 입력에 따라 비행선의 위치(localposition)은 변화한다.
transform.localPosition = new Vector3(clampedXPos, clampedYPos, transform.localPosition.z);

```
# 하...... vscode dotnet 연동방법
왠지는 모르겠지만  vscode cmd에서는 dotnet으로 자동으로 인식을 못해서 수동으로 json setting에 추가해줘야 한다.
하.... 3시간동안 찾아도 안나오던걸  chatgpt바로 해주네 ㅅㅂ chatgpt 짜증난다.
어떨때는 개 멍청하고 어떨땐느 바로 알려주고 뭐냐...


### 애니메이션 편집
animation tap에서 편집이 가능하다.


### Particle System과 Laser Bullets
주의! Partile System은 Object가 아니다!
Why? Object에 추가되는 컴포넌트이기 때문이다.

Particle Inspecter 속성들
Duration : Particle이 Play되는 시간
Emission-Rate over time : 초당 발사 속도
Life time : 발사된 Particle이 유지되는 시간
Start speed : particle의 속도(속도를 빠르게 하면 같은 시간에도 더 말리 나간다.)
simulation Space : 발사된 레이저의 위치 기준을 어디로 둘 것이냐
- 발사 이후의 레이저는 그대로 공간상에서 진행해야 하므로 위치 기준을 world로 지정

- Trail
Particle 입자에 잔상을 남기는 것이다.
여러 속성들이 있지만 중요한 속성!
size affects width=> 이 속성은  particle의 크기가 작아지면 잔상의 크기도 작아진다.<br>
강의에서는 particle의 크기를 없애서 잔상만 나오게 해서 레이저 같은 효과를 주려고 했으나
이 속성이 켜져 있으면 particle의 크기가 엇어지는 순간 잔상도 없어지기 때문에 꺼야하는 속성 이었다.

# 중첩 프리팹 prefab
프리팹이란 object를 저장해서 인스턴스 형태로 가져다 쓰는 거고
프리팹을 변경하면 가져다 쓴 인스턴스가 모두 바뀐다.
물론 인스턴스에서 바뀐 변경사항들은 덮어씌워지지 않는다.
Ex) 인스턴스의 색을 파란색으로 바꾸고 나서 원래 프리패의 색은 노란색으로 변경함
이 경우 인스턴스의 색은 파란색이거나 파란+노랑 색으로 변경됨

그리고 부모 object의 경우 size를 변경하게 되면 자식 object의 사이즈도 변경되기 때문에 주의해야 한다.

그래서 단순히 옆에 두고 싶은 경우 자식이 아니라 형제 컴포넌트로서 공통된 부모 object소속을 시키는 것이 낫다.

## 변경사항
중첩된 프리팹의 경우 하위 인스턴스의 변경도 상위 인스턴스의 변경으로 인지된다.
<b>즉, 자식 인스턴스의 변경사항을 자식 프리팹에 적용할 수 없고 부모 프리팹에만 적용된다.</b>
그러나, 자식 프리팹의 변경사항은 인스턴스에 적용된다.


# Foreach
다른 언어에서와 마찬가지로 Collection개체를 순회화면 명령을 수행하는 문법이다.
간단히 말하면 특정 명령을 반복해서 수행하게 해주는 문법이다.
```
foreach(ObjectType item in things)
{
    todothings.....
}

```

# 변수를 정리하는 방법 
지금까지 많은 변수들을 script내부에서 선언해 왔다.<br>
이것들은 나중에 보아도 이해할 수 있도록 정리하는 방법을 소개한다.
## 속성 지정
script에서 [SerializedField] 처럼 대괄호 내부에 글자를 작성하므로서 변수에 속성을 지정해 줄 수 있다.
### Header
이 속성은 변수에 한정된다기 보다는 Inspecter에서 변수들의 범주를 나타낼 수 있게 하는 코드이다.
```
[Header("General_set_up")] 
float xRange=10f
```
이 경우 Inspecter에서는 xRange 위에 General_set_up이라는 제목이 달리게 된다.
### tooltip
```
[Tooltip("How fast move up and down")] float controlspeed =10f
```
이 속성은 inspecter에서 마우스를 가져다 댓을 경우 Tooltip 옆에 적힌 도움말을 띄운다.


# 충돌 시스템
* static colider
colider만 있는 경우

* colider+rigidbody
대부분 충돌 발생+ 물리적 힘도 받음!

* kinematic rigidbody 
충돌은 발생하지만 외부의 물리적 힘은 안 받음
=> 이동시키기 위해서는 스크립트 작성이 필요

* colider+trigger
통과시키지만, OntriggerEnter함수에서 받을 수 있는 이벤트 실행

```
question
왜 우주선에 rigidbody에 ues gravity를 적용시켰을 때 카메라가 못따라갔을까?
아하! 우주선의 부모 컴포넌트는 그대로 timeline을 따라 이동하기 때문에 카메라는 우주선의 위치에 영향을 받지 않는다.
```

# Script에서의 Instance화
```
Instance(obejct,vector3, quaternion)
오브젝트, 위치, 회전각 이 세 요소를 가지고 프리페의 인스턴스를 생성해내는 메소드이다.

```
## 부모하위에 Instance 생성법
```
object.transform.parent= object2
```
object의 부모를 obejct2로 한다 해당 코드를 통해서 생성되는 instance를 부모에 할당해 hierachy를 정리할 수 있다.


# Start method 의미
나는 Start가 unity 화면 상단 재생 버튼을 누렀을 때 실행되는 건줄 알았는데
gpt에 쳐보니 script가 부착된 object가 최초 활성화 됫을때 실행되는 함수라고 한다.

# public을 통한 타 script 참조
GameObject.FindObjectOfType<>을 통해 타 script(class)를 불러올 수 있다.
단 pulic class, method만

주의!!! 이 때 참조대상 script는 게임 object에 부착되어 있어야 한다.!!

# UI 추가
TextMeshPro Package필요
Creat-UI를 통해서 추가 가능
Cansvas라는 객체 생성됨

## 캔버스(Canvas)가 안보임?
Scene탭 우측 상단에 Gizmo(구 형 아이콘)을 클릭하면 보인다.

## Text 설정
TEXT객체에 script를 붙여서 설정
```
using TMPro라는 것이 필요
TMP_TEXT라는 속성을 가져옴
해당 속성에 string을 대입해서 글자 변경
```

# Rigidbody의 특성
부모 객체에  rigidbody를 설정하면 자식의 colider를 모두 고려한 충돌이 발생한다.



# 타임라인 control 속성 추가




# 싱글톤 패턴
클래스를 인스턴스화 할 때 하나의 인스턴스로 제한하는 소프트웨어 설계 패턴
어쨋든, 클래스의 하나의 인스턴스만 존재하도록 설정

## Unity Manual에서 Order of excution for event function 문서

이벤트 실행 순서
Awake-OnEnable-Reset-Start
Awakee=> play 실행 시 처음 실행되는 문서

## SceneReLoad시 재시작 막는 방법
DontDestroyOnLoad(gameObject)
스크립트가 부착된 게임 오브젝트가 신 리로드시 삭제되지 않도록 설정
=> 신 리로드시 기존 object가 삭제됨을 알 수 있다.


## sound Effect를 한번에 적용하는 방법
Effect Obejct가 생성되는 기존 코드를 이용하기 위해서
그냥 Effect prepab에 audio 컴포넌트를 추가하고 play on awake속성을 통해 생성과 동시에 play 되도록 함

# Skybox 하늘의 효과를 바꾸는 방법
Material 객체를 하늘에 드래그 한다 이 때 Material의 shader를 skybox proceder로 바꿔준다.
shader가 6side인 경우 6면을 통해 하늘을 설정 가능\


## 안개 설정하는 방법
lighting 객체(조명 객체)를 통해서 가능하다.


# Post Processing
우리가 사진찍고 snow하는 것처럼
후 보정효과를 주는 것
package manager-> post processing 설치
1. 빈 객체 생성(포스트 프로세싱 효과를 담기 위해)
2. Post-process Volume Componenet를 해당 객체에 추가하기
4. is Global 설정하기!!!
5. Profile 속성에 새 profile 할당하기
Assets->create-> post-process profile 
6. PostProcessing을 위한 layer를 생성
7. 1번에서 생성한 객체에 layer할당
8. main camera에 postprocessing compoenet할당
9. layer 할당, anti-aliasing mode=> fast approximate .....
fast mode 설정
10. Trigger =>Main Camera
11. Player rig 업데이트
12. post processing 객체 prepap설정하기
13. post-process 객체에서 volume 속성에서 add effect 클릭해서 표과 추가
14. 
