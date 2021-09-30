# CMake

## 1. 개요
* * *
  Makefile을 통해 빌드과정의 반복성에 대한 문제를 해결할 수 있다. 그러나 Makefile을 사용하는 것에 큰 문제가 하나 있다. 바로 의존성이 바뀔 때마다 Makefile을 수정해야 한다는 것이다.
  
  CMake는 쉽게 말해 플랫폼에 독립적인 조건에서 Makefile을 만들어주는 개발 도구이다. 여기서 말하는 플랫폼에 독립적이라는 것은 개발 환경을 의미한다. 
  
  그럼 이제 CMake에 대해 자세히 알아본다.

## 2. 사용법
* * *
#### 2.1. CMake 전과정
  CMake는 아래의 그림과 같은 과정을 통해 빌드과정을 돕는다. 이때, CMake를 사용하기 위해 필요한 CMakeLists.txt 파일은 반드시 프로젝트 최상위 디렉토리에 존재해야 한다. CMakeLists.txt 파일을 생성한 후엔 CMake를 통해 Makefile을 생성한 뒤, Make를 이용하여 빌드를 진행한다.
  
![이미지1](../img/cmake_1.png)

  추가로 꼭 Make와 연동하여 빌드를 진행하지 않아도 된다. 원하는 빌드 프로그램을 선택하여 진행할 수 있다. 이와 관련된 내용은 필요하다면 추후에 포스팅하도록 한다. 
  
#### 2.2. CMakeLists.txt 파일 구조
  CMakeLists.txt 파일은 다음의 두 내용을 포함하고 있어야 한다. 
``` text
	# CMake 프로그램의 최소 버전
	cmake_minmum_required(VERSION 3.11)

	# set the project name and version
	project(Tutorial VERSION 1.0)
```
  
#### 2.3. CMake 예제


