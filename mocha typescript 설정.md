# MOCHA & Typescript 설정

## 1. 설정 방법

### 1.1. 타입스크립트 설치
--------------------------------------------------------------------------------
  먼저 타입스크립트를 설치해보자. 타입스크립트 설치방법은 [여기](./Node.js Typescript 설정.md)를 참조하자. 설치가 완료됐다면 tsconfig 파일의 exclude 속성값을 아래와 같이 추가한다.

``` javascript

/* tsconfig.json */
{
  "compilerOptions": {
  	...
  },
  "exclude": [
    "node_modules",
    "**/*.spec.ts"
  ]
}

```

### 1.2. 모카 설치
--------------------------------------------------------------------------------
  다음 명령어를 이용하여 mocha를 설치한다.

``` terminal

	$ npm install mocha @types/mocha --dev

```

### 1.3. ts-node 설치
--------------------------------------------------------------------------------
  다음 명령어를 이용하여 ts-node를 설치하여 메모리상에서 타입스크립트를 트랜스 파일링하여 실행할 수 있게 해준다.  

``` terminal

	$ npm install ts-node --dev

```

  설치가 완료됐다면, 다음과 같이 package.json 파일의 test script를 추가한다.

``` javascript

	"script" : {
		"test": npx mocha test/**/*.ts -r ts-node/register
	}

```

  test script를 자세히 보면 mocha의 -r 옵션을 통해 ts-node를 require하는 것을 볼 수 있다. 이렇게 하면 컴파일 뒤에 자동으로 실행이 된다. 

