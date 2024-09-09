---
layout: single
title: Chapter 15 while 문과 do 문, foreach 문으로 반복 처리하기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 while 문과 do 문, foreach 문으로 반복 처리하기에 대한 내용을 담고 있습니다.

# 1 while 문

>while 문은 조건식이 참일 동안 문장을 반복 실행한다. 코드 형태는 다음과 같다.

```cs
while (조건식)
{
	조건식이 참일 때까지 실행할 문장들...
}
```

>while 문의 조건식이 true일 동안 실행문을 반복하여 실행한다. 반복을 중지하려면 while 문 안쪽 코드에서 증감식 등을 사용하여 조건식 값을 변경해야 한다. while 문을 순서도로 표현하면 다음과 같다.

![](https://i.imgur.com/fSMSpk9.png)

## 1.1 while 문으로 '안녕하세요.' 여러 번 출력하기

- WhileDescription.cs

```cs
using System;

class WhileDescription
{
    static void Main()
    {
        int count = 0;                          // 초기식
        while (count < 3)                       // 조건식
        {
            Console.WriteLine("안녕하세요.");    // 실행문
            count++;                            // 증감식
        }
    }
}
```

- 실행 결과

```cs
안녕하세요.
안녕하세요.
안녕하세요.
```

>while 문은 for 문과 마찬가지로 반복문이다. 반복문은 일반적으로 초기식, 조건식, 실행문, 증감식의 식과 문을 가진다. 다만 for 문과 while 문이 그 위치가 조금 다를 뿐이다. 

## 1.2 다양하게 while 문 사용하기

- (1) while 문을 사용하여 1부터 5까지 출력하기

- WhileDemo.cs

```cs
using System;

class WhileDemo
{
    static void Main()
    {
        int i = 1; // 초기식부터 
        while (i <= 5) // 조건식을 만족하는 동안
        {
            Console.WriteLine("카운트 : {0}", i); // 실행문을 실행하고
            i++; // 증감식을 사용하여 인덱스 변수를 1씩 증가
        }
    }
}
```

- 실행 결과

```cs
카운트 : 1
카운트 : 2
카운트 : 3
카운트 : 4
카운트 : 5
```

>초기식인 1부터 조건식인 5까지 반복하면서 카운트를 출력하고, 증감식에서 1씩 증가시켜 총 다섯 번 반복하는 내용을 보여 준다. 이 예제 역시 for 문과 달리 초기식, 조건식, 증감식, 실행문 위치가 조금 다르다. 

- (2) 카운트 증가 프로그램

>while 문의 구성 요소는 초기식, 조건식, 실행문, 증감식이다.

- WhileLoop.cs

```cs
using System;

class WhileLoop
{
    static void Main()
    {
        int count = 1;                                // 초기식
        while (count <= 3)                            // 조건식
        {
            Console.WriteLine($"카운트 : {count}");    // 실행문
            count++;                                  // 증감식
        }
    }
}
```

- 실행 결과

```cs
카운트 : 1
카운트 : 2
카운트 : 3
```

>1부터 3까지 반복하여 카운트를 증가시키는 기본적인 while 문의 형태이다.

- (3) 초깃값을 감소시켜서 반복하기

- WhileDecrement.cs

```cs
using System;

class WhileDecrement
{
    static void Main()
    {
        int index = 5;
        while (index > 0)
        {
            Console.WriteLine($"안녕하세요. {index}");
            index--;
        }
    }
}
```

- 실행 결과

```cs
안녕하세요. 5
안녕하세요. 4
안녕하세요. 3
안녕하세요. 2
안녕하세요. 1
```

>index가 5로 설정된 상태에서 증감식에서 index--로 루프를 한 번 실행할 때마다 1씩 감소하도록 했다. index가 0이 되는 순간에 while 문을 종료하는 형태로 인덱스 변수 값을 감소시키면서 반복 실행할 수 있다.

- (4) while 문을 사용하여 1부터 100까지 합을 구하는 프로그램

- WhileSum.cs

```cs
using System;

class WhileSum
{
    static void Main()
    {
        const int N = 100;
        int sum = 0;

        int i = 1;
        while (i <= N)
        {
            sum += i;
            i++;
        }

        Console.WriteLine($"1부터 {N}까지의 합 : {sum}");
    }
}
```

- 실행 결과

```cs
1부터 100까지의 합 : 5050
```

>1부터 100까지 1씩 증가시키면서 반복하여 1부터 100까지 정수 합을 구하는 프로그램이다. 

- (5) while 문을 사용하여 짝수 합 구하기

- WhileEven.cs

```cs
using System;

class WhileEven
{
    static void Main()
    {
        int sum = 0;

        int i = 1;          // 초기식
        while (i <= 100)    // 조건식
        {
            if (i % 2 == 0) // 필터링(조건 처리)
            {
                sum += i;   // 실행문
            }
            i++;            // 증감식
        }

        Console.WriteLine($"1부터 100까지 짝수의 합 : {sum}");
    }
}
```

- 실행 결과

```cs
1부터 100까지 짝수의 합 : 2550
```

# 2 피보나치 수열을 while 문으로 표현하기

>이 예제는 1부터 20까지 범위 내에 있는 피보나치 수열을 출력한다.

- WhileFibonacci.cs

```cs
// 피보나치 수열 : 1 1 2 3 5 8 13 21 ...
using System;

class WhileFibonacci
{
    static void Main()
    {
        int first = 0;
        int second = 1;

        while (second <= 20)
        {
            Console.WriteLine(second);
            int temp = first + second;
            first = second;
            second = temp;
        }
    }
}
```

- 실행 결과

```cs
1
1
2
3
5
8
13
```

>반복 회차에 맞는 first, second 변수의 출력 값을 정리해 보면 다음과 같다.

| 회차  | first | second | temp   |
| --- | ----- | ------ | ------ |
| 1   | 0     | 1      | 0 + 1  |
| 2   | 1     | 1      | 1 + 1  |
| 3   | 1     | 2      | 1 + 2  |
| 4   | 2     | 3      | 2 + 3  |
| 5   | 3     | 5      | 3 + 5  |
| 6   | 5     | 8      | 5 + 8  |
| 7   | 8     | 13     | 8 + 13 |

>second 변수 값을 출력하면 1부터 20 사이의 피보나치 수열을 출력한다.

# 3 do while 반복문으로 최소 한 번은 실행하기

>do 문은 while 문과 비슷하지만, 일단 문장을 한 번 실행한 후 그다음에 조건을 따지는 구문이다. 이 또한 조건식이 참일 동안 문장을 반복 실행한다. do 문 형식은 다음과 같다.

```cs
do
{
	실행문;
} while (조건식);
```

>do 문 조건식이 true일 동안 실행문을 반복하여 실행한다. 이때 do 문은 마지막에 세미콜론(;) 기호로 끝나야 하는 것에 주의한다. do 문은 while (조건식)이 뒤에 오므로 무조건 한 번은 실행문이 실행된다.

## 3.1 do while 문을 사용하여 '안녕하세요.' 세 번 출력하기

- DoWhile.cs

```cs
using System;

class DoWhile
{
    static void Main()
    {
        int count = 0;                       // 초기식
        do
        {
            Console.WriteLine("안녕하세요."); // 실행문
            count++;                         // 증감식
        } while (count < 3);                 // 조건식
    }
}
```

- 실행 결과

```cs
안녕하세요.
안녕하세요.
안녕하세요.
```

>while 문과 달리 조건식이 맨 마지막에 나와서 한 번은 실행문을 실행하게 된다.

## 3.2 do while 문으로 합 구하기

- DoWhileSum.cs

```cs
using System;

class DoWhileSum
{
    static void Main()
    {
        int sum = 0;

        int i = 1;          // 초기식
        do
        {
            sum += i;       // 실행문
            i++;            // 증감식
        } while (i <= 5);   // 조건식

        Console.WriteLine($"합계 : {sum}");
    }
}
```

- 실행 결과

```cs
합계 : 15
```

>do while 문은 while 문과 기능이 동일하다. 다만 조건식이 뒤에 오는 것만 다르다.

## 3.3 1에서 100까지 3의 배수이면서 4의 배수인 정수 합 구하기

>do~while 문은 먼저 실행 후 반복한다고 해서 선행 반복이라고 한다.

- DoWhileDemo.cs

```cs
using System;

class DoWhileDemo
{
    static void Main()
    {
        int sum = 0;

        int i = 1;                          // 초기식
        do
        {
            if (i % 3 == 0 && i % 4 == 0)   // 필터링(조건식)
            {
                sum += i;                   // 실행문(문장)
            }
            i++;                            // 증감식
        } while (i <= 100);                 // 조건식(평가할 식)

        Console.WriteLine(sum);
    }
}
```

- 실행 결과

```cs
432
```

>이 예제는 do 문을 사용하여 1부터 100까지 반복하며 3의 배수이면서 4의 배수인 정수 합을 구한다.

# 4 foreach 문으로 배열 반복하기

>foreach 문은 배열(array)이나 컬렉션(collection) 같은 값을 여러 개 담고 있는 데이터 구조에서 각각의 데이터가 들어 있는 만큼 반복하는 반복문이다. 데이터 개수나 반복 조건을 처리할 필요 없이 데이터가 있는 만큼 반복하는 반복하는 구조이다. 

>foreach 문은 반복 가능한 항목들을 반복해서 가져온다. foreach 문의 형태는 다음과 같다.

```cs
foreach (항목 in 항목들) {...}
```

>foreach 문은 값 여러 개 중 하나를 특정 데이터 형식으로 뽑아 해당 변수에 임시로 담은 후 실행문에서 사용하는 형태이다.

```cs
foreach (데이터형식 변수 in 컬렉션형식)
{
	문장; // 변수에 들어 있는 값을 사용하는 문장이 온다
}
```

>이 형태를 보면 컬렉션 형식에 데이터가 들어 있는 만큼 문장을 실행시킨다. 여기에서는 변수에 데이터 형식에 맞는 데이터가 반복될 때마다 하나씩 저장한다. 

## 4.1 데이터가 들어 있는 만큼 반복하기

>foreach 문은 다음과 같이 사용하면 names에 저장된 문자열 2개가 출력된다.

```cs
> string[] names = { "C#", "ASP.NET" };
> foreach (string name in names)
. {
.     Console.WriteLine(name);
. }
C#
ASP.NET
```

## 4.2 문자열에서 문자 하나씩 뽑아 출력하기

>문자열은 그 자체가 문자 집합이다. 이러한 문자열에서 문자 하나씩을 뽑아 사용할 때는 foreach 문 같은 제어문이 도움이 된다. 참고로 코드 내에서 foreach를 입력한 후 Tab을 두 번 누르면 자동으로 코드 조각이 생성된다.

- ForEach.cs

```cs
using System;

class ForEach
{
    static void Main()
    {
        string str = "ABC123";

        foreach (char c in str)
        {
            Console.Write($"{c}\t");
        }
        Console.WriteLine();
    }
}
```

- 실행 결과

```cs
A       B       C       1       2       3
```

>이 코드에서 문자열은 string 변수에 담고, 문자열에서 하나씩 뽑은 문자는 char 변수에 담긴다. 이러한 코드에서는 다음과 같이 var 키워드를 사용해도 된다. 

- ForEachUp.cs

```cs
using System;

class ForEachUp
{
    static void Main()
    {
        var str = "ABC123";

        foreach (var c in str)
        {
            Console.Write($"{c}\t");
        }
        Console.WriteLine();
    }
}
```

- 실행 결과

```cs
A       B       C       1       2       3
```

