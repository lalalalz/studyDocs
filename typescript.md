# 타입스크립트 기본 문법

## 1. 타입스크립트란? 

### 1.1. 개요
--------------------------------------------------------------------------------
TypeScript는 JavaScript를 포함하는 상위 집합의 언어이다. 따라서 JavaScript의 모든 
기능을 지원한다. 여기에 타입을 부여하여 좀 더 타입과 관련된 에러 또는 버그를 줄일 수 
있도록 도와주는 언어이다. 

또한, 일반적으로 브라우저에서 TypeScript를 실행할 수 없기 때문에 JavaScript 파일로 
변환을 거쳐야만 한다. 

### 1.2. 참고

--------------------------------------------------------------------------------
https://www.typescriptlang.org/docs/handbook/intro.html

## 2. 타입 

### 2.1. 종류
--------------------------------------------------------------------------------
TypeScript에서 사용되는 Type들은 다음과 같다. 

``` markdown
- Boolean
- Number
- String
- Object
- Array
- Tuple
- Enum
- Any
- Void
- Null 
- Undefined
- Never
```

### 2.2. 타입 명시하기
--------------------------------------------------------------------------------
변수명 뒤에 콜론과 함께 타입명을 기재하면 해당 타입만을 갖는 변수로 설정할 수 있다. 
만약, 해당 타입과 다른 값이 입력되면 에러를 발생시킨다. 

``` typescript

    let numberValue:Number;

    numberValue = 1;                    //ok
    numberValue = 'how you like that?'  //error

```

### 2.3. Boolean
--------------------------------------------------------------------------------
타입이 true or false인 경우에 사용된다.

``` typescript
    
    let booleanType:Boolean; 

    booleanType = true;  //ok
    booleanType = 1      //error

```

### 2.4. Number
--------------------------------------------------------------------------------
타입이 숫자인 경우에 사용된다.

``` typescript
    
    let numberType:Number; 

    numberType = 1;                    //ok
    numberType = 'how you like that?'  //error

```

### 2.5. String
--------------------------------------------------------------------------------
타입이 문자열인 경우에 사용된다.

``` typescript
    
    let stringType:String; 

    stringType = "this type is a string";  //ok
    stringType = 1                         //error

```

### 2.6. Object
--------------------------------------------------------------------------------
타입이 객체인 경우에 사용된다. 여러 타입의 상위 타입이기 때문에 유용하지 않다.
또한, 객체 속성들에 대한 타입을 개별적으로 지정하거나 아예 지정을 하지 않아야 한다. 

``` typescript
    
    let objectType:Object; 

    booleanType = { };              //ok
    booleanType = { name: 'ab' }   //error  객체 속성들에 대한 정의가 없기 때문에

    let objectType2:{ name:String } = { name: 'lalalalz' } //ok

```

### 2.7. Array
--------------------------------------------------------------------------------
타입이 배열인 경우 사용된다. 해당 배열에 원소값들의 타입을 지정해 주어야 한다. 

``` typescript
    
    // 둘 다 가능!!
    let arrayType:Array<number>; 
    let arrayType:Number[];

    arrayType = [1,2,3]   //ok
    arrayType = ['a',1,2] //error

```

### 2.8. Tuple
--------------------------------------------------------------------------------
튜플은 배열의 길이가 고정되고 각 요소의 타입이 지정되어 있는 배열을 의미한다. 
타입이 튜플인 경우 사용되며, 각 원소값에 대한 타입이 다를 수 있다. 

``` typescript
    
    let tupleType:[String, Number]; 

    tupleType = ['a', 1];  //ok
    tupleType = [1, 'a'];  //error

    tupleType[0].toUpperCase()  //ok
    tupleType[1].toUpperCase()  //error

```

### 2.9. Enum
--------------------------------------------------------------------------------
Enum은 특정 상수들의 집합을 의미한다. 타입이 Enum인 경우에 사용되며, 기본값을 지정하지
않으면 1부터 시작된다. 기본값을 지정한 이후에는 기본값부터 1씩 증가되어 기본값이 설정
된다.

추가로 숫자로 default 값을 설정하면 양방향 포팅이 된다. 

``` typescript
    
    enum OS {
        WINDOW,  //1
        IOS,     //2
        ANDROID  //3
    }

    OS[0]         //'WINDOW'
    OS['WINDOW']  //0
    

    enum AVENGERS {
        CAPTAIN,  //1
        THOR = 10 //10
        HULK      //11
    }

```

### 2.10. Any
--------------------------------------------------------------------------------
모든 타입을 허용할 때 사용된다. 

``` typescript
    
    let anyType:any = 1; //ok
    anyType = 'string'   //ok
    anyType = {}         //ok

```

### 2.11. Function
--------------------------------------------------------------------------------
타입이 Function일 때 사용되며, 파라미터와 반환값에 대한 타입을 설정할 수 있다. 

``` typescript
    
    function sum(a:Number, b:Number):Number {
        return a + b;
    }

    sum(1, 2)   //ok
    sum('a', 2) //error

```

### 2.12. void
--------------------------------------------------------------------------------
타입이 void인 경우에 사용된다. 리턴값이 없는 함수에서 사용된다. 반환값이 void로 설정
되면, undefined를 반환한다. 또한, undefined, null이 할당할 변수에 사용된다. 

``` typescript

    function sum(a:Number, b:Number):void {
        return a + b;
    }

    console.log(sum(1,2)) //error => undefined

```

### 2.13. never
--------------------------------------------------------------------------------
함수의 끝에 절대 도달하지 않는다는 의미를 지닌 타입이며, never 타입인 경우에 사용된다.
추가로 error를 thorw 하는 함수에서 사용된다.

``` typescript

    function infLoop():never {
        while(true) {
            // do something
        }
    }

```

## 3. Type Aliases

### 3.1. 개요
--------------------------------------------------------------------------------
쉽게 말해, 타입에 별칭을 붙여주는 것이다. 별칭이 붙여지면 사용자가 정의한 임의의 타입
을 동일한 이름(별칭)으로 여러번 사용할 수 있게 해주는 좋은 기능이다. 

``` typescript

    type Point = {
        x : number;
        y : number;
    }

    let a:Point = { 1, 2 };
    let b:Point = { 3, 4 };


    type A = string | number;

    let c:A = 'a';
    let d:A = 1;

```

### 3.2. 사용법
--------------------------------------------------------------------------------
type 키워드와 해당 type의 이름을 적은 후 어떤 타입이든 정의해주면 된다. 

``` typescript

    type A = string | number;

    type B = {
        x : A;
        b : A;
    }

```


## 4. interface

### 4.1. 개요
--------------------------------------------------------------------------------
TypeScript 공식 사이트 문서에 따르면 interface는 다음과 같이 정의되어 있다. 
*"An interface declaration is another way to name an object type"*. 즉, *객체* 타
입의 이름을 지정하는 또 다른 방법이다. 


### 4.2. 타입 지정과 interface 간의 차이점
--------------------------------------------------------------------------------
공식 문서에 따르면 *"the key distinction is that a type cannot be re-opened to 
add new properties vs an interface which is always extendable"*라고 쓰여져 있다. 

``` typescript

    interface Animal {
        name : string
    }

    interface Animal {
        nameOfAnimal : string
    }
    
    //ok

    type Animal = {
        name : string
    }

    type Window = {
        nameOfAnimal : string
    }

    // error

```

