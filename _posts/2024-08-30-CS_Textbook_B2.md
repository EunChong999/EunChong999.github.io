---
layout: single
title: "Chapter 13 조건문 : switch 문으로 다양한 조건 처리하기"
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 switch 문으로 다양한 조건 처리하기에 대한 내용을 담고 있습니다.

>선택문(switch와 case, default 키워드를 사용하여 다양한 조건 처리)인 switch 문은 값에 따라 다양한 제어를 처리할 수 있다. 다중 if 문을 사용할 때 조건을 처리할 내용이 많다면 switch 문을 대신 사용할 수 있다. 

# 1 switch 문 소개

>switch 문의 형태는 다음과 같다. 표현식 값이 값1~값n 중 하나와 일치하면 해당 실행문을 실행하고, 일치하지 않으면 default 실행문을 실행한다.

```cs
switch (표현식)
{
	case 값1: 실행문1; break;
	case 값2: 실행문2; break;
	...
	case 값n: 실행문n; break;
	default: 실행문; break;
}
```

>즉, 표현식의 결괏값이 '값1'이면 '실행문1'을 수행하고, '값2'이면 '실행문2'를 수행하는 식으로 표현식에 맞는 실행문을 수행한다.

>switch 문에는 추가로 case와 default 키워드가 사용되는데, 이를 case와 default 레이블이라고 한다. case 레이블에는 상수(값)가 들어오고, default 레이블은 생략 가능하다.

# 2 switch 문 사용하기

- SwitchExpression.cs

```cs
using System;

class SwitchExpression
{
    static void Main()
    {
        int x = 2;

        switch (x)
        {
            case 1:
                Console.WriteLine("1입니다."); // x가 1일 때 실행
                break;
            case 2:
                Console.WriteLine("2입니다."); // x가 2일 때 실행
                break;
        }
    }
}
```

- 실행 결과

```cs
2입니다.
```

>x 변수 값을 1로 두면 "1입니다."가 출력되고, x 변수 값을 2로 두면 "2입니다."가 출력된다. 1과 2 이외의 값을 지정하면 현재 switch 문은 아무것도 출력하지 않는다. 객관식 문제에서 하나를 선택하는 유형을 처리할 때는 이와 같은 switch 문이 유용하다.

## 2.1 입력한 값에 따른 출력 구문을 switch 문으로 선택하기

>다음은 사용자에게 정수를 입력받은 후 값이 1, 2, 3일 때는 그에 해당하는 문자열을 출력하고, 나머지 정수는 default 레이블에서 지정한 문자열을 출력하도록 하는 예제이다. 

- Switch.cs

```cs
using System;

class Switch
{
    static void Main()
    {
        Console.WriteLine("정수를 입력하세요.");
        int answer = Convert.ToInt32(Console.ReadLine());

        // 선택문
        switch(answer)
        {
            case 1:
                Console.WriteLine("1을 선택했습니다.");
                break;
            case 2:
                Console.WriteLine("2를 선택했습니다.");
                break;
            case 3:
                Console.WriteLine("3을 선택했습니다.");
                break;
            default:
                Console.WriteLine("그냥 찍으셨군요.");
                break;
        }
    }
}
```

- 실행 결과

```cs
정수를 입력하세요.
3
3을 선택했습니다.
```

>원하는 값을 입력하면 그에 해당하는 문자열을 출력하는 것을 확인할 수 있다.

## 2.2 좋아하는 프로그래밍 언어 선택하기

>가장 좋아하는 프로그래밍 언어를 물어보는 프로그램을 다음과 같이 switch 문을 사용하여 만들 수 있다. 

- SwitchStatement.cs

```cs
using System;
using static System.Console;

class SwitchStatement
{
    static void Main()
    {
        WriteLine("가장 좋아하는 프로그래밍 언어는? ");
        Write("1. C\t");
        Write("2. C++\t");
        Write("3. C#\t");
        Write("4. Java\n");

        int choice = Convert.ToInt32(ReadLine());

        switch (choice)
        {
            case 1:
                WriteLine("C 선택");
                break;
            case 2:
                WriteLine("C++ 선택");
                break;
            case 3:
                WriteLine("C# 선택");
                break;
            case 4:
                WriteLine("Java 선택");
                break;
            default:
                WriteLine("C, C++, C#, Java가 아니군요.");
                break;
        }
    }
}
```

- 실행 결과

```cs
가장 좋아하는 프로그래밍 언어는?
1. C    2. C++  3. C#   4. Java
3
C# 선택
```

## 2.3 switch 문을 사용하여 오늘 날씨 물어보기

- SwitchWeather.cs

```cs
using System;

class SwitchWeather
{
    static void Main()
    {
        Console.WriteLine("오늘 날씨는 어떤가요? (맑음, 흐림, 비, 눈, ...");
        string weather = Console.ReadLine();

        switch (weather)
        {
            case "맑음":
                Console.WriteLine("오늘 날씨는 맑군요.");
                break;
            case "흐림":
                Console.WriteLine("오늘 날씨는 흐리군요.");
                break;
            case "비":
                Console.WriteLine("오늘 날씨는 비가 오는군요.");
                break;
            default:
                Console.WriteLine("혹시 눈이 내리나요?");
                break;
        }
    }
}
```

- 실행 결과

```cs
오늘 날씨는 어떤가요? (맑음, 흐림, 비, 눈, ...
맑음
오늘 날씨는 맑군요.
```

>이 예제처럼 case 레이블에 문자열로 값을 비교하는 것도 가능하다.