---
layout: single
title: Chapter 07 사용자한테 얻은 정보를 변수에 저장하기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 사용자한테 얻은 정보를 변수에 저장하기에 대한 내용입니다.

>프로그램을 실행할 때마다 서로 다른 값을 입력받으려면 콘솔에서 입력한 값을 변수에 저장할 수 있어야 한다. 

- 표준 입출력(standard input/output)
	- 키보드로 입력받고 모니터로 출력하는 일반적인 내용

# 1 문자열 입력 관련 메서드 

>Console 클래스로는 사용자가 콘솔에서 데이터를 입력받고 이를 다시 콘솔 화면에 출력할 수 있다. 지금까지 콘솔에 데이터를 출력할 때는 Console.Write() 또는 Console.WriteLine() 메서드를 사용했다. 사용자에게서 콘솔로 데이터를 입력받을 때는 다음 메서드를 주로 사용한다.

- ConsoleReadLine()
	- 콘솔에서 한 줄을 입력받는다. 또 콘솔 앱 프로그램에는 현재 시점에서 잠시 멈추는 기능이 있어 Enter를 누를 때까지 대기한다. 

- Console.Read()
	- 콘솔에서 한 문자를 정수로 입력받는다. 

- Console.ReadKey()
	- 콘솔에서 다음 문자나 사용자가 누른 기능 키를 가져온다. 

>Console.ReadLine() 메서드는 콘솔에 대기하고 있다 사용자가 한 줄을 입력한 후 Enter를 누르면 해당 문자열을 입력받아 그 결괏값을 반환한다.

## 1.1 Console.ReadLine() 메서드 사용하기 

>Console.ReadLine() 같은 입력 메서드는 C# 인터렉티브에서는 사용할 수 없다.

- ReadLineDemo.cs

```cs
using System;

class ReadLineDemo
{
    static void Main()
    {
        Console.ReadLine(); // <- 이 시점에서 대기하는 효과
    }
}
```

>실행하면 다음과 같이 콘솔 화면에서 대기한다. Console.ReadLine() 메서드가 실행되고 프로그램을 종료한다.

![](https://i.imgur.com/RyC0V0T.png)

>콘솔에서 아무 문자열이나 입력한 후 Enter를 누르면 그 값이 그대로 출력된다.

- ConsoleReadLineDemo.cs

```cs
using System;

class ConsoleReadLineDemo
{
    static void Main()
    {
        Console.WriteLine(Console.ReadLine());
    }
}
```

>프로그램을 실행한 후 한 줄을 입력받고 Enter를 누르면 입력한 문자열이 그대로 출력된다. "안녕하세요." 문자열을 입력하면 이 값을 입력받아 Console.WriteLine() 메서드로 다음과 같이 출력한다. 

![](https://i.imgur.com/tZwglwO.jpeg)

- InputName.cs

```cs
using System;

class InputName
{
    static void Main()
    {
        Console.Write("이름을 입력하시오 => "); // (1) "이름을 입력하시오" 출력
        string name = Console.ReadLine(); // (2) 입력받은 문자열을 name 변수에 저장
        Console.WriteLine("안녕하세요. {0}님.", name); // (3) name 변수 값을 {0}에 출력
    }
}
```

- 실행 결과

```cs
이름을 입력하시오 => 김은총
안녕하세요. 김은총님.
```

>실행한 후 '김은총'을 입력하면 다음과 같이 입력받은 값을 출력한다.

![](https://i.imgur.com/UMr6zb8.png)

>코드에서 (1)은 단순히 화면에 문자열을 출력하는 역할을 한다.

>(2)에서 Console.ReadLine() 메서드는 콘솔에서 Enter를 누를 때까지 문자열을 입력받는 기능을 제공한다. string 형 변수인 name에는 Console.ReadLine() 메서드로 입력한 문자열을 저장한다.

## 1.2 Console.Read() 메서드 사용하기

>Console.Read() 메서드를 사용하면 콘솔에서 문자를 하나만 입력받을 수 있다. 입력 값은 문자에 해당하는 정수로 변환된다. 정수에 해당하는 문자를 출력할 때는 Convert.ToChar() 메서드를 사용한다. 

- ConsoleReadDemo.cs

```cs
using System;

class ConsoleReadDemo
{
    static void Main()
    {
        int x = Console.Read(); // (1) 콘솔에서 문자 하나를 입력한 후 [Enter]
        Console.WriteLine(x); // (2) A를 입력했다면 A에 해당하는 정수 값 65 출력
        Console.WriteLine(Convert.ToChar(x)); // (3) 65에 해당하는 유니코드 문자 출력
    }
}
```

- 실행 결과

```cs
A
65
A
```

>실행하면 Console.Read() 메서드를 사용하여 콘솔에서 문자 하나를 입력받는다. 이렇게 입력된 문자는 정수형 변수로 변환된다. 예를 들어 A를 입력하면 아스키코드가 65를 저장한다. 다시 65에 해당하는 문자를 표현하려면 Convert.ToChar() 메서드로 묶어 준다.

# 2 형식 변환

>Console.ReadLine() 메서드를 사용하여 콘솔에서 입력받은 데이터는 문자열이다. 문자열 대신 정수나 실수 데이터를 입력받고 싶다면 입력된 문자열을 원하는 데이터 형식으로 변환할 수 있어야 한다. 

>같은 형식의 데이터끼리는 따로 형식 변환(type conversion)을 하지 않아도 그대로 값이 대입된다.

```cs
> int number1 = 1234; // 정수 1234를 number1 변수에 저장 
> int number2 = number1; // number1 값을 다시 number2 변수에 저장
> number2
1234
```

## 2.1 암시적 형 변환과 명시적 형 변환

>형식 변환은 크게 암시적(implicit)(묵시적) 형 변환과 명시적(explicit) 형 변환으로 구분할 수 있다. 암시적 형 변환은 변환 형식이 안전하게 유지되며 데이터가 손실되지 않아 특수한 구문이 필요 없다. 예를 들어 숫자 형식 중 int 형식은 그보다 더 큰 long 형식 변수에 그대로 담을 수 있다.

```cs
> int number1 = 1234;
> long number2 = (int)number1; // number1 값을 그보다 큰 long 형식 변수인 number2에 저장
> number2
1234
```

