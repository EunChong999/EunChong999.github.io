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

