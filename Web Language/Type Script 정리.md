## Type Script
👉 버그 줄임 + 쉬운 유지 보수 + 질 좋은 코드
👉 Java Script 기반으로한 언어 
자바 스크립트의 모든 기능 포함 + 자바 스크립트에 포함되지 않은 기능 포함 = Type Script
👉 Java Script보다 강력하고 upgrade된 java script라고 생각
### Type Script 특징
1. **타입 표기** : 변수 값에 데이터 타입 지정 가능

```
function add (a: number, b: number) {
	return a+b;
}
console.log(add(3, 5));
```

2. **객체지향적**
3. **컴파일 타임 오류**
❇️ **컴파일** : 어떤 언어의 코드 -> 다른 언어로 변환 과정
4. 프로그래밍 언어인 동시에 컴파일러

### TS Download & 실행
👉 **NPM (Node Package Manager)** : 타입스크립트를 설치하기 위해 사용되는 도구
👉 NPM은 Node JS의 한 부분 (Node JS 설치 필요)
👉 **npm install -g typescript** : Type Script Compiler -> tsc(TypeScript Compiler) 명령어를 사용해서 TS를 JS로 변환 가능
👉 node (확장자가 js인 파일이름 ex. app.js, ... etc) : 작성한 코드 실행

### TS 작성
1. tsc (확장자가 ts인 파일이름 (ex. app.ts, ... 등))
2. tsc --init : ts 실행 후 돌아왔을 때/ts code 작성 후 선언된 변수에 오류 발생 시 입력 (vs code 오류)
3. tsc -w : typescript compiler가 변경된 ts 파일 감시 -> 변경 내용을 자동으로 컴파일

4. **Type Inference(추론)**
👉 let a = 5;에서 a변수에 5를 할당하는 순간 type 추론에 의해 a의 type이 number로 인식됨
👉 type 표기가 없는 경우, 코드를 읽고 분석하여 타입 유추

```
function calculateCodingIQ(lostPoints) {
    return 100 - lostPoints;
}

👉 매개변수의 type이 어떻든 간에 function의 반환값이 number라는 것을 type 추론을 통해 알아냄
```

5. **Type Specification(명시)** 
👉 변수 선언 시, 변수 값의 type 명시 -> 변수 값의 데이터 타입 지정

```
let x:(type 명시시 콜론 필요) string(type) = '문자열'(value);

function getStudentDetails(studentID: para_Type): (type) { content }
👉 함수의 type부분에 object를 쓰는 대신 { object 구조 } 이런 방식으로 써도 됨

예시)
function getStudentDetails(studentID: number): {
	studentID: number;
	studentName: string;
	age: number;
	gender: string;
	subject: string;
	createDate: Date;
} {
	content...
}
```

6. **Interface**
👉 5번 특성에서 사용한 object 구조 방식을 따로 정의하여 type으로 사용
👉 인터페이스를 타입으로 가지면, 인터페이스의 구조를 그 값으로 가지도록 강제됨

```
interface student {
    studentID: number;
    studentName: string;
    age?: number;
    gender: string;
    subject: string;
    courseCompleted: boolean;
}

❇️ age?: number; 
👉 age 뒤의 ?로 object 구조에서 age를 선택적 프로퍼티로 만듦 
👉 함수 값을 리턴할 때 age에 값을 할당해도 되고 안 해도 됨
```

 👉 **method** : 객체 내에서 선언된 함수 → 인터페이스 내에서 쓸 수 있음
 
 ```
interface student {
    studentID: number;
    studentName: string;
    age?: number;
    gender: string;
    subject: string;
    courseCompleted: boolean;
	addComment?(comment: string): string;		// 선택적 메소드
	addComment?: (comment: string) => string;
}
```

👉  **ReadOnly Property** : 읽기 전용 프로퍼티, 객체 생성시 할당된 프로퍼티의 값을 바꿀 수 없음 (c언어의 const와 비슷)

```
interface student {
    readonly studentID: number;
    studentName: string;
    age?: number;
    gender: string;
    subject: string;
    courseCompleted: boolean;
	addComment?(comment: string): string;		// 선택적 메소드
	addComment?: (comment: string) => string;
}
```

7. Enum (열거형) & Literal Type
1) **Enum** : 연관된 item들을 함께 묶어서 표현

```
enum genderType {
    Male,           // Male = 0
    Female,         // Female = 1
    genderNeutral   // genderNeutral = 2
}

👉 Numeric Enum (숫자 열거형)
```

```
enum genderTypeString {     // string enum
    Male = 'male',
    Female = 'female',
    genderNeutral = 'genderneutral',
}

👉 String Enum (문자열 열거형)
```

2) **Literal Type** : |(파이프) 로 property 값 구분

```
interface student {
    readonly studentID: number,
    studentName: string,
    age?: number,
    gender: 'male' | 'female' | 'genderNeutral',	// Literal type
    subject: string,
    courseCompleted: boolean,
    addComment?(comment: string): string,
    addComment?: (Comment: string) => string;
};
```

👉 객체의 변수 선언 시 : student를 붙여줘야함
👉 string으로 type 유추함으로 인해 오류 발생함

8. Any Type, Union Type, Type Aliases, Type Guards
1) **Any Type** : 어떤 type의 값이든 변수에 할당 가능

```
let someValue: any = 5;
someValue = 'hello';
someValue = true;

👉 오류 발생 X
👉 코드의 유지 보수를 위해 any 타입은 피하는 것이 좋다!
```

2) **Union Type** : 제한된 타입들을 동시에 지정
👉 |(파이프)로 타입 구분만 하면 됨

```
let someValue: number | string
👉 someValue는 숫자 혹은 문자열만 값으로 지정 가능
```

3) **Type Aliases** : 반복되는 union type 등을 하나의 타입으로 새로 지정하고 재활용

```
type strOrNum = number | string;
```

4) **Type Guards**
👉 union type을 쓰는 변수와 union type 중 하나의 type을 쓰는 변수 
👉 둘 사이에 데이터 이동이 있을 때 오류 발생을 막기 위해 사용
👉 typeof Operator(연산자)와 조건문 사용
❇️ **typeof** : 변수의 데이터 타입을 반환하는 연산자

```
// price의 type : string | number, itemPrice의 type : number일 때
if (typeof price === 'string') {    // price 타입이 string일 경우
	itemPrice = 0;
}
else {	// price 타입이 number일 경우
	itemPrice = price;
}
```

9. 함수의 반환 타입, 선택적 매개변수, 매개변수의 디폴트 값
1) **함수의 반환 타입**

```
function 함수이름 (매개변수1, 매개변수2): 함수의 반환 타입 {

}

👉 void, string, string[], ... 등등
❇️ 함수에 정의된 모든 매개변수 👉 함수에 필요하다고 가정 (어느 하나라도 빠뜨리면 오류 발생!)
```

2) **선택적 매개변수**

```
function 함수이름 (매개변수1: 타입, 매개변수2?: 타입): 함수의 반환 타입 {

}

👉 매겨변수2 → 선택적 매개변수가 됨 (매개변수 이름 뒤에 ? 붙여주면 됨)
❇️ 선택적 매개변수는 필수 매개변수 뒤에 위치해야함!
```

3) **기본 매개변수** (Default Parameter)

```
function 함수이름 (매개변수1 = 값, 매개변수2 = 값): 함수의 반환 타입 {

}
👉 매개변수에 = 값을 써주면 기본 매개변수가 됨
```

4) **화살표 함수**(Arrow Function)

```
// General Function
function add(num1: number, num2: number) {
    return num1 + num2;
}
// Arrow Function
const add = (num1, num2) => num1 + num2;
```

10. 객체 지향 프로그래밍
👉 연관된 변수와 함수들을 한 덩어리로 묶어서 구조화하여 표현
👉 어플리케이션을 실제 세상에 존재하는 객체와 같은 단위로 쪼개고 객체들이 서로 상호 작용함으로써 시스템이 동작

1) **Class**
👉 객체의 뼈대, 설계도, 생산틀의 역할
👉 class 내에 정의된 함수들은 클라스 내 정의된 변수들에게 접근 가능
👉 class 내에 정의된 변수 : Property
👉 class 내에 정의된 함수 : Method

2) Class의 **인스턴스** : 만들어진 클래스를 바탕으로 객체 생성

```
class Employee {
    fullName: string;
    age: number;
    jobTitle: string;
    hourlyRate: number;
    workingHoursPerWeek: number;

    printEmployeeDetails = (): void => {
        console.log(`${this.fullName}의 직업은 ${this.jobTitle}이고 일주일의 수입은
        ${this.hourlyRate * this.workingHoursPerWeek}달러 이다.`);
    }
}

// Class Instance
let employee1 = new Employee();
employee1.printEmployeeDetails();
```

11. Constructor (생성자), Access Modifiers (접근 제한자), Getter & Setter
1) **Constructor** : 객체를 생성할 때 호출되는 함수 (객체의 초기화 담당)
👉 객체 생성 시, Constructor에 정의된 parameter의 값이 arguments로 전달 되어야 함!

```
constructor(fullName: string, age: number, jobTitle: string,
hourlyRate:number, workingHoursPerWeek:number) {
	this.fullName = fullName;
	this.age = age;
	this.jobTitle = jobTitle;
	this.hourlyRate = hourlyRate;
	this.workingHoursPerWeek = workingHoursPerWeek;
}
```

2) **Access Modifiers** : 클라스 속 멤버 변수 (프로퍼티)와 메소드에 적용
👉 클라스 외부로부터의 접근을 통제 (버그 감소, 코드의 안정성 향상)

```
public 👉 클라스 외부 접근 O
private 👉 클라스 외부 접근 X
protected 👉 클라스 내부, 상속받은 자식 클라스에서 접근 O
❇️ public 키워드는 반드시 명시할 필요 없음 (기본 키워드)

예시)
private fullName: string;
```

3) **Getter & Setter**
👉 class 내에 get과 set 키워드 사용

```
private _변수이름 👉 비공개 변수임을 나타낼 때, 변수 앞에 _를 씀
```

```
get fullName() {
	return this._fullName;
}

set fullName(value: string) {
	this._fullName = value;
}

// 위의 getter와 setter 사용 예제
employee1.fullName = 'Henry'
console.log(employee1.fullName);
```

4) Constructor와 Access Modifiers
👉 객체 생성 시, constructor의 매개변수로 전달된 값이 객체의 프로퍼티 값으로 자동 초기화되고 할당됨

```
constructor(
	private _fullName: string,
	private _age: number,
	private _jobTitle: string,
	private _hourlyRate: number,
	public workingHoursPerWeek: number) {
}
```
