---
layout: single
title: Chapter 12 제어문 소개 및 if/else 문
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 제어문 소개 및 if/else 문에 대한 내용을 담고 있습니다.

>우리는 살면서 수많은 선택을 하고 반복된 일을 한다. 이는 프로그래밍에서도 마찬가지인데, 여러 갈래 중 하나를 선택하려면 조건문을 사용하고 자주 반복되는 일은 반복문으로 처리할 수 있다. 선택과 반복을 제어한다고 해서 제어문이라고 한다.

# 1 제어문

>제어문(control statement)은 프로그램 실행 순서를 제어하거나 프로그램 내용을 반복하는 작업 등을 처리할 때 사용하는 구문으로 조건문과 반복문으로 구분한다. 

- 제어문의 종류

| 제어문      | 설명                                                                                                                                                               | 종류                                                                            |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| 순차문      | 기본적으로 모든 실행문은 순서대로 실행된다.                                                                                                                                         |                                                                               |
| 조건문(선택문) | 조건의 참 또는 거짓에 따라 서로 다른 명령문을 <br>실행할 수 있는 구조이다. 조건문은 다른 말로 <br>분기문 또는 비교 판단문이라고도 한다.                                                                               | if 문(조건 하나 비교)<br><br>else 문(조건 분기)<br><br>switch 문(다양한 조건)                   |
| 반복문      | 특정 명령문을 저장된 수만큼 반복해서 <br>실행할 때나 조건식이 참일 동안 <br>반복시킬 때 사용한다.                                                                                                      | for 문(구간 반복)<br><br>do 문(선행 반복)<br><br>while 문(조건 반복)<br><br>foreach 문(배열 반복) |
| 기타       | break 문 : 반복문 내에서 반복을 중지한다.<br><br>continue 문 : 반복문 내에서 <br>그다음 반복문으로 이동한다.<br><br>goto 문 : C#에서 자주 사용하지 않지만, <br>레이블(레이블 이름과 콜론(:)으로 만듦)로 <br>지정된 곳으로 직접 이동시킨다. |                                                                               |

# 2 순차문 : 순서대로 실행하기

>프로그램은 기본적으로 다음 순서대로 실행된다. Main() 메서드 시작 지점부터 끝 지점까지 코드가 나열되면 순서대로 실행한 후 종료한다.

![](https://i.imgur.com/WRbS6ps.png)

- SequenceDemo.cs

```cs
using System;

class SequenceDemo
{
    static void Main()
    {
        int kor = 100;
        int eng = 90;

        int tot = 0;
        double avg = 0.0;

        tot = kor + eng; // 총점 구하기
        avg = tot / 2.0; // 평균 구하기

        Console.WriteLine("총점 : {0}", tot);
        Console.WriteLine("평균 : {0:F1}", avg);
    }
}
```

- 실행 결과

```cs
총점 : 190
평균 : 95.0
```

>순서대로 변수를 선언하고, 총점과 평균을 구하고, 그 값을 출력하는 형태로 실행하고 있다. 이처럼 프로그램은 기본적으로 Main() 메서드에서 순서대로 실행하게 되어 있다.

# 3 조건문 : if 문과 가지치기

>프로그램 흐름을 여러 가지 가지치기(branching)할 수 있는데, 이때 if 문을 사용한다. if 문은 조건을 비교해서 판단하는 구문으로 if, else if, else 세 가지 키워드가 있다. 다음과 같이 if 키워드 다음에 괄호를 사용하여 조건문을 기록한다.

>if 문의 기본 형태는 다음과 같다.

```cs
if (조건식)
{
	조건문의 조건을 만족할 때 실행할 실행문들...
}
```

>if 문은 if (조건식) 실행문; 형태인데, 괄호 안의 조건식(논리식)이 참이면 실행문(문장)을 실행한다. if 문은 다음과 같이 중괄호가 없는 형태로도 사용한다. 이 경우를 단문(single statement)이라고 하는데, 실행문이 하나만 있을 때는 중괄호를 생략할 수 있다.

```cs
if (조건식)
	실행문;
```

- Note

>단문을 사용하는 if (조건식) 문장; 형태는 한 줄로 쓰거나 바로 그다음 줄에 작성할 수 있다. 또는 괄호를 사용할 수도 있다. 복문이면 반드시 블록 기호인 중괄호({})가 있어야 한다.

- 단문과 복문

|     |                                                                                                                                                            |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 단문  | if (1 == 1) Console.WriteLine("단문 1");<br><br>if (1 == 1)<br>    Console.WriteLine("단문 2");<br><br>if (1 == 1)<br>{<br>    Console.WriteLine("단문 3");<br>} |
| 복문  | if (1 == 1)<br>{<br>    Console.WriteLine("복문 A");<br>    Console.WriteLine("복문 B");<br>}                                                                  |

>if 문 흐름을 그림으로 표현하면 다음과 같다. 이러한 그림을 순서도(flowchart)라고 한다.

![](https://i.imgur.com/AvBkLNY.png)

## 3.1 if 문을 사용하여 조건 하나 처리하기

- If.cs

```cs
using System;

class If
{
    static void Main()
    {
        int score = 60;

        if (score >= 60) // score가 60 이상이면 '합격' 출력
        {
            Console.WriteLine("합격");
        }
    }
}
```

- 실행 결과

```cs
합격
```

>if 문 괄호에는 조건식이 들어온다. (score >= 60) 식 결과가 참이면 '합격'을 출력하는 실행문을 실행하고, 조건식 결과가 거짓이면 아무것도 실행하지 않는다. 이처럼 if 문은 조건식이 참이면 실행하고 그렇지 않으면 아무것도 실행하지 않는 구조이다.

- Note

>비주얼 스튜디오에서 C# 코드를 작성할 때 if를 입력한 후 Tab을 두 번 누르면 자동으로 if 문 코드를 생성한다. if 문 및 else, for, while, do 등 주요 명령어에 대한 코드 조각을 모두 제공한다.

- if + Tab + Tab
- else + Tab + Tab
- for + Tab + Tab

## 3.2 if 문을 비교 연산자와 함께 사용하기

>조건문인 if 문은 말 그대로 조건을 판단하기에 비교 연산자와 함께 자주 사용한다.

- IfDemo.cs

```cs
using System;

class IfDemo
{
    static void Main()
    {
        int x = 10;

        if (x == 10)
        {
            Console.WriteLine($"x는 {x}입니다.");
        }

        if (x != 20)
        {
            Console.WriteLine($"x는 20이 아닙니다.");
        }
    }
}
```

- 실행 결과

```cs
x는 10입니다.
x는 20이 아닙니다.
```

>비교 연산자 결과가  참이면 if 문을 수행하고, 거짓이면 if 문을 수행하지 않고 다음으로 진행한다.

## 3.3 if 문을 사용하여 문자열 비교하기

>문자열을 비교할 때 대 ○ 소문자를 구분한다. 이 때문에 if 문과 같은 곳에서 문자열을 비교할 때는 주의해야 한다. 

```cs
> string s1 = "Hello.";
> string s2 = "Hello.";
> s1 == s2
true
> if (s1 == s2) // s1과 s2가 같으면 true
. {
.     Console.WriteLine("Same.");
. }
Same.
```

>두 변수 값이 같으면 Same.을 출력하고, 같지 않으면 아무것도 출력하지 않는다. 

## 3.4 !(NOT) 연산자를 if 문의 조건식에서 사용하기

- IfNot.cs

```cs
using System;

class IfNot
{
    static void Main()
    {
        bool bln = false;
        if (!bln) 
        {
            Console.WriteLine("bln : false -> ! -> true");
        }
    }
}
```

- 실행 결과

```cs
bln : false -> ! -> true
```

>'~가 아니라면 ~를 실행하라'는 의미로 if 문과 !(NOT) 연산자는 짝을 이루어서 많이 사용한다.

## 3.5 중첩 if 문

>if 문 안에는 또 다른 if 문을 넣을 수 있다. 이러한 형태를 중첩 if 문이라고 한다. 조건을 하나 만족하고 또 다른 조건을 만족할 때 어떤 일을 진행해야 한다면 중첩 if 문을 사용할 수 있다.

- IfNested.cs

```cs
using System;

class IfNested
{
    static void Main()
    {
        string name = "C#";
        int version = 8;

        if (name == "C#") // 첫 번째 조건
        {
            if (version == 8) // 두 번째 조건
            {
                Console.WriteLine($"{name} {version}");
            }
        }
    }
}
```

- 실행 결과

```cs
C# 8
```

>name과 version에 들어 있는 값이 if 문 조건식에 맞으면 최종적으로 "C# 8" 문자열이 출력되는 예제이다. 조건 여러 개를 만족하고자 할 때는 이처럼 if 문 여러 개로 묶어서 비교할 수 있는데, 이를 중첩 if 문이라고 한다.

## 3.6 if 문으로 한 번에 조건 여러 개 처리하기

>논리 연산자를 if 문과 함께 사용하면 if 문 하나로 조건 여러 개를 처리할 수 있다.

```cs
> int number = 1234;
> if (number == 1234 && number >= 1000) // 조건 2개를 모두 만족하면
. {
.     Console.WriteLine("맞습니다.");
. }
맞습니다.
> if (number == 1234 || number <= 1000) // 조건 2개 중 하나라도 만족하면
. {
.     Console.WriteLine("하나라도 참이면 참");
. }
하나라도 참이면 참
```

>if 문 조건식은 &&와 \|\| 연산자를 사용하여 하나 이상의 조건을 함께 처리할 수 있다.

- Note

>out 키워드는 인라인 out 변수라는 out var 형태의 코드로, 문자열에서 특정 값으로 변환되는 값을 담는 변수를 자동으로 선언해 준다. 

- OutVariable.cs

```cs
using System;

class OutVariable
{
    static void Main()
    {
        // C# 6.0까지 사용 방법 : 변수를 미리 선언
        int r;
        if (int.TryParse("안녕", out r))
        {
            // "안녕"은 int 형으로 변환이 불가능하기에 이 코드는 실행되지 않음
            Console.WriteLine("{0}", r);
        }

        // C# 7.0 이후 out var 방식
        if (int.TryParse("1234", out var result))
        {
            // "1234"는 int 형식으로 변환이 가능하기에 result 선언과 동시에 1234가 저장됨
            Console.WriteLine(result);
        }
        Console.WriteLine(result); // if 문 밖에서도 사용 가능
    }
}
```

- 실행 결과

```cs
1234
1234
```

>int.TryParse(), double.TryParse() 등 형식 변환 메서드는 자주 사용한다. 문자열로 입력받은 자료를 특정 형식으로 변환 가능하다면, 바로 해당 변수를 선언한 후 코드 내에서 사용할 수 있도록 편리한 기능을 제공하는 것이 out var 코드이다. 

# 4 else 문

>else 문은 단독으로 사용할 수 없고 if 문 다음에 else 문이 오는 구조이다. else 문을 사용하면 if 문 조건이 거짓일 때 원하는 실행문을 실행할 수 있어 두 방향으로 분기하는 구조를 만들 수 있다. 

>if~else 문 구조는 다음과 같다. 조건식이 참이면 실행문1을 실행하고, 그렇지 않으면 실행문2를 실행한다.

```cs
if (조건식)
{
	조건식이 참일 때 실행할 실행문1;
}
else
{
	조건식이 거짓일 때 실행할 실행문2;
}
```

>if~else 문 흐름을 순서도로 표현하면 다음과 같다.

![](https://i.imgur.com/8sKdj7b.png)

>if~else 문은 다음 샘플 코드의 형태처럼 사용한다. 조건식 (1 != 1)이 거짓이므로 실행문2가 실행된다.

```cs
> if (1 != 1)
. {
.     Console.WriteLine("조건식이 참이기에 현재 문장이 실행됩니다.");
. }
. else
. {
.     Console.WriteLine("조건식이 거짓이기에 현재 문장이 실행됩니다.");
. }
조건식이 거짓이기에 현재 문장이 실행됩니다.
```

>if~else 문은 이 샘플 코드처럼 조건식이 참이면 첫 번째 문장이 실행되고, 조건식이 거짓이면 두 번째 문장이 실행되는 구조이다. 

## 4.1 else 문으로 두 가지 조건 처리하기

>비주얼 스튜디오 편집기에서 else를 입력한 후 Tab을 두 번 누르면 자동으로 else 문의 중괄호가 생성된다.

- Else.cs

```cs
using System;

class Else
{
    static void Main()
    {
        int score = 59;

        if (score >= 60)
        {
            Console.WriteLine("합격");
        }
        else
        {
            Console.WriteLine("불합격");
        }
    }
}
```

- 실행 결과

```cs
불합격
```

>(score >= 60) 조건식이 거짓이므로 else 문이 실행되어 '불합격'이 출력된다. 조건이 같은지 물어보려면 다음과 같이 한다.

```cs
> double pi = 3.14;
> 
> if (pi == 3.14)
. {
.     Console.WriteLine("pi는 3.14입니다."); // 참일 때 실행
. }
. else
. {
.     Console.WriteLine("pi는 3.14가 아닙니다."); // 거짓일 때 실행
. }
pi는 3.14입니다.
```

>다음과 같이 두 수를 입력한 후 그중 큰 수를 출력하게 할 수 있다.

- GreaterThanEqual.cs

```cs
using System;

class GreaterThanEqual
{
    static void Main()
    {
        Console.Write("첫 번째 수 : ");
        int first = Convert.ToInt32(Console.ReadLine());
        Console.Write("두 번째 수 : ");
        int second = Convert.ToInt32(Console.ReadLine());

        if (first >= second)
        {
            Console.WriteLine("큰 값 : {0}", first);
        }
        else
        {
            Console.WriteLine("큰 값 : {0}", second);
        }
    }
}
```

- 실행 결과

```cs
첫 번째 수 : 3
두 번째 수 : 5
큰 값 : 5
```

>(first >= second) 조건식을 만족하면 first 변수 값이 더 큰 값이고, 조건을 만족하지 않으면 second 변수 값이 더 큰 값이 된다. 

>다음과 같이 두 수 차이를 양의 정수로 구할 수도 있다.

```cs
> int first = 3;
> int second = 5;
> int diff = 0;
> 
> if (first > second)
. {
.     diff = first - second; // first 변수가 더 큼
. }
. else
. {
.     diff = second - first; // second 변수가 더 큼 
. }
> 
> Console.WriteLine($"{first}과 {second}의 차이 : {diff}");
3과 5의 차이 : 2
```

>단순히 두 차이를 구하려면 첫 번째 변수에서 두 번째 변수 값을 빼면 된다. 하지만 차이를 양의 정수로 구하려면 두 수 중에서 큰 값을 먼저 계산한 후 큰 값에서 작은 값을 빼면 된다.

>다음 코드는 if~else 문으로 입력 문자에 대한 대 ○ 소문자를 구분해서 알려 주는 프로그램이다. 

- CharTest.cs

```cs
using System;

class CharTest
{
    static void Main()
    {
        Console.WriteLine("영문 대문자 또는 소문자 하나를 입력하세요.");
        char c = Convert.ToChar(Console.ReadLine());

        if (c >= 'A' && c <= 'Z')
        {
            Console.WriteLine($"{c}는 대문자입니다.");
        }
        else
        {
            Console.WriteLine($"{c}는 소문자입니다.");
        }
    }
}
```

- 실행 결과

```cs
영문 대문자 또는 소문자 하나를 입력하세요.
a
a는 소문자입니다.
```

## 4.2 중첩 if~else 문

>다음은 콘솔창에서 문자 하나를 입력받은 후 입력된 문자가 'y'이면 "Yes"를 출력하고, 'n'이면 "No"를 출력하고, 다른 문자가 입력되면 "Cancel"을 출력하는 프로그램이다. 

- ElseNested.cs

```cs
using System;

class ElseNested
{
    static void Main()
    {
        Console.WriteLine("문자를 입력하세요. (y/n/c) : ");
        char input = Convert.ToChar(Console.ReadLine());
        if (input == 'y')
        {
            Console.WriteLine("Yes");
        }
        else
        {
            if (input == 'n')
            {
                Console.WriteLine("No");
            }
            else
            {
                Console.WriteLine("Cancel");
            }
        }
    }
}
```

- 실행 결과

```cs
문자를 입력하세요. (y/n/c) :
y
Yes
```

>조건식에는 &&와 \|\| 연산자를 사용해서 여러 조건을 처리할 수도 있고 if 문 자체를 여러 번 사용해서 여러 조건을 처리할 수도 있다.

- IfElseScoreGrade.cs

```cs
using System;

class IfElseScoreGrade
{
    static void Main()
    {
        Console.Write("점수 : ");
        int score = Convert.ToInt32(Console.ReadLine());
        string grade = "";

        if (score >= 90)
        {
            grade = "금메달";
        }
        else
        {
            if (score >= 80)
            {
                grade = "은메달";
            }
            else
            {
                if (score >= 70)
                {
                    grade = "동메달";
                }
                else
                {
                    grade = "노메달";
                }
            }
        }

        Console.WriteLine($"{grade}을 수상했습니다.");
    }
}
```

- 실행 결과

```cs
점수 : 90
금메달을 수상했습니다.
```

# 5 else if 문(다중 if 문, 조건식 여러 개 처리)

>앞에서는 if~else 문을 여러 개 중첩해서 사용하여 다중으로 조건을 처리할 수 있었다. else if 문을 사용하면 중첩하지 않고 여러 조건을 처리할 수 있다. else if 문의 형태는 다음과 같다. else if 문 부분을 여러 개 두어 더 많은 조건을 처리할 수 있는 구조이다. 조건식1이 참이면 실행문1을 실행하고, 그렇지 않고 조건식2가 참이면 실행문2를 실행한다. 어떤 조건식도 만족하지 않으면 실행문 n을 실행한다.

```cs
if (조건식1)
{
	실행문1;
}
else if (조건식2)
{
	실행문2;
}
...
else
{
	실행문n;
}
```

>다중 if 문의 순서도 형태는 다음과 같다.

![](https://i.imgur.com/Nil5Bsa.png)

```cs
> int number1 = 10;
> int number2 = 20;
> 
> if (number1 > number2) // 조건 처리 1
. {
.     Console.WriteLine("number1이 더 큽니다.");
. }
. else if (number1 < number2) // 조건 처리 2
. {
.     Console.WriteLine("number2가 더 큽니다.");
. }
. else
. {
.     Console.WriteLine("둘 다 같습니다.");
. }
number2가 더 큽니다.
```

>첫 번째 if 문에서 첫 번째 조건을 처리한 후 조건을 만족하지 않으면 두 번째 else if 문의 조건을 따진다. 두 번째 else if 문의 조건이 참이면 실행하고, 그렇지 않으면 else 문을 실행한다.

## 5.1 양수, 음수, 0을 판단하는 프로그램

>else if 문으로 양수인지 음수인지 0인지를 판단하는 프로그램을 만들 수 있다.

- PositiveNegativeZero.cs

```cs
using System;

class PositiveNegativeZero
{
    static void Main()
    {
        int number = -10;    // (1) 원하는 정수 데이터 입력

        if (number > 0)      // (a) 양수인지 판단
        {
            Console.WriteLine($"{number}은 양수입니다.");
        }
        else if (number < 0) // (b) 음수인지 판단
        {
            Console.WriteLine($"{number}은 음수입니다.");
        }
        else
        {
            Console.WriteLine($"{number}은 0입니다.");
        }
    }
}
```

- 실행 결과

```cs
-10은 음수입니다.
```

>(1)에 입력한 데이터가 -10이기에 (b) else if 문이 실행된다.

## 5.2 성적 분류 프로그램

- ElseIf.cs

```cs
using static System.Console;

class ElseIf
{
    static void Main()
    {
        int score = 59;

        if (score >= 90)
        {
            WriteLine("A");
        }
        else if (score >= 80)
        {
            WriteLine("B");
        }
        else if (score >= 70)
        {
            WriteLine("C");
        }
        else if (score >= 60)
        {
            WriteLine("D");
        }
        else 
        {
            WriteLine("F");
        }
    }
}
```

- 실행 결과

```cs
F
```

>else if 문 여러 개를 사용하여 다중으로 조건을 처리하고 마지막 else 문을 기본값으로 사용하는 다중 if 문 예이다.

>또 다음과 같이 사용자가 입력하는 점수에 따라 학점을 계산하는 프로그램도 만들 수 있다. 

- ScoreGrade.cs

```cs
using System;

class ScoreGrade
{
    static void Main()
    {
        int score = 0;
        char grade = 'F';

        Console.WriteLine("당신의 점수는? ");
        score = Convert.ToInt32(Console.ReadLine());

        if (score >= 90)
        {
            grade = 'A';
        }
        else if (score >= 80)
        {
            grade = 'B';
        }
        else if (score >= 70)
        {
            grade = 'C';
        }
        else if (score >= 60)
        {
            grade = 'D';
        }
        else 
        {
            grade = 'F';
        }

        Console.WriteLine($"점수 : {score}점");
        Console.WriteLine($"학점 : {grade}학점");
    }
}
```

- 실행 결과

```cs
당신의 점수는?
100
점수 : 100점
학점 : A학점
```

# 6 조건문(if 문)을 사용한 조건 처리 전체 정리

- IfElseAll.cs

```cs
using System;

class IfElseAll
{
    static void Main()
    {
        Console.Write("정수 입력 : _\b");
        int a = Convert.ToInt32(Console.ReadLine());

        // (1) if 문
        if (a % 2 == 0) // 짝수라면...
        {
            Console.WriteLine("짝수");
        }

        // (2) else 문
        if (a % 2 != 0) // 홀수
        {
            Console.WriteLine("홀수");
        }
        else
        {
            Console.WriteLine("짝수");
        }

        // (3) else if 문
        if (a % 3 == 0)
        {
            Console.WriteLine("3의 배수");
        }
        else if (a % 5 == 0)
        {
            Console.WriteLine("5의 배수");
        }
        else if (a % 7 == 0)
        {
            Console.WriteLine("7의 배수");
        }
        else
        {
            Console.WriteLine("3, 5, 7의 배수가 아닌 수");
        }
    }
}
```

- 실행 결과 
	- 콘솔에서 4를 입력했을 때

```cs
정수 입력 : 4
짝수
짝수
3, 5, 7의 배수가 아닌 수
```

- 실행 결과 
	- 콘솔에서 13을 입력했을 때

```cs
정수 입력 : 13
홀수
3, 5, 7의 배수가 아닌 수
```

- (1) if 문
	- 입력된 숫자 값을 2로 나누었을 때 나머지가 0과 같으면(즉, 짝수이면) 메시지가 출력되고, 그렇지 않으면 다음 구문으로 넘어간다.

- (2) else 문
	- 입력된 숫자 값을 2로 나누었을 때 나머지가 0과 다르면, 즉 홀수이면 첫 번째 문장(홀수)을 수행하고 그렇지 않으면 두 번째 문장(짝수)을 수행한다.

- (3) else if 문
	- 입력된 숫자 값을 3으로 나누었을 때 나머지가 0이면(즉, 3의 배수이면) 첫 번째 문장을 수행한다. 그렇지 않고 입력된 숫자 값을 5로 나누었을 때 나머지가 0이면(즉, 5의 배수이면) 두 번째 문장을 수행하고, 아니면 나머지 문장을 수행한다.

>if 문과 같은 조건문은 어떤 문제를 해결할 때 주로 해당 데이터를 필터링(걸러 냄)하는 역할을 한다. 주어진 데이터에서 짝수만 걸러 낸다든가, 오늘 작성한 글만 검색한다든가 등 역할을 수행할 때도 if 문을 사용한다.

- Note

>if~else 문과 TryParse() 메서드를 함께 사용하면 특정 형식으로 변환이 가능한지 체크할 수 있다. 

```cs
> string data = "1234";
> int result;
> if (int.TryParse(data, out result))
. {
.     Console.WriteLine("변환 가능 : {0}", result);
. }
. else 
. {
.     Console.WriteLine("변환 불가");
. }
변환 가능 : 1234
> double d;
> if (Double.TryParse(data, out d))
. {
.     Console.WriteLine("변환 가능 : {0}", d);
. }
변환 가능 : 1234
```

>TryParse() 메서드는 특정 형식으로 변환이 가능하면 true를 반환한다. C# 7.0 버전 이후로는 out var 형식을 지원하기에, 다음 코드처럼 미리 변수를 선언할 필요 없이 if 문에 out var r 형식으로 r 변수를 직접 만들어 사용할 수 있다.

```cs
> if (double.TryParse("3.14", out var r))
. {
.     WriteLine($"{r} : {r.GetType()}"); // 3.14 : System.Double
. }
. else
. {
.     WriteLine("변환 불가");
. }
3.14 : System.Double
> r
3.14
```

>변환이 가능하면 r 변수에는 변환된 값이 저장되고, 그렇지 않으면 데이터 형식의 기본값이 저장된다.

