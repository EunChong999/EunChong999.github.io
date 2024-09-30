---
layout: single
title: Chapter 27 널(null) 다루기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 널(null) 다루기에 대한 내용을 담고 있습니다.

>프로그래밍 언어에서 널(Null, NULL, null)은 아무것도 없는 상태를 나타낸다. 즉, null은 아무것도 없음을 의미하는 리터럴이다. 개체가 아무것도 참조하지 않는 것을 null 참조라고 한다.

# 1 null 값 

>null은 참조 형식이면서 아무것도 참조하지 않는다. 화살표(포인터)가 아무것도 가리키지 않아 값 자체가 없음을 의미한다. 

>null 값은 다음과 같이 정리할 수 있다. 

- 아무런 값이 없음

- 참조형 변수에 아무런 값을 설정하지 않음

- 알려지지 않은 값으로 아무 의미가 없거나 모르는 값, 값이 없음을 의미

- 변수가 아무런 값도 가리키고 있지 않음

- 변수가 이름만 만들고 아무런 참조도 하지 않음

- 개체가 만들어지고 아무런 값도 참조하지 않음을 나타냄

- 영어 단어로는 undefined

- 빈 값(Empty, "")과는 다름

## 1.1 null 값 사용하기

>int, float, double은 값 형식(value type)이고 string, object는 참조 형식(reference type)이다.

```cs
> int i = 0;            // 값 형식
> string s = null;      // 참조 형식
> s = "안녕하세요.";
> string empty = "";    // 빈 값(empty)은 null과는 다름
> i
0
> s
"안녕하세요."
> empty
""
```

# 2 null 기능 형식 : Nullable<\T> 형식

>기본 제공 형식을 null이 가능한 형식으로 변경하려면 Nullable<\T> 제네릭 형식을 사용하다. bool과 Nullable<\bool>의 차이점은 다음과 같다.

- bool 형식은 true와 false를 갖는다.
- Nullable<\bool> 형식은 true, false, null을 갖는다.

>Nullable<\T> 형식을 줄임 표현하는 방법은 데이터 형식 뒤에 ?(물음표) 기호를 붙이는 것이다. 예를 들어 bool?, int? 형식으로 null 기능 형식을 만들 수 있다.

>Nullable<\T> 형식이 제공하는 주요 멤버는 다음과 같다.

- **HasValue 속성**
	- 값이 있으면 true, null 값이면 false를 반환

- **Value 속성**
	- 값 반환

- **GetValueOrDefault**
	- 값 또는 기본값 반환

- Note

>Nullable<\T> 제네릭 구조를 사용하면 null 기능 형식의 변수를 만들 수 있다. 

```cs
> Nullable<bool> bln = null;
> bln.HasValue
false
> bln = true;
> bln.HasValue
true
```

## 2.1 null 기능 형식 사용하기 

>Nullable 형식은 null이 할당될 수 있는 형식을 의미한다.

```cs
> string s = null;  // 참조 형식 : null 할당 가능
> s
null
> 
> int i = null;     // 값 형식 : null 할당 불가능 -> 에러
(1,9): error CS0037: 'int'은(는) null을 허용하지 않는 값 형식이므로 null을 이 형식으로 변환할 수 없습니다.
> 
> int? i = null;
> i
null
> 
> double? d = null;
> d
null
> 
> // System.Nullable<T> 제네릭 클래스 : int?, double? 사용을 권장함
> Nullable<int> ii = null;
> int? ii = null;
> Nullable<double> dd = null;
> double? dd = null;
```

# 3 null 값을 다루는 연산자 

## 3.1 ?? 연산자(null 병합 연산자)

>물음표 2개(??)로 된 연산자인 null 병합 연산자(null coalescing operator)는 왼쪽 항이 null이 아니면 해당 값을 반환하고, 그렇지 않으면 오른쪽 값을 반환한다. 즉, 피연산자가 null이 아닐 때는 왼쪽 피연산자를 반환하고, null일 때는 오른쪽 피연산자를 반환한다.

```cs
> string nullValue = null;
> string message = "";
> 
> // (1) if 구문으로 null 값 비교 
> nullValue = null;
> if (nullValue == null)
. {
.     message = "[1] null이면 새로운 값으로 초기화합니다.";
. }
> message
"[1] null이면 새로운 값으로 초기화합니다."
> 
> // (2) ?? 연산자로 null 값 비교 
> nullValue = null;
> message = nullValue ?? "[2] null이면 새로운 값으로 초기화합니다.";
> message
"[2] null이면 새로운 값으로 초기화합니다."
> 
> nullValue = "Hello";
> message = nullValue ?? "[3] Nothing";
> message
"Hello"
```

>(1)처럼 일반적으로 null 값 비교는 if 문을 사용한다. if 문으로 null 값을 비교하는 코드를 (2)처럼 ?? 연산자를 사용하여 작성할 수 있다. ?? 연산자는 이처럼 기존에 if 문으로 잘 표현했던 코드를 새로운 형태로 좀 더 간결하게 표현한다.

>이러한 null 병합 연산자인 ?? 연산자를 null 값이 자료에 대해 특정 기본값으로 초기화될 때 유용하게 사용할 수 있다.

## 3.2 null 병합 연산자로 문자열 변수의 null 값 확인하기

```cs
> var result = "";
> var message = "";
> 
> message = null;
> result = message ?? "기본값";
> result
"기본값"
> 
> message = "있는 값";
> result = message ?? "기본값";
> result
"있는 값"
```

>null 병합 연산자를 사용하면 특정 변수 값이 null이면 새로운 '기본값'으로 초기화되고, null이 아닌 값으로 이미 초기화된 변수는 해당 값으로 그대로 사용한다.

## 3.3 null 기능 형식에 null 병합 연산자 사용하기

```cs
> int? value = null;               // null 기능 형식에 null로 초기화
> int defaultValue = value ?? -1;  // value가 null이면 -1 대입 
> defaultValue
-1
```

>이 코드에서 value 변수에는 null이 입력되었다. value ?? -1; 코드로 value 값이 null이면 null 대신에 -1을 defaultValue에 할당한다. 이러한 코드를 사용함으로써 null 때문에 발생하는 에러를 줄일 수 있다.

## 3.4 null 병합 연산자와 default 키워드

```cs
> int? x = null;
> int y = x ?? 100;           // x가 null이면 100으로 초기화
> int z = x ?? default(int);  // 정수형의 기본값인 0으로 초기화
> int z = x ?? default;       // 정수형의 기본값인 0으로 초기화
> $"y : {y}, z : {z}"
"y : 100, z : 0"
```

>특정 식의 결과에 null 대신 해당 형식의 기본값을 저장할 때는 default(T) 코드와 함께 사용 가능하다. default(int) 구문은 다음과 같이 default로 줄여 표현해도 된다.

```cs
> int? x = null;
> int z = x ?? default;
> z
0
```

## 3.5 null 병합 연산자와 null 기능 형식을 함께 사용하기

>null 기능 형식과 null 병합 연산자를 함께 사용하면 다음 코드도 실행 가능하다. 

```cs
> bool? unknown = null;
> if (unknown ?? true)
.     Console.WriteLine("출력됨");
출력됨
> unknown = false;
> if (!unknown ?? false)
.     Console.WriteLine("출력됨");
출력됨
```

## 3.6 null 조건부 연산자

>null 조건부 연산자(null conditional operator)인 ?. 연산자는 null 기능 형식 뒤에 붙어 해당 값이 null인지 테스트한다.

```cs
> double? d = null;
> d
null
> d?.ToString()
null
```

>d가 null이면 null을 반환한다.

```cs
> double? d = 1.0;
> d?.ToString()
"1"
> d?.ToString("#.00")
"1.00"
```

>d가 null이 아니면 ToString() 메서드를 실행한다.

## 3.7 null 조건부 연산자 사용하기

>null 조건부 연산자인 ?.는 null 기능 형식에 사용하여 코드를 줄여서 표현할 수 있다.

```cs
> int? len;
> string message;
> 
> message = null;
> len = message?.Length;
> len
null
> 
> message = "안녕";
> len = message?.Length;
> len
2
```

>문자열 변수 message 값이 null이면 ?. 연산자를 실행했을 때 null 값을 반환하고, 그렇지 않으면 ?. 연산자 뒤에 오는 속성 또는 메서드를 실행한다. ?. 연산자는 ?\[] 형태로 배열 또는 인덱서에도 사용된다.

## 3.8 null 조건부 연산자와 컬렉션 클래스

>?. 연산자는 컬렉션이 null이면 null이고, 그렇지 않으면 뒤에 오는 속성 값을 반환한다. 엘비스의 머리 모양과 비슷하다고 하여 Elvis 연산자라고도 한다.

```cs
> List<string> list = null;
> int? numberOfList;
> 
> numberOfList = list?.Count; // (1) 리스트가 null이면 null 반환
> numberOfList
null
> 
> list = new List<string>();
> list.Add("안녕하세요."); list.Add("반갑습니다.");
> 
> numberOfList = list?.Count; // (2) 리스트가 null이 아니므로 Count 속성 값만 2 반환
> numberOfList
2
```

>제네릭 컬렉션 값이 null이면 ?. 연산자는 null을 반환하고, 그렇지 않으면 ?. 연산자 뒤에 있는 컬렉션의 카운트를 나타내는 Count 속성 값을 반환한다.

## 3.9 null 조건부 연산자와 null 병합 연산자 함께 사용하기

>?? 연산자는 컬렉션이 null이 아니면 해당 값을 반환한다. null이면 뒤에 저장한 값을 반환한다.

```cs
> int num;
> List<string> list;
> 
> // (1) 컬렉션 리스트가 null이면 Count를 읽을 수 없기에 0으로 초기화
> list = null;
> num = list?.Count ?? 0; // null이면 0 반환, 오른쪽 값 사용
> num
0
> 
> // (2) 컬렉션 리스트가 null이 아니면 Count 속성 값을 사용
> list = new List<string>(); list.Add("또 만나요.");
> num = list?.Count ?? 0; // null이 아니기에 왼쪽 값 사용
> num
1
```

>?. 연산자의 결괏값이 null이면 null 대신에 ?? 연산자를 사용하여 새로운 값으로 초기화할 수 있다.

>C# 프로그래밍에서 가장 많은 에러를 발생시키는 부분이 바로 널(null) 관련 에러이다. 특정 개체가 참조되지 않은 상태로 사용되면 반드시 에러가 발생된다. 이러한 null 관련 에러를 잡으려면 반드시 null 값이 아닌 실제 값으로 초기화하고, null 확인을 null 병합 연산자와 null 조건부 연산자를 사용하여 null 대신에 기본값 등으로 초기화해야 한다. null 관련 연산자는 null 처리에서 if 문이 아닌 식을 사용하여 처리할 수 있도록 도움을 준다.


