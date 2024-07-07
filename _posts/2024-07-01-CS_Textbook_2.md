---
layout: single
title: Chapter 02 C# 프로그램 작성
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 C# 프로그램 작성에 대한 내용입니다.

# 1 프로그램 

## 1.1 비주얼 스튜디오

- Note
>비주얼 스튜디오 기반의 C# 프로그래밍 방식에서 가장 많이 사용되는 것은  크게 다음 세 가지이다.
	-  콘솔 앱 프로그램 
		- 명령 프롬프트(명령창, 터미널) 화면에서 실행되는 프로그램을 작성하는 방식으로 C# 프로그래밍 언어를 학습하는 데 주로 사용된다.
	- 윈도 응용 프로그램
		- 윈도 운영 체제에서 실행되는 윈도 기반의 프로그램을 작성할 때 사용한다.
	- 웹 응용 프로그램
		- 웹 사이트, 게시판, 쇼핑몰 같은 웹 기반 프로그램을 작성할 때 사용한다.


- Note
	- 프로젝트(project)
	>프로젝트란 프로그램 하나를 이루는 가장 작은 단위가 되는 프로그램을 의미한다. 비주얼 스튜디오에서 프로젝트는 확장자가 CSPROJ(C# 프로젝트를 의미)인 파일로, 관련된 여러 파일을 이름 하나로 묶는 역할을 한다.
	- 솔루션(solution)
	>솔루션이란 하나 이상의 프로젝트를 모아서 만든 프로그램이다. 비주얼 스튜디오에서 솔루션은 확장자가 SLN(솔루션의 약자)인 파일로 하나 이상의 프로젝트를 묶어서 관리할 때 사용한다.

>즉, 솔루션은 하나 이상의 프로젝트로, 프로젝트는 하나 이상의 C# 소스 파일로 구성된다. 프로젝트는 비주얼 스튜디오의 솔루션 탐색기(solution explorer)에서 표시된다.

- 프로젝트와 솔루션

![](https://i.imgur.com/AMngFi1.png)

- Note
>C# 파일은 HelloWorld.cs처럼 확장자가 CS인데, 컴파일 과정을 거치면 실행 가능한 EXE 파일을 생성한다(윈도우가 아닌 다른 환경이라면 DLL 파일을 생성한다). 

- Note
	- 라이브러리(Library)
	>라이브러리란 코드에서 반복되는 많은 기능들을 매번 다시 작성하는 것을 방지하기 위해, 로직을 따로 모아둔 파일이다. 즉, 표준화된 함수 및 데이터 타입을 모아 놓은 것이다. 라이브러리 파일을 포함시켜 주면 그 안에 함수들을 자유롭게 사용할 수 있어 작업 속도와 코드 신뢰성을 확보할 수 있다. 이러한 라이브러리를 크게 '정적 라이브러리(.lib)'와 '동적 라이브러리(.dll)'로 구분할 수 있으며 어떤 시점에 메인 프로그램에 연결되는가에 따라 구분된다고도 볼 수 있다.
	- 정적 라이브러리(.lib, Static Link Library)
	>정적 라이브러리는 컴파일 시점에 링커에 의해 메인 소스와 결합된다. 컴파일할 때, 해당 파일 내의 함수들이 복사되는 것이다. 정적 라이브러리를 이용하는 경우에는 만들어진 실행파일만 전달하면 되기에 배포작업이 쉽지만, 실행파일 크기는 라이브러리에 따라 커질 수 있다.
	- 동적 라이브러리(.dll, Dynamic Link Library)
	>동적 라이브러리는 컴파일 시점에 메인 코드와 결합되지 않는다. 프로그램을 실행하면 dll 파일을 필요할 때 호출한다. 그렇기에 실행파일과 dll 파일은 독립적으로 존재한다고 볼 수 있다. 실행파일 크기를 줄일 수 있지만(메모리를 절약할 수 있지만) dll 파일 위치에 유의하며 배포해야 한다. 

- C# 소스 코드 컴파일

![](https://i.imgur.com/Q3Ripib.png)

## 1.2 C# 인터렉티브

- C# 인터렉티브
>C# 인터렉티브(interactive)(대화형)란 한 줄씩 코드를 실행하면서 C#의 여러 명령을 학습할 수 있는 도구이다. 간단한 코드는 C# 인터렉티브를 사용한다.

```cs
> Console.WriteLine("필요한 소스만 화면에 표시");
필요한 소스만 화면에 표시
```

- 프로그램 작성 및 실행 단계

![](https://i.imgur.com/ez81MwJ.png)

- Note 
	- F5 
		- 디버깅 시작
	- Ctrl + F5 
		- 디버그하지 않고 시작
	- Ctrl + Shift + F 
		- 파일 찾기
	- Ctrl + S 
		- 현재 파일 저장
	- Ctrl + A 
		- 전체 선택
	- Ctrl + C 
		- 복사(copy)
	- Ctrl + V 
		- 붙여넣기(paste)
	- Ctrl + ; 
		- 솔루션 탐색기 열기
	- Ctrl + ,
		- 특정 파일 또는 클래스 찾기

# 2 C#의 기본 코드 구조

>C# 프로그램은 class와 Main() 메서드가 반드시 있어야 하고, 하나 이상의 문(statement)이 있어야 한다.

```cs
using System; // 네임스페이스 선언부

class ClassSimple
{ // 중괄호 사용 : 프로그램 범위를 그룹화
	static void Main(string[] args) // Main() 메서드
	{
		Console.WriteLine("Hello World!"); // 세미콜론 : 명령어의 끝
	}
}
```

>C#의 기본 코드는 위쪽에 네임스페이스 선언부와 Main() 메서드가 오고, 중괄호 시작과 끝을 사용하여 프로그램 범위를 구분한다.

- 네임스페이스
>자주 사용하는 네임스페이스를 위쪽에 미리 선언해 둘 수 있다.
- Main() 메서드 
>프로그램의 시작 지점이며, 반드시 있어야 한다.
- 중괄호({})
>프로그램 범위(스코프)를 구분 짓는다.
- 세미콜론(;)
>명령어(문, 문장)의 끝을 나타낸다.

## 2.1 using 키워드와 네임스페이스

>C#은 네임스페이스, 클래스, Main() 메서드로 구성된다.

- C#의 기본 코드 구조

![](https://i.imgur.com/XRUttcO.png)

>콘솔 화면에 문자열을 출력하려면 네임스페이스.클래스.메서드(); 형태로 사용해야 한다. 하지만 매번 네임스페이스를 입력하면 번거롭다. 이때 using 키워드를 사용하여 코드 위쪽에 using System;처럼 구문을 넣으면 네임스페이스를 생략하고 클래스.메서드(); 형태로 줄여서 쓸 수 있다. 즉, C#의 모든 명령문 체계는 다음과 같이 네임스페이스.클래스.메서드(); 형태이거나 네임스페이스를 제외한 클래스.메서드(); 형태로 주로 사용한다.

- 네임스페이스, 클래스, 메서드

![](https://i.imgur.com/ImhjTYh.png)

>예를 들어 다음 두 코드는 동일하다. 위쪽 코드는 네임스페이스.클래스.메서드(); 형태고, 아래쪽 코드는 네임스페이스를 using으로 선언했기 때문에 클래스.메서드(); 형태이다. 

```cs
// using을 사용하지 않는 코드 형태
class UsingDemo
{
	static void Main()
	{
		System.Console.WriteLine("Hello World");
	}
}
```

```cs
using System;

class UsingDemo
{
	static void Main()
	{
		Console.WriteLine("Hello World");
	}
}
```

## 2.2 using static 구문

>C# 6.0 버전 이후부터는 using static System.Console; 구문으로 System.Console을 생략한 WriteLine() 메서드만 사용할 수 있다. Console 클래스의 WriteLine() 메서드는 using static 구문으로 위쪽에 System.Console을 정의해 두면 WriteLine() 메서드만 호출해도 된다.

```cs
using static System.Console;

class WriteLineDemo
{
	static void Main()
	{
		WriteLine("명령 프롬프트에 출력할 내용");
	}
}
```

>다음과 같이 구문 2개를 동시에 위쪽에 둘 수도 있다.

```cs
using static System.Console;
using static System.Math;
```

- Note
	>정규화된 이름은 네임스페이스 이름과 형식 이름까지 전체를 지정하는 방식이다. 다음과 같이 네임스페이스.클래스.메서드(); 형태로 전체 이름을 다 지정하는 것을 정규화된 이름(fully qualified names)이라고 한다. 

```cs
System(네임스페이스).Console(클래스).WriteLine()(메서드);
```
>
>이 코드는 System 네임스페이스에 있는 Console 클래스의 WriteLine() 메서드를 사용하여 콘솔에 한 줄을 출력한다.

## 2.3 Main() 메서드 : 프로그램 진입점

>C# 기본 구조에서 반드시 사용되는 Main() 메서드는 프로그램의 시작점이다. 반드시 Main() 메서드가 있어야 하고 Main() 메서드에서 프로그램을 실행하고 종료한다.

- Main() 메서드 앞에 static 키워드가 있어 개체를 생성하지 않고 바로 클래스에 있는 Main() 메서드를 실행할 수 있다.
- Main() 메서드가 2개이면 "프로그램에 진입점이 2개 이상 정의되어 있습니다."라는 에러 메시지가 출력되어 프로그램이 컴파일되지 않는다.

- Note
>비주얼 스튜디오에서는 Main() 메서드에 대한 코드 조각을 제공한다. 비주얼 스튜디오에서 svm을 입력한 후 Tab을 두 번 누르면 자동으로 static void Main() {} 코드 블록을 작성한다. Console.WriteLine() 메서드도 cw를 입력한 후 Tab을 두 번 누르면 자동으로 Console.WriteLine(); 코드를 입력한다.

```cs
// svm + Tab Tab 입력
static void Main(string[] args)
{

}
```

```cs
// cw + Tab Tab 입력
Console.WriteLine();
```

## 2.4 중괄호 위치

>클래스와 Main() 메서드처럼 프로그램의 시작과 끝을 나타낼 때는 중괄호 열기({)와 닫기(})를 사용한다. 이때 중괄호 위치는 크게 두 가지 스타일로 사용할 수 있다.

>중괄호의 시작과 끝을 맞추는 Allman 스타일과 줄의 맨 마지막에 시작 중괄호를 넣는 K&R 스타일을 가장 많이 사용한다.

```cs
// Allman 스타일 : 시작과 끝을 맞추는 형태
class BraceLocation
{
	static void Main()
	{
		
	}
}
```

```cs
// K&R 스타일 : 줄의 맨 마지막에 시작 중괄호를 넣는 형태 
class BraceLocation {
	static void Main() {
	
	}
}
```

## 2.5 대 ○ 소문자 구분하기

>C#은 대 ○ 소문자를 구분한다. 예를 들어 Console.WriteLine("안녕하세요.")처럼 WriteLine() 메서드의 대 ○ 소문자를 정확히 입력하지 않으면 에러가 발생한다.

```cs
using system;

class casesensitive
{
	static void Main()
	{
		console.writeline("C#은 대소문자 구분 언어");
	}
}
```

>예제를 실행하면 다음 에러가 발생한다.

- CS0246 'system' 형식 또는 네임스페이스 이름을 찾을 수 없습니다. using 지시문 또는 어셈블리 참조가 있는지 확인하세요. 
	- System의 첫 글자를 소문자로 써서 발생했다.
- CS0103 'console' 이름이 현재 컨텍스트에 없습니다. 
	- Console의 첫 글자를 소문자로 써서 발생했다.

>System과 Console을 대문자로 변경한 후 다시 컴파일한다. 또 에러가 발생했다.

- CS5001 프로그램에는 진입점에 적합한 정적 'Main' 메서드가 포함되어 있지 않습니다.
	- Main의 첫 글자를 소문자로 써서 발생했다.
- CS0117 'Console'에는 'writeline'에 대한 정의가 포함되어 있지 않습니다.
	- WriteLine의 첫 글자를 소문자로 써서 발생했다.

>main()을 Main()으로 바꾸고 writeline을 WriteLine으로 바꾸어서 컴파일한다. 이제는 정상적으로 컴파일되고 잘 실행된다.

>완성된 코드 및 실행 결과는 다음과 같다.

- CaseSensitive.cs

```cs
using System;

class CaseSensitive
{
	static void Main()
	{
		Console.WriteLine("C#은 대소문자 구분 언어");
	}
}
```

- 실행 결과

```cs
C#은 대소문자 구분 언어
```

- Note
	>프로그램을 작성하는 단계는 일반적으로 다음 세 단계를 반복한다.
	- 1단계. 디자인 타임
		- 프로그램을 디자인하고 C#으로 코드를 작성하는 과정
		- 비주얼 스튜디오에서 프로젝트를 만들고 코드를 작성
	- 2단계. 컴파일 타임
		- 비주얼 스튜디오 같은 IDE를 사용하여 컴퓨터가 이애할 수 있도록 컴파일하는 과정
		- 비주얼 스튜디오에서 F5 또는 빌드(Ctrl + Shift + B)를 해서 소스 코드 컴파일
	- 3단계. 런타임
		- 작성한 프로그램이 잘 실행되는지 기기에서 테스트하는 과정
		- 비주얼 스튜디오에서 Ctrl + F5로 실행 테스트