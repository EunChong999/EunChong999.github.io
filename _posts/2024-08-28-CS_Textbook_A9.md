---
layout: single
title: Chapter 10 관계형 연산자와 논리 연산자 사용하기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 관계형 연산자와 논리 연산자 사용하기에 대한 내용을 담고 있습니다.

# 1 관계형 연산자

>관계형 연산자(relational operator)(또는 비교 연산자(comparative operator))는 두 항이 큰지, 작은지 또는 같은지 등을 비교하는 데 사용한다. 관계형 연산자의 결괏값은 논리 데이터 형식인 참(True) 또는 거짓(False)으로 출력된다.

>관계형 연산자의 종류는 다음과 같다.

- 관계형 연산자

| 연산자 | 예      | 의미                        | 설명                                       |
| --- | ------ | ------------------------- | ---------------------------------------- |
| <   | A < B  | 작으지(LessThan)             | A가 B보다 작으면 True, <br>그렇지 않으면 False       |
| <=  | A <= B | 작거나 같은지(LessThanEqual)    | A가 B보다 작거나 같으면 True,<br>그렇지 않으면 False    |
| >   | A > B  | 큰지(GreaterThan)           | A가 B보다 크면 True,<br>그렇지 않으면 False         |
| >=  | A >= B | 크거나 같은지(GreaterThanEqual) | A가 B보다 크거나 같으면 True,<br>그렇지 않으면 False    |
| ==  | A == B | 같은지(Equal)                | A와 B가 같으면 True,<br>그렇지 않으면 False         |
| !=  | A != B | 다른지(NotEqual)             | A와 B가 같지 않으면 True,<br>그렇지 않으면(같으면) False |

```cs
> int x = 3;
> int y = 5;
> x == y
false
> x != y
true
> x > y
false
> x >= y
false
> x < y
true
> x <= y
true
```

>C#에서 두 데이터를 비교할 때 사용하는 비교 연산자 중에서 == 연산자는 데이터가 같은 값인지 확인한다. 같으면 참(true)을, 다르면 거짓(false)을 데이터인 bool(불) 형식의 데이터를 반환한다.
>나머지 관계형 연산자도 그 의미에 맞게 논리 형식의 결과가 주어진다.

## 1.1 == 연산자를 사용하여 문자열 값 비교하기

>비교 연산자 중에서 == 연산자는 왼쪽 항과 오른쪽 항의 값이 같은지 물어본다. 같으면 참을, 다르면 거짓을 반환한다. 다음 코드는 문자열을 비교하는 식인데 대 ○ 소문자를 구분하기 때문에 "AAA"와 "aaa"는 서로 다른 문자열로 인식하여 결괏값은 False가 출력된다.

```cs
> Console.WriteLine("AAA" == "aaa");
False
```

# 2 논리 연산자

>논리 연산자(logical operator)는 논리곱(AND), 논리합(OR), 논리부정(NOT)의 조건식에 대한 논리 연산을 수행한다. 연산의 결과 값은 참(True) 또는 거짓(False)의 bool 형식으로 반환되어 Boolean(불리언) 연산자라고도 한다. 논리 연산자도 비교 연산자와 마찬가지로 결괏값은 참 또는 거짓을 반환한다. 

>논리 연산자의 종류는 다음 표와 같다.

- 논리 연산자

| 연산자  | 예        | 의미                    | 설명                                                                                                                                                |
| ---- | -------- | --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| &&   | A && B   | 논리곱<br>AND 조건<br><br> | A항과 B항 모두 참(True)일 때만 참(True), <br>그렇지 않으면 거짓(False). <br>즉, 항 2개 중 하나라도 거짓(False)이면 거짓(False)<br><br>'~이고, 그리고' 의미로 사용<br><br>양쪽 모두 참(True)일 때 참 |
| \|\| | A \|\| B | 논리합<br>OR 조건<br>      | A항과 B항 모두 거짓(False)일 때만 거짓(False),<br>그렇지 않으면 참(True).<br>즉, 항 2개 중 하나라도 참(True)이면 참(True)<br><br>'~이거나, 또는' 의미로 사용<br><br>양쪽 중 한쪽만 참(True)이라도 참  |
| !    | !A       | 논리부정<br>NOT 조건<br>    | A항이 참(True)이면 거짓(False)을, <br>A항이 거짓(False)이면 참을 반환<br><br>'~가 아닌' 의미로 사용<br><br>참(True)과 거짓(False)을 뒤집음                                          |

>A항(식)과 B항(식)의 값에 따른 세 가지 결과의 논리표(진리표(truth table))는 다음 표와 같이 표시할 수 있다. 

- 논리표

| **A** | **B** | **A AND B** | A OR B       | NOT A  |
| ----- | ----- | ----------- | ------------ | ------ |
| **A** | **A** | **A && B**  | **A \|\| B** | **!A** |
| True  | True  | True        | True         | False  |
| True  | False | False       | True         | False  |
| False | True  | False       | True         | True   |
| False | False | False       | False        | True   |

## 2.1 논리 AND 연산자(&&) 사용하기

>논리 AND 연산자는 둘 다 참일 때만 참을 반환한다. 

```cs
> Console.WriteLine(true && true);  // 둘 다 참일 때만 참
True
> Console.WriteLine(true && false); // 하나라도 거짓이면 거짓
False
```

- LogicalAnd.cs

```cs
using System;

class LogicalAnd
{
    static void Main()
    {
        Console.WriteLine($"true  && true  -> {true && true}  ");
        Console.WriteLine($"true  && false -> {true && false} ");
        Console.WriteLine($"false && true  -> {false && true} ");
        Console.WriteLine($"false && false -> {false && false}");
    }
}
```

- 실행 결과

```cs
true  && true  -> True
true  && false -> False
false && true  -> False
false && false -> False
```

>실행 결과처럼 && 연산자는 둘 다 참일 때만 반환한다.

## 2.2 논리 OR 연산자(||) 사용하기

```cs
> false || true // 하나라도 참이면 참
true
> false || false // 둘 다 거짓일 때만 거짓
false
```

- LogicalOr.cs

```cs
using System;

class LogicalOr
{
    static void Main()
    {
        Console.WriteLine($"true  || true  -> {true || true}  ");
        Console.WriteLine($"true  || false -> {true || false} ");
        Console.WriteLine($"false || true  -> {false || true} ");
        Console.WriteLine($"false || false -> {false || false}");
    }
}
```

- 실행 결과

```cs
true  || true  -> True
true  || false -> True
false || true  -> True
false || false -> False
```

>실행 결과처럼 || 연산자는 하나라도 참이면 참을 반환하고, 둘 다 거짓일 때는 거짓을 반환한다.

- Note

>C#에서 단락(short-circuiting) 기능은 AND 연산과 OR 연산을 진행할 때 부분의 결괏값에 따라서 나머지 연산 결과가 결정된다. 다음 두 가지 유형이 있다. 

- (연산식1 && 연산식2)
	- 연산식1이 거짓(False)이면 연산식2와 상관없이 전체 결괏값은 거짓(False)이 된다. 
- (연산식1 || 연산식2)
	- 연산식1이 참(True)이면 연산식2의 결괏값과 상관없이 전체 결괏값은 참(True)이 된다.

## 2.3 논리 NOT 연산자(!) 사용하기

```cs
> (1 == 1)
true
> !(1 == 1)
false
> (1 != 1)
false
> !(1 != 1)
true
```

>NOT 연산자는 항이 하나인 단항 연산자이다.

- LogicalNot.cs

```cs
using System;

class LogicalNot
{
    static void Main()
    {
        Console.WriteLine($"!true  -> {!true}");
        Console.WriteLine($"!false -> {!false}");
    }
}
```

- 실행 결과

```cs
!true  -> False
!false -> True
```

>실행 결과처럼 ! 연산자는 조건식 결과를 반대로 바꾸어 준다.

## 2.4 세 가지 논리 연산자 모두 사용하기

- LogicalOperator.cs

```cs
using static System.Console; // System.Console까지 생략 가능

class LogicalOperator
{
    static void Main()
    {
        var i = 3;
        var j = 5;
        var r = false;

        r = (i == 3) && (j != 3); // r = true && true => true
        WriteLine(r);

        r = (i != 3) || (j == 3); // r = false || false => false
        WriteLine(r);

        r = (i >= 5);                    // r => false
        WriteLine("{0}", !r);            // false <-> true

        WriteLine(false && true);        // false
        WriteLine((1 == 1) || (1 != 1)); // true
        WriteLine(!(1 == 1));            // true -> false
    }
}
```

- 실행 결과

```cs
True
False
True
False
True
False
```

>웹 사이트의 로그인 페이지 등을 작성하다 보면 아이디와 암호가 모두 정확(True)해야 하는 로그인을 처리할 경우가 있는데, 이때는 AND(&&) 연산을 수행한다. 그리고 로그인 후 관리자 또는 회원만 게시판에 글을 작성하도록 처리할 경우에는 OR(||) 연산을 주로 수행한다.

- Note

>C#에서 코드 분석을 쉽게 하려면 F10(프로시저 단위 실행) 또는 F11(한 단계씩 코드 실행)을 적절히 사용하면 도움이 된다. 

>디버깅 모드에서 (i == 3) 같은 조건식에 마우스 커서를 올리면 True와 False의 값을 알려 준다. 

