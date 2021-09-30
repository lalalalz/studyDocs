# Node.js   TypeScript 개발 설정

## 1. 설정 방법

### 1.1. 개요
--------------------------------------------------------------------------------
  타입스크립트로 개발된 코드는 JavaScript Runtime 환경인 Node.js에서 실행할 수 없다. 따라서, TypeScript로 개발된 코드를 JavaScript 코드로 변환하여 Node.js에서 실행하여야 한다. 그럼 TypeScript Compiler를 설치하는 방법에 대해 알아보자. 


### 1.2. 컴파일러 설치 및 설정
--------------------------------------------------------------------------------
  TypeScript Compiler 설치를 위해 Node.js가 설치되어 있어야 한다. Node.js의 설치가 끝나면, 다음 명령어를 실행하여 TypeScript Compiler를 설치하자.

``` bash

	npm install typescript --save-dev

```

  위 명령을 통해 컴파일러 설치를 완료했다면, 다음 명령어를 통해 TypeScript 설정 파일을 생성하자..

``` bash

	tsc --init // 루트 폴더에 tsconfig.json 파일 생성!

```

  다음은 루트 폴더에 포함된 TypeScript 파일들을 컴파일하는 명령어다.

``` bash

	npx tsc // 루트 폴더에 포함된 모든 TypeScript 파일들을 컴파일한다..

```

위 명령어를 통해 컴파일된 결과물들은 위에서 설정한 outDir에 저장된다. 

### 1.3. ts-node
--------------------------------------------------------------------------------
  ts-node는 Node.js를 위한 TypeScript 실행 엔진이다. 해당 엔진은 타입스크립트를 자바스크립트로 자동으로 변환하여 타입스크립트를 즉시 Node.js에서 실행될 수 있게 해준다. 즉, 알아서 컴파일하여 node로 실행시켜주는 엔진이다. 해당 엔진은 다음 명령어를 통해 설치할 수 있다.

``` bash

	npm install -D ts-node

```

  설치가 완료되면 다음 명령어를 통해 작성한 타입스크립트를 실행시킬 수 있다. 

``` bash

	npx ts-node ./src/'YourTypeScriptFile or YourTypeScriptModule' 

```

### 1.4. 타입스크립트 설정
--------------------------------------------------------------------------------
  [1.2.]에서 *tsc-init* 명령으로 생성된 타입스크립트 설정 파일을 확인하면 다음과 같은 화면이 보일 것이다. 해당 파일의 *compilerOptions* 속성값 수정을 통해 TypeScript 설정을 할 수 있다. 다음은 타입스크립트 설정 파일 화면이다. 

![이미지1](../img/typescript_설정_1.png)

  각 옵션들은 주석을 통해 설명이 되어 있다. 해당 설명을 읽고, 본인에게 필요하다면 해당 옵션을 설정하면 된다. 다음은 일반적으로 많이 사용되는 옵션들을 나열한 것이다.

``` typescript

	"compilerOptions": {
        "strict": true,
        "module": "commonjs",
        "moduleResolution": "node",
        "lib": ["es2015","es2016","es2017","es2018","es2019","es2020"],
        "target": "ES5",
        "outDir": "./dist",
        "esModuleInterop": true
    }

```

  마지막으로 위 옵션 중 *outDir* 옵션에 대해 짚고 넘어가자. 해당 옵션에 대해 간단히 설명하자면, 컴파일 결과를 저장할 디렉토리의 주소를 지정하는 옵션이며, 지정된 디렉토리에 *npx tsc* 명령의 결과들이 저장된다.  