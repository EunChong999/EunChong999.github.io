---
layout: single
title: Chapter 17 배열 사용하기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 배열 사용하기에 대한 내용을 담고 있습니다.

>배열(이름 하나로 같은 데이터 형식을 여러 개 보관해 놓는 그릇)은 동일한 데이터 형식을 갖는 데이터의 집합체를 의미한다. 배열을 사용하면 편리하게 데이터를 모아서 관리할 수 있다.

# 1 컬렉션 

- 컬렉션(collection)
	- 이름 하나로 데이터 여러 개를 담을 수 있는 그릇

>C#에서 다루는 컬렉션은 배열(array), 리스트(list), 사전(dictionary) 등이 있다.

- (1) 배열 미리보기 코드 샘플

```cs
> var array = new string[] { "Array", "List", "Dictionary" };
> foreach (var arr in array) { Console.WriteLine(arr); }
Array
List
Dictionary
```

- (2) 리스트 미리보기 코드 샘플

```cs
> var list = new List<string> { "Array", "List", "Dictionary" };
> foreach (var item in list) { Console.WriteLine(item); }
Array
List
Dictionary
```

- (3) 사전 미리보기 코드 샘플

```cs
> var dictionary = new Dictionary<int, string> {
.     { 0, "Array" }, { 1, "List" }, { 2, "Dictionary"} };
> foreach (var pair in dictionary) { 
.     Console.WriteLine($"{pair.Key} - {pair.Value}"); }
0 - Array
1 - List
2 - Dictionary
```

# 2 배열

- 배열
	- 이름 하나로 데이터 여러 개를 저장하는 데이터 구조

![](https://i.imgur.com/FO7DmJK.png)

- 변수 하나에 값 하나만 저장할 수 있는 변수와 달리 배열에는 배열 이름 하나에 데이터 여러 개를 보관할 수 있다. 이처럼 변수 여러 개를 이름 하나로 관리하는 것을 배열이라고 한다.

- 배열은 요소들의 순서 있는 집합이다. 각 요소는 인덱스로 접근할 수 있으며, 인덱스는 0부터 시작한다. 

- 배열 하나에는 데이터 형식(정수형 배열, 문자열 배열 등) 하나만 보관할 수 있다.

- 배열은 메모리의 연속된 공간을 미리 할당하고, 이를 대괄호([])와 0부터 시작하는 정수형 인덱스를 사용하여 접근하는 구조이다. 

- 배열을 선언할 때는 new 키워드로 배열을 생성한 후 사용할 수 있다.

- 배열에서 값 하나는 요소(element) 또는 항목(item)으로 표현한다.

>배열을 사용하면 다음 장점이 있다.

- 이름 하나로 변수 여러 개를 묶어 관리하기에 편하다.

- 반복문으로 쉽게 반복해서 값을 사용할 수 있다.

- 필요한 데이터 개수를 정확히 정한다면 메모리를 적게 사용하여 프로그램 크기가 작아지고 성능이 향상된다.

>다음 샘플 코드는 학생 3명의 총점을 구한다. 이러한 방식이라면 학생이 30명일 때는 변수를 30개 선언해야 하는데, 변수는 하나면 충분하다. 그래서 배열이 필요한 것이다.

```cs
> var kor1 = 90; // 1번 학생
> var kor2 = 80; // 2번 학생
> var kor3 = 70; // 3번 학생
> var tot = kor1 + kor2 + kor3;
> $"총점 : {tot}"
"총점 : 240"
```

## 2.1 문자열에서 문자 하나씩 뽑아 오기

>문자열은 문자의 배열을 의미한다. 문자열은 그 자체를 문자 배열로 분리해서 사용할 수 있다.

```cs
> // 문자열 == 문자의 배열
> string arr = "C#8";
> Console.WriteLine(arr[0]);
C
> Console.WriteLine(arr[1]);
#
> Console.WriteLine(arr[2]);
8
```

>문자열 변수 뒤에 [0], [1], [2]를 붙여 0번째 위치부터 n - 1번째 위치까지 들어 있는 문자를 하나씩 빼낼 수 있다. 이처럼 0번째부터 시작하는 숫자를 인덱스(index) 또는 첨자(subscript)라고 한다.

## 2.2 문자열에 직접 인덱서([]) 사용하기

>변수 이름이 아닌 문자열 자체에 직접 인덱서([]) 기호를 사용하여 특정 인덱스에 해당하는 문자 값을 직접 뽑아낼 수도 있다. 

```cs
> "ABC"[0]
'A'
> "ABC"[1]
'B'
> "ABC"[2]
'C'
> "ABC".GetType()
[System.String]
> "ABC"[0].GetType()
[System.Char]
```

>이와 같이 문자열에서 인덱서 기호인 []를 사용하여 뽑아낸 자료 하나는 Char 형식이 된다.

# 3 배열 선언하기

>배열은 데이터 형식 이름 뒤에 [] 기호를 사용하여 선언한다. 배열에 저장된 데이터는 정수형 인덱스로 접근 가능하다. 배열에 있는 데이터는 for 문 또는 foreach 문을 사용하여 반복해서 출력할 수 있다. 

>예를 들어 정수형 배열은 다음과 같이 선언할 수 있다.

```cs
> int[] numbers;
```

>배열 선언 후 new 연산자를 사용하여 배열 크기만큼 메모리 영역을 잡을 수 있다. 배열을 선언할 때 사용된 new 키워드는 형식을 인스턴스화(instantiate) 시켜 주는 연산자이다. 특정 형식(여기에서는 배열)을 실제 사용 가능한 개체로 만들어 준다. new 키워드는 배열을 지정한 크기로 만들어 주는 연산자라고 할 수 있다. 

>정수형 배열을 선언한 후 요소 개수를 다음과 같이 생성할 수 있다.

```cs
> int[] numbers;
> numbers = new int[3];
```

- Note
	- 프로그래밍에서 인스턴스(instance)는 새로운 실체 또는 개체(object)를 의미한다. 즉, 새로운 개체를 만드는 작업을 인스턴스화라고 한다.

>또는 다음과 같이 한 줄로 줄여서 표현해도 된다.

```cs
> int[] intArray = new int[3];
```

>배열 크기를 생성할 때 사용하는 숫자를 첨자라고 한다. 첨자는 흔히 인덱스라고 한다. 이 코드에서 intArray의 첨자는 3이다.

>선언된 배열은 0부터 시작하는 인덱스를 사용하여 접근할 수 있다. 예를 들어 intArray[0], intArray[1], intArray[2] 순서대로 첨자 3으로 선언된 배열은 0, 1, 2인 인덱스 3개를 가진다. 일상생활에서는 1부터 숫자를 세지만 C#에서는 0부터 숫자를 세는데, 이러한 규칙을 0 기반(zero base) 또는 (n-1) 규칙이라고 한다. 따라서 인덱스는 0부터 시작된다.

>인덱스는 보통 0부터 n - 1(전체 요소에서 1개를 뺀)까지 배열과 컬렉션의 요소를 반복해서 출력해 주는 용도로 사용한다.

>배열을 만드는 방법을 한글로 표현하면 다음과 같다.

```cs
데이터형식[] 배열이름 = new 데이터형식[크기];
```

>이러한 배열에는 세 가지 종류가 있다.

- **1차원 배열**
	- 배열의 첨자를 하나만 사용하는 배열

- **다차원 배열**
	- 첨자 2개 이상을 사용하는 배열(2차원, 3차원, ...)

- **가변(jagged) 배열**
	- '배열의 배열'이라고도 하며, 이름 하나로 다양한 차원의 배열을 표현
# 4 1차원 배열

>1차원 배열을 선언하여 메모리 영역을 확보하는 코드 형태는 다음과 같다.

```cs
데이터형식[] 배열이름;
```

>1차원 배열의 요소에 값을 대입하는 코드는 다음과 같다.

```cs
배열이름[인덱스] = 값;
```

>1차원 배열의 참조는 정수형 인덱스를 사용하여 접근할 수 있다.

```cs
Console.WriteLine(배열이름[인덱스]);
```

>1차원 배열 관련 용어에서 인덱스와 첨자는 같은 뜻으로 사용하며, 인덱스로 배열의 요소 하나를 가져올 수 있다.

- 인덱스와 요소

| 인덱스 또는 첨자                                                                   | 요소                                                  |
| --------------------------------------------------------------------------- | --------------------------------------------------- |
| 복수의 데이터를 구분 짓는 번호<br>int[] intNum = new int[10]; <br><- 여기에서 숫자 10이 인덱스(첨자) | 배열의 요소 : 첨자 하나를 가지는 배열<br>사원번호[3]<br><- 세 번째 배열의 요소 |

>예를 들어 다음과 같이 arr 이름의 배열을 선언하면, 메모리상에 다음과 같이 공간이 5개 잡힌다.

```cs
> int[] arr = new int[5];
```

![](https://i.imgur.com/oVm2snk.png)

>인덱스가 5이므로 C#에서 배열의 첨자는 0부터 시작해서 선언할 때 첨자인 (5-1)까지 5개를 만든다. C#에서는 (n-1) 규칙 또는 0 기반(zero base) 또는 제로 오프셋(zero offset)이라고 해서 모든 배열과 같은 데이터 구조의 인덱스는 0번째부터 사용된다.

## 4.1 1차원 배열 만들기

```cs
> ushort[] numbers;         // (1) 배열 선언
> numbers = new ushort[2];  // (2) 배열의 요소 개수 생성 : 요소 개수가 2이므로 [0], [1] 사용
> 
> numbers[0] = 3840;        // (3) 배열 초기화
> numbers[1] = 2160;
> 
> Console.WriteLine($"{numbers[0]} * {numbers[1]}"); // (4) 배열 사용
3840 * 2160
```

>정수형 배열인 numbers를 생성한 후 요소 개수 2를 new 키워드로 할당한다. 배열의 요소 개수를 직접 지정할 때는 반드시 new 키워드를 사용한다. 

>요소 개수를 2로 선언했으므로 [0], [1]로 요소가 2개 생성된다. 각 요소에는 [0], [1] 형태의 인덱스를 사용하여 값을 할당할 수 있다. 

>배열 값은 numbers[n] 형태로 가져와 사용할 수 있다. 요소를 2개 지정하여 배열을 만들면 0, 1의 인덱스를 사용할 수 있지만, 다음과 같이 2를 지정하면 에러가 발생한다.

```cs
> ushort[] numbers = new ushort[2];
> numbers[2]
System.IndexOutOfRangeException: 인덱스가 배열 범위를 벗어났습니다.
```

## 4.2 1차원 배열에 문자열 저장하기

```cs
> string[] phones;          // (1) 배열 생성
> phones = new string[2];   // (2) 배열의 요소 생성
> 
> phones[0] = "112";        // (3) 배열에 값 대입
> phones[1] = "119";
> 
> Console.WriteLine("{0}, {1}", phones[0], phones[1]); // (4) 배열 값 사용
112, 119
```

>문자열 배열을 선언하고 요소 2개를 생성한다. 각 요소에는 '112'와 '119'의 값을 넣고 출력했다.

## 4.3 배열 선언과 동시에 초기화해서 코드 줄이기

- ArrayOne1.cs

```cs
using System;
using System.Linq;

class ArrayOne1
{
    static void Main()
    {
        int[] intArray;             // 1차원 배열 선언
        intArray = new int[3];      // 메모리 영역 확보(0, 1, 2)

        intArray[0] = 1;            // 배열 초기화
        intArray[1] = 2;
        intArray[2] = 3;

        // (1) for 문 사용 출력 : 정확하게 배열 범위를 알고 있을 때
        for (int i = 0; i < 3; i++) // 배열 참조
        {
            Console.WriteLine($"{i}번째 인덱스 : {intArray[i]}");
        }

        // (2) foreach 문 사용 출력 : intArray에 데이터가 있는 동안 반복
        foreach (int intValue in intArray)
        {
            Console.WriteLine("{0}", intValue);
        }
    }
}
```

- 실행 결과

```cs
0번째 인덱스 : 1
1번째 인덱스 : 2
2번째 인덱스 : 3
1
2
3
```

- ArrayOne2.cs

```cs
using System;
using System.Linq;

class ArrayOne2
{
    static void Main()
    {
        // 1차원 배열 선언, 요소 생성, 초기화를 동시에...
        int[] intArray = new int[3] { 1, 2, 3 };

        for (int i = 0; i < 3; i++)
        {
            Console.WriteLine($"{i}번째 인덱스 : {intArray[i]}");
        }

        foreach (int intValue in intArray)
        {
            Console.WriteLine("{0}", intValue);
        }
    }
}
```

- 실행 결과

```cs
0번째 인덱스 : 1
1번째 인덱스 : 2
2번째 인덱스 : 3
1
2
3
```

>배열을 선언할 때 바로 요소 생성 및 초기화를 할 수 있다. 이때는 var 키워드로 코드를 줄일 수 있고, 요소 개수를 생략할 수도 있다.

- ArrayOne3.cs

```cs
using System;
using System.Linq;

class ArrayOne3
{
    static void Main()
    {
        // 1차원 배열 선언, 요소 생성, 초기화를 동시에...
        // 요소 개수 생략 가능 : 생략하면 뒤에서 지정한 요소 개수만큼 자동 생성
        var intArray = new int[] { 1, 2, 3 };

        for (int i = 0; i < 3; i++)
        {
            Console.WriteLine($"{i}번째 인덱스 : {intArray[i]}");
        }

        foreach (int intValue in intArray)
        {
            Console.WriteLine("{0}", intValue);
        }
    }
}
```

- 실행 결과

```cs
0번째 인덱스 : 1
1번째 인덱스 : 2
2번째 인덱스 : 3
1
2
3
```

>마지막으로 선언과 동시에 초기화할 때는 new 키워드와 배열형([])까지 생략할 수 있다.

- ArrayOne4.cs

```cs
using System;
using System.Linq;

class ArrayOne4
{
    static void Main()
    {
        // 1차원 배열 선언, 요소 생성, 초기화를 동시에...
        // new 키워드와 int[] 생략하고 바로 초기화 가능
        int[] intArray = { 1, 2, 3 };

        for (int i = 0; i < 3; i++)
        {
            Console.WriteLine($"{i}번째 인덱스 : {intArray[i]}");
        }

        foreach (int intValue in intArray)
        {
            Console.WriteLine("{0}", intValue);
        }
    }
}
```

- 실행 결과

```cs
0번째 인덱스 : 1
1번째 인덱스 : 2
2번째 인덱스 : 3
1
2
3
```

## 4.4 문자열 배열 선언과 동시에 초기화하여 출력하기

>다음 코드는 문자열 배열을 생성하고 문자열 3개를 입력한 후 배열의 인덱스를 사용하여 출력한다.

```cs
> string[] languages = { "Korean", "English", "Spanish" };
> Console.WriteLine($"{languages[0]}, {languages[1]}, {languages[2]}");
Korean, English, Spanish
```

>문자열 배열을 선언할 때 new 키워드 없이 바로 중괄호를 사용하여 요소 개수를 생성과 동시에 초기화할 수 있다. 마찬가지로 배열에 들어 있는 값은 [0], [1], [2] 식으로 정수형 인덱스를 사용하여 출력할 수 있다.

## 4.5 숫자 구분자와 함께 사용하기

```cs
> int[] numbers = { 1, 1_000, 10_000, 1_000_000 };
> 
> foreach (int number in numbers) // 배열에 데이터가 있는 만큼 반복
. {
.     Console.WriteLine(number);
. }
1
1000
10000
1000000
```

>이 코드의 주석 처리한 부분보다는 숫자 구분자를 사용한 부분이 숫자 요소의 내용을 확인할 때 좀 더 가독성이 좋아진다. 

## 4.6 이진수 리터럴을 배열에 저장하기

```cs
> int[] numbers = { 0b1, 0B10, 0b0100, 0B00001000 }; // 이진수(1, 2, 4, 8)가 저장된 배열
> 
> foreach (var n in numbers)
. {
.     Console.WriteLine(n);
. }
1
2
4
8
```

>이진수 리터럴과 숫자 구분자를 사용하면 여러 데이터에서 가독성이 좋아진다. 0b 접두사를 붙이고 이진수를 네 자리 단위로 표시할 수도 있다.

```cs
> int[] numbers = { 0b1, 0b10, 0b100, 0b1000, 0b1_0000, 0b10_0000 };
> numbers[0]
1
> numbers[1]
2
```

>다음 샘플 코드처럼 이진수 문자열과 숫자 구분자를 함께 쓰면 가독성이 더욱 좋아진다.

```cs
> int[] numbers = { 0b1, 0B10, 0b100, 0B0000_1000 };
> numbers
int[4] { 1, 2, 4, 8 }
```

## 4.7 Length 속성으로 배열 크기 구하기

>배열 크기인 요소 개수를 얻으려면 [배열이름.Length] 형태로 Length 속성(property)을 사용한다. 배열은 0부터 시작하는 정수형 인덱스를 사용하기에 주로 for 문 같은 반복문과 함께 쓴다.

```cs
> char[] characters = { 'a', 'b', 'c', 'd' };   // 문자 배열
> characters.Length
4
> 
> for (int i = 0; i < characters.Length; i++)   // 배열 크기만큼 반복
. {
.     Console.WriteLine(characters[i]);
. }
a
b
c
d
```

>배열 내용을 출력할 때 for 문 같은 반복문을 사용하면 편리하게 많은 수의 배열 요소를 출력할 수 있다. 배열 형식의 Length 속성을 사용하면 반복문에서 반복 범위를 쉽게 결정할 수 있다. 

## 4.8 배열 인덱스에 증감 연산자 사용하기

>배열 인덱스는 정수형이기에 다음 코드처럼 증감 연산자와 함께 사용할 수도 있다. 여기에서 주의할 점은 인덱스가 정해진 크기를 벗어나면 에러가 발생한다는 것이다.

```cs
> int[] array = { 1, 2, 3 };
> array[3]
System.IndexOutOfRangeException: 인덱스가 배열 범위를 벗어났습니다.
> 
> int index = 0; // 배열 인덱스는 0부터 시작하기에 0으로 index 변수 초기화
> 
> Console.WriteLine(array[index++]); // array[0] 출력 후, index == 1로 증가
1
> Console.WriteLine(array[index++]); // array[1] 출력 후, index == 2로 증가
2
> Console.WriteLine(array[index++]); // array[2] 출력 후, index == 3로 증가
3
> 
> Console.WriteLine(array[--index]); // index == 2로 감소 후, array[2] 출력
3
> Console.WriteLine(array[--index]); // index == 1로 감소 후, array[1] 출력
2
> Console.WriteLine(array[--index]); // index == 0로 감소 후, array[0] 출력
1
> array[--index]
System.IndexOutOfRangeException: 인덱스가 배열 범위를 벗어났습니다.
```

>배열 인덱스를 지정하는 [] 영역에는 정수형 값이 필요하다. 이 정수형 값을 표현할 때는 ++, \-\- 등 증감 연산자를 함께 사용할 수 있다.

## 4.9 배열을 사용하여 국어 점수의 총점과 평균 구하기

>배열을 사용하지 않는다면 학생 3명의 점수를 저장하는 변수를 3개 선언해야 한다. 학생이 50명이라면 변수를 50개 선언해야 한다. 배열을 사용하면 데이터 여러 개를 편리하게 처리할 수 있다. 

- ArrayTotalAvg.cs

```cs
using System;
using System.Linq;

class ArrayTotalAvg
{
    static void Main()
    {
        int[] kor = new int[3]; // int 형식 요소를 3개 갖는 1차원 배열 선언
        int sum = 0;            // 합계가 담길 변수 sum 선언과 동시에 0으로 초기화
        float avg = 0;          // 평균이 담길 실수형 변수 avg 선언과 동시에 0으로 초기화

        kor[0] = 100;           // 배열의 각 요소에 값 대입
        kor[1] = 90;
        kor[2] = 80;

        sum = kor[0] + kor[1] + kor[2]; // 총점 계산
        avg = sum / (float)3.0;         // 평균 계산

        // 총점과 평균 출력 : 평균은 소수점 두 자리까지 출력
        Console.WriteLine($"총점 : {sum}, 평균 : {avg:0.00}");
    }
}
```

- 실행 결과

```cs
총점 : 270, 평균 : 90.00
```

>참고로 실수형 자료에서는 다음과 같이 간단히 소수 둘째 자리까지 표현 가능하다.

```cs
> $"{3.141592:0.00}"
"3.14"
```

## 4.10 값을 입력받아 배열에 저장한 후 출력하기

>콘솔에서 반드시 정수 3개를 입력해야 정상적으로 실행된다.

- ArrayStudent.cs

```cs
using System;
using System.Linq;

class ArrayStudent
{
    static void Main()
    {
        // 요소가 3개인 1차원 배열 생성
        int[] students = new int[3];

        // 사용자에게 정수 데이터 3개를 입력받아 배열에 저장
        students[0] = Convert.ToInt32(Console.ReadLine());
        students[1] = Convert.ToInt32(Console.ReadLine());
        students[2] = Convert.ToInt32(Console.ReadLine());

        // 총점 구하고 출력
        int total = students[0] + students[1] + students[2];
        Console.WriteLine($"총점 : {total}");
    }
}
```

- 실행 결과

```cs
100
90
80
총점 : 270
```

>콘솔에서 입력된 정수를 배열의 요소 3개로 받은 후 값 3개를 더하여 출력하는 간단한 예제이다.

## 4.11 배열 값을 foreach 문으로 반복해서 출력하기

```cs
> float[] arr = { 10.5f, 20.1f, 30.2f };
> float sum = 0.0f;
> 
> foreach(float f in arr) // arr 변수에 데이터가 있는 동안 반복해서 실행
. {
.     sum += f;
. }
> sum
60.8000031
> Console.WriteLine(sum);
60.8
```

>실수형 배열인 arr을 생성한 후 값 3개로 초기화한다. 배열의 데이터는 foreach 문으로 있는 만큼 반복해서 가져와 사용할 수 있다. 

>참고로 중간에 sum을 출력해 보니 60.800031처럼 오차가 발생한다. 이때는 좀 더 정밀한 데이터로 바꾸어 사용할 수 있다. 다음 코드처럼 float를 decimal 형식으로 변경하면 된다.

```cs
> decimal[] arr = { 10.5M, 20.1M, 30.2M };
> decimal sum = 0.0M;
> foreach (decimal d in arr)
. {
.     sum += d;
. }
> sum
60.8
> Console.WriteLine(sum);
60.8
```

- Note 

>C#에서는 배열을 선언할 때 {}를 사용하여 빈 배열을 만들 수 있다. 하지만 배열은 선언한 후 크기를 동적으로 다시 설정할 수 없기 때문에 빈 배열을 만들어도 쓸모가 없다.

- ArrayEmpty.cs

```cs
using System;
using System.Linq;

class ArrayEmpty
{
    static void Main()
    {
        // 빈 배열 선언
        string[] authors = { };
        if (authors.Length > 0)
        {
            Console.WriteLine($"글쓴이가 {authors.Length}명 있습니다.");
        }
        else
        {
            Console.WriteLine($"글쓴이가 아무도 없습니다.");
        }
    }
}
```

- 실행 결과

```cs
글쓴이가 아무도 없습니다.
```

# 5 다차원 배열 

>2차원 배열 및 3차원 배열처럼 차원이 2 이상인 배열을 다차원 배열이라고 한다. 다차원 배열은 다음과 같이 선언한다.

```cs
데이터형식[,] 배열이름;  // 2차원 배열 선언
데이터형식[,,] 배열이름; // 3차원 배열 선언
```

>2차원 배열의 인덱스는 다음과 같이 표현할 수 있다.

![](https://i.imgur.com/WRr1oYd.png)

>1차원, 2차원, 3차원 배열을 선언하는 방법은 다음과 같다. C#에서 배열을 선언할 때는 콤마를 기준으로 차원을 구분한다.

```cs
int[] oneArray;     // 1차원 배열 선언
int[,] twoArray;    // 2차원 배열 선언
int[,,] threeArray; // 3차원 배열 선언
```

>배열을 선언하고 나서 사용하려면 값을 초기화해야 하는데, 차수별 배열을 초기화하는 형태는 다음과 같다.

```cs
// 배열 초기화 : 배열 이름 = new 데이터 형식[요소 개수, 요소 개수];
oneArray = new int[2] { 1, 2 };
twoArray = new int[2, 2] { { 1, 2 }, { 3, 4 } };
threeArray = new int[2, 2, 2] { { { 1, 2 }, { 3, 4 } }, { { 5, 6 }, { 7, 8 } } };
```

## 5.1 2차원 배열 만들기

```cs
> char[,] arr = new char[2, 2]; // (1) 2차원 배열 선언
> 
> arr[0, 0] = 'A';              // (2) 2차원 배열 초기화
> arr[0, 1] = 'B';
> arr[1, 0] = 'C';
> arr[1, 1] = 'D';
> 
> $"{arr[0, 0]}, {arr[0, 1]}"   // (3) 2차원 배열 사용
"A, B"
> $"{arr[1, 0]}, {arr[1, 1]}"
"C, D"
```

>2차원 배열은 표 형태로 데이터를 관리할 때 유용하다.

## 5.2 2차원 배열 생성 및 반복문으로 사용하기

- ArrayTwo1.cs

```cs
using System;
using System.Linq;

class ArrayTwo1
{
    static void Main()
    {
        int[,] intArray;            // 2차원 배열 선언
        intArray = new int[2, 3];   // 2 * 3개의 요소 생성

        intArray[0, 0] = 1;         // 2차원 배열 초기화
        intArray[0, 1] = 2;
        intArray[0, 2] = 3;
        intArray[1, 0] = 4;
        intArray[1, 1] = 5;
        intArray[1, 2] = 6;

        for (int i = 0; i < 2; i++)
        {
            for (int j = 0; j < 3; j++)
            {
                Console.Write($"{intArray[i, j]}_");
            }
            Console.Write("\n");    // 행 출력 후 개행
        }
    }
}
```

- 실행 결과

```cs
1_2_3_
4_5_6_
```

>2차원 배열을 출력할 때는 for 문을 2개 사용하여 반복해서 접근한다.

## 5.3 2차원 배열 선언과 동시에 초기화하기

- ArrayTwo2.cs

```cs
using System;
using System.Linq;

class ArrayTwo2
{
    static void Main()
    {
        // 2차원 배열 선언과 동시에 초기화
        int[,] intArray = new int[2, 3] { { 1, 2, 3 }, { 4, 5, 6 } };

        for (int i = 0; i < 2; i++)
        {
            for (int j = 0; j < 3; j++)
            {
                Console.Write($"{intArray[i, j]}_");
            }
            Console.Write("\n");
        }
    }
}
```

- 실행 결과

```cs
1_2_3_
4_5_6_
```

>이외에도 2차원 배열은 다음 두 방법처럼 선언과 동시에 초기화할 수도 있다.

- **첫 번째 방법**

```cs
int[,] intArray = new int[,] { { 1, 2, 3 }, { 4, 5, 6 } };
```

- **두 번째 방법**

```cs
int[,] intArray = { { 1, 2, 3 }, { 4, 5, 6 } };
```

>2차원 배열의 요소를 초기화하는 것은 이중 중괄호로 초기화한 후 이중 for 문을 사용하여 출력하는 구조이다.

- ArrayTwoFor.cs

```cs
using System;
using System.Linq;

class ArrayTwoFor
{
    static void Main()
    {
        int[,] arr = { { 1, 2, 3 }, { 4, 5, 6 } };
        for (int i = 0; i < 2; i++) // 이중 for 문으로 2차원 배열 출력
        {
            for (int j = 0; j < 3; j++)
            {
                Console.WriteLine($"arr[{i},{j}] = {arr[i, j]}");
            }
        }
    }
}
```

- 실행 결과

```cs
arr[0,0] = 1
arr[0,1] = 2
arr[0,2] = 3
arr[1,0] = 4
arr[1,1] = 5
arr[1,2] = 6
```

## 5.4 3행 2열짜리 2차원 배열에 행과 열이 같으면 1, 다르면 0을 입력한 후 출력하기

- ArraySameIndex.cs

```cs
using System;
using System.Linq;

class ArraySameIndex
{
    static void Main()
    {
        int[,] arr = new int[3, 3];
        for (int i = 0; i < 3; i++)
        {
            for (int j = 0; j < 3; j++)
            {
                if (i == j)
                {
                    arr[i, j] = 1; // 행과 열이 같으면 1로 채우기
                }
                else
                {
                    arr[i, j] = 0;
                }

                Console.Write(arr[i, j]);
            }
            Console.WriteLine();
        }
    }
}
```

- 실행 결과

```cs
100
010
001
```

## 5.5 2차원 배열을 사용하여 합계와 평균 구하기

- 학생 3명의 점수와 합계, 평균

| 이름  | 국어  | 영어  | 합계  | 평균  |
| --- | --- | --- | --- | --- |
| 백승수 | 90  | 100 | 190 | 95  |
| 이세영 | 80  | 90  | 170 | 85  |
| 권경민 | 100 | 80  | 180 | 90  |

- ArraySumAverage.cs

```cs
using System;
using System.Linq;

class ArraySumAverage
{
    static void Main()
    {
        int[,] scores =
        {
            { 90, 100, 0, 0 },
            { 80, 90, 0, 0 },
            { 100, 80, 0, 0 }
        };

        for (int i = 0; i < 3; i++)
        {
            scores[i, 2] = scores[i, 0] + scores[i, 1]; // 합계
            scores[i, 3] = scores[i, 2] / 2;            // 평균
        }
        Console.WriteLine("국어 영어 합계 평균");

        for (int i = 0; i < 3; i++)
        {
            for (int j = 0; j < 4; j++)
            {
                Console.Write($"{scores[i, j],4} ");
            }
            Console.WriteLine();
        }
    }
}
```

- 실행 결과

```cs
국어 영어 합계 평균
  90  100  190   95
  80   90  170   85
 100   80  180   90
```

## 5.6 3차원 배열 만들기

- ArrayThreeDescription.cs

```cs
using System;
using System.Linq;

class ArrayThreeDescription
{
    static void Main()
    {
        // (1) 3차원 배열 선언
        string[,,] names = new string[2, 2, 2]; // 2 * 2 * 2 = 8

        // (2) 3차원 배열 초기화
        names[0, 0, 0] = "C#";
        names[0, 0, 1] = "ASP.NET";

        names[0, 1, 0] = "Windows Forms";
        names[0, 1, 1] = "WPF";

        names[1, 0, 0] = "Xamarin";
        names[1, 0, 1] = "Unity";

        names[1, 1, 0] = "UWP";
        names[1, 1, 1] = "Azure";

        // (3) 3차원 배열 사용
        Console.WriteLine("\n0층");
        Console.WriteLine($"{names[0, 0, 0],20}, {names[0, 0, 1],20}");
        Console.WriteLine($"{names[0, 1, 0],20}, {names[0, 1, 1],20}");

        Console.WriteLine("\n1층");
        Console.WriteLine($"{names[1, 0, 0],20}, {names[1, 0, 1],20}");
        Console.WriteLine($"{names[1, 1, 0],20}, {names[1, 1, 1],20}");
    }
}
```

- 실행 결과

```cs

0층
                  C#,              ASP.NET
       Windows Forms,                  WPF

1층
             Xamarin,                Unity
                 UWP,                Azure
```

>3차원 배열은 행과 열로 구성된 2차원 배열을 층으로 쌓아 관리하는 형태의 데이터 구조를 다룰 때 사용한다.

## 5.7 3차원 배열 만들고 for 문 3개로 출력하기

- ArrayThree.cs

```cs
using System;
using System.Linq;

class ArrayThree
{
    static void Main()
    {
        int[,,] intArray = new int[2, 3, 4]
        {
            { { 1, 2, 3, 4 }, { 5, 6, 7, 8 }, { 9, 10, 11, 12 } },          // 0층
            { { 13, 14, 15, 16 }, { 17, 18, 19, 20 }, { 21, 22, 23, 24 } }  // 1층
        };

        for (int i = 0; i < 2; i++)         // 층 반복
        {
            for(int j = 0; j < 3; j++)      // 행 반복
            {
                for (int k = 0; k < 4; k++) // 열 반복
                {
                    Console.Write("{0,2} ", intArray[i, j, k]);
                }
                Console.Write("\n");
            }
            Console.WriteLine();
        }
    }
}
```

- 실행 결과

```cs
 1  2  3  4
 5  6  7  8
 9 10 11 12

13 14 15 16
17 18 19 20
21 22 23 24
```

>[,,] 형태로 3차원 배열을 선언하고 의미상으로 층, 행, 열로 된 데이터 구조를 저장할 수 있다. 3차원 배열은 for 문 3개를 사용하여 각 차원을 구분해서 출력한다. 

## 5.8 배열 관련 Rank, Length 속성과 GetLength() 메서드 사용하기

>모든 배열은 요소 개수 및 각 차원에 해당하는 요소 크기를 확인할 수 잇다. 먼저 배열은 Length 속성을 사용하여 배열 길이를 알 수 있다. 추가로 Rank 속성을 사용하면 배열의 차수를 구할 수 있는데, 3차원 배열이면 3을 반환한다. 또 각 차수에 해당하는 길이를 알고자 할 때는 GetLength(n)을 사용하여 GetLength(0), GetLength(1), GetLength(2) 형태로 1차원, 2차원, 3차원의 Length를 구할 수 있다.

- ArrayGetLengthDemo.cs

```cs
using System;
using System.Linq;

class ArrayGetLengthDemo
{
    static void Main()
    {
        // 3차원 배열 선언(요소 개수 생성), 초기화(층/행/열)
        int[,,] arr = new int[2, 2, 2]
            { { { 1, 2 }, { 3, 4 } }, { { 5, 6 }, { 7, 8 } } };

        Console.WriteLine("차수 출력 : {0}", arr.Rank);
        Console.WriteLine("길이 출력 : {0}", arr.Length);

        // 층(면), 행, 열 구분해서 출력
        for (int i = 0; i < arr.GetLength(0); i++)          // 층
        {
            for (int j = 0; j < arr.GetLength(1); j++)      // 행
            {
                for (int k = 0; k < arr.GetLength(2); k++)  // 열
                {
                    Console.Write("{0}\t", arr[i, j, k]);
                }
                Console.WriteLine();
            }
            Console.WriteLine();
        }
    }
}
```

- 실행 결과

```cs
차수 출력 : 3
길이 출력 : 8
1       2
3       4

5       6
7       8
```

>배열의 Rank 속성으로 1차원, 2차원, 3차원 배열을 구분할 수 있다. 또는 각 차원의 Length는 GetLength() 메서드로 구할 수 있다.

# 6 가변 배열

>차원이 2개 이상인 배열은 다차원 배열이고, 배열 길이가 가변 길이인 배열은 가변 배열이라고 한다. 지그재그 형태의 배열이며, 데이터형식\[]\[] 배열이름; 형태로 사용한다(예 int\[]\[] zagArray).

- ZigZag.cs

```cs
using System;
using System.Linq;

class ZigZag
{
    static void Main()
    {
        // [2][] 형태로 두 번째를 비워 두면 동적으로 자료 n개로 초기화 가능
        int[][] zagArray = new int[2][];

        zagArray[0] = new int[] { 1, 2 };       // 0번째 행에 요소 2개로 초기화
        zagArray[1] = new int[] { 3, 4, 5 };    // 1번째 행에 요소 3개로 초기화

        for (int i = 0; i < 2; i++)
        {
            // n번째 행의 길이만큼 반복 : 두 번, 세 번 반복
            for (int j = 0; j < zagArray[i].Length; j++)
            {
                Console.Write($"{zagArray[i][j]}\t");
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

- 실행 결과

```cs
1       2
3       4       5
```

# 7 var 키워드로 배열 선언하기

>배열은 선언과 동시에 초기화할 때 배열 이름 앞에 int[] 같은 배열 형식 대신에 var 키워드를 사용하여 선언할 수 있다.

- ArrayWithVarKeyword.cs

```cs
using System;
using System.Linq;

class ArrayWithVarKeyword
{
    static void Main()
    {
        var i = 5;          // 자동으로 정수 형식이 설정됨 -> int i = 5;
        Console.WriteLine("i : {0}, 타입 : {1}", i, i.GetType());

        var s = "Hello";    // 문자열 형식으로 형식화됨
        Console.WriteLine("s :{0}, 타입 : {1}", s, s.GetType());

        var numbers = new int[] { 1, 2, 3 };    // 배열 형식
        foreach (var item in numbers)           // var item에서 item은 numbers 형식
        {
            Console.WriteLine("item : {0}, 타입 : {1}", item, item.GetType());
        }
    }
}
```

- 실행 결과

```cs
i : 5, 타입 : System.Int32
s :Hello, 타입 : System.String
item : 1, 타입 : System.Int32
item : 2, 타입 : System.Int32
item : 3, 타입 : System.Int32
```

>변수 및 배열을 선언하자마자 동시에 초기화할 때는 var 키워드를 사용할 수 있다. 이를 암시적으 형식화된 로컬 변수 또는 배열이라고 한다. var 키워드로 변수 또는 배열을 선언하면 자동으로 저장되는 값을 유추하여 해당 형식으로 초기화한다.

