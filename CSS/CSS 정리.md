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

#### 스타일 적용 우선순위

1. 인라인 스타일
2. 내부/외부 스타일 시트
3. 웹 브라우저 기본 스타일

## CSS 기본 속성
---
### 색상

![[css_colors.png]]
👉 색상 이름으로 표현
👉 RGB 색상값으로 표현: 범위(0~255)
👉 16진수 색상값으로 표현: 범위(00~FF)

```
<style>
	.blue { color: rgb(0,0,255); }
	.green { color: rgb(0,128,0); }	
	.silver { color: rgb(192,192,192); } </style>
<style>
	.blue { color: #0000FF; }
	.green { color: #008000; }
	.silver { color: #C0C0C0; }
</style>
```

### 배경 설정

1. **background-color** 👉 배경색 설정
2. **background-image** 👉 배경 이미지 설정

```
<style>
	body { background-image: url("/examples/images/img_background_good.png"); }
</style>
```

3. **background-repeat** 👉 수평, 수직 방향으로 반복되어 나타남

```
<style> 
	body { background-image: url("/examples/images/img_man.png"); background-repeat: repeat-x; } 
</style>

※ repeat-x: 수평 반복, repeat-y: 수직 반복, no-repeat: 반복x
```

4. **background-position** 👉 배경 이미지의 상대 위치 설정

```
<style>
	body {
		background-image: url("/examples/images/img_man.png");
		background-repeat: no-repeat;
		background-position: top right;
	}
 </style>

※ 키워드 조합
1. left top    4. right top    7. center top
2. left center 5. right center 8. center center
3. left bottom 6. right bottom 9. center bottom

※ 상대 위치를 px, %로 직접 명시 가능 (기준: left top)
background-position: 100px 200px;
```

5. **background-attachment** 👉 배경 이미지를 해당 위치를 고정, 스크롤과는 무관하게 화면 위치에서 이동하지 않음

```
<style>
	body {
		background-image: url("/examples/images/img_man.png");
		background-repeat: no-repeat;
		background-position: left bottom;
		background-attachment: fixed;
	} 
</style>
```

6. **background 속성 한번에 적용** 👉 한 줄에 배경 설정 가능

```
<style>
	body { background: #FFCCCC url("/examples/images/img_man.png") no-repeat left bottom fixed; } 
</style>
```

### 텍스트
1. **color** 속성 👉 텍스트의 색상 설정
2. **direction** 속성 👉 텍스트가 써지는 방향 설정 ( rtl / ltr(기본) )
3. **letter-spacing** 속성 👉 텍스트 내의 글자 사이의 간격 설정

```
.decLetterSpacing { letter-spacing: -3px; }
```

4. **word-spacing** 속성 👉 텍스트 내의 단어 사이의 간격 설정

```
.decWordSpacing { word-spacing: -3px; }
```

5. **text-indent** 속성 👉 단락의 첫 줄에 들여쓰기 설정

```
.paraIndent { text-indent: 30px; }
```

6. **text-align** 속성 👉 텍스트의 수평 방향 정렬 설정 ( left / right / center )

7. **text-decoration** 속성 👉 텍스트에 여러 가지 효과를 설정/제거에 사용

```
h2 { text-decoration: overline/line-through/underline/none; }
```

8. **text-transform** 속성 👉 영문자에 대한 대소문자/단어의 첫 문자만 대문자 설정

```
h2 { text-transform: uppercase/lowercase/capitalize; }
```

9. **line-height** 속성 👉 텍스트의 줄 간격 설정

```
.narrowLineHeight { line-height: 0.8; }
```

10. **text-shadow** 속성 👉 텍스트에 간단한 그림자 효과 설정

```
h2 { text-shadow: 2px 1px #3399CC; }
```

### 글꼴 설정

1. **font-family** 속성 👉 하나의 글꼴만/여러 개의 글꼴을 같이 설정
👉 여러 개의 글꼴로 설정되어 있으면, 웹 브라우저는 위에서부터 순서대로 글꼴을 읽어 들임
👉 사용자의 컴퓨터에 첫 번째로 읽어 들인 글꼴이 없으면 다음 글꼴을 확인
👉 글꼴의 이름이 한 단어 이상이면, 따옴표를 사용
👉 여러 개의 글꼴을 나열할 때에는 쉼표(,)로 구분

```
.serif { font-family: "Times New Roman", Times, serif; }
```

2. **font-style** 속성 👉 주로 이탤릭체를 사용하기 위해 사용
👉 normal(일반), italic(이탤릭체), oblique(텍스트 기울기)

```
.normal { font-style: normal; }
```

3. **font-variant** 속성 👉 속성값이 small-caps로 설정되면, 텍스트에 포함된 영문자 중 모든 소문자를 작은 대문자(small-caps) 글꼴로 변경
👉 대문자는 기존 크기 그대로 출력

.smallCaps { font-variant: small-caps/normal; }

4. font-weight 속성: 텍스트를 얼마나 두껍게 표현할지를 설정

속성값: lighter, normal, bold, bolder, 숫자 등

.bold { font-weight: 600/normal/bolder; }

5. font-size 속성: 텍스트의 크기 설정

절대적/상대적 크기

백분율 단위(%): 기본 크기를 100%로 놓고, 그에 대한 상대적인 크기를 설정

배수 단위(em): 기본 크기를 1em으로 놓고, 그에 대한 상대적인 크기를 설정, 웹 브라우저를 통해 크기를 재조정 가능

픽셀 단위(px): 스크린의 픽셀(pixel)을 기준으로 하는 절대적인 크기를 설정