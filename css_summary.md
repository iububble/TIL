# css란?

Cascading style sheet의 줄임말.<br>
Style sheet언어로서 Html 요소를 꾸미는데 사용된다.

# html에 적용하기

css를 html에 적용하는 데에는 크게 3가지 방법이 있다.<br>

> ## 1. html의 style attribute 사용
>
> ```
> <h1 style="color:red">hello world!</h1>
> ```
>
> <h1 style="color:red">hello world!</h1>
> html의 tag에 style 속성값에 css를 작성하여 적용시킨다.<br>
> 이 경우 적용태그에 바로 작성하므로 이해가 쉽고 적용도 간단하다.

> ## 2. `<style>`태그를 사용
>
> ```
> <style type="text/css">
> h2 {
>     border: 1px solid green;
> font-style:italic;
> }
> </style>
> <h2>hello world!</h2>
> ```
>
> <style type="text/css">
> strong {
> border: 1px solid black;
> font-style:italic;
> }
> </style>
>
> <strong>hello world!</strong><br>
> 현재는 markdown 문서라서 style태그를 이용한 color관련 css는 적용되지 않는 듯 하다.(추론)

> ## 3. `<link>`태그를 사용하여 file 단위로 적용
>
> `<link rel="stylesheet" href="style.css">`<br>
> style.css파일의 css를 현재 html파일에 적용한다.

# css의 구조

```
    p     {color:blue  ; }
  선택자    속성   값 구분자
```

선택자를 통해 css적용 범위 선택<br>
{}(중괄호)내부에 속성과 값으로 구성된 css 작성

# 선택자의 종류

## 선택자의 우선순위 중요!!!!

<b style="text-decoration: underline">구체적일 수록 우선순위가 높다.</b><br>
style 속성<-id선택자<-class 선택자<-tag선택자

### 1. 그냥 태그

p, h2, h1, a 등등 기본적인 html 태그를 선택자로 사용

### 2. class 선택자

형태 [.클래스 이름] class=클래스이름을 가진 tag를 모두 선택한다.

```
<style>
.name {
    text-decoration:underline;
}
</style>
<h3 class="name">my name is Amily</h3>
```

<style>
.name {
    text-decoration:underline;
}
</style>
<h3 class="name">my name is Amily</h3>

### 3. id 선택자

형태 [#id이름] id=id이름을 가진 tag 선택 <br>단 id는 한 html문서 내에서 중복 불가.

```
<style>
#james {
    font-style:italic;
}
</style>
<h3 id="james">my name is james</h3>
```

<style>
#james {
font-style:italic;
}
</style>

<h3 id="james">my name is james</h3>

### 4. 자식 선택자

A선택자 > B선택자 <br>
A선택자 태그 내부의 첫번째 B선택자를 선택

```
<style type="text/css">
h4 > p {
    font-style:italic;
    text-decoration:underline;
}
</style>
<h4>
    <p>hello css world!</p>
    <h3 id="james">my name is james</h3>
</h4>
```

<style type="text/css">
h4 > p {
    font-style:italic;
    text-decoration:underline;
}
</style>
<h4>
    <p>hello css world!</p>
    <h3 id="james">my name is james</h3>
</h4>

# 상속

html의 태그들은 아래처럼 중첩구조로 되어있다.

```
<html>
<head></head>
<body>
    <h2> 안녕하세요<h2>
    <p>
    여기는 제 블로그 입니다.
    </p>
</body>
</html>
```

이 때 몇몇 css속성은 상위 태그와 동일한 값을 가지게 된다.<br>
이를 상속이라고 부른다. 그러나 우선순위를 통해서 변경할 수도 있다.

# CSS Positon

css의 여러 속성중 position이 있다.
이는 해당 태그가 위치하는 방식을 나타낸다.

## 1. static

position의 기본 값이다.<br>
html에 작성된 순서대로 위치

## 2. absolute

해당 css가 적용된 태그의 상위태그를 기준으로 위치한다.

## 3. fixed

상위 태그와 상관없이 웹 페이지를 기준으로 위치한다.

## 4. relative

static에서 위치한 <b>기본 위치</b>를 기준으로 위치한다.

## 5. sticky

스크롤을 통해서 화면에서 벗어나려 할 때 페이지를 기준으로 고정되 위치한다.<br>
참고 https://daleseo.com/css-position-sticky-header/

# Flex box
