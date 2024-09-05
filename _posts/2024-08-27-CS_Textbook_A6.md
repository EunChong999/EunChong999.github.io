---
layout: single
title: Chapter 07 사용자한테 얻은 정보를 변수에 저장하기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 사용자한테 얻은 정보를 변수에 저장하기에 대한 내용을 담고 있습니다.

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

>하지만 반대로 long 형식의 변수를 int 형식의 변수에 저장하려면 다음 샘플 코드처럼 명시적으로 (int)를 붙여 long을 int로 변경해야 한다. 명시적 형 변환은 캐스팅(casting)이라고도 한다.

```cs
> long number1 = 1234;
> int number2 = (int)number1; // long 형식의 변수를 int 형식의 변수로 변환해서 저장
> number2
1234
```

>이 경우에는 데이터가 손실되어 엉뚱한 데이터가 저장될 수도 있다. 

- TypeConversionError.cs

```cs
using System;

class TypeConversionError
{
    static void Main()
    {
        long l = long.MaxValue; // (1) long 형식 변수의 가장 큰 값을 l 변수에 저장
        Console.WriteLine($"l의 값 : {l}");
        int i = (int)l; // (2) l 변수 값을 int 형식으로 변환하여 i 변수에 저장
        Console.WriteLine($"i의 값 : {i}");
    }
}
```

- 실행 결과

```cs
l의 값 : 9223372036854775807
i의 값 : -1
```

>(int) 표현식을 사용하여 long 형식의 변수를 int 형식의 변수로 변환했다. 다만 int 형식 변수의 크기를 벗어나는 데이터를 저장하면 잘못된 데이터가 저장될 수 있으니 주의해야 한다. 

>마찬가지로 정수 형식을 담을 수 있는 int 형식의 변수 값을 0~255만 담을 수 있는 정수 형식 변수인 byte에 담을 때는 (byte)를 붙여야 한다. 값이 255 이상이라면 잘못된 데이터가 저장되니 주의해야 한다. 다음은 int를 byte로 변환하는 예제이다.

- IntToByte.cs

```cs
using System;

class IntToByte
{
    static void Main()
    {
        int x = 255;
        byte y = (byte)x;

        Console.WriteLine($"{x} -> {y}"); // 보간된 문자열을 사용하여 x와 y의 값 출력
    }
}
```

- 실행 결과

```cs
255 -> 255
```

## 2.2 Convert 클래스를 사용하여 형식 바꾸기

>데이터 형식 변환은 괄호 기호 이외에 Convert 클래스의 주요 메서드도 사용할 수 있다.

- Convert 클래스의 주요 메서드

| 메서드                | 설명                        |
| ------------------ | ------------------------- |
| Convert.ToString() | 숫자 데이터 형식을 문자열로 변경        |
| Convert.ToInt32()  | 숫자 데이터 형식을 정수 형식으로 변경     |
| Convert.ToDouble() | 숫자 데이터 형식을 실수 형식으로 변경     |
| Convert.ToChar()   | 입력받은 숫자 또는 문자열 하나를 문자로 변경 |

>예를 들어 숫자 데이터 형식을 문자열로 변경하고 싶다면 Convert.ToString() 메서드를 사용한다. 다음은 정수형 변수 a를 선언한 후 문자열로 변경하여 문자열 변수 b에 대입하는 샘플 코드이다.

```cs
int a = 1234;
string b = Convert.ToString(a);
```

- TypeConversion.cs

```cs
using System;

class TypeConversion
{
    static void Main()
    {
        double d = 12.34;
        int i = 1234;

        d = i; // 큰 그릇에 작은 그릇의 값을 저장
        Console.WriteLine("암시적 형식 변환 = " + d);

        d = 12.34;
        i = (int)d; // () 사용 : 정수형 데이터만 저장됨
        Console.WriteLine("명시적 형식 변환 = " + i);

        string s = "";
        s = Convert.ToString(d);
        Console.WriteLine("형식 변환 = " + s);
    }
}
```

- 실행 결과

```cs
암시적 형식 변환 = 1234
명시적 형식 변환 = 12
형식 변환 = 12.34
```

>Convert.ToInt32()는 int.Parse() 메서드로, Convert.ToDouble()은 double.Parse() 메서드로 대체해서 사용할 수도 있다. 

## 2.3 정수 형식으로 변환하는 세 가지 방법 

>정수 형태의 문자열을 정수 형식으로 변환하는 세 가지 방법은 다음 샘플 코드와 같다.

```cs
> string strNumber = "1234";
> int number1 = Convert.ToInt32(strNumber);
> $"{number1} - {number1.GetType()}"
"1234 - System.Int32"
> int number2 = int.Parse(strNumber);
> $"{number2} - {number2.GetType()}"
"1234 - System.Int32"
> int number3 = Int32.Parse(strNumber);
> $"{number3} - {number3.GetType()}"
"1234 - System.Int32"
```

>코드의 GetType() 메서드는 닷넷에서 제공하고, 이를 사용하면 모든 값의 데이터 형식을 알 수 있다.

- GetTypeDemo.cs

```cs
using System;

class GetTypeDemo
{
    static void Main()
    {
        int i = 1234;
        string s = "안녕하세요.";
        char c = 'A';
        double d = 3.14;
        object o = new object(); // 개체 : 개체를 생성하는 구문

        Console.WriteLine(i.GetType());
        Console.WriteLine(s.GetType());
        Console.WriteLine(c.GetType());
        Console.WriteLine(d.GetType());
        Console.WriteLine(o.GetType());
    }
}
```

- 실행 결과

```cs
System.Int32
System.String
System.Char
System.Double
System.Object
```

>모든 변수에 GetType() 메서드를 요청하면 해당 변수의 닷넷 데이터 형식을 알려준다. object o = new Object(); 형태의 코드는 모든 데이터 형식을 담을 수 있는 그릇을 만드는 작업이다. 즉, 개체를 생성하는 작업이다. 

## 2.4 여러 가지 형식으로 변환하기 

- ReadLineInteger.cs

```cs
using System;

class ReadLineInteger
{
    static void Main()
    {
        Console.Write("정수를 입력하세요 : ");
        string input = Console.ReadLine(); // 문자열 입력
        int number = Convert.ToInt32(input); // 정수로 형식 변환
        Console.WriteLine($"{number}-{number.GetType()}");
    }
}
```

- 실행 결과

```cs
정수를 입력하세요 : 10
10-System.Int32
```

>Console.ReadLine() 메서드의 결괏값은 문자열이기에 이를 정수형으로 변경하려면 Convert 클래스의 Int32() 메서드로 묶어 준다. 정수형으로 변경할 수 없는 문자열이 들어올 때는 다음 에러가 발생한다. 

```cs
> Convert.ToInt32("Hello");
System.FormatException: 입력 문자열의 형식이 잘못되었습니다.
```

- ReadLineRealNumber.cs

```cs
using System;

class ReadLineRealNumber
{
    static void Main()
    {
        Console.Write("실수를 입력하세요 : ");
        string input = Console.ReadLine(); // 실수 입력
        double PI = Convert.ToDouble(input); // 실수로 변환
        Console.WriteLine(PI);
    }
}
```

- 실행 결과

```cs
실수를 입력하세요 : 3.14
3.14
```

>Console.ReadLine()으로 입력받은 실수 형태의 문자열을 실제 실수 데이터 형식으로 변경할 때는 Convert.ToDouble() 메서드로 묶어 주면 된다. 실수 데이터 형식을 입력받을 때는 ToDouble() 메서드 이외에 ToSingle()과 ToDecimal()도 사용할 수 있다.

>문자열 및 숫자 이외에 문자 하나만 입력받을 수도 있다. 참고로 이 예제는 문자 하나 이상을 입력하면 에러가 발생한다.

- ReadLineCharacter.cs

```cs
using System;

class ReadLineCharacter
{
    static void Main()
    {
        Console.Write("문자를 입력하세요 : ");
        string input  = Console.ReadLine(); // 문자열 입력 
        char c = Convert.ToChar(input); // 문자로 변환
        Console.WriteLine(c);
    }
}
```

- 실행 결과 

```cs
문자를 입력하세요 : 가
가
```

# 3 이진수 다루기 

>우리가 평소에 사용하는 숫자 체계는 십진수이다. 컴퓨터에서는 이진수를 사용한다. 그래서 컴퓨터가 숫자를 인식하게 하려면 십진수를 이진수로 변환해야 한다. C#에서는 컴퓨터에서 사용하는 숫자 체계인 이진수를 표현할 때 다음 방식을 사용한다.

```cs
Convert.ToString(숫자, 2)
```

>Convert 클래스의 ToString() 메서드는 특정 숫자의 값을 문자열로 변환할 수 있다. 정수 값을 이진수 문자열로 얻고 싶다면 Convert.ToString(정수, 2); 형태로 두 번째 옵션에 이진수를 나타내는 2를 지정한다.

```cs
> Convert.ToString(10, 2)
"1010"
> Convert.ToString(5, 2)
"101"
```

>이때 이진수의 결괏값이 0010이라면 앞에 00이 생략된 10까지만 출력된다. 그래서 보통 비트 연산식은 이해하기 편하게 여덟 자리로 잡고, 00000010 형태로 이진수로 출력할 때는 Convert.ToString() 뒤에 한 번 더 PadLeft() 메서드를 사용해서 8칸을 기준으로 이진수 문자열을 출력하고 앞부분은 0으로 채운다. 

```cs
Convert.ToString(숫자, 2).PadLeft(8, '0');
```

>예를 들어 다음과 같이 사용할 수 있다.

```cs
> Convert.ToString(5, 2).PadLeft(4, '0')
"0101"
```

- BinaryString.cs

```cs
using System;

class BinaryString
{
    static void Main()
    {
        byte x = 10; // 0000 1010

        Console.WriteLine(
            $"십진수 : {x} -> 이진수 : {Convert.ToString(x, 2).PadLeft(8, '0')}");
    }
```

- 실행 결과

```cs
십진수 : 10 -> 이진수 : 00001010
```

- Note 

>십진수를 이진수로 또는 이진수를 십진수로 변환시키는 것을 진법 변환이라고 하는데 C#에서는  Convert 클래스의 ToString()과 ToInt32() 메서드를 사용하여 변환이 가능하다. 

- RadixTransformation.cs

```cs
using System;

class RadixTransformation
{
    static void Main()
    {
        Console.WriteLine($"십진수 10을 이진수로 변경 : {Convert.ToString(10, 2)}");
        Console.WriteLine($"이진수 1010을 십진수로 변경 : {Convert.ToInt32("1010", 2)}");
    }
}
```

- 실행 결과

```cs
십진수 10을 이진수로 변경 : 1010
이진수 1010을 십진수로 변경 : 10
```

## 3.1 이진수 리터럴 

>정수 앞에 숫자 0과 영문자 b를 붙이는 0b 또는 0B 접두사를 붙여 특별한 과정 없이 바로 이진수로 표현할 수 있다. 0b0010처럼 표현하면 이진수 0010이 된다. 

```cs
> byte b1 = 0b0010; // 이진수 0010 -> 십진수 2
> byte b2 = 0B1100; // 이진수 1100 -> 십진수 12
> $"십진수 : {b1}" // 컴퓨터에서는 자동으로 십진수 단위로 처리함
"십진수 : 2"
> $"십진수 : {b2}"
"십진수 : 12"
```

>프로그램 소스 코드에서는 기본적으로 십진수 단위로 자료가 처리된다. 하지만 컴퓨터가 사용하는 이진수를 표현할 때는 0b와 0B 접두사를 두고 이진수 리터럴로 표현한다. 

## 3.2 언더스코어(\_) 문자로 숫자 구분하기

>현실 세계에서는 100만을 숫자 1.000.000 형태로 세 자리마다 콤마를 넣어 쉽게 구분할 수 있게 한다. 프로그램 소스 코드에서는 콤마 기호를 사용할 수 없는 대신 밑줄 문자인 언더스코어 (\_)를 사용하여 구분할 수 있다.

>이진수, 십진수, 16진수 등을 표현할 때는 언더스코어(\_) 문자를 사용하여 숫자를 구분할 수 있다. 언더스코어(\_) 문자는 1개 이상(또는 여러 개) 사용할 수 있다. 긴 숫자를 표현할 때 숫자 구분자를 두면 가독성이 높아진다.

```cs
> int bin = 0b0001_0001; // 0001 0001
> bin
17
> int dec = 1_000_000; // 1,000,000
> dec
1000000
> int hex = 0xA0_B0_C0; // A0 B0 C0
> hex
10531008
```

>0b 접두사는 이진수 리터럴을 나타낸다. 현실 세계에서 1,000,000처럼 구분자가 있는 숫자는 1_000_000처럼 표현할 수 있다. 0x를 접두사로 붙여 16진수를 표현할 수 있는데, 16진수도 언더스코어(\_) 문자를 구분자로 둘 수 있다.

# 4 var 키워드로 암시적으로 형식화된 로컬 변수 만들기

>변수를 선언할 때 int, string 등 기본 제공 키워드 대신 var 키워드를 사용하면 입력되는 값에 따라 자동으로 형식이 결정된다. C#에서 var는 매우 강력한 형식이다. C# 컴파일러는 var로 선언된 변수에 저장되는 값을 자동으로 추론해서 적당한 형식으로 변환하는데, 이 기능을 형식 추론(type interface)이라고 한다.

```cs
> int number = 1234; // 명시적으로 형식화된(explicit typing)
> var number = 1234; // 암시적으로 형식화된(implicit typing)
```

- Var.cs

```cs
using System;

class Var
{
    static void Main()
    {
        var name = "C#"; // string 형식으로 변환함
        Console.WriteLine(name);

        var version = 8.0; // double 형식으로 변환함
        Console.WriteLine("{0:0.0}", version);
    }
}
```

- 실행 결과

```cs
C#
8.0
```

>var 키워드로 선언된 변수에 문자열이 들어오면 자동으로 string 형식으로 선언된다. 마찬가지로 실수형 데이터가 저장되면 double 형식의 변수가 만들어진다. 

>var 키워드로 선언된 변수의 데이터 형식을 확인할 수도 있다. 다음 샘플 코드처럼 모든 변수에 GetType() 메서드를 요청하면 해당 변수의 데이터 형식을 알려준다.

```cs
> var number = 1234; // = int number
> number.GetType()
[System.Int32]
> var message = "안녕하세요."; // = string message;
> message.GetType()
[System.String]
```

- Note

>자바스크립트 같은 다른 프로그래밍 언어를 알고 있다면 var 키워드가 모든 값을 담고 있어 C#도 동일하다고 오해하곤 한다. 하지만 C#의 var 키워드는 프로그램 소스 코드 작성의 편의성을 위해 만든 키워드이지 모든 값을 다 담을 수 있는 키워드가 아니다. 자바스크립트의 var에 해당하는 C# 키워드는 dynamic이다. 

## 4.1 Console.ReadLine() 메서드의 입력 값을 var로 선언한 변수로 받기

>콘솔에서 사용자가 입력하는 값을 var로 선언된 변수에 담아 사용할 수도 있다.

- VarInput.cs

```cs
using System;

class VarInput
{
    static void Main()
    {
        var s = Console.ReadLine(); // 문자열 입력받기
        var c = Convert.ToChar(Console.Read()); // 문자 하나 입력받기
        Console.WriteLine($"{s} : {s.GetType()}, {c} : {c.GetType()}");
    }
}
```

- 실행 결과

```cs
Hello
C
Hello : System.String, C : System.Char
```

>Console.ReadLine() 메서드의 반환값은 string 형식인 것을 알기에 s 변수는 자동으로 string 형식의 변수가 된다. 마찬가지로 Convert.ToChar() 메서드의 반환값은 char 형식이기에 c 변수의 형식은 자동으로 char 형식이 된다. 

- Note 

>다음 코드는 Console.ReadKey() 메서드를 사용하여 키보드에서 입력한 키 값을 알아낸다. ConsoleKeyInfo 구조체와 ConsoleKey 열거형을 사용했다. 

- KeyboardInput

```cs
using System;

class KeyboardInput
{
    static void Main()
    {
        Console.WriteLine("아무키나 누르세요.");
        ConsoleKeyInfo cki = Console.ReadKey(true); // 키보드 키 값 입력
        Console.WriteLine("{0}", cki.Key); // 키
        Console.WriteLine("{0}", cki.KeyChar); // 유니코드
        Console.WriteLine("{0}", cki.Modifiers); // Ctrl, Shift, Alt 조합
        if (cki.Key == ConsoleKey.Q)
        {
            Console.WriteLine("Q를 입력하셨군요...");
        }
    }
}
```

- 실행 결과

```cs
아무키나 누르세요.
Q
Q
Shift
Q를 입력하셨군요...
```

>이것은 Shift와 Q를 함께 눌렀을 때의 실행 결과이다.

# 5 변수의 기본값을 default 키워드로 설정하기

>변수를 선언하고 초기화할 때는 해당 변수의 데이터 형식으로 초기화하면 된다. C#에서 기본으로 제공하는 값으로 초기화하고 싶다면 다음과 같이 default 키워드를 사용한다.

```cs
> int i = default;
> double d = default;
> char c = default;
> string s = default;
> $"[{i}], [{d}], [{c}], [{s}]"
"[0], [0], [\0], []"
> $"[{i}], [{d}], [{c == Char.MinValue}], [{s == null}]"
"[0], [0], [True], [True]"
```

>숫자 데이터 형식은 0을, char는 \\0을, string은 null을 기본값으로 가진다.

- Note

>특정 형식의 기본값을 변환해 주는 키워드도 default이다. defatult(T) 형태로도 사용하며, T 자리에는 특정 형식이 들어오는데 이를 기본 식(default expression)이라고 한다. 이것을 사용하면 int, bool, string 등 기본값을 알 수 있다. 

```cs
> int intDefault = default(int); // int 형식의 기본값
> intDefault
0
> bool boolDefault = default(bool); // bool 형식의 기본값
> boolDefault
false
> string strDefault = default(string); // string 형식의 기본값
> strDefault
null
> using System.Text;
> StringBuilder sbDefault = default(StringBuilder); // StringBuilder 클래스의 기본값
> sbDefault
null
```

>실행 결과처럼 특정 형식이 가지는 기본값은 default 키워드 또는 default(T) 형태로 알 수 있다. 

- Note

>C#에서는 튜플 리터럴(tuple literal)을 제공한다. 

>var 키워드로 변수를 선언한 후 괄호에 콤마를 구분해서 숫자 데이터를 넣으면 자동으로 t.Item1, t.Item2 형태로 값이 저장되어 그 값을 사용할 수 있다.

```cs
> var t = (100, 200);
> Console.WriteLine(t.Item1);
100
> Console.WriteLine(t.Item2);
200
```

>Item1, Item2처럼 자동 생성되는 형태를 사용하지 않을 때는 다음과 같이 변수 여러 개를 괄호 안에 선언할 수 있는데, x에는 300이 저장되고 y에는 400이 저장된다.

```cs
> var (x, y) = (300, 400);
> Console.WriteLine($"{x}, {y}");
300, 400
```


