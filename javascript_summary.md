# JAVASCRIPT란?

웹을 집에 비유하자면<BR>
HTML은 철근구조, CSS는 인테리어 꾸미기라면?<br>
JAVASCRIPT는 전선을 설치해서 집의 가구들이 작동하도록 하는 것과 유사하다.

- 출처 : 내생각

# 라이브러리란?

코딩을 하다가 주로 반복되는 코드를 정리해서 타인이 쓸 수 있게 한 것

# jQuery란?

- javascript라이브러리 종류 하나
- element를 선택하는 강력한 규칙
- 선택된 대상을 제어하는 다양한 방법
- javascript보다 간단하다.

## jQuery 문법

```
$(제어대상).method1().method2();
 jquery는 자기자신을 return하기 때문에
 뒤에 .method를 통해서 중첩해서 메소드 적용이 가능하다.

```

이러한 jquery의 속성을 *chain*이라고 한다.<br>

그리고 추가적으로 문법을 소개하자면<br>
.attr(속성이름, 속성값) => attribute의 줄임말로서 제어대상의 속성을 제어한다.

## javascript vs jquery

js(javascript)로는 되게 긴 코드들을 jquery로는 짧게 쓸 수 있다.<br>
그리고 브라우저별 설정을 다르게 해줘야하는 경우도 jquery가 알아서 해주는 부분도 있다.

## wrapper

```
$('선택자').method1().method2();

```

jQuery는 주로 위와 같이 $를 사용하는 문법을 사용한다.<br>
이 $가 타 라이브러리와 겹치는 것을 예방하기 위해<br>

1. 임시로 $를 인자로 받는 함수를 설정하여 해당 함수 내부에 jquery를 작성한다.<br>
   이 경우 $는 지역변수로 인식되기 때문에 타 라이브러리의 $와 중첩되지 않는다.

그리고 이렇게 선언한 함수를 뒤에 `(jquery)`를 추가해 줌으로서 바로 실행하여준다.

2. $를 jquery로 바꿔서 작성하는 방법이 있다.

## event bubbling과 event 위임

## event 버블링이란?

Dom(문서 객체 모델)구조를 통해 event가 번져 나가는 것<br>
쉽게 말해 자식 요소에서 발생한 event(상호작용)이 부모에게 전달됨을 말한다.
예시

```
<div onClick="alert('div')">
<p onClick="alert('p')">
<button>test</button>
</p>
</div>
```

<div onClick="alert('div')">
<p onClick="alert('p')">
<button>test</button>
</p>
</div>
위 코드의 경우 test 버튼을 클릭하면 p경고창이 뜨고 확인을 누르면 div경고창이 뜬다.<br>
test는 onclick속성이 없음에도 경고창이 뜬 이유가 바로 event 버블링이다.
https://ko.javascript.info/bubbling-and-capturing
https://hangeoreum.tistory.com/entry/JS-Event-Delegation%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EC%9C%84%EC%9E%84

## 이벤트 위임

이벤트 위임이라 함은 상위 객체 이벤트를 제어함으로서 <br>
아직 생성되지 않은 dom객체의 이벤트를 제어함을 말한다.
그 원리는 event 버블링을 기반으로 두고 있다.<br>
즉, 상위 객체에만 이벤트 handler가 있더라도 이벤트 버블링을 통해 상위객체까지 전달되어 온다.

## 백틱(`), 키보드 물결표의 사용\

(백틱=키보드 물결표)를 따옴표 대신 사용하면 ${}를 통해 문자열 내부에 변수를 넣을 수 있다.

```
var name='jinha'
$('#ul').append("<li>hello world ${name}</li>")
```
