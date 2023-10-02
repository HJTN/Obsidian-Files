# 변수 선언
---
## 1. var
👉 변수 선언 후, 변수값 변경 가능

``` kotlin
fun main() {
	var a: Int
	a = 123
	println(a)
}
```
## 2. val
👉 변수 선언 후, 변수값 변경 불가능 (초기화만 가능)
👉 Java의 final과 같음

``` kotlin
fun main() {
	val a: Int = 1232
	a = 999 // Error 발생!
	println(a)
}
```

## 3. lateinit
👉 기본 자료형을 제외(String은 가능)하고 객체 생성 시 초기화를 하지 않고 변수만 선언할 수 있음

``` kotlin
class A {
	lateinit var a: String

	fun test(): String {
		if(::a.isInitialized) {
			return a
		} else {
			return "null"
		}
	}
}
```

## 4. lazy
👉 변수의 초기화 시점이 변수를 사용할 때 초기화 됨

``` kotlin
fun main() {
	val num: Int by lazy {
		println("초기화")
		7
	}
	println("start")
	println(num)
	println(num)
}
```
# NULL 처리
---
## ? 처리
👉 변수값으로 null 지정 가능

``` kotlin
fun main() {
	val a: String? = null
	val b: String = "111"
	val c: String = null // Error 발생
}
```
## 엘비스 연산자 (?: )
👉 ?: 왼쪽에 있는 표현식이 null이 아니면 이를 반환하고, 그렇지 않으면 오른쪽에 있는 표현식을 반환

``` kotlin
val a = b?.length ?: -1
```
## !! 처리
👉 null이 아님을 명시

``` kotlin
fun main() {
	val dog: Animal? = Animal()
	val nonNullDog: Animal = dog!!
	dog!!.sound()
}
```
# Type 변환
---
👉 to{Type}() 함수로 다른 Type 변환 가능

``` kotlin
fun main() {
	var a: Int = 123
	var b: String = a.toString()
	println(b)
}
```

# 배열 생성
---

``` kotlin
fun main() {
	var intArr: Array<Int> = arrayOf(1,2,3,4)
	var intArr2 = arrayOfNulls<Int>(5)
	var intArr3: Array<Any> arrayOf(1, "cmd", 3.2, true)
	println(intArr)
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
	println(a)
	println(b)
}
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

## 반복문 생성

``` kotlin
// While문
var i: Int = 0
while(i < 3) {
	println(i)
	i++
}

// for문
for(i in 0..3) {
	println(i)
}

for(i in 3 downTo 0) {
	println(i)
}

for(i in 0..5 step 2) {
	println(i)
}

for(i in 'a'..'e') {
	println(i)
}
```

## 반복문 흐름 제어

``` kotlin
// 흐름 제어 (break) 👉 반복 중 종료
for(i in 0..5) {
	if(i == 2) {
		break
	}
	println(i)
}

// 흐름 제어 (continue) 👉 반복 중 건너뛰기
for(i in 0..5) {
	if(i == 2) {
		continue
	}
	println(i)
}

// 반복문에 Label 지정 기능
fun main() {
	loop@for(i in 1..10) {
		for(j in 1..10) {
			if(i == 1 && j == 2) break@loop
		}
	}
}
👉 label이 지정된 반복문을 기준으로 즉시 break 됨
```
# 함수 생성
---

``` kotlin
fun main() {
	println("Hello Kotlin!")
}

// 함수 기본형 👉 fun 함수명(매개변수: Type): Return Type {}
fun add(a: Int, b: Int, c: Int): Int {
	return a + b + c
}

// 단일 표현식 함수
fun add(a: Int, b: Int, c: Int) = a + b + c
```
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
	var c: (String) -> Unit = {s -> println(s)}
	var d = {s: String -> println(s)}
	// s 변수 반환
	var e = {s: String -> s}
	// Parameter가 없는 경우
	var f = {
		println("444")
	}
	// Parameter가 하나일 경우, it 키워드 사용 가능
	var g: (String) -> Unit = {println(it)}

	c("111")
	d("222")
	println(e("333"))
	f()
	g("555")
}

fun a(str: String): String {
	return str
}

fun b(funs: (String) -> String) {
	println(funs("000"))
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
		println("$name $price")
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
	println(b)
}

class Book(var name: String, var price: Int) {
	fun dc() {
		price -= 100
	}

	fun printData() {
		println("$name $price")
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
	println(b)
}

class Book(var name: String, var price: Int) {
	fun dc() {
		price -= 100
	}

	fun printData() {
		println("$name $price")
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
		println(price)
	}
}

class Book(var name: String, var price: Int) {

}

fun main() {
	var price = 4000
	var a = Book("a", 2000)
	a.let {
		println(it.price)
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
	println(Counter.count)
	Counter.clear()
	println(Counter.count)
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
	println("${Food.total}")
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
		println(count)
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
				println(count)
			}
		}).count()
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
# Class 생성
---
👉 Java와 달리 생성자를 따로 만들 필요 없음
👉 객체 생성 시, 클래스의 속성에 따라 입력해주면 됨

``` kotlin
class User(var name: String, var age: Int, val birth: String) {
	fun printUser() {
		println("$name $age $birth")
	}
}

// init : 해당 Class를 토대로 객체 생성 시 최초 실행되는 부분 (여러 개 생성 가능)
class User(var name: String, var age: Int, val birth: String) {
	init {
		println("$name $age $birth")
	}
	init {
		println(age)
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
		println("$name $age")
	}
}

class Dog(var dog_name: String, var dog_age: Int) : Animal(dog_name, dog_age) {
	fun dogIntroduce() {
		super.introduce()
	}

	override fun introduce() {
		println("Overrided!")
	}
}
```

## 추상 클래스
👉 Java와 동일

``` kotlin
abstract class Animal {
	abstract fun eat()
	fun dog() {
		println("멍멍")
	}
}

class Cat : Animal() {
	override fun eat() {
		println("츄르")
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
		println("음식")
	}
}

class Dog(var name: Int) : Runner, Eater {
	override fun run() {
		println("산책 시간")
	}

	override fun eat() {
		println("사료")
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
		println("$name을 마십니다")
	}
}

class Cola: Drink() {
	var type = "콜라"
	override fun drink() {
		println("$type을 마십니다")
	}
	fun washD() {
		println("$type을 설거지 합니다")
	}
}
```
# Data Class
---
👉 Class에 has, equals, toString, copy, componentX 함수를 자동으로 구현해주는 Class

``` kotlin
fun main() {
	val copyA = a("a", 123)

	println(copyA == a("a", 123))
	println(copyA)

	val copyB = b("b", 123)

	println(copyB == b("b", 123))
	println(copyB)

	println(copyB.copy())
	println(copyB.copy(name="c"))
	println(copyB.copy(id=234))

	val list = listOf<b>(
		b("a", 123),
		b("b", 234),
		b("c", 345)
	)

	for((a,b) in list) {
		println("$a $b")
	}
}

class a(val name: String, val id: Int)
data class b(val name: String, val id: Int)
```
# enum Class
---
👉 enum처럼 사용하는 Class

``` kotlin
fun main() {
	var a = tt.A
	println(a)
	println(a.msg)
	println(a.isA())
}

enum class tt(val msg: String) {
	A("a"),
	B("b"),
	C("c")

	fun isA() = this == tt.A
}
```
# by 키워드
---
## **Delegation (위임)**
👉 어떤 일의 책임 & 처리를 다른 Class 혹은 Method에게 넘긴다는 의미
👉 다른 Class의 기능을 사용하되 그 기능을 변경하지 않는 경우, 상속 대신 위임을 사용
👉 위임을 활용하면 하나의 객체가 다른 객체에 미치는 영향이 감소함
## **Delegation**을 사용하는 이유
👉 하위 Class가 상위 Class를 상속 받아서 상위 Class의 Method를 Override하는 경우가 많음
👉 프로그램을 유지 보수하는 경우, 상위 Class의 내용이 변경되면 하위 Class에서 Error가 발생할 수 있음
## 상속의 문제점
1. 상/하위 Class 간의 결합도가 높아지거나 상속 구조가 복잡해질 경우, 상위 Class의 변화가 하위 Class에 주는 영향을 예측하기 어려움
2. 불필요한 상위 Class의 Method까지 구현할 필요가 있음
3. final Class의 경우, 상속이 불가능
4. 하위 Class로 내려갈수록 기능이 추가되면서 Error를 파악하기 어려움
👉 Kotlin의 경우, 상속으로 인한 종속성, 의존성 문제를 방지하기 위해 Class는 기본적으로 final 접근자로 지정됨
👉 상속이 필요한 경우, Class를 open 접근자로 명시해야 함
## **Delegation Pattern**
👉 Software Engineering에서 위임 패턴은 객체 구성 중 상속과 동일한 코드 재사용을 지원하는 객체 지향 디자인 패턴
👉 하나의 Class를 다른 Class에 위임하도록 "by" 키워드를 이용하여 위임 선언을 하고, 위임된 Class에 있던 Interface Method를 별도의 참조 없이 호출할 수 있도록 지원하는 기능

## Class Delegation

``` kotlin
fun main() {  
    val b = User("홍길동",23)  
    DUser(b).print()  
}  
  
interface clickEvent {  
    fun print()  
}  
  
class User(val name: String, val age: Int): clickEvent {  
    override fun print() {  
        println("User name: $name, User age: $age")  
    }  
}  
  
class DUser(ce: clickEvent): clickEvent by ce
```
### 위 Code 설명
👉 DUser Class의 "by" 절은 DUser Class의 객체 내부에 ce를 저장함
👉 Compiler는 clickEvent Interface의 모든 Method를 ce로 전달하면서 DUser Class 생성
👉 Override문이 존재하면 Compiler는 위임 객체의 Method 대신에 Override로 구현된 Method를 사용

``` kotlin
// DUser Class에 override문으로 print() Method 재정의
class Duser(ce: clickEvent): clickEvent by ce {
	override fun print() {
		println("abcde")
	}
}

❇️ 실행 시 출력 값
abcde
```
## Property Delegation
👉 Property의 Getter, Setter를 다른 객체에 위임하는 것
### Character Class with Get(), Set()
``` kotlin

```
## Delegation의 장단점
1. 상속은 하나의 Super Class만 가능하나, 위임은 복수의 Interface 가능
2. Interface 정의 필요
3. Code가 유연해지나, 관련 지식이 없으면 이해하기 어려움
4. 상속은 객체의 크기에 따라 비용이 증가
# 참고 자료
---
1. [코틀린 문법 총정리](https://cjw-awdsd.tistory.com/20)
2. [코틀린 기초 문법 정리](https://haruple.tistory.com/206)
3. [null 처리 방법](https://onlyfor-me-blog.tistory.com/450)
4. [DiMo의 Kotlin 강좌](https://www.youtube.com/watch?v=8RIsukgeUVw&list=PLQdnHjXZyYadiw5aV3p6DwUdXV2bZuhlN&index=1)
5. [코틀린 기본 문법](https://everybody-yeah.tistory.com/9)
6. [by the way, what is this?](https://velog.io/@jojo_devstory/%EC%BD%94%ED%8B%80%EB%A6%B0-Kotlin-by-by-the-way-what-is-this)
7. [Kotlin By 키워드에 대한 이해](https://developer88.tistory.com/entry/Kotlin-By-%ED%82%A4%EC%9B%8C%EB%93%9C%EC%97%90-%EB%8C%80%ED%95%9C-%EC%9D%B4%ED%95%B4-Property-Delegate-Pattern)
8. [Delegated Property](https://velog.io/@evergreen_tree/KotlinDelegation-2.-Delegated-Property)