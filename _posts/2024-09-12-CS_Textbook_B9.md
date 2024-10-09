---
layout: single
title: Chapter 20 구조체 사용하기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 구조체 사용하기에 대한 내용을 담고 있습니다.

# 1 구조체 

>구조체는 이름 하나로 데이터를 묶어 관리하는 역할을 한다. 변수는 이름 하나로 공간을 하나 갖고, 배열은 이름 하나로 데이터 형식이 동일한 공간을 여러 개 갖는다. 변수와 배열을 확장하여 이름 하나로 데이터 형식을 1개 또는 여러 개 보관하는 그릇 역할을 하는 것이 바로 구조체이다.

>구조체는 int, string 등 서로 다른 자료를 한 집단으로 정의하여 이름 하나로 지정할 수 있는 여러 항목의 모임이다. 즉, 구조체 변수란 이름 하나로 데이터 형식 1개 이상을 하나로 보관해 놓는 그릇 역할을 한다. 그리고 구조체 배열은 이름 하나로 데이터 형식 1개 이상을 여러 개 보관해 놓는 그릇 역할을 한다. 

# 2 구조체 만들기

>구조체를 만드는 방법은 다음과 같다. 구조체를 의미하는 struct 키워드를 사용하여 구조체를 만들고, 중괄호 안에 구조체 멤버들을 생성한다.

```cs
struct 구조체이름
{
	데이터형식 변수1;
	데이터형식 변수2;
	데이터형식 변수3;
}
```

>여기에서 구조체 이름은 새로운 데이터 형식이 되며, 변수를 선언할 때 구조체 이름을 사용할 수 있다. 구조체를 가리켜 사용자 정의 데이터 형식이라고도 한다.

>다음 샘플 코드는 Point 이름으로 X와 Y를 담을 수 있는 구조체를 만들고 값을 저장한 후 이를 다시 출력한다.

```cs
> struct Point
. {
.     public int X;
.     public int Y;
. }
> Point p;
> p.X = 100;
> p.Y = 200;
> $"{p.X}, {p.Y}"
"100, 200"
```

>이처럼 구조체를 사용하면 이름 하나로 여러 데이터를 저장하여 사용할 수 있다. 

## 2.1 구조체를 사용하여 하나 이상의 변수 또는 배열을 묶어 관리하기

- StructDemo.cs

```cs
using System;

struct Point
{
    public int X; // public 키워드로 외부에서 int X 변수를 사용하도록 설정
    public int Y;
}

class StructDemo
{
    static void Main()
    {
        Point point;   // Point 구조체 형식의 변수 선언
        point.X = 100; // 점을 구분해서 X 변수에 값을 할당 
        point.Y = 200; // 점을 구분해서 Y 변수에 값을 할당
        Console.WriteLine($"X : {point.X}, Y : {point.Y}");
    }
}
```

- 실행 결과

```cs
X : 100, Y : 200
```

>구조체를 선언할 때는 struct 키워드를 사용한다. 여기에서는 struct Point {} 형태로 이름이 Point인 구조체를 만들었다. 만든 구조체는 int, string 형식의 변수 선언과 동일한 방법으로 선언한 후 사용할 수 있다. 변수는 값을 하나만 저장하지만, 구조체는 점(.)으로 구분하여 구조체를 선언할 때 사용한 변수 여러 개를 이름 하나(point)로 묶어 쓸 수 있다. 

# 3 구조체 선언 및 사용하기

>구조체를 선언하고 사용하려면 먼저 구조체 변수를 선언한다. 

>구조체 선언은 struct 키워드와 public을 붙인 변수를 사용하여 만든다. 

```cs
> struct BusinessCard
. {
.     public string Name;
.     public int Age;
.     public string Address;
. }
```

>선언된 구조체 이름을 사용하여 마치 int, string 형식처럼 변수를 만들 수 있다.

```cs
> BusinessCard my;
```

>이와 같이 명함을 의미하는 BusinessCard라는 이름의 구조체를 선언하고 메모리상에 다음 공간이 잡힌다.

![](https://i.imgur.com/Qy0IfJG.png)

>구조체 형식 변수인 my는 이름 하나로 Name, Age, Address를 묶어 저장할 수 있다.

```cs
> my.Name = "백승수";
. my.Age = 21;
. my.Address = "서울시";
```

>구조체의 각 항목을 일반적으로 구조체 멤버(member)라고 한다. 구조체 멤버에 값을 할당할 때는 점(.)으로 구분해서 값을 입력한다.

```cs
구조체변수이름.멤버이름 = 값;
```

>이렇게 구조체를 사용하면 서로 다른 데이터 형식을 묶어 관리하므로 편하다. 다음과 같이 점(.)으로 구분하여 각 멤버를 호출해서 사용한다.

```cs
> Console.WriteLine($"{my.Name}, {my.Age}, {my.Address}");
백승수, 21, 서울시
```

## 3.1 구조체를 사용하여 변수 하나로 여러 개를 묶어 관리하기

- StructVariable.cs

```cs
using System;

class StructVariable
{
    static void Main()
    {
        Product product; // 구조체 형식 변수 선언

        product.Id = 1;  // 구조체 변수의 각 멤버에 값을 할당
        product.Title = "좋은 책";
        product.Price = 10000M;

        // 구조체 형식 변수 사용
        string message =
            $"번호 : {product.Id}\n상품명 : {product.Title}\n가격 : {product.Price}";
        Console.WriteLine(message);
    }
}

// (1) 멤버가 3개인 Product 구조체 선언
struct Product
{
    public int Id;
    public string Title;
    public decimal Price;   
}
```

- 실행 결과

```cs
번호 : 1
상품명 : 좋은 책
가격 : 10000
```

>struct 키워드로 만든 개체는 일반 변수처럼 사용할 수 있다. 구조체 내에 전역적으로 선언된 변수를 멤버 변수라고 한다. 멤버 변수는 외부에서 사용하도록 public 키워드를 붙인다. public 키워드를 액세스 한정자(access modifier)라고도 한다.

>구조체를 사용하면 이름 하나로 서로 다른 데이터 형식을 여러 개 가지는 변수들을 묶어 관리할 수 있다. 구조체 변수를 사용하면 점(.)을 찍어 멤버 변수 여러 개의 목록을 볼 수 있어 편리하다.

>(1)에서 구조체 멤버가 되는 변수들은 public 액세스 한정자를 붙여 외부에서 사용 가능하도록 설정한다.

# 4 구조체 배열

>구조체에도 배열을 사용할 수 있다. 다음과 같이 구조체 배열을 사용하여 명함 구조체를 1000개 만들 수 있다.

```cs
명함구조체[] 명함배열 = new 명함구조체[1000];
```

>만든 구조체 배열은 다음과 같이 0번째 인덱스부터 999번째 인덱스까지 배열로 이름, 주소, 전화번호 멤버에 접근해서 값을 할당하거나 참조해서 사용할 수 있다.

![](https://i.imgur.com/Wbj5GSr.png)

## 4.1 구조체 배열을 사용해서 데이터 대입 및 출력하기

>다음 코드에서는 구조체와 클래스를 namespace 키워드를 사용하여 한 번 더 묶어 주었다.

- StructArray.cs

```cs
using System;

namespace StructArray
{
    struct BusinessCard // (1) 구조체 선언
    {
        public string Name;
        public int Age;
    }

    class StructArray
    {
        static void Print(string name, int age) // 출력 전담 함수
            => Console.WriteLine($"{name}은(는) {age}살입니다.");

        static void Main()
        {
            BusinessCard biz; // 구조체 형식 변수 선언
            biz.Name = "백승수";
            biz.Age = 17;
            Print(biz.Name, biz.Age);

            BusinessCard[] names = new BusinessCard[2]; // 구조체 형식 배열 선언
            names[0].Name = "이세영"; names[0].Age = 102;
            names[1].Name = "권경민"; names[1].Age = 31;
            for (int i = 0; i < names.Length; i++)
            {
                Print(names[i].Name, names[i].Age);
            }
        }
    }
}
```

- 실행 결과

```cs
백승수은(는) 17살입니다.
이세영은(는) 102살입니다.
권경민은(는) 31살입니다.
```

>C#에서 구조체 사용은 클래스 사용에 비해서 빈도가 극히 적은 편이다. 하지만 간단한 구조의 데이터를 모아 처리할 때는 클래스보다 처리 속도가 좋기에 적절하게 사용한다.

# 5 구조체 매개변수 : 함수의 매개변수에 구조체 사용하기

- StructParameter.cs

```cs
using System;

struct Member // Member 구조체 선언
{
    public string Name;
    public int Age;
}

class StructParameter
{
    static void Main()
    {
        string name = "백승수";  // 변수 사용
        int age = 21; 
        Print(name, age);       // 매개변수를 따로 선언

        Member m;               // 구조체 사용
        m.Name = "이세영";
        m.Age = 100;
        Print(m);               // 구조체 매개변수를 사용하여 전달
    }

    static void Print(string name, int age) =>
        Console.WriteLine($"이름 : {name}, 나이 : {age}");

    static void Print(Member member) =>
        Console.WriteLine($"이름 : {member.Name}, 나이 : {member.Age}");
}

```

- 실행 결과

```cs
이름 : 백승수, 나이 : 21
이름 : 이세영, 나이 : 100
```

>변수로 Print 함수에 name과 age를 전달하는 형태와 구조체로 Print 함수에 구조체 변수인 member를 전달하는 두 가지 형태를 확인할 수 있다.

>한 번에 함수에 전달해야 하는 매개변수가 많다면, 이처럼 구조체로 묶어 구조체 변수 하나로 사용하면 복잡하지 않고 편리하게 매개변수를 전달할 수 있다. 

# 6 내장형 구조체

>닷넷 프레임워크에 이미 내장(built-in)된 구조체 중에서 날짜 처리를 전담하는 DateTime과 TimeSpan 구조체, 문자 관련 처리를 담당하는 Char 구조체를 자주 사용한다. 

- **DateTime 구조체** 
	- 시간/날짜 관련 모든 정보를 제공한다.
- **TimeSpan 구조체**
	- 시간/날짜 간격에 대한 모든 정보를 제공한다.
- **Char 구조체**
	- 문자 관련 모든 정보를 제공한다. 예를 들어 특정 문자가 숫자 형식인지 기호 문자인지 공백 문자인지 등을 판단하는 기능을 제공한다.
- **Guid 구조체**
	- 절대로 중복되지 않는 유일한 문자열을 생성한다.

## 6.1 날짜 관련 구조체 사용하기

>날짜 관련 내장 구조체에는 DateTime과 TimeSpan이 있다. 

```cs
> Console.WriteLine($"현재 시간 : {DateTime.Now}"); // (1) 현재 시간 출력
현재 시간 : 2024-09-12 오후 9:44:54
> DateTime.Now.Year // (2) 년, 월, 일, 시, 분, 초 출력
2024
> DateTime.Now.Month
9
> DateTime.Now.Day
12
> DateTime.Now.Hour
21
> DateTime.Now.Minute
45
> DateTime.Now.Second
3
> DateTime.Now.Millisecond
437
> 
> DateTime now = DateTime.Now; // (3) DateTime 형식의 변수 선언 후 속성 또는 메서드 호출
> Console.WriteLine(now.Date);
2024-09-12 오전 12:00:00
> Console.WriteLine(now.ToLongTimeString());
오후 9:46:35
```

>DateTime 구조체의 Now 속성은 현재 사용 중인 컴퓨터의 시간과 관련한 모든 정보를 알려 준다. 단순하게 날짜 전체 정보를 화면에 출력하려면 DateTime.Now를 사용한다. 각각의 날짜와 시간 정보를 따로 호출하려면 DateTime.Now.Year부터 DateTime.Now.Millisecond까지 사용해서 문자열을 묶어 원하는 모든 날짜와 시간 정보를 얻을 수 있다.

- TimeSpanDemo.cs

```cs
using System;

class TimeSpanDemo
{
    static void Main()
    {
        // 시간 차(D-Day) 구하기 : TimeSpan 구조체
        TimeSpan dday = Convert.ToDateTime("2024-12-25") - DateTime.Now;
        Console.WriteLine(
            $"{DateTime.Now.Year}년도 크리스마스는 {(int)dday.TotalDays}일 남음");

        // 지난 시간 구하기
        TimeSpan times = DateTime.Now - Convert.ToDateTime("2005-05-27");
        Console.WriteLine($"내가 지금까지 며칠 살아왔는지? {(int)times.TotalDays}"); 
    }
}

```

- 실행 결과

```cs
2024년도 크리스마스는 103일 남음
내가 지금까지 며칠 살아왔는지? 7048
```

>날짜 차이는 TimeSpan 구조체를 사용할 수 있다. 앞으로 남은 시간은 (해당 시간 - 현재 시간)을 TimeSpan 구조체 변수에 담고, 이 변수의 주요 속성을 사용하여 여러 가지 형태로 값을 추출해 낼 수 있다.

## 6.2 인라인 out 변수로 문자열 형식의 날짜를 날짜 형식으로 변환하기

- OutVariableDemo.cs

```cs
using System;

class OutVariableDemo
{
    static void Main()
    {
        if (DateTime.TryParse("2019/12/25", out var xmas))
        {
            Console.WriteLine(xmas);
        }
    }
}

```

- 실행 결과

```cs
2019-12-25 오전 12:00:00
```

>이 코드에서는 문자열 형식의 날짜이기에 날짜 형식인 DateTime의 xmas 변수를 생성하고 사용한다. 여기에서 out var xmas는 out DateTime xmas 형태로 명확하게 지정할 수도 있다.

## 6.3 1부터 8760까지 정수에 해당하는 날짜를 반환하는 함수

>DateTime 구조체의 AddHours() 같은 메서드를 사용하면 다음 유형을 구할 때 편리하다.

>일반적으로 1년은 365일 8760시간이다. 1년을 시간으로 환산하면 1부터 8760까지로 표현할 수 있다. 1은 20XX년 1월 1일 0시고, 8760은 20XX년 12월 31일 23시이다. 

- f(1) => 2019년 1월 1일 0시
- f(8760) => 2019년 12월 31일 23시
- f(x) => 해당 숫자에 맞는 일시

- GetDateTimeFromYearlyHour.cs

```cs
using System;

class GetDateTimeFromYearlyHour
{
    static void Main()
    {
        Console.WriteLine(GetDateTimeFromYearlyHourNumber(1));
        Console.WriteLine(GetDateTimeFromYearlyHourNumber(8760/2));
        Console.WriteLine(GetDateTimeFromYearlyHourNumber(8760));
    }

    static DateTime GetDateTimeFromYearlyHourNumber(int number)
    {
        return (new DateTime(2019, 1, 1, 0, 0, 0)).AddHours(--number);
    }
}

```

- 실행 결과

```cs
2019-01-01 오전 12:00:00
2019-07-02 오전 11:00:00
2019-12-31 오후 11:00:00
```

>DateTime 구조체의 AddHours() 메서드는 현재 시간에 시간 값을 더한 후 다시 그 값을 돌려준다. 이것으로 1월 1일 0시부터 12월 31일 23시까지의 시간을 1부터 8760에 해당하는 시간 정보로 변환해 알려 준다.

## 6.4 문자 관련 구조체 사용하기

- CharStruct.cs

```cs
using System;

class CharStruct
{
    static void Main()
    {
        char a = 'A'; char b = 'a';
        char c = '1'; char d = '\t'; // 이스케이프 시퀀스도 문자 하나로 인식

        if (Char.IsUpper(a))         // 대문자인가?
        {
            Console.WriteLine("{0}은(는) 대문자", a);
        }
        if (Char.IsLower(b))         // 소문자인가?
        {
            Console.WriteLine("{0}은(는) 소문자", b);
        }
        if (Char.IsNumber(c))        // 숫자형인가?
        {
            Console.WriteLine("{0}은(는) 숫자형", c);
        }
        if (Char.IsWhiteSpace(d))    // 공백 문자인가?
        {
            Console.WriteLine("{0}은(는) 공백 문자", d);
        }

        Console.WriteLine(Char.ToLower(a)); // A -> a
        Console.WriteLine(Char.ToUpper(b)); // a -> A

        string s = "abc";
        if (Char.IsUpper(s[0]))      // 첫 글자가 대문자인가?
        {
            Console.WriteLine("첫 글자가 대문자로 시작합니다.");
        }
        else
        {
            Console.WriteLine("첫 글자가 소문자로 시작합니다.");
        }

        Console.WriteLine(Char.MinValue); // 문자의 최솟값
        Console.WriteLine(Char.MaxValue); // 문자의 최댓값
    }
}

```

- 실행 결과

```cs
A은(는) 대문자
a은(는) 소문자
1은(는) 숫자형
        은(는) 공백 문자
a
A
첫 글자가 소문자로 시작합니다.

?
```

>이 실행 결과는 콘솔창에서 제대로 출력되지 않을 수 있다. System 네임스페이스에 있는 Char 구조체는 여러 가지 속성과 메서드를 제공한다. 이것으로 특정 문자에 대한 속성을 가져오거나 다른 문자 형태로 변환하는 등 작업을 할 수 있다.

## 6.5 Guid 구조체로 유일한 값 출력하기

>닷넷 프레임워크에 내장된 구조체 중에서 Guid는 GUID(Globally Unique IDentifier) 값을 출력한다. GUID 값은 유일한 값을 의미하는데, 실행할 때마다 동일한 값을 만날 확률이 0이다.

- GuidDemo.cs

```cs
using System;

class GuidDemo
{
    static void Main()
    {
        string unique = Guid.NewGuid().ToString();
        Console.WriteLine($"유일한 값 : {unique}");

        Console.WriteLine($"유일한 값 : {Guid.NewGuid().ToString("D")}");
    }
}

```

- 실행 결과

```cs
유일한 값 : 4a8f5b04-1dec-4a1d-bcb2-154c319a1ed9
유일한 값 : c8cc02b1-ae6d-453e-b2cf-c3038be04a03
```

>Guid.NewGuid().ToString() 형태로 실행할 때마다 서로 다른 문자열을 출력할 수 있다. 이렇게 출력되는 문자열은 데이터 레코드를 구분하는 고유한 키 값으로도 많이 사용한다.

>Guid 값을 ToString() 메서드로 출력할 때 형식 지정자로 D를 사용해 보았다. D를 사용하면 하이픈으로 구분된 32자리 숫자로 표현된다. D 이외에 N, B, P, X 등이 있다.

>DateTime과 TimeSpan 같은 내장 구조체는 많이 쓰지만, 사용자가 직접 만드는 사용자 정의 구조체는 잘 쓰지 않는다. 요즘은 클래스가 구조체 역할까지 하기에 주로 사용하며, 구조체는 내장 구조체를 기본으로 사용한다.