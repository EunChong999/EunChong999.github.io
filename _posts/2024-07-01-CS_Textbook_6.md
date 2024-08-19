---
layout: single
title: Chapter 06 숫자 이외의 데이터 형식 사용하기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 숫자 이외의 데이터 형식 사용하기에 대한 내용입니다.

# 1 문자 데이터 형식 : char

>문자형 변수는 2바이트 공간에 문자 하나를 저장한다. 문자형 변수는 char 키워드로 선언하고 값을 초기화할 때는 작은따옴표 2개를 사용하여 문자 하나를 묶어 준다. 

>문자 하나를 답을 변수를 선언하고 사용하는 샘플 코드는 다음과 같다. C# 인터렉티브에서는 Console.WriteLine()을 사용하는 대신 다음과 같이 변수를 입력하여 직접 출력할 수도 있다. 

```cs
> char grade = 'A';
> grade
'A'
```

>문자 데이터 형식인 char 키워드로 선언된 변수는 문자 하나를 저장하는 데 사용한다. char 데이터 형식은 16비트 저장 공간을 차지한다. char 키워드로 선언되는 변수는 단일 유니코드(unicode) 문자를 저장한다. 일반적인 영문 및 한글 등 모든 언어 문자를 표현할 수 있다. 단일 문자는 작은따옴표(')로 묶는다. char 자료형에는 문자 여러 개를 저장할 수 없다. 즉, 작은따옴표 안에는 문자 하나만 넣을 수 있다. char 데이터 형식의 닷넷 형식은 System.Char이다. $"{a}, {b}" 형태를 사용하여 한 번에 문자 또는 문자열을 묶어 출력할 수 있다.

```cs
> char a = 'A';
> char b = 'B';
> $"{a}, {b}"
"A, B"
> System.Char c = 'ABC'; // 문자를 여러 개 저장하면 에러 발생
(1,17): error CS1012: 문자 리터럴에 문자가 너무 많습니다.
```

- CharacterDemo.cs

```cs
using System;

class CharacterDemo
{
    static void Main()
    {
        char grade = 'A';
        char kor = '가';

        Console.WriteLine(grade);
        Console.WriteLine(kor);
    }
}
```

- 실행 결과

```cs
A
가
```

>char 변수에 'A', '가'처럼 문자 하나를 작은따옴표로 묶어서 저장했다. char 변수에 문자를 하나 이상 지정하면 "문자 리터럴에 문자가 너무 많습니다."라는 에러 메시지가 출력된다. 

# 2 문자열 데이터 형식 : string 

>일반적으로 가장 많이 사용하는 데이터 형식은 문자열을 나타내는 string이다. string 키워드를 사용하면 문자열 데이터 형식의 변수를 선언할 수 있다. 문자열은 반드시 큰따옴표(")로 묶는다. string 키워드에 해당하는 닷넷 프레임워크 형식은 System.String이다.

- StringKeyword.cs

```cs
using System;

class StringKeyword
{
    static void Main()
    {
        string name = "김은총";
        Console.WriteLine("안녕하세요. {0}입니다.", name);
    }
}
```

- 실행 결과

```cs
안녕하세요. 김은총입니다.
```

>하나 이상의 문자로 구성된 문자열은 큰따옴표로 묶어서 string 변수에 담는다. 

## 2.1 @ 기호로 여러 줄 문자열 저장하기

>문자열 앞에 @ 기호를 붙이면 문자열 자체를 그대로 문자열로 저장한다. 이때 이스케이프 시퀀스도 함께 저장한다.

- MultiLineString.cs

```cs
using System;

class MultiLineString
{
    static void Main()
    {
        string multiLines = @"
            안녕하세요.
            반갑습니다.
        ";

        Console.WriteLine(multiLines);
    }
}
```

- 실행 결과

```cs

            안녕하세요.
            반갑습니다.
```

>실행하면 줄 바꿈 및 소스 코드에 있는 빈 공백까지 모두 포함하여 문자열로 저장되는 것을 확인할 수 있다.

>이처럼 C# 코드 기반에서 디렉터리 경로나 자바스크립트 코드 블록, SQL 문 등 여러 줄에 걸쳐 작성할 내용은 @ 기호를 앞에 붙여 문자열 하나로 인식하게 할 수 있다. 

## 2.2 문자열 보간법



