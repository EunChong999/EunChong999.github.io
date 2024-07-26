---
layout: single
title: Chapter 05 숫자 데이터 형식 사용하기
categories: []
tags:
  - C#
  - Study
---
>이 포스트는 숫자 데이터 형식 사용하기에 대한 내용입니다.

>프로그래밍에서는 정수 및 실수 데이터를 자주 사용한다.

# 1 숫자 데이터 형식

>C#에서는 숫자 형식의 데이터를 다룰 때 사용하는 int 키워드를 포함하여 여러 가지 키워드를 제공한다. 숫자 데이터 형식은 크게 정수 데이터 형식과 소수점이 있는 실수 데이터 형식으로 나누며, 다시 부호 있는 숫자와 부호 없는 숫자로 나눈다.    

![](https://i.imgur.com/5bSIW9p.png)

# 2 정수 데이터 형식

>정수형 키워드에는 s와 u 접두사가 붙는데 이는 signed와 unsigned의 약자로, 부호를 붙이느냐 붙이지 않느냐의 차이가 있다.

- 부호 있는(signed)
	- +,- 부호가 있는 정수형이다. 즉, 양수와 음수를 모두 지원한다.
- 부호 없는(unsigned)
	- 부호 없이 + 값만 다루는 정수형이다. 즉, 양수만 지원한다.

>각 정수 데이터 형식의 키워드는 그와 동일한 역할을 하는 닷넷(.NET) 형식을 제공한다. 예를 들어 int 형식과 동일한 닷넷 데이터 형식은 System.Int32이다.

>변수를 선언할 때도 마찬가지로 int 대신 System.Int32를 사용할 수 있다. 코드 위쪽에 System 네임스페이스를 using 구문으로 선언했으면 Int32로 줄여서 표현도 가능하다.

>정수 데이터 형식의 종류는 다음 표와 같다. 
>정수 데이터 형식을 표현하는 데 키워드 8개를 사용한다. 

- 정수 데이터 형식

| 종류             | 데이터 형식 | 닷넷 형식         |
| -------------- | ------ | ------------- |
| 부호 있는 정수(+, -) | sbyte  | System.SByte  |
|                | short  | System.Int16  |
|                | int    | System.Int32  |
|                | long   | System.Int64  |
| 부호 없는 정수(+)    | byte   | System.Byte   |
|                | ushort | System.UInt16 |
|                | uint   | System.UInt32 |
|                | ulong  | System.UInt64 |

- IntegerDemo.cs

```cs
using System;

class IntegerDemo
{
    static void Main()
    {
        int min = -2147483648; // 정수형이 가질 수 있는 최솟값
        int max = +2147483647; // 정수형이 가질 수 있는 최댓값

        Console.WriteLine("int 변수의 최솟값 : {0}", min);
        Console.WriteLine("int 변수의 최댓값 : {0}", max);
    }
}
```

- 실행 결과

```cs
int 변수의 최솟값 : -2147483648
int 변수의 최댓값 : 2147483647
```

>int 키워드를 사용한 정수형은 최소 -21억부터 최대 +21억까지 데이터를 저장한다. 

- Note

>C# 7.0 버전부터는 언더스코어(\_) 문자를 사용하는 숫자 구분자(digit separator)를 제공하여 세 자리마다 콤마로 구분되는 긴 숫자 형태를 표현할 수 있다.

```cs
> int number = 1_000_000;
> Console.WriteLine(number);
1000000
```

>숫자 형식을 표현할 때 언더스코어(\_) 문자는 무시한다. 숫자 구분자를 사용하면 숫자를 표시할 때 가독성이 높아진다. 

# 3 부호 있는 정수 데이터 형식

>C#은 +와 - 정수를 다룰 수 있는 데이터 형식을 제공한다. sbyte, short, int, long 순서대로 작은 수부터 큰 수까지 담아 놓을 수 있다. 상세한 내용은 다음 표와 같다. 

- 부호 있는 정수 데이터 형식


| 데이터 형식 | 비트   | 범위                                         | 닷넷 형식        |
| ------ | ---- | ------------------------------------------ | ------------ |
| sbyte  | 8비트  | -128~+127                                  | System.SByte |
| short  | 16비트 | -32768~+32767                              | System.Int16 |
| int    | 32비트 | -2147483648~+2147483647                    | System.Int32 |
| long   | 64비트 | -9223372036854775808~ +9223372036854775807 | System.Int64 |

- SignedInteger.cs

```cs
using System;

class SignedInteger
{
    static void Main()
    {
        sbyte iSByte = 127;
        short iInt16 = 32767;
        int iInt32 = 2147483647;
        long iInt64 = 9223372036854775807;

        Console.WriteLine("8비트 sbyte : {0}", iSByte);
        Console.WriteLine("16비트 short : {0}", iInt16);
        Console.WriteLine("32비트 int : {0}", iInt32);
        Console.WriteLine("64비트 long : {0}", iInt64);
    }
}
```

- 실행 결과

```cs
8비트 sbyte : 127
16비트 short : 32767
32비트 int : 2147483647
64비트 long : 9223372036854775807
```

>이 코드는 sbyte, short, int, long 키워드로 선언된 변수가 가질 수 있는 가장 큰 값을 넣은 후 출력한다.

# 4 부호 없는 정수 데이터 형식

>부호 없는 정수 데이터 형식은 - 값을 사용할 수 없지만, + 값은 부호 있는 정수형의 2배 크기로 사용할 수 있는 데이터 형식을 제공한다.

>부호 없는 정수 데이터 형식은 byte, ushort, uint, ulong 키워드 4개를 사용한다. 각 범위는 다음 표와 같이 부호 있는 범위보다 2배 더 큰 양의 정수 값을 제공한다.

| 데이터 형식 | 비트   | 범위                      | 닷넷 형식         |
| ------ | ---- | ----------------------- | ------------- |
| sbyte  | 8비트  | 0~+255                  | System.Byte   |
| ushort | 16비트 | 0~+65535                | System.UInt16 |
| uint   | 32비트 | 0~+4294967295           | System.UInt32 |
| ulong  | 64비트 | 0~+18446744073709551615 | System.UInt64 |

>일반적으로 사람 나이는 sbyte 형식으로도 충분하지만, 간혹 sbyte의 최댓값인 127을 넘을 때가 있어 byte 형식을 사용하기도 한다.

```cs
> byte age = 100;
> age
100
```

- UnsignedInteger.cs

```cs
using System;

class UnsignedInteger
{
    static void Main()
    {
        byte iByte = 255;
        ushort iUInt16 = 65535;
        uint iUInt32 = 4294967295;
        ulong iUInt64 = 18446744073709551615;

        Console.WriteLine("8비트 byte : {0}", iByte);
        Console.WriteLine("16비트 ushort : {0}", iUInt16);
        Console.WriteLine("32비트 uint : {0}", iUInt32);
        Console.WriteLine("64비트 ulong : {0}", iUInt64);
    }
}
```

- 실행 결과

```cs
8비트 byte : 255
16비트 ushort : 65535
32비트 uint : 4294967295
64비트 ulong : 18446744073709551615
```

>이 코드는 byte, ushort, uint, ulong 키워드로 선언된 변수가 가질 수 있는 가장 큰 값을 넣은 후 출력한다. 부호 있는 정수형보다 2배 큰 값을 넣을 수 있다.

>정수 데이터 형식의 범위를 넘는 숫자를 넣으면 어떻게 될까? 코드가 실행되지 않고 바로 에러가 발생한다. byte 형식 변수는 0에서 255까지 정수를 저장할 수 있어 그보다 큰 256은 저장할 수 없다.

```cs
> byte b = 256;
(1,10): error CS0031: '256' 상수 값을 'byte'(으)로 변환할 수 없습니다.
```

- Note
	>부호 있는 정수형 데이터 형식인 sbyte, short, int, long과 부호 없는 데터 형식인 byte, ushort, uint, ulong의 최솟값과 최댓값은 다음과 같이 MinValue와 MaxValue 속성으로 출력할 수 있다.

```cs
> Console.WriteLine("[32비트] int 최솟값 : {0}", int.MinValue); // 부호 있는 정수형
[32비트] int 최솟값 : -2147483648
> Console.WriteLine("[32비트] int 최댓값 : {0}", int.MaxValue);
[32비트] int 최댓값 : 2147483647
```

```cs
> Console.WriteLine("[08비트] byte 최솟값 : {0}", byte.MinValue); // 부호 없는 정수형
[08비트] byte 최솟값 : 0
> Console.WriteLine("[08비트] byte 최댓값 : {0}", byte.MaxValue);
[08비트] byte 최댓값 : 255
```

# 5 실수 데이터 형식

>부동소수점 데이터 형식으로 표현되는 실수를 컴퓨터에서 표현하는 방법은 복잡하다. 실수 데이터는 부동소수점 방식과 10진 방식을 다루는 세 가지 데이터 형식 키워드인 double, float, decimal을 제공한다. 

![](https://i.imgur.com/FTO6x4F.png)

> double, float는 부동소수점 방식이다. decimal은 10진 방식이며, 소수점 28자리 정도까지의 자료를 다루는 금융 관련 프로그램을 만들 때 유용하다. 

>실수 데이터 형식이 갖는 크기와 값의 범위는 다음 표와 같다. 다음 표기법은 지수 표기법으로 표현했는데, float 데이터 형식의 최댓값은 약 $3.4\times10^{38}$