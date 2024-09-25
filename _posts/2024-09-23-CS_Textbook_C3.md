---
layout: single
title: Chapter 25 컬렉션 사용하기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 컬렉션 사용하기에 대한 내용을 담고 있습니다.

>배열처럼 특정 항목의 집합을 리스트 또는 컬렉션이라고 한다. 컬렉션은 배열, 리스트, 사전을 사용하여 관련 개체의 그룹을 만들고 관리한다.

# 1 배열과 컬렉션

>컬렉션 클래스는 데이터 항목의 집합을 메모리상에서 다루는 클래스로, 문자열 같은 간단한 형태도 있다. 그리고 특정 클래스 형식의 집합 같은 복잡한 형태도 있다.

>C#의 컬렉션은 다음 세 종류로 나눈다.

- **배열**
	- 일반적으로 숫자처럼 간단한 데이터 형식을 저장한다.

- **리스트**
	- 간단한 데이터 형식을 포함한 개체들을 저장한다.

- **사전**(dictionary)
	- 키와 값의 쌍으로 관리되는 개체들을 저장한다.

>일반적으로 기본형 그룹을 배열로 보고, 새로운 타입(클래스)의 그룹을 컬렉션으로 비교하기도 한다.

- **배열**
	- 정수형, 문자열 등 집합을 나타낸다.

- **컬렉션**
	- 개체의 집합을 나타낸다. 리스트, 집합, 맵, 사전도 컬렉션과 같은 개념으로 사용한다.

>여러 데이터를 저장하는 형태라면 배열, 리스트, 컬렉션은 모두 의미가 같다.

```cs
> string[] colors = { "red", "green", "blue" };
> colors.Length
3
> colors[0]
"red"
> colors[1]
"green"
> colors[2]
"blue"
```

>데이터를 그룹으로 묶어 관리할 때는 일반적으로 배열로 관리한다. 배열은 크기가 고정되어 있다. 배열은 크기가 고정되어 있어 새로운 데이터를 추가할 수 없다. 이러한 단점을 제거한 것이 바로 컬렉션이다.

- 컬렉션은 반복하여 사용할 수 있는 형식 안정성으로 크기를 동적으로 변경할 수 있는 장점이 있다.
- 컬렉션은 데이터를 조회, 정렬, 중복 제거, 이름과 값을 쌍으로 관리하는 등 여러 장점이 있다.

>닷넷에는 컬렉션과 관련한 여러 클래스를 제공한다.

- Stack 클래스
- Queue 클래스
- ArrayList 클래스

>정적인 멤버를 가지는 Math 클래스와 달리 컬렉션 관련 클래스들을 사용하려면, 먼저 클래스의 인스턴스를 선언해야 한다.

>닷넷 프레임워크에는 많은 양의 컬렉션 클래스가 있다.

>컬렉션(리스트) 관련 클래스들은 다음과 같이 몇몇 네임스페이스에 있다. 각 네임스페이스에는 다음 목록에서 제시한 클래스를 포함하여 더 많은 클래스가 있다.

- 컬렉션의 종류

| 컬렉션 관련 클래스가 있는 네임스페이스                | 항목                                                         |
| ------------------------------------ | ---------------------------------------------------------- |
| System 네임스페이스                        | Array 클래스                                                  |
| System.Collections 네임스페이스            | Stack 클래스, Queue 클래스, ArrayList 클래스                        |
| System.Collections.Generic 네임스페이스    | List<T> 클래스, LinkedList<T> 클래스, Stack<T> 클래스, Queue<T> 클래스 |
| System.Collections.Concurrent 네임스페이스 | ConcurrentStack<T> 클래스, ConcurrentQueue<T> 클래스             |

# 2 리스트 출력 구문

>리스트에 담긴 모든 요소를 사용할 때는 foreach 문을 쓰고, 필요한 영역의 리스트를 사용할 때는 for 문을 써서 리스트를 출력한다.

- foreach 문과 for 문

| 리스트 출력 구문 | 특징                                                                |
| --------- | ----------------------------------------------------------------- |
| foreach 문 | 빠르고 쉽다.<br><br>모든 요소를 반복 출력한다. 필요한 속성만 선별해서 출력도 가능하다.             |
| for 문     | 복잡하지만 유연하다.<br><br>모든 요소 또는 필요한 영역의 요소를 반복 출력한다. 요소에 읽고 쓰기가 가능하다. |

# 3 Array 클래스

>Array 클래스는 배열을 매개변수로 받아 정렬, 역순, 변환 등 작업을 진행한다. Array 클래스의 주요 메서드는 다음과 같다.

- **Array.Sort()**
	- 배열을 정렬한다.

- **Array.Reverse()**
	- 배열을 역순으로 바꾼다.

- **Array.ConvertAll()**
	- 배열을 특정 값으로 변환한다.

## 3.1 Array 클래스의 Sort() 메서드로 배열 정렬하기

>다음과 같이 arr 배열에 정수 데이터가 무작위로 저장되었을 때 Array.Sort() 메서드에 배열을 매개변수로 입력한 후 실행하면 arr 배열이 정렬된다.

```cs
> int[] arr = { 3, 2, 1, 4, 5 };
> Array.Sort(arr); // 정렬
> foreach (var item in arr)
. {
.     Console.WriteLine(item);
. }
1
2
3
4
5
```

## 3.2 Array 클래스의 Reverse() 메서드로 배열을 거꾸로 변환하기

```cs
> int[] arr = { 1, 2, 3 };
> Array.Reverse(arr); // 배열을 역순으로 변환
> arr
int[3] { 3, 2, 1 }
```

>코드 실행 결과처럼 Array 클래스의 여러 메서드 중에서 Reverse()를 사용하면 배열에 저장된 데이터를 역순으로 반환한다.

## 3.3 Array 클래스의 ConvertAll 메서드로 형식 변환하기

>Array.ConvertAll() 메서드를 사용하면 숫자 모양의 문자열 배열을 정수형 배열로 변경할 수 있다. 숫자 형태로 저장된 문자열 배열을 정수형 배열로 변경할 때는 다음과 같이 사용한다.

```cs
> string[] strArr = { "10", "20", "30" };
> int[] intArr = Array.ConvertAll(strArr, int.Parse);
> foreach (var number in intArr)
. {
.     Console.WriteLine(number);
. }
10
20
30
```

# 4 컬렉션 클래스

>닷넷에는 Stack, Queue, ArrayList, Hashtable 등 자료 구조를 다루는 컬렉션 클래스를 제공한다.

- Stack 클래스
- Queue 클래스
- ArrayList 클래스
- Hashtable 클래스

# 5 Stack 클래스

>Stack 클래스는 단어 그대로 음식을 담는 접시처럼 아래에서 위로 데이터를 쌓는 형태의 자료 구조를 다룬다. Stack 클래스는 LIFO(Last In First Out)(후입선출) 특성을 보이는데, 나중에 들어온 데이터가 먼저 출력되는 자료 구조이다.

>Stack 클래스의 주요 속성 및 메서드는 다음과 같다.

- **Count**
	- 스택에 있는 데이터 개수 조회

- **Push()**
	- 스택에 데이터 저장

- **Pop()**
	- 스택에서 데이터 꺼내기

>스택 구조를 다룰 때 가장 많이 나오는 단어는 오버플로(Overflow)이다. 오버플로는 스택이 꽉 차는 것을 의미한다. 반대인 언더플로(Underflow)는 스택이 비어 있는 것을 의미한다.

## 5.1 Stack 클래스 사용하기

>먼저 Stack 클래스를 사용하려면 System.Collections 네임스페이스를 포함해야 한다.

```cs
> using System.Collections;
```

>Stack 클래스의 인스턴스를 stack 이름으로 생성한다. Stack 클래스의 인스턴스인 소문자 stack은 일반적으로 stack 개체로 읽는다.

```cs
> Stack stack = new Stack();
```

>Stack 클래스는 Push() 메서드로 object 형식의 데이터를 저장할 수 있다.

```cs
> stack.Push("First");
> stack.Push("Second");
```

>Stack 클래스에 저장된 데이터는 Pop() 메서드로 읽어 올 수 있다. 이때 나중에 입력된(Push) 데이터가 먼저 출력된다.

```cs
> stack.Pop()
"Second"
> stack.Pop()
"First"
```

>스택에 저장된 데이터가 아무것도 없는데, Pop() 메서드를 요청하면 다음과 같이 에러가 발생할 수 있다. 

```cs
> stack.Pop()
System.InvalidOperationException: 스택이 비어 있습니다.
  + System.Collections.Stack.Pop()
```

## 5.2 Stack 클래스의 주요 멤버 사용하기

- StackNote.cs

```cs
using System;
using System.Collections; // 주요 자료 구조 관련 클래스들

class StackNote
{
    static void Main()
    {
        Stack stack = new Stack(); // (1) Stack 클래스의 인스턴스 생성

        stack.Push("첫 번째"); // (2) 데이터 입력 
        stack.Push("두 번째");
        stack.Push("세 번째");

        Console.WriteLine(stack.Pop()); // (3) 데이터 출력 : 세 번째
        Console.WriteLine(stack.Pop()); // (3) 데이터 출력 : 두 번째
        Console.WriteLine(stack.Pop()); // (3) 데이터 출력 : 첫 번째

        // 비어 있는 스택에서 Pop() 요청하면 에러
        try
        {
            Console.WriteLine(stack.Pop()); // 언더플로 발생
        }
        catch (Exception ex)
        {
            Console.WriteLine($"예외 내용 : {ex.Message}");
        }
    }
}
```

- 실행 결과

```cs
세 번째
두 번째
첫 번째
예외 내용 : Stack empty.
```

>Stack 클래스에 Push() 메서드로 데이터를 입력한 후 이를 Pop() 메서드로 꺼내어 쓰는 내용이다. 더 이상 스택에 데이터가 없을 때는 'Stack empty.' 예외가 발생한다. 참고로 스택에 너무 많은 데이터가 저장되어 스택이 꽉 차면 '스택 오버플로' 에러가 발생한다.

## 5.3 Stack 클래스의 Peek() 메서드로 최근 데이터만 가져오기

```cs
> using System.Collections;
> 
> Stack stack = new Stack(); // (1) Stack 개체 생성
> 
> stack.Push("닷넷 프레임워크"); // (2) Push()로 데이터 저장
> stack.Push("닷넷 코어");
> stack.Push("닷넷 생태계");
> 
> $"{stack.Peek()}, {stack.Count}" // (3) Peek()로 제일 위(마지막) 데이터 반환
"닷넷 생태계, 3"
> stack.Pop(); // (4) Pop()로 현재 스택의 가장 마지막 데이터 제거
> $"{stack.Peek()}, {stack.Count}" // (5) 스택의 마지막 데이터 반환 : 비어 있으면 에러
"닷넷 코어, 2"
> 
> if (stack.Count > 0) // (6) Count로 스택의 데이터 개수 확인
. {
.     stack.Pop(); // 가장 마지막 데이터 제거
.     Console.WriteLine($"{stack.Peek()}, {stack.Count}");
. }
닷넷 프레임워크, 1
> 
> stack.Clear(); // (7) Clear()로 스택 비우기
> stack.Count
0
```

>Stack 클래스의 Peek() 메서드는 스택 위에 있는 데이터를 가져오지만 Pop() 메서드처럼 제거하지는 않는다. 스택에 데이터를 넣고 계속해서 사용할 때는 Peek() 메서드를 쓴다.

# 6 Queue 클래스

>Queue 클래스는 Stack 클래스와 달리 먼저 들어온 데이터가 먼저 나온다. 일반적으로 은행에서 먼저 온 사람을 처리하는 것처럼 큐(Queue)라는 단어는 기다림 통로(은행 줄서기) 또는 FIFO(First In First Out)(선입선출)로 표현되며, 먼저 들어온 것이 먼저 나가는 형태의 데이터를 다룬다.

>여기에서 Enqueue()는 큐에 데이터를 저장하는 메서드고, Dequeue()는 큐에서 데이터를 출력하는 메서드이다.

```cs
> using System.Collections;
> 
> var queue = new Queue(); // (1) Queue 클래스의 인스턴스 생성
> 
> queue.Enqueue(10); // (2) 큐(대기 행렬)에 데이터 입력 : Enqueue()
> queue.Enqueue(20); 
> queue.Enqueue(30);
> 
> queue.Dequeue() // (3) 큐에서 데이터 출력 : Dequeue()
10
> queue.Dequeue()
20
> queue.Dequeue()
30
> queue.Dequeue()
System.InvalidOperationException: 큐가 비어 있습니다.
  + System.Collections.Queue.Dequeue()
```

>큐 개체에 Enqueue() 메서드로 10, 20, 30 형태로 데이터를 저장한 후 Dequeue() 메서드를 호출하면 다시 10, 20, 30 형태로 순서대로 데이터를 출력하는 구조가 바로 큐 클래스이다.

# 7 ArrayList 클래스

>C# 1.0 버전부터 제공되던 ArrayList 클래스는 컬렉션 형태의 데이터를 저장하고 관리하는 여러 편리한 API를 제공한다. 

```cs
> using System.Collections;
> 
> ArrayList list = new ArrayList();
> list.Add("C#");
> list.Add("TypeScript");
> 
> for (int i = 0; i < list.Count; i++)
. {
.     Console.WriteLine(list[i].ToString());
. }
C#
TypeScript
```

>ArrayList 클래스의 인스턴스인 list를 생성한 후 Add() 메서드로 문자열 등을 저장할 수 있다. 그런 다음 for 문 등으로 list[i] 형태로 ArrayList에 저장된 값을 읽어 사용할 수 있다. ArrayList의 Add() 메서드는 매개변수로 object 형식을 받기에 문자열을 포함한 C#의 모든 데이터 형식을 저장하고 사용할 수 있다. Add()로 추가된 항목은 Remove() 같은 메서드로 제거할 수 있다.

# 8 Hashtable 클래스

>Hashtable 클래스는 정수 인덱스 및 문자열 인덱스를 사용할 수 있다.

```cs
> using System.Collections;
> 
> // (1) Hashtable의 인스턴스 생성
> Hashtable hash = new Hashtable();
> 
> // (2) 배열형 인덱서를 사용 가능한 구조 및 문자열 인덱스 사용 가능
> hash[0] = "닷넷 프레임워크"; // (a) 배열과 같은 n번째 형태 사용 가능
> hash["CORE"] = "닷넷 코어"; // (b) 문자열 인덱스 사용 가능
> hash["ECO"] = "닷넷 생태계";
> 
> // (3) 직접 출력
> hash[0]
"닷넷 프레임워크"
> hash["CORE"]
"닷넷 코어"
> hash["ECO"]
"닷넷 생태계"
> 
> // (4) key와 value 쌍으로 출력 가능
> foreach (object o in hash.Keys)
. {
.     Console.WriteLine(hash[o]);
. }
닷넷 생태계
닷넷 코어
닷넷 프레임워크
```

>Hashtable은 배열처럼 hash[0], hash[1], ... 형태로 데이터를 저장할 수 있고, hash["CORE"], hash["ECO"]처럼 문자열 형태의 인덱스를 사용할 수 있다는 특징이 있다.
