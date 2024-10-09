---
layout: single
title: Chapter 19 닷넷 API
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 닷넷 API에 대한 내용을 담고 있습니다.

>C#이 사용할 수 있는 API 집합체인 닷넷(닷넷 프레임워크와 닷넷 코어)에는 굉장히 많은 API가 있다.

# 1 닷넷 API 탐색기와 Docs

>마이크로소프트는 닷넷 API 탐색기를 제공하여 웹에서 모든 API 검색을 할 수 있다. 다음 URL에서 닷넷 API 탐색기를 실행할 수 있다. 

- https://docs.microsoft.com/en-us/dotnet/api/

# 2 클래스, 구조체, 열거형, 네임스페이스

>닷넷에서 제공하는 대부분의 API는 클래스이다. 그리고 구조체, 열거형이 있고, 이러한 클래스, 구조체, 열거형을 특정 이름으로 묶어 관리하는 네임스페이스가 있다.

- **클래스**(class)
	- Console 클래스, String 클래스 등 거의 대부분이 클래스이다.
- **구조체**(struct)
	- DateTime 구조체, TimeSpan 구조체 형태로 표현하며, 클래스와 거의 동일하게 사용한다.
- **열거형**(enumeration)
	- Color 열거형 등이 있으며, 특정 목록을 관리할 때 편리하다.
- **네임스페이스**(namespace)
	- System 네임스페이스처럼 많은 양의 클래스와 구조체, 열거형을 묶어서 관리하다.

# 3 Math 클래스 사용하기

>닷넷에서 제공하는 수학 관련 내장 클래스인 Math는 다음 기능들을 제공한다. 

- Math.E 
	- 자연 로그 상수 값 출력
- Math.PI
	- 원주율 출력
- Math.Abs()
	- 절댓값 출력
- Math.Max()
	- 최댓값 출력
- Math.Min()
	- 최솟값 출력
- Math.Pow()
	- 거듭제곱 출력
- Math.Ceiling() 메서드
	- 지정된 십진수보다 크거나 같은 정수 값 반환
		- Decimal 환경에서는 Decimal.Ceiling() 형태로 사용 가능
- Math.Floor() 메서드
	- 지정된 십진수보다 작거나 같은 최대 정수 값 반환
		- Decimal 환경에서는 Decimal.Floor() 형태로 사용 가능

>Math.E로는 자연 로그 상수를 출력할 수 있고, Math.PI로는 원주율을 출력할 수 있다.

```cs
> $"자연 로그 : {Math.E}"
"자연 로그 : 2.71828182845905"
> $"원주율(PI) : {Math.PI}"
"원주율(PI) : 3.14159265358979"
```

>Math.Abs()로 절댓값을 구한다.

```cs
> $"-10의 절댓값 : {Math.Abs(-10)}"
"-10의 절댓값 : 10"
```

>Math 클래스의 Max()와 Min() 메서드로 두 수 중에서 큰 값과 작은 값을 구할 수 있다.

```cs
> Math.Max(3, 5)
5
> Math.Min(3, 5)
3
```

>Math.Pow() 메서드는 거듭제곱을 구할 때 사용한다.

```cs
> $"거듭제곱 : 2의 10제곱 : {Math.Pow(2, 10)}"
"거듭제곱 : 2의 10제곱 : 1024"
```

>Math.Round() 메서드로는 특정 자리에서 반올림할 수 있다.

```cs
> $"3.15를 소수점 둘째자리에서 반올림 : {Math.Round(3.15, 1)}"
"3.15를 소수점 둘째자리에서 반올림 : 3.2"
```

>추가로 Math 클래스의 Round(), Ceiling(), Floor() 메서드를 사용하면 반올림, 올림, 내림을 쉽게 구할 수 있다.

```cs
> Math.Round(1.1F)
1
> Math.Ceiling(1.1F)
2
> Math.Floor(1.1F)
1
```

>다음 코드에서 Math 클래스의 Sqrt() 함수(메서드)는 9라는 값을 매개변수로 입력하면 무조건 3을 반환한다. 이러한 함수는 몇 번을 실행해도 매개변수가 동일하다면 같은 결과를 반환하기에 순수 함수(pure function)라고 한다.

```cs
> Math.Sqrt(9)
3
> Math.Sqrt(9)
3
```

>랜덤 값을 반환하는 Random 클래스의 Next() 메서드는 비순수 함수(impure function)라고 한다. 매개변수 없이 매번 실행할 때마다 서로 다른 값이 나오는 비순수 함수이다.

```cs
> (new Random()).Next()
1458067299
> (new Random()).Next()
1992359394
```

## 3.1 Math 클래스와 using static 구문 함께 사용하기

>Console 클래스와 마찬가지로 Math 클래스도 using static 구문을 사용하여 줄여서 표현할 수 있다. 

- UsingStaticClassesDemo.cs

```cs
using System;
using static System.Console;
using static System.Math;

class UsingStaticClassesDemo
{
    static void Main()
    {
        // (1) 기본 사용 방식
        WriteLine(Math.Pow(2, 10));

        // (2) using static 지시문으로 줄여서 표현
        WriteLine(Pow(2, 10));
        WriteLine(Max(3, 5));
    }
}

```

- 실행 결과

```cs
1024
1024
5
이 창을 닫으려면 아무 키나 누르세요...
```

>Console과 Math 클래스를 여러 번 사용한다면 using static 구문으로 생략하여 코드를 간결하게 유지할 수 있다.

# 4 클래스 또는 메서드 이름을 문자열로 가져오기 : nameof 연산자

>프로그래밍에서는 클래스 또는 메서드 이름 자체를 문자열로 사용할 필요가 있다. 이때는 nameof 연산자를 사용하여 문자열로 가져올 수 있다. nameof 연산자는 특정 변수, 메서드, 속성에 대한 이름 자체를 문자열로 가져올 때 사용한다. 단순하게 System 같은 네임스페이스를 "System" 형태의 문자열로 관리하기보다는 nameof(System)으로 관리하면, System을 다른 네임스페이스로 한꺼번에 변경하는 등 리팩터링 기능을 적용할 때 도움을 받을 수 있다.

>Console 클래스 또는 WriteLine() 메서드를 nameof() 연산자로 묶으면 문자열로 반환한다. 

```cs
> nameof(System)
"System"
> nameof(Console)
"Console"
> nameof(Console.WriteLine)
"WriteLine"
```

