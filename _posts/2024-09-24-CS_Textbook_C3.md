---
layout: single
title: Chapter 24 예외 처리하기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 예외 처리하기에 대한 내용을 담고 있습니다.

>예외 처리는 try~catch~finally와 throw를 사용한다.

# 1 예외와 예외 처리

>C# 프로그래밍에서 예외(exception)는 프로그래밍이 실행되는 동안 발생하는 에러(error)(오류)를 의미한다. 코드를 잘못 작성하거나 기타 다른 이유로 발생한 예외는 프로그램을 강제적으로 종료하거나 틀린 결과가 나오는 식으로 발생한다. 이러한 예외에 대한 대비로 예외 처리를 해야 한다.

>오류(에러)는 문법(컴파일) 오류, 런타임(실행) 오류, 알고리즘(논리) 오류 등으로 분류된다.

- **문법 오류**(syntax error)
	- 잘못된 명령어를 입력했거나 입력 실수로 발생하는 오류이다. 문법 오류는 컴파일 오류라고도 하며, 대부분 C# 컴파일러가 잡아 준다. 

- **런타임 오류**(runtime error)
	- 프로그램을 만든 후 실행할 때 발생하는 오류이다. 컴파일 과정에서는 발생하지 않고 실행할 때 발생하기에 많은 테스트를 진행하면서 잡을 수 있다.

- **알고리즘 오류**(logic error)
	- 주어진 문제에서 잘못된 해석으로 잘못된 결과를 초래하는 오류를 알고리즘 오류 또는 논리(로직) 오류라고 한다. 문법 오류나 런타임 오류는 쉽게 발견할 수 있다. 하지만 알고리즘 오류는 처리 결과가 틀렸는데도 알 수 없는 경우가 많기 때문에 가장 해결하기가 어렵다. 

# 2 try~catch~finally 구문

>C#에는 예외 처리를 위해 try, catch, finally 같은 세 가지 키워드가 준비되어 있다. try 블록은 혹시 모를 예외가 발생할 만한 구문을 묶어 주고, catch 블록은 예외가 발생했을 때 처리해야 하는 구문을 묶어 주며, finally 블록은 예외가 발생 또는 발생하지 않아도 마무리 관련 처리를 해야 할 구문을 묶어 주는 데 사용한다.

```cs
try
{
	// 예외가 발생할 만한 코드 작성
}
catch
{
	// 예외가 발생할 때 처리해야 할 코드 블록
}
finally
{
	// 예외가 발생하거나 정상일 때 모두 처리해야 할 코드 블록
}
```

## 2.1 try와 catch 구문으로 예외 처리하기

>C#에서는 try, catch, finally 같은 키워드를 사용하여 예외가 발생했을 때 그에 대한 처리를 담당하는 구문을 작성할 수 있다. 에러가 발생할 때 비정상적으로 종료되지 않고 정상적으로 종료시키려면 try~catch 구문을 사용한다. 

- TryCatch.cs

```cs
using System;

class TryCatch
{
    static void Main()
    {
        try
        {
            int[] arr = new int[2];
            arr[100] = 1234; // 예외(에러) 발생 : System.IndexOutOfRangeException
        }
        catch
        {
            Console.WriteLine("에러가 발생했습니다.");
        }
    }
}
```

- 실행 결과

```cs
에러가 발생했습니다.
```

>정수형 배열인 arr은 요소 2개를 담을 수 있다. 그런데 arr[100] 형태로 없는 인덱스에 값을 입력하면 예외가 발생한다. try로 묶인 코드 내에서 에러가 발생하면 catch 절이 실행된다. 앞 코드는 일부러 에러를 발생시킨 것으로, catch 절이 실행되는 것을 확인할 수 있다.

# 3 Exception 클래스로 예외 처리하기

>닷넷에서 모든 예외에 대해 처리할 주요 기능을 담아 놓은 클래스가 Exception이다. Exception 클래스의 주요 속성에는 Message가 있는데, 현재 예외 설명을 출력한다.

## 3.1 예외 처리 구문에 Exception 클래스 사용하기

- ExceptionDemo.cs

```cs
using System;

class ExceptionDemo
{
    static void Main()
    {
        try
        {
            int[] arr = new int[2];
            arr[100] = 1234;
        }
        catch (Exception ex) // ex 변수에는 상세한 예외 정보가 담김
        {
            Console.WriteLine(ex.Message);
        }
    }
}
```

- 실행 결과

```cs
Index was outside the bounds of the array.
```

>TryCatch.cs 내용과 동일한데 catch (Exception ex) 형태로 catch 절을 변경했다. 이렇게 하면 예외 내용을 Exception 클래스 형식의 변수인 ex에 담는다. Exception 클래스는 Message 속성으로 예외 내용을 알려준다.

>일반적으로 catch 절의 형태는 다음과 같이 e 또는 ex 변수로 사용한다.

- catch (Exception e)
- catch (Exception ex)

## 3.2 FormatException 클래스 형식의 예외받아 처리하기

>Exception 클래스와 마찬가지로 FormatException 같은 클래스들은 각각 고유의 예외가 발생했을 때 해당 예외 정보를 담고 있다. 다음 코드에서 inputNumber에 정수 문자열이 아닌 실수 문자열을 입력하면 Convert.ToInt32() 메서드는 FormatException 형태의 에러를 발생시킨다.

- FormatExceptionDemo.cs

```cs
using System;
using static System.Console;

class FormatExceptionDemo
{
    static void Main()
    {
        string inputNumber = "3.14";
        int number = 0;

        try
        {
            number = Convert.ToInt32(inputNumber);
            WriteLine($"입력한 값 : {number}");
        }
        catch (FormatException fe)
        {
            WriteLine($"에러 발생 : {fe.Message}");
            WriteLine($"{inputNumber}는 정수여야 합니다.");
        }
    }
}
```

- 실행 결과

```cs
에러 발생 : Input string was not in a correct format.
3.14는 정수여야 합니다.
```

>코드를 실행했더니 잘못된 값이 입력되어 FormatException 예외가 발생했고, 이를 catch 절에서 잡아 예외 처리했다.

## 3.3 간헐적으로 발생하는 예외 처리하기

>프로그램을 컴파일한 후 실행한다. 이때 런타임할 경우 try 절에서 발생한 예외를 catch 절에서 처리한다. 다음 프로그램은 DateTime.Now.Second API를 사용하여 현재 프로그램을 실행하는 시점의 초를 구해 온다. 구한 값이 짝수이면 (now % 2) 코드 부분이 0으로 되어 2 / 0; 형태가 된다. 모든 수는 0으로 나눌 수 없기에 이 부분에서 에러가 발생한다. 에러가 발생하면 catch 절이 실행되고 프로그램이 정상적으로 종료된다. 구한 초가 홀수라면 정상적으로 메시지가 출력되고, 프로그램도 정상적으로 종료된다.

- TryCatchDemo.cs

```cs
using System;

class TryCatchDemo
{
    static void Main()
    {
        try
        {
            int now = DateTime.Now.Second;
            Console.WriteLine($"[0] 현재 초 : {now}");

            // 실행 시간이 짝수이면 0으로 나누기에 에러 발생
            int result = 2 / (now % 2);
            Console.WriteLine("[1] 홀수 초에서는 정상 처리");
        }
        catch
        {
            Console.WriteLine("[2] 짝수 초에서는 런타임 에러 발생");
        }
    }
}
```

- 실행 결과
	- 실행시키는 시점에 초(Second)의 값이 홀수일 때

```cs
[0] 현재 초 : 5
[1] 홀수 초에서는 정상 처리
```

- 실행 결과
	- 실행시키는 시점에 초의 값이 짝수일 때

```cs
[0] 현재 초 : 50
[2] 짝수 초에서는 런타임 에러 발생
```

>이처럼 예외 처리 구문을 사용하면 런타임할 때 발생할지 모르는 예외에서도 예외 처리를 할 수 있다.

# 4 throw 구문으로 직접 예외 발생시키기

>C#에서 throw 구문은 이름에서도 알 수 있듯이 무엇인가를 던진다. 여기에서 무엇인가는 바로 인위적으로 예외(에러)를 발생시키는 것을 의미한다.

>try~catch~finally 구문과 함께 예외 처리를 할 때는 throw 구문을 사용할 수 있는데, throw는 무조건 특정 예외를 발생시킨다. throw 키워드 뒤에 특정 예외 관련 클래스(Exception, ArgumentException, ...)의 인스턴스를 넘겨주면 해당 예외를 직접 발생시킨다.

```cs
> throw new Exception();
System.Exception: 'System.Exception' 형식의 예외가 Throw되었습니다.
  + <Initialize>.MoveNext()
> throw new ArgumentException();
System.ArgumentException: 값이 예상 범위를 벗어났습니다.
```

## 4.1 throw 구문으로 무작정 에러 발생시키기

- TryFinallyDemo.cs

```cs
using System;

class TryFinallyDemo
{
    static void Main()
    {
        Console.WriteLine("[1] 시작");

        try // 예외가 발생할 만한 구문이 들어오는 곳
        {
            Console.WriteLine("[2] 실행");
            throw new Exception(); // 무작정 에러 발생
        }

        finally // 예외가 발생하든 하지 않든 간에 실행(마무리 영역)
        {
            Console.WriteLine("[3] 종료");
        }
    }
}
```

- 실행 결과

```cs
[1] 시작
[2] 실행
Unhandled exception. System.Exception: Exception of type 'System.Exception' was thrown.
   at TryFinallyDemo.Main() in C:\Users\User\source\repos\ConsoleApp1\Program.cs:line 12
[3] 종료
```

>다음 구문으로 try 절에서 무조건 에러가 발생한다.

```cs
> throw new Exception();
```

>이 구문은 다음 구문의 줄임 표현이다.

```cs
> Exception ex = new Exception();
> throw ex;
```

- ExceptionHandling.cs

```cs
using System;

class ExceptionHandling
{
    static void Main()
    {
        int a = 3;
        int b = 0;

        try
        {
            a = a / b; // (1) b가 0이므로 런타임 에러 발생
        }
        catch (Exception ex)
        {
            Console.WriteLine($"예외(에러)가 발생됨 : {ex.Message}");
        }
        finally
        {
            Console.WriteLine("try 구문을 정상 종료합니다.");
        }

        try
        {
            // (2) Exception 클래스에 에러 메시지를 지정하여 무조건 에러 발생
            throw new Exception("내가 만든 에러");
        }
        catch (Exception e)
        {
            Console.WriteLine($"예외(에러)가 발생됨 : {e.Message}");
        }
        finally
        {
            Console.WriteLine("try 구문을 정상 종료합니다.");
        }
    }
}
```

- 실행 결과

```cs
예외(에러)가 발생됨 : Attempted to divide by zero.
try 구문을 정상 종료합니다.
예외(에러)가 발생됨 : 내가 만든 에러
try 구문을 정상 종료합니다.
```

>예외 처리를 할 때는 try~catch~finally가 쌍을 하나 이룬다. catch 절은 Exception 클래스 같은 예외 형식을 다르게 하여 여러 번 지정할 수 있다. 특정 경우에 무조건 예외를 발생시키고자 할 때는 throw 절을 사용한다.
