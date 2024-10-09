---
layout: single
title: Chapter 16 break, continue, goto로 반복문 제어하기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 break, continue, goto로 반복문 제어하기에 대한 내용을 담고 있습니다.

>break 문은 반복문과 switch 문을 빠져나가는 역할을 한다. continue 문은 반복문의 나머지 코드를 실행하지 않고 반복문 다음 처리 영역으로 넘어간다. goto 문은 특정 레이블로 지정된 영역으로 이동한다. 

# 1 break 문

>반복문(for, while, do)을 빠져나올 때는 break 문을 사용할 수 있다.

## 1.1 아무것도 하지 않는 프로그램

>다음 코드는 말 그대로 아무것도 하지 않는 프로그램이다. for 문 안에 break를 두어 바로 for 문을 빠져나온다. 

- BreakFor.cs

```cs
using System;

class BreakFor
{
    static void Main()
    {
        for (int i = 0; i < 5; i++)
        {
            if (i >= 0)
            {
                break; // 현재 코드를 만나면 현재 for 문을 종료함
            }
        }
    }
}
```

- 실행 결과

```cs
이 창을 닫으려면 아무 키나 누르세요...
```

>이처럼 break 키워드를 사용하여 for, while, do 반복문을 바로 빠져나올 수 있다.

## 1.2 무한 루프 빠져나오기

>프로그래밍 언어에서 무한 루프는 조건이 맞지 않아 루프를 무한정 도는 경우이다. 특정 조건을 만족할 때 루프를 빠져나오는 구문은 continue 또는 break를 사용할 수 있다.

- BreakInfiniteLoop.cs

```cs
using System;

class BreakInfiniteLoop
{
    static void Main()
    {
        int number = 0;

        while (true) // 무한 루프
        {
            Console.WriteLine(++number);

            if (number >= 5)
            {
                break;
            }
        }
    }
}
```

- 실행 결과

```cs
1
2
3
4
5
```

>while (true)는 무한 루프이다. while 문이 계속해서 반복하도록 설정한 후 number 값을 1씩 증가시켜 출력하고, 5보다 커지면 break로 while 문을 빠져나오도록 했다.

## 1.3 break로 반복문 끝내기

- BreakDemo.cs

```cs
using System;

class BreakDemo
{
    static void Main()
    {
        for (int i = 0; i < 100; i++)
        {
            if (i == 5)
            {
                break; // i == 5일 때 for 문 종료
            }
            Console.Write($"{(i + 1)}번 반복\t");
        }
        Console.WriteLine();
    }
}
```

- 실행 결과

```cs
1번 반복        2번 반복        3번 반복        4번 반복        5번 반복
```

>for 문과 while 문에서 break를 만나면 바로 반복문을 더 이상 실행하지 않고 빠져나온다.

## 1.4 break 문을 사용하여 while 문 빠져나오기

- WhileBreak.cs

```cs
using System;

class WhileBreak
{
    static void Main()
    {
        int goal = 22;
        int sum = 0;

        int i = 1;
        while (i <= 10)
        {
            sum += i;

            if (sum >= goal)
            {
                break;
            }

            i++;
        }

        Console.WriteLine(
            $"1부터 {i}까지의 합은 {sum}이고, 목표치 {goal} 이상을 달성했습니다.");
    }
}
```

- 실행 결과

```cs
1부터 7까지의 합은 28이고, 목표치 22 이상을 달성했습니다.
```

>합을 계속 구해 나가는 과정에서 22 이상이 되면 더 이상 합계를 구하지 않고 반복문을 빠져나올 때 break 키워드를 사용한다.

# 2 continue 문으로 코드 건너뛰기

- ForIfContinue.cs

```cs
using System;

class ForIfContinue
{
    static void Main()
    {
        for (int i = 1; i <= 5; i++)
        {
            if (i % 2 == 0)
            {
                // 현재 반복 중지 후 다음 반복으로 이동
                continue; // 짝수 건너뛰기
            }
            Console.WriteLine(i); // 1, 3, 5
        }
    }
}
```

- 실행 결과

```cs
1
3
5
```

>for를 사용하여 1부터 5까지 반복한다. 그리고 if를 사용하여 짝수인지 판단하여 짝수이면 continue를 실행한다. 반복문에서 continue를 만나면 continue 아래 코드는 실행하지 않고 반복문의 다음 반복으로 이동한다. for 문에서는 증감식(i++)으로 이동한다. 이러한 continue의 동작은 for, while, do 문에서도 동일하다. 

## 2.1 continue 문으로 3의 배수를 제외한 수의 합 구하기

```cs
> int sum = 0;
> for (int i = 1; i <= 100; i++)
. {
.     if (i % 3 == 0)
.     {
.         continue; // 3의 배수이면 [i++] 코드 영역으로 이동
.     }
.     sum += i;
. }
> Console.WriteLine("SUM : {0}", sum);
SUM : 3367
```

>if (i % 3 == 0) { continue; } 코드로 3의 배수일 때는 continue를 만나서 이후 실행문을 실행하지 않고 다음 반복으로 넘어간다. 그래서 3의 배수를 제외한 수의 합만 sum 변수에 저장된다.

# 3 goto로 프로그램 흐름을 원하는 대로 바꾸기

>goto 구문은 특정 레이블로 이동하는 기능을 한다. C#에서 레이블은 콜론(:) 기호를 레이블 이름 뒤에 붙여 만든다. 이렇게 만든 레이블 코드는 평상시에는 주석처럼 아무 의미 없는 코드로 사용하지만, goto 구문 뒤에 레이블을 지정하면 해당 레이블로 이동하는 기능을 한다.

```cs
레이블:
goto 레이블:
```

- GoToDemo.cs

```cs
using System;

class GoToDemo
{
    static void Main()
    {
        Console.WriteLine("시작");
        Start:
        Console.WriteLine("0, 1, 2 중 하나 입력 : _\b");
        int chapter = Convert.ToInt32(Console.ReadLine());

        if (chapter == 1)
        {
            goto Chapter1; // (1)번 코드 영역으로 이동
        }
        else if (chapter == 2)
        {
            goto Chapter2; // (2)번 코드 영역으로 이동
        }
        else 
        {
            goto End;      // (3)번 코드 영역으로 이동
        }

        Chapter1:          // (1)
        Console.WriteLine("1장입니다.");

        Chapter2:          // (2)
        Console.WriteLine("2장입니다.");

        goto Start;

        End:               // (3)
        Console.WriteLine("종료");
    }
}
```

- 실행 결과

```cs
시작
0, 1, 2 중 하나 입력 : _
1
1장입니다.
2장입니다.
0, 1, 2 중 하나 입력 : _
2
2장입니다.
0, 1, 2 중 하나 입력 : _
1
1장입니다.
2장입니다.
0, 1, 2 중 하나 입력 : _
2
2장입니다.
0, 1, 2 중 하나 입력 : _
0
종료
```

>사용자한테 0, 1, 2 중 하나를 입력받은 후 1이면 Chapter1로 설정된 레이블로 이동하고, 2이면 Chapter2로 이동하고, 나머지 값이 입력되면 End 레이블로 이동하여 프로그램을 종료한다.

>점프문은 for, while, do, foreach 등과 함께 사용하여 실행 시점을 다른 곳으로 이동(점프)시키는 역할을 한다. 참고로 goto 문은 최근에는 거의 사용하지 않는 구문이다. 

