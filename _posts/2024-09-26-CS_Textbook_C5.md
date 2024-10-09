---
layout: single
title: Chapter 26 제네릭 사용하기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 제네릭 사용하기에 대한 내용을 담고 있습니다.

>C# 2.0 버전부터는 제네릭(generic)이라고 해서 특정 형식을 지정하여 컬렉션에 저장하고 사용할 수 있다. 제네릭 컬렉션은 다른 데이터 형식을 추가할 수 없도록 형식의 안정성을 적용한다. 고전적인 컬렉션 클래스와 달리 System.Collections.Generic 네임스페이스에 들어 있는 제네릭 컬렉션 클래스는 요소를 다룰 때 데이터 형식 변환 등 작업이 따로 필요하지 않다. 제네릭은 Cup<\T>를 Cup Of T로 발음하여 형식 매개변수인 T에 따른 Cup 클래스의 개체를 생성하는 것이다.

# 1 Cup of T

>컵(Cup)에 들어가는 Tea(T)가 무엇인지에 따라 오렌지 주스 컵, 커피 컵, 사이다 컵 등이 결정된다. 이처럼 넘어오는 데이터 형식에 따라 해당 개체 성격을 변경하는 구조를 제네릭이라고 한다. 제니릭을 사용하면 여러 목적의 컬렉션 형식을 만들 수 있다. 

# 2 Stack 제네릭 클래스 사용하기

>Stack 클래스의 제네릭 버전은 Stack<\T> 형태로 표현한다. 영어 발음으로는 Stack of T로 발음한다. T는 특정 형식을 받아들이는 형식 매개변수이다. 

1 . 먼저 Stack<\T> 클래스를 사용하려면 System.Collections.Generic 네임스페이스를 포함한다.

```cs
> using System.Collections.Generic;
```

2 . 제네릭 클래스의 인스턴스를 생성하려면 Stack<\T> 형태인 Stack<\string>으로 문자열만 다룰 수 있는 Stack 클래스를 만들어야 한다.

```cs
> Stack<string> stack = new Stack<string>();
```

3 . Stack<\string>으로 선언된 stack 개체는 문자열만 입력받을 수 있다.

```cs
> stack.Push("First");
```

4 . 마찬가지로 Pop() 메서드의 결과도 문자열로 바로 출력된다.

```cs
> stack.Pop()
"First"
```

>일반 클래스인 Stack 제네릭 클래스인 Stack<\T>는 하는 일이 동일하다. 다만 Stack 클래스는 데이터를 object로 다루고, Stack<\T> 클래스는 T로 지정한 데이터로 다룬다. object로 만든 데이터를 실제 사용하려는 string과 같은 형식으로 표현할 때는 중간에 변환 과정을 거치기 때문에 이 부분에서 추가 작업을 진행하는 비용이 발생한다. 그래서 정확한 데이터 형식을 쓸 수 있는 Stack<\T> 같은 제네릭 클래스를 사용하면 좋다.

## 2.1 제네릭 클래스 사용의 장점

1 . Stack 클래스는 System.Collections 네임스페이스에 있는 오래된 클래스이다.

```cs
> // (1) 제네릭 사용 전
> using System.Collections;
> Stack stack = new Stack();
> stack.Push(3840);
> int width = (int)stack.Pop(); // Convert 필요
> width
3840
```

>일반 클래스를 사용하면 Push() 메서드에 object로 값을 받고 Pop() 메서드에서도 object로 반환하기에 (int) 코드를 붙이는 것과 같은 형식 변환이 필요하다.

2 . Stack<\T> 클래스는 제네릭 클래스로 System.Collections.Generic 네임스페이스에 있다.

```cs
> // (2) 제네릭 사용 후
> using System.Collections.Generic;
> Stack<int> stack = new Stack<int>();
> stack.Push(2160);
> int height = stack.Pop(); // Convert 필요 없음
> height
2160
```

>제네릭 클래스를 사용하면 Stack<\T> 클래스에 저장된 Stack<\int> 형태로 int 형식의 데이터만 받고, Pop() 메서드에서도 int 형식으로 반환하기에 따로 형식 변환이 필요 없다.

3 . Stack이 아닌 Stack<\T> 클래스를 사용하면 값형 데이터를 참조형 데이터로 변환하는 박싱 작업과 그 반대로 참조형 데이터를 값형 데이터로 변환하는 언박싱 작업을 하지 않아도 되므로 성능이 향상된다. 또 Stack<\int>처럼 명확하게 int 형식 데이터만 받게 지정하면 string 형식이 들어올 때 에러를 발생시키므로 안정적이다. 

```cs
> // 제네릭 장점 : (a) 박싱과 언박싱에 대한 비용
> Stack stack = new Stack();
> stack.Push(1234);           // int(값형) to object(참조형) : 박싱
> int num = (int)stack.Pop(); // object(참조형) to int(값형) : 언박싱
> num
1234
> 
> // 제네릭 장점 : (b) 필요한 데이터 형식만 사용하여 형식이 안정적
> Stack<int> stack = new Stack<int>();
> stack.Push("Hello");
(1,12): error CS1503: 1 인수: 'string'에서 'int'(으)로 변환할 수 없습니다.
> stack.Push(5678);
> int num = stack.Pop();
> num
5678
```

# 3 List<\T> 제네릭 클래스 사용하기

>List<\T>는 List of T로 읽는다. 즉, 무언가의 리스트를 나타낸다. 예를 들어 List<\int>는 정수형 리스트를 나타내고, List<\string>은 문자열의 리스트를 나타낸다. 

## 3.1 배열과 List<\T> 제네릭 클래스

>정수형 배열을 사용하여 데이터 2개를 담고 출력하는 코드는 다음과 같다.

```cs
> // (1) 배열 사용
> int[] arrNumbers = new int[2];
> arrNumbers[0] = 10;
> arrNumbers[1] = 20;
> for (int i = 0; i < arrNumbers.Length; i++)
. {
.     Console.WriteLine(arrNumbers[i]);
. }
10
20
```

>제네릭 리스트를 사용하여 앞 코드와 기능이 동일한 코드를 다음과 같이 작성할 수 있다.

```cs
> List<int> lstNumbers = new List<int>();
> lstNumbers.Add(30);
> lstNumbers.Add(40);
> for (int i = 0; i < lstNumbers.Count; i++)
. {
.     Console.WriteLine(lstNumbers[i]);
. }
30
40
```

## 3.2 리스트 제네릭 클래스

>C#에서 사용하는 제네릭 클래스 중에서 List<\T> 제네릭 클래스를 자주 사용한다. 이를 사용하면 특정 형식에 해당하는 리스트(컬렉션, 배열)을 아주 쉽게 만들고 관리할 수 있다.

```cs
> using System.Collections.Generic;
> 
> List<string> colors = new List<string>(); // (1) 인스턴스 생성 및 샘플 데이터 입력
> colors.Add("Red");
> colors.Add("Green");
> colors.Add("Blue");
> 
> for (int i = 0; i < colors.Count; i++)    // (2) for 문으로 출력하는 예
. {
.     Console.Write($"{colors[i]}\t");
. }
Red    Green    Blue	
> 
> foreach (var color in colors)             // (3) foreach 문으로 출력하는 예 
. {
.     Console.Write($"{color}\t");
. }
Red	   Green	Blue	
```

>List<\string>, List<\int>, List<\decimal> 등 특정 형태를 담을 수 있는 컬렉션 클래스도 만들 수 있다. 이렇게 만든 제네릭 컬렉션 개체는 for 문 또는 foreach 문 등으로 쉽게 가져다 사용할 수 있다.

# 4 Enumerable 클래스로 컬렉션 만들기

>System.Linq 네임스페이스에 들어 있는 Enumerable 클래스는 Range()와 Repeat() 메서드를 제공하므로 특정 범위의 정수 컬렉션을 손쉽게 만들 수 있다. Enumerable.Range() 메서드는 테스트용으로 만들 때 유용하다.

- **Enumerable.Range(1, 10)**
	- 1에서 10까지 정수 컬렉션 생성

- **Enumerable.Range(0, 10)**
	- 0에서 9까지 정수 컬렉션 생성

- **Enumerable.Repeat(-1, 10)**
	- -1을 열 번 반복하는 정수 컬렉션 생성

>다음과 같이 Enumerable.Range(1, 10)을 요청하면 1부터 10까지 정수 컬렉션을 만든다. C# 인터렉티브에서는 for 문 또는 foreach 문을 사용하지 않고도 바로 결괏값을 확인할 수 있다. 

```cs
> Enumerable.Range(1, 10)
RangeIterator { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 }
```

>또 다른 유용한 메서드인 Repeat()에 (100, 5) 형태로 매개변수를 전달하면 100이 5개인 정수 컬렉션을 만든다. 

```cs
> Enumerable.Repeat(100, 5)
RepeatIterator { 100, 100, 100, 100, 100 }
```

>콤마가 포함된 배열을 가져오려면 string.Join() 메서드와 함께 사용한다.

```cs
> string.Join(",", Enumerable.Range(1, 5))
"1,2,3,4,5"
```

>다음 코드는 메서드 체인 방식으로 1부터 100까지 정수 중 짝수를 구하고 거꾸로 정렬한 후 10개를 제외하고 5개를 가져온다. 

```cs
> Enumerable.Range(1, 100).Where(i => i % 2 == 0).Reverse().Skip(10).Take(5)
TakeIterator { 80, 78, 76, 74, 72 }
```

## 4.1 Enumerable 클래스의 주요 메서드 사용하기

- EnumerableDemo.cs

```cs
using System;
using System.Linq;

class EnumerableDemo
{
    static void Main()
    {
        var numbers = Enumerable.Range(1, 5); // 1부터 5까지
        foreach (var n in numbers)
            Console.Write("{0}\t", n);
        Console.WriteLine();

        var sameNumbers = Enumerable.Repeat(-1, 5); // -1을 5개
        foreach (var n in sameNumbers)
            Console.Write("{0}\t", n);
        Console.WriteLine();
    }
}
```

- 실행 결과

```cs
1       2       3       4       5
-1      -1      -1      -1      -1
```

# 5 Dictionary<\T, \T> 제네릭 클래스 사용하기

1 . Dictionary<\T, \T> 제네릭 클래스는 문자열과 같은 키와 값의 쌍으로 데이터를 관리한다. 다음 코드는 string 키와 string 값을 컬렉션으로 관리할 수 있는 data 개체를 Dictionary 제네릭 클래스로 만든다.

```cs
> // (1) Dictionary 클래스의 인스턴스 생성 : IDictionary 인터페이스로 받기
> IDictionary<string, string> data = new Dictionary<string, string>();
```

>물론 다음과 같이 var로 줄임 표현해도 된다. 

```cs
> // (1) 간단히 아래처럼 사용 가능
> var data = new Dictionary<string, string>();
```

2 . Add() 메서드로 데이터를 입력하고, Remove() 메서드로 데이터를 삭제할 수 있다. 또 배열의 [] 기호를 사용하여 값을 추가할 수도 있다. 키 값은 중복을 허용하지 않기에 이미 있는 키 값을 추가할 때는 에러가 발생한다.

```cs
> data.Add("cs", "C#");           // (2) 데이터 입력
> data.Add("aspx", "ASP.NET");
> 
> data.Remove("aspx");            // (3) 데이터 삭제
> data["cshtml"] = "ASP.NET MVC"; // (4) 인덱서를 사용해서 데이터 입력
> 
> try                             // (5) 키 값 중복 불가 : 에러 발생
. {
.     data.Add("cs", "Csharp");
. }
. catch (Exception ex)
. {
.     Console.WriteLine(ex.Message);
. }
동일한 키를 사용하는 항목이 이미 추가되었습니다.
```

4 . 여러 가지 방식으로 Dictionary 개체 값을 출력한다.

```cs
> // (6) 출력 : foreach (var item in data)로 줄임 표현 가능
> foreach (KeyValuePair<string, string> item in data)
. {
.     Console.WriteLine("{0}은(는) {1}의 확장자입니다.", item.Key, item.Value);
. }
cs은(는) C#의 확장자입니다.
cshtml은(는) ASP.NET MVC의 확장자입니다.
> 
> foreach (var item in data)
. {
.     Console.WriteLine("{0}은(는) {1}의 확장자입니다.", item.Key, item.Value);
. }
cs은(는) C#의 확장자입니다.
cshtml은(는) ASP.NET MVC의 확장자입니다.
> 
> Console.WriteLine(data["cs"]); // (7) 인덱서를 사용하여 출력 가능
C#
```

5 . 없는 키 값을 요청하면 에러가 발생한다. 이때 TryGetValue() 또는 ContainsKey() 메서드를 사용하여 확인 또는 값을 추가할 수 있다.

```cs
> // (8) 없는 키 요청 : 에러 발생
> try
. {
.     Console.WriteLine(data["vb"]);
. }
. catch (KeyNotFoundException knfe)
. {
.     Console.WriteLine(knfe.Message);
. }
지정한 키가 사전에 없습니다.
> 
> // (9) cs 키가 있으면 csharp 변수에 담아 출력
> if (data.TryGetValue("cs", out var csharp))
. {
.     Console.WriteLine(csharp);
. }
C#
> // (9) cs 키가 있으면 csharp 변수에 담아 출력
. if (data.TryGetValue("cs", out var csharp))
. {
.     Console.WriteLine(csharp);
. }
. else
. {
.     Console.WriteLine("cs 키가 없습니다.");
. }
C#
> 
> // (10) 키 값이 없으면 입력하고 출력
> if (!data.ContainsKey("json"))
. {
.     data.Add("json", "JSON");
.     Console.WriteLine(data["json"]);
. }
JSON
>
```

6 . 경우에 따라서는 키와 값을 따로 컬렉션으로 뽑아 사용 가능하다.

```cs
> // (11) Value 값을 따로 뽑아 출력
> var values = data.Values;
> values
Dictionary<string, string>.ValueCollection(3) { "C#", "ASP.NET MVC", "JSON" }
> 
> // (12) Key 값을 따로 뽑아 출력 
> var keys = data.Keys;
> keys
Dictionary<string, string>.KeyCollection(3) { "cs", "cshtml", "json" }
```

>모든 값을 담을 수 있는 ArrayList 클래스 대신에 필요한 값을 선택해서 담을 수 있는 List<\string>, List<\int> 등 제네릭 클래스는 성능도 빠르고 사용하기도 편리하다. 이러한 제네릭 클래스는 List<\T>처럼 표현하며, 이 전체를 표현하는 단어는 Cup<\T>이다.

