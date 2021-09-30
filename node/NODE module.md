# Node.js Module

## 1.  모듈

### 1.1. Node.js 모듈
--------------------------------------------------------------------------------
  자바스크립트는 한정적인 용도로 만들어져 복수의 JavaScript 파일을 로드할 경우 하나의 파일로 merge되어 동일한 유효범위를 갖는다. 이때, *파일과 일대일 매핑되며 독립적인 실행 영역(Scope)를 가질 수 있게 모듈*이라는 기능을 추가하여 JavaScript를 범용적으로 사용할 수 있게 했다. 

  이때, 모듈 시스템 표준으로 제안된 것이 CommonJS와 AMD(Asynchronous Module Definition)이였는데 사실상 Node.js는 CommonJS를 채택하여 기본적으로 CommonJS 방식을 따르고 있다. 

  한편, ES6에서는 Client-Side JavaScript에서도 동작하는 모듈 기능을 추가하였는데 해당 모듈에 대한 키워드는 익히 알고 있는 export와 import이다. 반면에 CommonJS 방식은 require 함수와 exports, module.export를 사용한다. 

### 1.2. 모듈 내보내기
--------------------------------------------------------------------------------
  위에서 언급했듯이 Node.js는 모듈 시스템이 적용되어 있다. 그리고 각 모듈은 파일과 일대일 매핑되며, 독자적인 실행 영역을 갖게 된다. 이때, 해당 모듈을 외부에서도 참조할 수 있도록 해주는 기능을 모듈 내보내기 기능이라고 한다. 다음을 통해 ES6와 CommonJS 방식 모듈 내보내기를 알아보자. 

#### 1.2.1. exports - CommonJS
  외부에 공개할 대상을 **exports 객체**의 프로퍼티 또는 메소드를 정의한다. 

``` javascript

	exports.PI = Math.PI;
	exports.square = function (x) {
		return x * x;
	}
	
```

#### 1.2.2. module.export - CommonJS
  exports 객체는 프로퍼티 또는 메소드를 여러개 정의할 수 있지만, **module.exports 객체**에는 하나만 가능하다. 그렇다면 module.exports와 exports는 무엇이 다른 것일까?

  공식문서에 따르면 exports 객체와 module.exports는 서로 참조하는 객체이며, module.exports의 shortcut에 불과하다. 그러나 항상 export(내보내기)되는 것은 module.exports이다. 추가로 module은 해당 파일(모듈) 객체를 가르키는 참조 변수이다. 

``` javascript

	module.exports = {
		PI: Math.PI;
		square: function (x) {
			return x * x;
		}
	}

```
#### 1.2.3. export - ES6
  외부에 공개하고 싶은 대상앞에 **export 키워드**를 붙여주고, 여러 개를 export 할 수 있다.

``` javascript

	export PI = Math.PI;
	
	export function square(x) {
		return x * x;
	}
	
	export class Person {
		constructor(name) {
			this.name = name;
		}
	}

```

### 1.3. 모듈 가져오기 
--------------------------------------------------------------------------------
  위에서 모듈 내보내기에 대해 알아보았다. 그렇다면 내보내진 모듈을 가져와 참조하는 방법에 대해 알아보자. 


#### 1.3.1. require - CommonJS
  일반적으로 module.export로 내보내진 모듈을 가져올 때 require 전역 함수를 사용한다. 그러나 모듈(파일)뿐만 아니라 디렉터리를 지정할 수도 있다. 그리고 디렉터리에 포함된 index.js 파일을 찾아 로드한다. 

``` code

	project/
	|_________mymodule.js
	|_________mydirectory/
			  |_________index.js
			  |_________another.js
			  
	
```

``` javascript

	// 1. 모듈을 지정하여 가져올 때
	const MyModule = require('./mymodule.js');
	
	// 2. 디렉터리를 지정하여 가져올 때
	const MyModule = require('./mydirectory);

```

#### 1.3.2. import - ES6
  require와 동일한 목적을 가지고 있지만, Babel과 같은 ES6 코드를 변환해주는 도구를 사용할 수 있을 때만 사용할 수 있다. 

``` javascript

	import Module from 'module';
	import { prop1, prop2 } as Module from 'module';

```

### 1.4. 요약
--------------------------------------------------------------------------------

1. CommonJS
	* module.exports : 한개만 내보내기
	* exports : 여러개 내보내기 
	* module.exports와 exports는 서로 참조
	* require : 가져오기, 디렉토리 일 경우에는 index.js 파일을 로드함.

2. ES6
	* export : 여러개 내보내기
	* import : 가져오기
	* transpiler가 필요함
