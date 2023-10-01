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

## 7. 