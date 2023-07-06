# HTML이란?

> HyperText Markup Langauge의 약어이다.<br>
> markup 언어로서 브라우저에서 작동한다.<br>
> 그리고 동시에 HyperText(링크)를 통해 페이지간 이동이 가능하다.

> ## Markup Langauge이란?

> 텍스트를 일정한 규칙에 따라 작성하여 **문서의 구조와 형태**를
> 나타내는 언어를 말한다.<br>

> HTML 이외에도 XML XTML등이 있다.

> ## Markup 이란?

> 문맥을 제외한 **추가적인 정보**를 나타낸다.<br>
> html에서는 이를 나타내는 수단이 **Tag**와 **Attribute**이다.<br>
> 출처 : https://zdnet.co.kr/view/?no=00000010047880

> ## Tag와 Attribute
>
> ### Tag란?
>
> contents를 감싸거나 그 자체만으로 정보를 나타내는 꺽쇄를 말한다.<br> >
> Ex) `<h1> hello world</h1>`
>
> ### Attribute란?
>
> Tag 내부에 작성되어서 추가적인 정보를 전달한다.<br>
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

웹사이트들은 정형화된 구조를 가지고 있다.<br>
정형화된 구조를 구분하는 Semantic Tag 제공

Header, Footer aside, article main 등등...

참고자료 https://velog.io/@gil0127/Semantic-Tag-%EC%A0%95%EB%A6%AC

## 왜 쓰는가?

- 웹페이지를 보지 않고 코드레벨에서도 구조를 파악하기 용이하다.
- 비시각적인 정보를 제공할 수 있다.<br>
  Ex) 시각장애인, 색맹 같은 분들이 사용하는 도구가 html태그를 통해 사이트의 구조와 contents를 해석한다.
