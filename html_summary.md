# HTML이란?

> HyperText Markup Langauge의 약어이다.<br>
> markup 언어로서 브라우저에서 작동한다.<br>
> HyperText(링크)를 통해 페이지간 이동 가능.

> ## Markup Langauge이란?

> 텍스트를 일정한 규칙에 따라 작성하여 **문서의 구조와 형태**를
> 나타내는 언어<br>
> HTML 이외에도 XML XTML등이 있다.

> ## Markup 이란?

> 문맥을 제외한 **추가적인 정보**를 나타낸다.<br>
> html에서는 이를 나타내는 수단이 **Tag**와 **Attribute**이다.<br>
> 출처 : https://zdnet.co.kr/view/?no=00000010047880

> ## Tag와 Attribute
>
> 앞서 말했듯, html은 Tag와 Attribute를 사용해 추가적인 정보를 전달한다.<br>
> Ex) `<p>this sentance is in paragraph</p>`
>
> `<p>`는 문장이 문단에 속함을 나타낸다.
>
> ### Tag란?
>
> contents를 감싸거나 그 자체만으로 정보를 나타내는 꺽쇄를 말한다.<br> >
> Ex) `<h1> hello world</h1>`
> 이처럼 여는 태그, 닫는 태그로 구성된다.<br>
> 그러나 img처럼 태그 하나로만 구성될 수도 있다.<br>
> Ex) `<img src="test.jpg" alt="test">
>
> ### Attribute란?
>
> Tag에 추가적으로 작성되어서 추가적인 정보를 전달한다.<br>
> Ex) `<img alt="테스트입니다.">` <br>
>
> alt는 이미지가 표현 불가시 출력할 정보를 나타내는 attribute이다.<br> >
> 실제 모습<br> >
> <img Alt="test입니다."  src="test.png">

# Box 구조

웹페이지를 설계할 때는 박스형태로 페이지를 구분해 보는 것이 유용하다.<br>
이는 작업단위를 나누기도 용이하고, css작업할 때도 수월하다.(공감!)

# HTML Tag의 종류

딱 떨어지는 구분이 아니고 태그의 특징 참고용

## Item

화면에 보여지는 컨텐츠를 나타냄<br>
a, video, button, input 등등

## Box

페이지의 구조를 나타날 때 사용
header, footer, div, nav, span form 등등

## Block

태그가 표현하는 contents와 관계없이 해당 가로줄 전체를 차지한다.

## Inline

Block과 반대로 컨텐츠의 크기대로만 차지한다.

# Semantic Tag와 웹 사이트 구조

## Semantic Tag이란?

의미를 가진 태그를 말한다.<br>

웹사이트들은 정형화된 구조를 가지고 있다.<br>
이를 의미를 가진 태그(Semantic Tag)를 통해 구분한다.

Header, Footer aside, article main 등등...

참고자료 https://velog.io/@gil0127/Semantic-Tag-%EC%A0%95%EB%A6%AC

## 왜 쓰는가?

- 웹페이지를 보지 않고 코드레벨에서도 구조를 파악하기 용이하다.<br>
  (개발자의 유지보수 면에서 용이하다.)
- 비시각적인 정보를 제공할 수 있다.<br>
  Ex) 시각장애인, 색맹 같은 분들이 사용하는 도구가 태그를 통해 사이트의 구조와 contents를 해석하기 용이하다.
- 검색엔진이 쉽게 이해할 수 있다.

# HTML 주요 구조 태그

- `<!DOCTYPE html>`
  과거에는 이 문서는 HTML로 작성됨을 나타내는 필수 서문이었으나 현재는 관습적으로 html 문서에 작성

* `<html></html>`
  html의 root 태그로서 페이지 전체를 감싸는 태그
  lang 속성을 통해 페이지의 언어 설정

* `<head></head>`
컨텐츠가 아닌 작성자가 페이지에 포함시킬 정보를 태그 내부에 작성.<br>
Ex) <meta charset="utf-8"> 현재 페이지는 utf-8 인코딩 방식사용<br>
  <meta name="viewport" content="width=device-width"> <br>
  <title> 브라우저 최상단에 표시될 제목을 표시한다.<br>
*`<body></body>`<br>
사용자에게 보여질 주요내용은 이 태그 내부에 주로 작성
