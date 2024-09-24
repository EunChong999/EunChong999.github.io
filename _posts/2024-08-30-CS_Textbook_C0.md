---
layout: single
title: Chapter 21 열거형 형식 사용하기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 열거형 형식 사용하기에 대한 내용을 담고 있습니다.

# 1 열거형 형식 사용하기

>C#에서 열거형(enumeration) 형식은 기억하기 어려운 상수들을 기억하기 쉬운 이름 하나로 묶어 관리하는 표현 방식이다. 일반적으로 열거형으로 줄여 말한다. 열거형을 사용하면 값 리스트 여러 개를 이름 하나로 관리할 수 있는 장점이 있다. 열거형은 enum 키워드를 사용하고 이늄 또는 이넘으로 읽는다. 

## 1.1 ConsoleColor 열거형으로 콘솔의 전경색 및 배경색 바꾸기

- ConsoleColorDemo.cs

```cs

```

>예제를 실행하면 다음 화면이 나온다.

![](https://i.imgur.com/ZZmA52N.png)

>ConsoleColor 열거형은 Red, Green, Blue 같은 색상 값을 편리하게 기억할 수 있게 한다. ConsoleColor 열거형을 Console.ForegroundColor와 Console.BackgroundColor 속성에 대입하면 글자색 및 배경색으로 바꿀 수 있다.

>비주얼 스튜디오에서 ConsoleColor를 입력한 후 점(.)을 누르면 ConsoleColor 열거형의 목록이 나타나 콘솔에서 사용할 수 있는 색상 값을 편리하게 지정할 수 있다. 이처럼 ConsoleColor 같은 열거형을 사용하면 색상 항목 여러 개를 모두 기억할 필요 없이 ConsoleColor 열거형 이름 하나만 기억하면 되므로 프로그램 코드를 작성할 때 편리하다.

# 2 열거형 만들기

>이미 만들어져 있는 열거형이 아닌 원하는 열거형을 직접 정의해서 사용할 수도 있다. 이를 사용자 정의 열거형이라고 한다. 사용자 정의 열거형은 다음과 같이 enum 키워드를 사용하여 선언할 수 있다.

```cs
enum 열거형이름
{
    열거형변수1,
    열거형변수2,
    열거형변수3
}
```

>열거형을 선언할 때 다음과 같이 기본값을 설정할 수도 있다.

```cs
enum 열거형이름
{
    열거형변수1 = 기본값1,
    열거형변수2 = 기본값2,
    열거형변수3 = 기본값3
}
```

- EnumerationDemo.cs

```cs
using System;

enum Priority // 우선순위를 묶어 관리할 수 있는 Priority 열거형 생성
{
    High,
    Normal,
    Low
}

class EnumerationDemo
{
    static void Main()
    {
        Priority high = Priority.High; // 인텔리센스의 도움을 받을 수 있어 편리함
        Priority normal = Priority.Normal;
        Priority low = Priority.Low;

        Console.WriteLine($"{high}, {normal}, {low}");
    }
}
```

- 실행 결과

```cs
High, Normal, Low
```

>우선순위를 나타내는 Priority 열거형에 High, Normal, Low 세 가지 항목을 준다. Priority high 변수에는 Priority.High 값을 주는 형태로 Priority 열거형을 사용할 수 있다. 열거형 변수 값을 콘솔에서 문자열로 출력하면 열거형의 멤버 이름이 문자열로 출력된다.

# 3 열거형 항목에 상수 값 주기

```cs
enum Align
{
	Top,
	Bottom,
	Left,
	Right
}
```

>앞처럼 열거형을 선언하면 기본적으로 Align.Top은 0, Align.Bottom은 1, Align.Left는 2, Align.Right는 3의 상수 값을 가진다. 기본값 이외의 값으로 설정하려면 다음 코드 샘플처럼 각 항목에 원하는 값을 지정한다.

```cs
enum Align
{
	Top = 0,
	Bottom = 2,
	Left = 4,
	Right = 8
}
```

>요일 정보를 열거형으로 관리하면 다음과 같이 선언할 수 있다.

```cs
enum Weekday
{
	Sunday,    Monday,    Tuesday,    Wednesday,    Thursday,   Friday,    Saturday
}
```

>마찬가지로 커피 사이즈에 대한 열거형은 다음과 같이 선언할 수 있다.

```cs
enum CoffeeSize
{
	Small,    Medium,    Large
}
```

>이처럼 열거형을 사용하면 여러 개로 구성된 상수들을 열거형 이름 하나로 묶어 관리하기 편하다.

## 3.1 열거형으로 관련 있는 항목을 묶어 관리하기

- EnumAnimal.cs

```cs
using System;

class EnumAnimal
{
    enum Animal { Mouse, Cow, Tiger }

    static void Main()
    {
        Animal animal = Animal.Tiger;
        Console.WriteLine(animal);

        if (animal == Animal.Tiger)
        {
            Console.WriteLine("호랑이");
        }
    }
}
```

- 실행 결과

```cs
Tiger
호랑이
```

>프로그램 소스 코드를 작성할 때 비주얼 스튜디오는 다음과 같이 자동으로 열거형 목록을 인텔리센스로 제공한다.

![](https://i.imgur.com/O54ABhK.png)

>열거형을 사용하면 항목 여러 개를 이름(Animal) 하나로 관리하기에 프로그램을 비주얼 스튜디오의 인텔리센스 도움을 받으면서 만들 수 있어 편리하다.

## 3.2 열거형 값을 정수형 또는 문자열로 사용하기

>열거형의 각 항목은 지정하는 순서대로 0번째 인덱스부터 정수형 값이 저장된다. 열거형 값을 정수형으로 변환하면 각각의 인덱스를 반환한다. 

- EnumIndex.cs

```cs
using System;

namespace EnumIndex
{
    enum Animal { Rabbit, Dragon, Snake }

    class EnumIndex
    {
        static void Main()
        {
            Animal animal = Animal.Dragon;
            int num = (int)animal;
            string str = animal.ToString();
            Console.WriteLine($"Animal.Dragon : {num}, {str}");
        }
    }
}
```

- 실행 결과

```cs
Animal.Dragon : 1, Dragon
```

>Animal 열거형은 Rabbit, Dragon, Snake 3개를 멤버로 가진다. 또 각 멤버는 0, 1, 2의 인덱스 값을 가진다. 열거형 변수인 animal을 정수형으로 변환하여 출력하면 각 멤버가 가지는 인덱스 값이 출력되고, 문자열로 변환하여 출력하면 각 멤버 이름이 출력된다.

## 3.3 열거형 인덱스 순서 변경하기

>열거형 인덱스의 기본값은 0, 1, 2이지만 새로운 값으로 설정할 수 있다.

- EnumIndexChange.cs

```cs
using System;

enum Animal
{
    Horse,      // 0
    Sheep = 5,  // 1 => 5
    Monkey      // 2 => 6
}

class EnumIndexChange
{
    static void Main()
    {
        Console.WriteLine((int)Animal.Monkey);
    }
}
```

- 실행 결과

```cs
6
```

>Animal 열거형의 세 가지 항목인 Horse, Sheep, Monkey는 기본적으로 0, 1, 2의 값을 가진다. Sheep 값을 5로 설정하면 Monkey는 그다음 값인 6으로 자동 설정된다.

## 3.4 열거형과 switch 문 함께 사용하기

>열거형 값을 비교할 때는 switch 문과 사용하면 편리하다.

- EnumSwitch.cs

```cs
using System;

namespace EnumSwitch
{
    enum Animal { Chicken, Dog, Pig }

    class EnumSwitch
    {
        static void Main()
        {
            Animal animal = Animal.Dog;

            switch (animal)
            {
                case Animal.Chicken:
                    Console.WriteLine("닭");
                    break;
                case Animal.Dog:
                    Console.WriteLine("개");
                    break;
                case Animal.Pig:
                    Console.WriteLine("돼지");
                    break;
                default:
                    Console.WriteLine("기본값 설정 영역");
                    break;
            }
        }
    }
}
```

- 실행 결과

```cs
개
```

>코드 자체만 보아서는 값을 비교하는 부분이 길어 보인다. 하지만 비주얼 스튜디오에서는 열거형 값을 switch 문에 대입하면 자동으로 열거형 항목에 해당하는 case 문을 만드는 기능을 제공하기에 편리하게 입력할 수 있다.

# 4 열거형 관련 클래스 사용하기

## 4.1 지정된 열거형의 상수 리스트를 배열로 가져오기

>Enum 클래스의 GetNames() 메서드를 사용하면 지정된 열거형에서 상수 이름의 배열을 검색한다. 

- EnumGetNames.cs

```cs
using System;
class EnumGetNames
{
    static void Main()
    {
        Type cc = typeof(ConsoleColor);       // ConsoleColor 열거형의 Type을 cc 변수에 저장
        string[] colors = Enum.GetNames(cc);  // 모든 색상 이름을 반환

        foreach (var color in colors)         // 출력
        {
            Console.WriteLine(color);
        }
    }
}
```

- 실행 결과

```cs
Black
DarkBlue
DarkGreen
... 이하 생략
```

>ConsoleColor 같은 열거형의 모든 멤버를 문자열 배열로 얻을 때는 Enum.GetNames() 메서드에 해당 열거형 형식을 typeof 연산자로 지정하면 된다. 참고로 실행 결과는 다르게 나올 수 있다.

## 4.2 문자열을 특정 열거형으로 변환하기

>Enum.Parse() 메서드로 문자열을 사용하여 실제 열거형을 만들 수 있다. 하나 이상 열거된 상수 이름이나 숫자 값의 문자열 표현을 해당하는 열거형 개체로 변환한다.

- EnumParse.cs

```cs
using System;
class EnumParse
{
    static void Main()
    {
        string color = "Red"; // 열거형에 없는 상수 문자열을 지정하면 예외

        // (1) 문자열로 지정 문자열에 해당하는 열거 상수 가져오기
        Console.ForegroundColor = //ConsoleColor.Red;
            (ConsoleColor)Enum.Parse(typeof(ConsoleColor), color);

        Console.WriteLine("Red");
        Console.ResetColor();
    }
}
```

![](https://i.imgur.com/hROUZW1.png)

>(1)에서 직접 ConsoleColor.Red를 지정할 수 있다. "Red" 문자열을 받으면 Red 상수로 변경하고, "Black" 상수를 받으면 Black 상수로 변경하는 등 프로그래밍을 할 때 Enum.Parse() 메서드를 사용할 수 있다.

>열거형을 사용하면 변수에 어떤 값을 저장해야 하는지 명확한 값 목록을 제공한다. 이때 비주얼 스튜디오의 인텔리센스 기능을 이용하면 점(.)만 찍으면 해당 목록이 제공되기에 편리함을 느낄 수 있다. 처음에 열거형을 만드는 수고는 큰 프로그램을 제작할 때 여러모로 도움이 되는 C#의 필수 기능이다. 