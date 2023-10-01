# 변수 선언
---
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

## ❇️ ? 표시
👉 변수값으로 NULL 지정 가능

``` kotlin
fun main() {
	var a: Int? = null
	print(a)
}
```

# Type 변환
---
👉 to{Type}() 함수로 다른 Type 변환 가능

``` kotlin
fun main() {
	var a: Int = 123
	var b: String = a.toString()
	print(b)
}
```

# 배열 생성
---

``` kotlin
fun main() {
	var intArr: Array<Int> = arrayOf(1,2,3,4)
	var intArr2 = arrayOfNulls<Int>(5)
	var intArr3: Array<Any> arrayOf(1, "cmd", 3.2, true)
	print(intArr)
}
```

# 함수 생성
---

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

# 조건문
---

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

# 반복문
---

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

# Class 생성
---
👉 Java와 달리 생성자를 따로 만들 필요 없음
👉 객체 생성 시, 클래스의 속성에 따라 입력해주면 됨

``` kotlin
class User(var name: String, var age: Int, val birth: String) {
	fun printUser() {
		print("$name $age $birth")
	}
}

// init : 해당 Class를 토대로 객체 생성 시 최초 실행되는 부분 (여러 개 생성 가능)
class User(var name: String, var age: Int, val birth: String) {
	init {
		print("$name $age $birth")
	}
	init {
		print(age)
	}
}
```
## 상속

👉 부모 클래스에 open 키워드가 설정되어 있어야 함
👉 서브 클래스의 속성 이름은 부모 클래스의 속성 이름과 달라야 함
👉 함수를 override할 경우, override 키워드 사용 (부모 클래스의 함수에 open 키워드가 설정되어 있어야 함)

``` kotlin
open class Animal(var name: String, var age: Int) {
	open fun introduce() {
		print("$name $age")
	}
}

class Dog(var dog_name: String, var dog_age: Int) : Animal(dog_name, dog_age) {
	fun dogIntroduce() {
		super.introduce()
	}

	override fun introduce() {
		print("Overrided!")
	}
}
```

## 추상 클래스
👉 Java와 동일

``` kotlin
abstract class Animal {
	abstract fun eat()
	fun dog() {
		print("멍멍")
	}
}

class Cat : Animal() {
	override fun eat() {
		print("츄르")
	}
}
```

## 인터페이스
👉 Java와 달리 추상 함수와 속성과 일반 함수 선언 가능
👉 생성자는 생성 불가능
👉 구현부({})가 있으면, open 함수로 간주하고, 없으면 abstract 함수로 간주함

``` kotlin
interface Runner {
	// 추상 함수로 간주
	fun run()
}

interface Eater {
	// open 함수로 간주
	fun eat() {
		print("음식")
	}
}

class Dog(var name: Int) : Runner, Eater {
	override fun run() {
		print("산책 시간")
	}

	override fun eat() {
		print("사료")
	}
}
```

# 접근 제한자
---
## Public
👉 아무것도 쓰지 않을 시 기본적으로 지정되는 제한자
👉 클래스 외부에서 접근 가능

## Private
👉 클래스 내부에서만 접근 가능

## Protected
👉 클래스 자신과 상속받은 클래스만 접근 가능
# 참고 자료
---
1. [코틀린 문법 총정리](https://cjw-awdsd.tistory.com/20)
2. [코틀린 기초 문법 정리](https://haruple.tistory.com/206)