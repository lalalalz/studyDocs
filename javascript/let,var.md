## 1. let과 var의 차이점

### 1.1.개요
--------------------------------------------------------------------------------

  javascript에서는 변수를 선언할 때 두 가지 방식을 지원한다. 

``` javascript
var myVariable_1 = 'something';
let myVariable_2 = 'something';
```

  두 방식은 마치 비슷한 것처럼 보이는데 둘의 차이점이 무엇인지 확인하고, 어떤 방식을 사용해야 할 지에 대해 공부해보고자 한다.

### 1.2. var 타입의 변수
--------------------------------------------------------------------------------
  MDN Docs 정의에 따르면 var 타입의 변수는 다음과 같은 특징들을 갖는다. *The var statement declares a function-scoped or globally-scoped variable* 즉, var 타입 변수의 스코프는 function 안에서는 지역변수로 function이 아닌 곳에서는 global 변수로 선언된다는 뜻이다.

``` javascript
	
	for(var varType = 0; varType < 5; ++varType) {
		console.log(varType);
	}
	// function 내부가 아닌 곳에서 선언된 var 타입 변수는
	// globally 하게 선언 처리되어 아래와 같이 실행될 수 있다.
	console.log("varType" : varType); // output => varType : 5
```

  또한, MDN Docs는 다음과 같은 특징들도 설명한다. *var declarations, where they occur, ar processed before any code is executed* 즉, 코드가 실행되기 이전에 var 타입 변수 선언은 처리된다는 뜻이다. 이것을 호이스팅이라고 하는데 호이스팅 특징을 이용하면 다음과 같은 코드도 가능하다.

``` javascript
	
	console.log(varType)  // output => undefined
	
	var varType = 1;
	
	console.log(varType)  // output => 1

```

이 뿐만 아니라 var 타입 변수는 여러번 선언이 가능하다. 다음 코드를 살펴보자.

``` javascript

	var varType = 1;
	// 중복 선언이 가능하다. 
	var varType = 2;
	
```

  이와 같은 특징들로 인해 var 타입의 변수는 오류를 발생시킬 가능성을 높일 수 있다. 

### 1.3. let 타입 변수
--------------------------------------------------------------------------------
  let 타입 변수는 var 타입 변수와는 다르게 block-level scoped 특징을 갖는다. 또한, 호이스팅이 안되는 것은 아니지만 변수를 선언하기 전에는 변수에 접근할 수가 없다는 특징을 갖으며, 중복 선언도 되지 않는다. 
  
``` javascript

	for(let letType = 0; letType < n; ++letType) {
		console.log('let Type : ', letType);
	}
	// error 발생
	console.log('let Type : ', letType);
	
	// error 발생
	console.log(letType_2);
	let letType_2 = 1;
	
	
	let letType_3 = 1;
	// error 발생
	let letType_3 = 2;

```
  이와 같은 특징들은 var 타입 변수와는 대조적이다. 따라서, var 타입의 변수보다는 오류를 발생시킬 가능성이 상대적으로 적다. 
  
### 1.4. 결론
--------------------------------------------------------------------------------
  결론적으로 var 타입의 변수보다는 let 타입의 변수를 사용하는 것이 오류를 발생시킬 가능성이 상대적으로 적기 때문에 let 타입 변수를 사용하는 것이 좋을 것이다. 물론, var 타입의 변수가 잘못된 것은 아니기에 개발자가 원한다면 사용하는 것은 문제가 되지 않는다. 그러나 나는 let 타입의 변수를 사용할 것이다. 