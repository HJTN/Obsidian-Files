## CSS 정의
---
👉 Cascading Style Sheets의 약자
👉 HTML 요소들이 각종 미디어에서 어떻게 보이는가를 정의하는 데 사용되는 스타일 시트 언어
👉 웹 페이지의 스타일을 별도의 파일로 저장할 수 있게 해주므로 사이트의 전체 스타일을 손쉽게 제어
👉 웹 사이트의 스타일을 일관성 있게 유지, 유지 보수 또한 쉬워짐
👉 외부 스타일 시트는 보통 확장자를 .css 파일로 저장

## CSS 문법
---
```
(선택자) { (속성명): (속성값); (속성명): (속성값); }
```

### 선택자 종류

1. **HTML 요소 선택자**: HTML 요소의 이름을 직접 사용
```
<style>
	h2 { color: teal; text-decoration: underline; }
</style>

👉 <h2>이 부분에 스타일을 적용합니다.</h2>
```

2. **아이디(id) 선택자**: CSS를 적용할 대상으로 특정 요소를 선택할 때 사용

```
<style>
	#heading { color: teal; text-decoration: line-through; }
</style>

👉 <h2 id="heading">이 부분에 스타일을 적용합니다.</h2>
```

3. **클래스(class) 선택자**: 특정 집단의 여러 요소를 한 번에 선택할 때 사용

```
<style>
	.headings { color: lime; text-decoration: overline; }
</style>

👉 <h2 class="headings">이 부분에 스타일을 적용합니다.</h2>
👉 <p>class 선택자를 이용하여 스타일을 적용할 HTML 요소들을 한 번에 선택할 수 있습니다.</p>
👉 <h3 class="headings">이 부분에도 같은 스타일을 적용합니다.</h3>
```

4. **그룹(group) 선택자**: 언급한 여러 선택자를 같이 사용하고자 할 때 사용
👉 여러 선택자를 쉼표(,)로 구분하여 연결
👉 코드를 간결하게 만들어 줌

```
<style>
	h1 { color: navy; }
	h1, h2 { text-align: center; }
	h1, h2, p { background-color: lightgray; }
</style>
```

### 주석표시

```
/* 주석 내용 */
```

### CSS 적용 방법

1. **인라인 스타일(Inline style)**: HTML 요소 내부에 style 속성을 사용

```
<h2 style="color:green; text-decoration:underline">
	인라인 스타일을 이용하여 스타일을 적용하였습니다.
</h2>
```

2. **내부 스타일 시트(Internal style sheet)**: head 태그 안에 style 태그를 사용

```
<head>
	<style>
		body { background-color: lightyellow; }
		h2 { color: red; text-decoration: underline; }
	</style>
</head>
```

3. **외부 스타일 시트(External style sheet)**: 외부에 작성된 스타일 시트 파일(.css) 이용
👉 웹 페이지의 head 태그에 link 태그를 사용하여 외부 스타일 시트를 포함해야만 스타일이 적용됨

```
<head>
	<link rel="stylesheet" href="/examples/media/expand_style.css">
</head>
```

※ 스타일 적용 우선순위

인라인 스타일

내부/외부 스타일 시트

웹 브라우저 기본 스타일