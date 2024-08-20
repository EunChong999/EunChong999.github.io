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

>문자열 보간법(string interpolation) 또는 보간된 문자열 기능은 문자열을 묶을 때 편리하게 사용할 수 있다. 문자열 템플릿(string template) 또는 템플릿 문자열(template string)이라고도 한다. 프로그래밍을 하다 보면 문자열을 묶어서 결과를 출력할 일이 많다. 이때 효과적으로 문자열을 처리하려고 String.Format() 메서드 등을 주로 사용한다. C# 6.0 버전부터는 템플릿 문자열이라는 문자열 보간법을 제공해서 $"{}" 형태로 문자열을 묶어서 출력하는 간결한 형태를 유지할 수 있다. 

```cs
> string message = "Hello";
> $"{message}"
"Hello"
```

>Console.WirteLine() 메서드에서 제공하는 {0}, {1} 형태의 자리 표시자 대신 직접 특정 변수 값을 중괄호 기호로 표현할 수 있다. 이때 문자열 앞에는 $ 기호가 와야 한다.

```cs
> int number = 3;
> string result = "홀수";
> Console.WriteLine($"{number}은(는) {result}입니다.");
3은(는) 홀수입니다.
```

>문자열 보간법에 사용되는 변수 값은 모두 문자열로 처리된다.

## 2.3 String.Format() 메서드로 문자열 묶기

>String.Format() 또는 string.Format() 메서드는 모두 동일한 표현법이다.

```cs
> string msg = string.Format("{0}님, {1}", "백승수", "안녕하세요.");
> Console.WriteLine(msg);
백승수님, 안녕하세요.
```

>String.Format()은 Console.WriteLine() 메서드처럼 {0}, {1}, {2} 순서대로 뒤에서 오는 문자열을 채워 문자열로 변환해 준다. 

## 2.4 문자열을 묶는 여러 가지 방법 비교

>문자열 앞에 $ 기호를 두고, 문자열 내에서 중괄호 기호를 사용하여 특정 변수 값을 문자열에 포함할 수 있다. 

```cs
> string message = "String Interpolation";
> Console.WriteLine("Message : {0}", message) // WriteLine() 메서드 기본 제공
Message : String Interpolation
> Console.WriteLine("Message : " + message); // 더하기 연산자
Message : String Interpolation
> Console.WriteLine($"Message : {message}"); // 문자열 보간법
Message : String Interpolation
```

```cs
> string name = "C#";
> string version = "8.0";
> Console.WriteLine("{0} {1}", name, version); // WriteLine() 메서드의 기본 기능 사용
C# 8.0
> string result = String.Format("{0} {1}", name, version); // String.Format() 메서드 사용
> Console.WriteLine(result);
C# 8.0
> Console.WriteLine($"{name} {version}"); // 문자열 보간법 사용
C# 8.0
> $"{name} {version}" // C# 인터렉티브에서는 Console.WriteLine() 생략 가능
"C# 8.0"
```

>C# 6.0 버전에서 새로 소개된 문자열 보간법을 사용하면 String.Format() 메서드 대신 $ 기호와 여는 중괄호와 닫는 중괄호 사이에 직접 변수 값을 지정할 수 있는데, 이것으로 코드를 간소화할 수 있다. 

# 3 논리 데이터 형식 : bool

>논리 데이터 형식인 참(true) 또는 거짓(false) 값을 저장하려면 bool 키워드를 사용한다. bool 키워드로 선언하는 변수는 논리형 값인 참(true)과 거짓(false) 정보를 저장한다. 이를 사용하면 어떤 상태를 참과 거짓으로 구분하여 제어할 수 있다. bool 데이터 형식은 1비트의 저장 공간을 차지한다. 1비트 공간을 채우는 키워드는 true와 false이다. bool 데이터 형식에는 true와 false 키워드로 표현되는 값을 2개만 저장할 수 있다. 이것으로 결괏값을 참/거짓, 예/아니요 등으로 표현할 수 있다. bool 키워드에 해당하는 닷넷 형식은 System.Boolean이다. 

- BooleanDemo.cs

```cs
using System;

class BooleanDemo
{
    static void Main()
    {
        bool bln = true;
        Console.WriteLine(bln);

        bool isFalse = false;
        Console.WriteLine(isFalse);
    }
}
```

- 실행 결과

```cs
True
False
```

>C#에서 논리 데이터 형식에 사용하려고 미리 정의된 키워드는 true와 false이다. 다만 Console.WirteLine() 메서드로 출력되는 문자열은 True와 False로 표현된다.

# 4 변하지 않는 값 : 상수

>문자열 변수에 const 키워드를 붙이면 상수로 선언된다. 

```cs
> const double PI = 3.14; // 상수 선언과 동시에 초기화
> const string SITE_NAME = "마이크로소프트"; // 상수 참조
> PI
3.14
> SITE_NAME
"마이크로소프트"
```

>변수를 선언할 수 있는 모든 데이터 형식 앞에 const를 붙여 상수로 만들었다. 

>상수 내용은 변경할 수 없다. 상수를 선언한 후 상수 값을 새로운 값으로 변경하려고 하면 에러가 발생한다. 

```cs
> string name = "김은총";
> name = "EunChong"; // 변수 : 변경 가능
> const int age = 18; // 상수 : age는 20으로 고정
> age = 45; // age를 45로 변경하려고 하면 에러 발생
(1,1): error CS0131: 할당식의 왼쪽은 변수, 속성 또는 인덱서여야 합니다.
> Console.WriteLine($"{name} - {age}"); // 변수와 상수 사용
EunChong - 18
> const double PI = 3.14;
> const string SITE_NAME = "마이크로소프트";
> PI
3.14
> SITE_NAME
"마이크로소프트"
```

- Note 

>상수는 변하지 않는 값을 저장할 때 유용하고, 변수는 변하는 값을 저장할 때 유용하다. 

```cs
> const string name = "박용준"; // 상수 : 변하지 않는 값
> int age = 45; // 변수 : 변하는 값
> $"이름 : {name}, 나이 : {age}"
"이름 : 박용준, 나이 : 45"
```

>영어 단어로 mutable은 '변할 수 있는'이고, immutable은 '변할 수 없는'이다. 변수(variable)는 mutable이고 상수(constant)는 immutable이다. 

# 5 닷넷 데이터 형식

>문자, 문자열, 논리 데이터를 표현할 때는 char, string, bool 키워드를 사용했다. 이와 동일한 표현인 닷넷 데이터 형식은 System.Char, System.String, System.Boolean이다.

- CharStringBoolean.cs

```cs
using System;

class CharStringBoolean
{
    static void Main()
    {
        Char c = 'A';
        String s = "안녕하세요.";
        Boolean b = true;

        Console.WriteLine("{0}\n{1}\n{2}", c, s, b);
    }
}
```

- 실행 결과

```cs
A
안녕하세요.
True
```

>Char, String, Boolean을 사용해서 변수를 선언하는 방식은 char, string, bool 키워드를 표현하는 방식과 동일하다. 

# 6 래퍼 형식

>데이터 형식을 지정할 때 사용되는 int, string 등 키워드는 닷넷 데이터 형식으로도 제공한다. 이러한 닷넷 데이터 형식을 다른 말로 래퍼 형식(wrapper type)이라고 한다. 래퍼 형식은 int, string 같은 기본 형식을 클래스 또는 구조체로 감싼 닷넷 데이터 형식을 의미한다. 

```cs
> int number1 = 1234; // int 키워드 : 기본 형식
> Int32 number2 = 1234; // System.Int32 구조체 : 닷넷 형식
> $"{number1}, {number2}"
"1234, 1234"
> string str1 = "안녕"; // string 키워드 : 기본 형식
> String str2 = "안녕"; // System.String 클래스 : 닷넷 형식
> $"{str1} {str2}"
"안녕 안녕"
```

- Note

>DateTime에서 날짜 관련 정보를 제공한다.

```cs
> DateTime.Now // 날짜 전체
[2024-08-20 오전 11:03:00]
> $"{DateTime.Now.Year}-{DateTime.Now.Month}-{DateTime.Now.Day}" // 항목별 출력
"2024-8-20"
> $"{DateTime.Now.Hour}:{DateTime.Now.Minute}:{DateTime.Now.Second}"
"11:4:28"
```

