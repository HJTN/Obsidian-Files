# 변수 선언
## 1. var
👉 변수 선언 후, 변수값 변경 가능

``` kotlin
fun main() {
	var a: Int
	a = 123
	print(a)
}
```
## 2. val
👉 변수 선언 후, 변수값 변경 불가능 (초기화만 가능)
👉 Java의 final과 같음

``` kotlin
fun main() {
	val a: Int = 1232
	a = 999 // Error 발생!
	print(a)
}
```

## 3. ? 표시
👉 변수값으로 NULL 지정 가능

``` kotlin
fun main() {
	var a: Int? = null
	print(a)
}
```

## 4. Type 변환
👉 to{Type}() 함수로 다른 Type 변환 가능

``` kotlin
fun main() {
	var a: Int = 123
	var b: String = a.toString()
	print(b)
}
```

## 5. 배열 생성

``` kotlin
fun main() {
	var intArr: Array<Int> = arrayOf(1,2,3,4)
	var intArr2 = arrayOfNulls<Int>(5)
	var intArr3: Array<Any> arrayOf(1, "cmd", 3.2, true)
	print(intArr)
}
```

## 6. 함수 생성

``` kotlin
fun main() {
	print("Hello Kotlin!")
}

// 함수 기본형 👉 fun 함수명(매개변수: Type): Return Type {}
fun add(a: Int, b: Int, c: Int): Int {
	return a + b + c
}

// 단일 표현식 함수
fun add(a: Int, b: Int, c: Int) = a + b + c
```

## 7. 조건문

``` kotlin
if (조건) {
	처리 내용
} else {
	처리 내용
}

// is : 변수값의 Type 비교
if (a is Int) {
	처리 내용
}

// Switch문과 비슷
when(a) {
	변수값 종류 -> 처리 내용
	변수값 종류 -> 처리 내용
	else -> 처리 내용
}

// when문으로 변수값 지정 가능
var b =
when(a) {
	1 -> a
	"cmd" -> a
	else -> a
}
```

## 8. 반복문

``` kotlin
// While문
var i: Int = 0
while(i < 3) {
	print(i)
	i++
}

// for문
for(i in 0..3) {
	print(i)
}

for(i in 3 downTo 0) {
	print(i)
}

for(i in 0..5 step 2) {
	print(i)
}

for(i in 'a'..'e') {
	print(i)
}

// 흐름 제어 (break) 👉 반복 중 종료
for(i in 0..5) {
	if(i == 2) {
		break
	}
	print(i)
}

// 흐름 제어 (continue) 👉 반복 중 건너뛰기
for(i in 0..5) {
	if(i == 2) {
		continue
	}
	print(i)
}
```

## 9. Class 생성
👉 Java와 달리 생성자를 따로 만들 필요 없음
👉 객체 생성 시, 클래스의 속성에 따라 입
