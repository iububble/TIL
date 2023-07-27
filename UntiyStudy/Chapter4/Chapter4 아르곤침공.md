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

<b>사용법</b>
[Window]-[Sequencing]-[Timeline]을 통해 창 생성
[window]-[animation]창 필요