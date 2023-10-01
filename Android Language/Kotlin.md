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

# 고차함수 / 람다함수
---
👉 함수를 클래스에서 만들어 낸 Instance처럼 취급
👉 함수를 Parameter로 넘겨줄 수 있음
👉 함수를 결과값으로 반환 받을 수 있음

``` kotlin
fun main() {
	// 함수를 Parameter로 넘겨줄 때 ::을 붙임
	b(::a)

	// 람다함수 작성
	// var 변수명: (입력 Type) -> 반환 Type = {입력 변수명: 입력 Type -> 처리 구문}
	var c: (String) -> Unit = {s -> print(s)}
	var d = {s: String -> print(s)}
	// s 변수 반환
	var e = {s: String -> s}
	// Parameter가 없는 경우
	var f = {
		print("444")
	}
	// Parameter가 하나일 경우, it 키워드 사용 가능
	var g: (String) -> Unit = {print(it)}

	c("111")
	d("222")
	print(e("333"))
	f()
	g("555")
}

fun a(str: String): String {
	return str
}

fun b(funs: (String) -> String) {
	print(funs("000"))
}
```

# Scope 함수
---
👉 함수형 언어를 편리하게 사용할 수 있도록 도와주는 기본 함수
## 1. apply
👉 Instance의 함수나 속성값을 람다함수를 사용해 변경할 수 있는 함수
👉 코드가 깔끔해짐

``` kotlin
fun main() {
	var a = Book("a", 2000)
	a.apply {
		name = "b"
		dc()
	}
	a.printData()
}

class Book(var name: String, var price: Int) {
	fun dc() {
		price -= 100
	}

	fun printData() {
		print("$name $price")
	}
}
```

## 2. run
👉 apply와 같은 기능이나, 구문의 마지막 값을 반환해주는 차이

``` kotlin
fun main() {
	var a = Book("a", 2000)
	var b = a.run {
		name = "b"
		dc()
		"Complete"   // 반환
	}
	print(b)
}

class Book(var name: String, var price: Int) {
	fun dc() {
		price -= 100
	}

	fun printData() {
		print("$name $price")
	}
}
```

## 3. with
👉 run과 똑같으나, 사용법만 다름

``` kotlin
fun main() {
	var a = Book("a", 2000)
	var b = with(a) {
		name = "b"
		dc()
		"Complete"   // 반환
	}
	print(b)
}

class Book(var name: String, var price: Int) {
	fun dc() {
		price -= 100
	}

	fun printData() {
		print("$name $price")
	}
}
```

## 4. let / also
👉 also는 apply와 기능이 비슷하고, let은 run과 기능이 비슷함
👉 it 키워드를 사용하여 객체의 변수를 참조함
👉 변수명이 같은 경우, 혼동이 올 수 있어 다음과 같은 기능을 사용

``` kotlin
fun main() {
	var price = 4000
	var a = Book("a", 2000)
	a.run {
		// 2000이 출력되어야 하지만 main문의 price가 Scope 우선 순위가 높아서 4000이 출력됨
		print(price)
	}
}

class Book(var name: String, var price: Int) {

}

fun main() {
	var price = 4000
	var a = Book("a", 2000)
	a.let {
		print(it.price)
	}
}

class Book(var name: String, var price: Int) {

}
```

## 5. Object
👉 객체가 하나만 필요한 경우에 사용하는 키워드 (싱글톤 디자인 패턴)
👉 Class 내부에 생성 가능

``` kotlin
// Object 생성 -> object 키워드 사용
fun main() {
	Counter.countUp()
	print(Counter.count)
	Counter.clear()
	print(Counter.count)
}

object Counter {
	var count = 0
	fun countUp() {
		count++
	}

	fun clear() {
		count = 0
	}
}

// Class 내부에 Object 생성 -> companion object 키워드 사용
fun main() {
	var a = Food()
	var b = Food()
	a.up()
	b.up()
	print("${Food.total}")
}

class Food() {
	companion object {
		var total = 0
	}

	fun up() {
		total++
	}
}
```

# Observer 패턴
---
👉 Listener 또는 Callback이라고 함
👉 특정 이벤트를 감시하면서 발생 시, 특정 기능이 호출되도록 만든 패턴

``` kotlin
fun main() {
	EventPrinter().start()
}

interface EventListener {
	fun onEvent(count: Int)
}

class Counter(var listener: EventListener) {
	fun count() {
		for(i in 0..20) {
			if(i % 5 == 0) {
				listener.onEvent(i)
			}
		}
	}
}

class EventPrinter: EventListener {
	override fun onEvent(count: Int) {
		print(count)
	}

	fun start() {
		var count = Counter(this)
		count.count()
	}
}

// Listener를 익명 클래스로 정의하는 방법
class EventPrinter: EventListener {
	fun start() {
		Counter(object: EventListener {
			override fun onEvent(count: Int) {
				print(count)
			}
		}).count()
	}
}
```

# 다형성 as
---
👉 Class를 Casting하는 역할

``` kotlin
fun main() {
	var a = Drink()
	a.drink()

	var b: Drink = Cola()
	b.drink()

	if(b is Cola) {
		b.washD()
	}

	// Cola와 b로 동시 캐스팅된 c
	var c = b as Cola
	c.washD()
	b.washD()
}

open class Drink {
	var name = "음료"
	open fun drink() {
		print("$name을 마십니다")
	}
}

class Cola: Drink() {
	var type = "콜라"
	override fun drink() {
		print("$type을 마십니다")
	}
	fun washD() {
		print("$type을 설거지 합니다")
	}
}
```

# Collection List
---
## listOf
👉 추가한 객체를 대체, 추가, 삭제하지 못함
## mutableListOf
👉 추가한 객체를 대체, 추가, 삭제 가능
👉 add, sort, shuffle 등 함수 지원

``` kotlin
fun main() {
	val a = listOf<Int>(1,2,3)
	val b = mutableListOf<Int>()

	b.add(1)
	b.add(2)
	b.add(3)
	b.add(2,6)
	print(a)
	print(b)
}
```

# NULL 처리
---

# 참고 자료
---
1. [코틀린 문법 총정리](https://cjw-awdsd.tistory.com/20)
2. [코틀린 기초 문법 정리](https://haruple.tistory.com/206)