# Code  Style  Guide _ Javascript 

## 1. 개요

### 1.1. 개요
--------------------------------------------------------------------------------
  이번 글은 *Google JavaScript Style Guide* 를 참고하여 만
  든 글이다.  웬만하면 모든 내용을 따르지만 조금은 불편하
  고 가독성이 떨어진다고 판단되는 내용은 조금은 변형해서 
  작성하였다.. 

  이 글을 통해 일관되고 효율적인 Javascript Style을 익히고, 
  그것을 통해 협업에 기반이 될 수 있도록 하는 것이 가장 큰 
  목표이다. 

  마지막으로 해당 글은 *Google JavaScript Style Guide* 의 
  모든 내용을 포함하지는 않을 것이며 꼭 필요한 내용과 기본
  이 되는 내용만을 포함할 것이다.

  만약, 여기에 설명되지 않거나 빠져있는 내용은 모두 *Google
  JavaScript Style Guide* 를 참고하도록 한다. 


### 1.2. 참고
--------------------------------------------------------------------------------
* https://google.github.io/styleguide/jsguide.html 



## 2. Source File basics

### 2.1. File name
--------------------------------------------------------------------------------
  파일 이름은 모두 lowercase, underscores, dash를 조합하여 
  작성.

  공백은 포함하지 않으며, 영어로만 작성한다. 

``` javascript

main.js          //good
server_db.js     //good
server_router.js //good

Main.js          //bad
serverDB.js		 //bad
SERVER_ROUTER.js //bad

```

### 2.2. File encoding
--------------------------------------------------------------------------------
  소스 파일은 UTF-8로 인코딩한다.

## 3. Formatting

### 3.1. Braces
--------------------------------------------------------------------------------
  중괄호는 빈블록이 아닐 경우, K&R style을 따르도록 하며, 
  모든 제어문에 포함시킨다. 심지어 제어문이  단일 문장이
  여도 포함되어야 한다. 그리고 첫문장은 새 줄에  작성되어
  야 한다. 

  또한, 제어문이 아무것도 없는 빈 블록인 경우에는 중괄호
  를  연후에 줄바꿈 없이 바로 닫도록 한다. 

  예외적으로 단순한 if 문은 줄바꿈없이 작성해도 좋다. 단, 가
  독성이 좋아지는 경우에만 해당한다.   

  * 중괄호를 열기 전에 하나의 공백을 추가한다.
  * 중괄호를 열기 전에 줄바꿈을 하지 않는다.
  * 줄괄호를 연 후에 줄바꿈을 한다.
  * 중괄호를 닫기 전에 줄바꿈을 한다.
  * 중괄호를 닫은 후에 줄바꿈을 한다. 
  * 빈 블록일 경우엔 중괄호를 한줄에서 열고 닫는다.

``` javascript

/////////////////////////////////////good
if(someVeryLongCondition())  doSomething(); 

/////////////////////////////////////bad
if(someVeryLongCondition())
	doSomething();
	
/////////////////////////////////////good
for (let i = 0; i < foo.length; i++) {
	bar(foo[i]);
}

/////////////////////////////////////bad
for (let i = 0; i < foo.length; i++) bar(foo[i]);

/////////////////////////////////////good
try {
	doSomeThing();
} 
catch(error) {
    console.log(error)
}

/////////////////////////////////////bad
try {
	doSomeThing();
} catch(error) {
	console.log(error);
}

/////////////////////////////////////good
function doSomeThing() {}

/////////////////////////////////////bad
function doSomeThing() {
}

```

### 3.2. indentation
--------------------------------------------------------------------------------
  모든 Block이 시작될 때 공백 4칸을 추가한다. 또한, Block
  이 끝날 때는 동일한 indent level을 갖도록 한다.

  코드 뿐만 아니라, 코드에 딸려 있는 주석도 동일하게 적용
  되며, 추가적으로 배열, 객체, 클래스 등도 해당 규칙을 따를
  수 있다.

``` javascript

	//good
	if (condition) {
1234
12345678if(condition2) {
		1234doSomeThing();
12345678}
1234}

	//bad
1234if (condition) {
1234doSomeThing();	
1}

	//good
1234let myArray = [1, 2, 3]
	
	//good(optional)
1234let myArray = [
12345678a,
12345678b,
12345678c
1234];
	
	//bad
1234let myArray = [
1234a,
1234b,
1234c,
1234];
	
```

### 3.3 Stetements
--------------------------------------------------------------------------------
  모든 문장은 한줄에 한 문장씩 작성하며, 세미콜론을 꼭 포
  함시킨다. 

``` javascript

	//good
	doSomeThing();
	doSomeThing2();

	//bad
	doSomeThing(); doSomeThing2();
	
	//good
	

```

### 3.4. Column limit
--------------------------------------------------------------------------------
  모든 문장은 최대 80칸을 넘지 않도록 작성한다. 예외적으
  로 클릭이 필용한 URL, copy & paste가 필요한 긴 문자열,
  shell command, module import 등은 80칸을 넘는 것을 허용한다. 

  80칸을 실제로 dash 또는 slash로 표현한 뒤에 해당 규칙을
  지킬 수 있도록 하자.

``` javascript
-------------------------------------------------------------------------------- (80개)
let myString = `abjaskldfjl;kasjdfklasjdlkfjaslk;djfklsjdfkljsl;djaflsjd;fljas;l
	fjkdsaf;ljdsalkfjdsalkfjlksa;djflkasjdfjsa;ldjf;saljd;lfjsa;ldf`
 
```


### 3.5. Line-wrapping
--------------------------------------------------------------------------------
  줄바꿈은 주로 80칸 규칙을 지키기 위해 사용되며, 계속
  진행되는 문장은 줄을 바꾼 이후에 4칸을 띄운다. 

``` javascript
	
	currentEstimate = 
		calc(currentEstimate + x * x currentEstimate) / 
			2.0
```

### 3.6. Whitespace
--------------------------------------------------------------------------------
  공백은 다음과 같은 상황에서 사용된다.

  * 예약어 (function, super는 제외)와 열린 괄호 사이
  * 열린 중괄호 앞에 (함수의 첫번째 인자가 객체 또는 배열 안에 첫번째 객체)
  * 진수 연산자 양쪽
  * 컴마 또는 세미콜론 후에
  * 객체 리터럴에서 콜론 앞뒤
  * double slash(//, comment) 후에

### 3.7. Alignment
--------------------------------------------------------------------------------
  수평 정렬은 꼭 요구되지는 않지만, 필요하다면 규칙을 허
  용한다. 만약, 규칙을 허용한다면 필요한 whitespace는 허
  용한다.

``` javascript
	
	// ok
	{
        tiny 	: 1234;
        longger : 1235;	
	}
	
	// ok
	{
        tiny : 1234;
        longger : 1235;
	}

```

### 3.8. Function arguments
--------------------------------------------------------------------------------
  함수 파라미터는 웬만하면 함수 이름과 같은 라인에 기재
  한다. 만약, 80칸 규칙을 위배하면 줄바꿈을 통해 규칙을 
  준수할 수 있다. 줄을 바꾼 이후에는 상위 indent levet + 4
  칸의 공백을 추가한다. 

  또는, 각 파라미터를 한줄에 하나씩 배치하는 방법도 허용
  한다. 

``` javascript
	
	// good
	doSomething(parmeter1, parameter2 parameter3);
	
	// good
	doSomething(parameter1, parameter2,
		parameter3, parameter4, parmeter5);

	// good
	doSomething(
		parameter1,
		parameter2,
		parameter3,
	)

```

### 3.8. Comments
--------------------------------------------------------------------------------
  주석은 다음과 같이 두가지 방식을 허용한다. double slash
  를 이용하는 경우에는 double slash 이후에 한칸 띄우고 코
  멘트를 작성한다. 

  block comment를 이용하는 경우에는 slash가 포함된 줄은 
  비우고, 에스터리스크( * ) 앞에서 한칸 띄운 뒤 작성한다.

``` javascript
	
	// comment
	
	/* comment
	 * comment
	 * comment
	 */

```

  파라미터에  주석하는 경우는 block comment를 이용하
  고,  comment 앞 뒤로 한 칸씩 띄운다.

``` javascript

	someFunction(parameter1, /* comment parameterName = */ true );

```

## 4. Naming

### 4.1. Rules common to all Identifiers
--------------------------------------------------------------------------------
  변수 또는 식별자는 오직 ASCII와 숫자를 이용하여 네이밍
  하도록 한다. 또한, 불분명하고 익숙치 않은 약어는 네이밍
  에 포함하지 않도록 하고, 최대한 서술하는 형태의 네이밍
  을 하도록 한다. 

``` javascript

	// good
	errorCount
	dnsConnectionIndex
	customerId
	
	// bad
	n
	nErr
	nCompConns
	cstmrId
```

### 4.2. Rules by identifier type
--------------------------------------------------------------------------------
  변수 또는 식별자는 다음 형태로 네이밍하도록 한다. 

  

| 변수 또는 식별자   | 작성 타입 | 비고 |
| ---------------- | --------- | ---- |
| Package names | lowerCamelCase |      |
| Class names | UpperCamelCase | nouns or noun phrases |
| Method names | lowerCamelCase | verbs or verb phrases |
|  |  | private인 경우 끝에 trailing underscores(_)를 붙여준다. (getter, setter 제외) |
| Enum names | UpperCamelCase | singular nouns |
|                  |           | Individual items는 CONSTANT_CASE |
| Constant names | CONSTANT_CASE | 모두 대문자로 표시하며, 단어는 underscores로 구분한다. |
|                  |           | private인 경우에도 trailing underscores 처리를 하지 않아도 된다. (private를 명시하기 때문) |
| | | const 키워드를 사용한다고 모두 CONSTANT_CASE를 사용하는 것이 아니다. 실제 상수인 것만 해당한다. |
| Non-constant names | lowerCamelCase | nonus or nonu phrases |
|                  |           | private인 경우 끝에 trailing underscores를 붙여준다. |
| Parameter names | lowerCamelCase | 한 글자로 paramter를 선언하지 않아야 한다. |
| Local variable names | lowerCamelCase | 함수 내 상수 역시 lowerCamleCase를 사용한다. |
| Template paramter names | loserCamelCase |  |
| Module-local names | UpperCamelCase | export 되지 않는 모듈은 private 처리를 따로 하지 않아도 된다.(underscores) |


## 5. Language features

### 5.1. Local variable declarations
--------------------------------------------------------------------------------
  지역 변수 선언은 다음과 같은 사항들을 준수한다.

  * const, let으로 선언하라.
  * 한줄에 하나의 선언만 하라.
  * 선언후엔 반드시 초기화하라.

### 5.2. Array literals
--------------------------------------------------------------------------------
  마지막 원소와 닫는 대괄호가 줄바꿈 형태로 선언될 때 마
  지막에 컴마를 포함하라.

``` javascript
	
	const values = [
		'first value',
		'second value',
	]

```

### 5.3. Object literals
--------------------------------------------------------------------------------
  객체 리터럴은 다음과 같은 사항을 준수한다.

  * 마지막 원소와 닫는 대괄호가 줄바꿈 형태로 선언될 때 마지막에 컴마를 포함하라.
  * Object constructor를 사용하지 말고 { } 형태로 선언하라.
  * key는 작은 따옴표를 포함하거나 포함하지 않거나 섞어 사용하지 말아라.
  * 

### 5.4. Classes
--------------------------------------------------------------------------------
  클래스는 다음과 같은 사항을 준수한다.

  * constructor 내부에서 모든 필드를 초기화 한다. 
  * private 필드는 trailing underscore 처리를 한다.
  * 필드는 절대로 prototype에 설정하지 않는다.
  * static method는 base 클래스에서만 호출할 수 있다.
  * static method는 웬만하면 module-local 함수로 정의한다.
  * getter와 setter는 꼭 필요한 경우가 아니라면 사용하지 않도록 한다.
  * getter와 setter 대신 일반적인 method를 사용하라.

### 5.5. Function
--------------------------------------------------------------------------------
  함수는 다음과 같은 사항을 준수한다. 

  * Top-level 함수는 바로 exports 객체로 정의될 수 있다. 
  * 중첩 함수는 화살표 함수를 선호한다. 
  * 파라미터와 리턴 타입은 JSDoc을 통해 주석을 단다.

``` javascript

	exports.processString = (str) => {
		// Process the string
	}

	const processString = (str) => {
		// Process the string
	};
	
	exports = {processString};
	
```


### 5.6. String literals
--------------------------------------------------------------------------------
  문자열은 다음과 같은 사항을 준수한다.

  * 작은 따옴표만을 이용한다. 
  * 필요한 경우 template literal을 이용한다. ( ` ` )
  * line continuations을 사용하지 않는다.
  * 

### 5.7 Number literals
--------------------------------------------------------------------------------
  숫자는 다음과 같은 사항을 준수한다. 

  * 2진수, 8진수, 16진수 등은 꼭 prefix를  사용하고, lowercase 형태로 선언한다. 

``` javascript
	
	let number1 = 0x15;
	let number2 = 0b11;
	let number3 = 0o44;

```

### 5.8. Control structures
--------------------------------------------------------------------------------
  ES6 문법에는 서로 다른 세 종류의 for 문이 존재한다. 웬
  만하면 for - of 구문을 사용하도록 한다. 만약, dict-style 객
  체인 경우라면 for - in 구문을 허용한다. 그러나 가능하다면
  for - of와 Object.key를 이용하는 것을 선호한다. 

``` javascript

	// good perfered
	for(let ket of myObject) {
		console.log(myObject.key);
	}
	
	// ok if dict-style object
	for(let prop in myObject) {
		console.log(prop);
	}

```

### 5.9. Eqauality Checks
--------------------------------------------------------------------------------
  일반적으로 === or !== 연산자를 사용하라. 단 예외적으로
  다음과 같은 경우에는 == or !== 를 사용해도 좋다.

``` javascript
	
	if(someObjectOrPrimitive == null) {
		// Checking for null catches both null
		// and undefined for objects and primitives.
	}

```

### 5.11. Disallowed features
--------------------------------------------------------------------------------
  다음 사항들은 사용하지 않는다.

  *  with
  *  dval
  *  automatic semicolon insertion
  *  non-standard features
  *  never use new on the primitives object

