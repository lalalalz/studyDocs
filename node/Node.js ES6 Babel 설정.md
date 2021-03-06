# Node.js ES6 Babel 설정하기

## 1. 개요

### 1.1.  Babel이란?
--------------------------------------------------------------------------------
  바벨이란 무엇일까? 공식 문서에 따르면 바벨은 다음과 같이 정의되어 있다. *Babel is a JavaScript Compiler*. 즉, 바벨은 자바스크립트 컴파일러다. 좀 더 정확히는 ECMAScript 2015+ 코드를 현재 브라우저 또는 환경에 호환이 가능한 코드로 변환해주는 역할을 하는 자바스크립트 컴파일러이다. 

### 1.2. Node.js와 Babel
--------------------------------------------------------------------------------
  노드 공식 문서에 따르면 어떤 노드가 어떤 ECMAScript 기능을 지원하는지 파악할 수 있다고 나와있다. 이말은 노드 버전에 따라 지원하는 자바스크립트가 다를 수 있음을 의미한다. 이 때, 바벨을 이용하면 쉽게 버전 호환성을 해결할 수 있다. 

### 1.3. 설정방법
--------------------------------------------------------------------------------
  다음은 바벨을 설치하고 설정하는 방법이다. 해당 자료는 바벨 공식 홈페이지를 참고하였으며, 일반적인 설치 및 설정방법에 해당한다. 추가적으로 알고싶다면, [바벨 공식 홈페이지 - Usage Guide](https://babeljs.io/docs/en/usage)를 이용하자.

#### 1.3.1. 설치
  다음 명령어를 통해 바벨을 설치하자.

``` bash
	
	npm install --save-dev @babel/core @babel/cli @babel/preset-env @babel/node 

```

각 모듈에 대해 더 알고 싶다면 [공식홈페이지](https://babeljs.io/docs/en/usage) 링크를 이용하자.

#### 1.3.2. 설정
  다음 *.babelrc* 파일을 프로젝트 최상위 디렉토리에 추가하거나,

``` javascript
	
	{
		"presets": ["@babel/env"],
	}

```

프로젝트 최상위 디렉토리에 포함된 *package.json* 파일에 바벨 설정을 추가하여 설정을 할 수 있다.

``` javascript

	{
		"babel": {
			"presets": ["@babel/env"],
		}
	}

```

#### 1.3.3. 실행
  다음 명령어를 통해 바벨 컴파일 후 노드를 실행할 수 있다.

``` bash

	$ npx babel-node index.js
	This is the result of index file execution
	
```