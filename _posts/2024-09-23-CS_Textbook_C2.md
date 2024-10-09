---
layout: single
title: Chapter 23 문자열 다루기
categories:
  - Language
tags:
  - C#
  - Study
---
>이 포스트는 문자열 다루기에 대한 내용을 담고 있습니다.

>닷넷 프레임워크에 내장된 클래스 중에서 문자열 관련 클래스(String, StringBuilder)는 문자열 길이 반환, 문자열 공백 제거, 대 ○ 소문자로 변환 등 기능을 하는 메서드를 제공한다. C#의 문자열은 유니코드(unicode) 문자열이기에 다국어를 지원하고, 문자열 관련 모든 기능도 다국어를 제대로 처리한다.

# 1 문자열 다루기

>문자열 관련 속성 또는 메서드는 다음 표와 같다.

| 속성 및 메서드              | 설명                    |
| --------------------- | --------------------- |
| Length                | 문자열 길이 값 반환           |
| ToUpper()             | 문자열을 모두 대문자로 변환       |
| ToLower()             | 문자열을 모두 소문자로 변환       |
| Trim()                | 문자열 양쪽 공백을 잘라 냄       |
| Replace(원본문자열, 대상문자열) | 원본 문자열을 대상 문자열로 변경    |
| Substring(문자열인덱스, 길이) | 지정된 문자열 인덱스부터 길이만큼 반환 |

## 1.1 문자열 관련 주요 메서드 다루기

```cs
> string message = "hello, World!";
> Console.WriteLine(message.ToUpper());
HELLO, WORLD!
> Console.WriteLine(message.ToLower());
hello, world!
> message.Replace("hello", "안녕하세요.").Replace("World", "세계.") // 바꾸기
"안녕하세요., 세계.!"
```

>소문자로만 된 문자열을 담은 message 변수 값은 ToUpper() 메서드를 사용하면 대문자로 변경할 수 있고, ToLower() 메서드를 사용하면 소문자로 변경할 수 있다. 문자열 변수에 Replace() 메서드를 여러 번 호출할 때마다 계속해서 값을 바꿀 수 있다. 이렇게 메서드를 여러 번 점(.)을 찍어 구분하면서 호출하는 방법을 메서드 체인 또는 체이닝이라고 한다.

## 1.2 메서드 체이닝

>C#에서 문자열 같은 개체 하나에서 메서드를 여러 번 호출하는 방법을 메서드 체인(method chain) 또는 메서드 체이닝(method chaining) 또는 파이프라인(pipelines)이라고 한다.

>다음 코드는 " Hello " 문자열에서 "Hello"를 "Hi"로 변경한다. 그리고 시작 공백을 없애고(TrimStart)마지막 공백을 없앤 후(TrimEnd) 양쪽 공백을 없에는(Trim) 추가 작업을 수행한다.

```cs
> " Hello ".Replace("Hello", "Hi").TrimStart().TrimEnd().Trim()
"Hi"
```

>참고로 이러한 메서드 체이닝은 C#으로 함수형 프로그래밍을 표현하는 방법 중 하나이다.

## 1.3 String 클래스

>System.String 클래스는 string 키워드와 동일하게 문자열 변수를 생성할 때 사용한다. 

```cs
> String s1 = "안녕하세요."; // String 클래스
> string s2 = "반갑습니다."; // string 키워드
> $"{s1} {s2}"
"안녕하세요. 반갑습니다."
```

>소문자로 시작하는 string 키워드는 대문자로 시작하는 String 클래스와 기능이 동일하다.

>참고로 String 클래스에 문자 배열을 전달하면 문자열로 변환할 수 있다.

```cs
> char[] charArray = { 'A', 'B', 'C' };
> String str = new String(charArray);
> str
"ABC"
```

## 1.4 Length 속성을 사용하여 문자열 길이 구하기

```cs
> string s1 = "Hello.";
> string s2 = "안녕하세요.";
> $"{s1.Length}, {s2.Length}" // 문자열 길이 : String.Length 속성
"6, 6"
```

>문자열 변수에 괄호가 붙지 않는 Length 속성을 요청하면 문자열 길이를 알려준다.  영문이나 한글과 상관없이 동일하게 문자 개수를 알려 준다.

## 1.5 String.Concat() 메서드 사용하여 문자열 연결하기

```cs
> string s1 = "안녕" + "하세요.";
> string s2 = String.Concat("반갑", "습니다.");
> $"{s1} {s2}"
"안녕하세요. 반갑습니다."
```

>C#에서 문자열을 묶는 방법은 여러 가지가 있다. 더하기 연산자를 사용하거나 간단히 문자열 2개를 묶을 때는 String.Concat() 메서드를 사용할 수 있다.

## 1.6 문자열을 묶는 세 가지 표현 방법 정리하기

```cs
> var displayName = "";
> var firstName = "승수";
> var lastName = "백";
> 
> // (1) 더하기(+) 연산자 사용
> displayName = "이름 : " + lastName + firstName;
> displayName
"이름 : 백승수"
> 
> // (2) string.Format(), String.Format() 메서드 사용
> displayName = string.Format("이름 : {0}{1}", lastName, firstName);
> displayName
"이름 : 백승수"
> 
> // (3) 문자열 보간법 사용
> displayName = $"이름 : {lastName}{firstName}";
> displayName
"이름 : 백승수"
```

>이 예제처럼 더하기 연산자, String.Format() 메서드, $""와 {} 형태의 문자열 보간법을 사용하여 문자열을 묶을 수 있다. 추가로 String.Concat() 메서드도 사용할 수 있다.

## 1.7 문자열을 비교하는 두 가지 방법 정리하기

>C#에서 == 연산자를 사용한 문자열 비교는 대 ○ 소문자를 구분한다. 대 ○ 소문자를 구분하지 않고 문자열을 비교하려면 문자열 변수의 Equals() 메서드에 추가 옵션인 StringComparison 열거형의 OrdinalIgnoreCase 값을 사용해야 한다.

```cs
> string userName = "RedPlus";
> string userNameInput = "redPlus";
> 
> if (userName.ToLower() == userNameInput.ToLower()) // (1) == 연산자 사용
. {
.     Console.WriteLine("[1] 같습니다.");
. }
[1] 같습니다.
> 
> if (string.Equals(userName, userNameInput, // (2) string.Equals() 메서드 사용
.     StringComparison.InvariantCultureIgnoreCase))
. {
.     Console.WriteLine("[2] 같습니다.");
. } 
[2] 같습니다.
```

>String.Equals() 메서드는 문자열 변수 2개의 값을 비교한다. 기본값은 대 ○ 소문자를 구별하지만, 세 번째 매개변수로 StringComparison.InvariantCultureIgnoreCase 열거형을 옵션으로 주면 대 ○ 소문자를 구별하지 않는다.

## 1.8 문자열의 대 ○ 소문자 비교하기

```cs
> string s1 = "Github";
> string s2 = "github";
> 
> // (1) 문자열 값의 대소문자를 구분
> if (s1 == s2)
. {
.     Console.WriteLine("같다.");
. }
. else
. {
.     Console.WriteLine("다르다.");
. }
다르다.
> 
> // (2) 문자열의 대소문자를 구분하지 않고 비교
> if (s1.Equals(s2, StringComparison.OrdinalIgnoreCase))
. {
.     Console.WriteLine("같다.");
. }
같다.
```

>또 다른 간단한 방법은 문자열 변수의 ToLower()와 ToUpper() 메서드를 사용하여 한 가지 방식으로 변경한 후 == 연산자로 비교할 수 있다.

## 1.9 ToCharArray() 메서드로 문자열을 문자 배열로 변환하기

```cs
> string s = "Hello.";
> char[] ch = s.ToCharArray(); // 문자열을 문자 배열로 변환
> ch
char[6] { 'H', 'e', 'l', 'l', 'o', '.' }
> for (int i = 0; i < ch.Length; i++)
. {
.     Console.Write($"{ch[i]}\t");
. }
H	e	l	l	o	.	
```

>문자열 변수에 ToCharArray() 메서드를 실행하면 문자열을 문자의 배열로 반환한다. 그렇게 생성된 ch 배열을 for 문을 사용하여 문자로 하나씩 출력하면 문자열이 문자 배열로 변환되어 출력하는 것을 확인할 수 있다.

## 1.10 Split() 메서드로 문자열 분리하기

```cs
> string src = "Red,Green,Blue";
> string[] colors = src.Split(','); // 특정 구분자를 사용하여 문자열 배열 만들기
> colors
string[3] { "Red", "Green", "Blue" }
```

>원본 문자열인 src 변수에는 콤마로 구분하여 문자열 3개가 저장된다. 이러한 형태에서는 콤마 같은 구분자를 바탕으로 새로운 문자열 배열을 만들 때 Split() 메서드를 사용한다.

## 1.11 문자열의 null 값 및 빈 값 체크하기

>문자열 변수에는 ""처럼 빈 값이나 null 값이 들어올 수 있다. string.IsNullOrEmpty() 메서드로 문자열 변수를 묶어 주면 null 또는 빈 값인지 알 수 있다.

```cs
> var str = "";
> var str = String.Empty;
> 
> if (str == null || str == "") // (1) null 비교와 "" 값 비교를 사용하여 처리
. {
.     WriteLine($"{nameof(str)} 변수 값은 null 또는 빈 값(Empty)입니다.");
. }
str 변수 값은 null 또는 빈 값(Empty)입니다.
> 
> if (string.IsNullOrEmpty(str)) // (2) string.IsNullOrEmpty() 메서드를 사용하여 처리
. {
.     WriteLine($"{nameof(str)} 변수 값은 null 또는 빈 값(Empty)입니다.");
. }
str 변수 값은 null 또는 빈 값(Empty)입니다.
```

>(1)처럼 null과 ""를 비교하는 코드를 한 번에 해 주는 API가 (2)의 string.IsNullOrEmpty() 메서드이다. String.IsNullOrEmpty()와 string.IsNullOrEmpty()처럼 String은 대문자 클래스 이름 또는 소문자 키워드 중 하나로 표현된다.

## 1.12 문자열 변수의 유효성을 검사하는 세 가지 방법 

```cs
> string userName = "a_b_c";
> 
> // (1) 빈 값(Empty)과 null 값 확인
> userName = null;
> if (userName != "" && userName != null)
. {
.     var s = userName.Split('_'); // null일 때 에러 발생
. }
> 
> // (2) (1)과 동일한 표현 방법
> userName = "";
> if (!string.IsNullOrEmpty(userName))
. {
.     var s = userName.Split('_');
. }
> 
> // (3) ((1), (2)) + "공백"까지 처리
> userName = "";
> if (!string.IsNullOrWhiteSpace(userName))
. {
.     var s = userName.Split('_');
. }
```

>이 코드는 if 문 3개가 한 번도 실행되지 않고, 출력 내용이 없어 실행 결과도 출력하지 않는다.

# 2 문자열 처리 관련 주요 API 

1 . 문자열 변수는 초기화하지 않으면 기본적으로 null 값으로 초기화한다. 일반적으로 빈 문자열을 의미하는 "" 또는 String.Empty 속성으로 초기화한다.

```cs
> string str = "";
> str = String.Empty;
```

2 . 문자열 변수의 Length 속성을 사용하여 문자열 길이를 구할 수 있다. 한글 및 영문 모두 한 글자로 표현한다.

```cs
> string str = " Abc Def Fed Cba ";
> str.Length
17
```

3 . 문자열은 문자 배열을 의미한다. Str[5] 형태로 다섯 번째 인덱스의 문자 하나를 구할 수 있다.

```cs
> string str = " Abc Def Fed Cba ";
> str[6 - 1]
'D'
```

4 . ToUpper() 메서드로는 대문자로 변경하고, ToLower() 메서드로는 소문자로 변경한다.

```cs
> string str = " Abc Def Fed Cba ";
> str.ToUpper()
" ABC DEF FED CBA "
> str.ToLower()
" abc def fed cba "
```

5 . Trim() 메서드를 사용하면 문자열의 시작과 끝부분에서 하나 이상의 공백을 제거할 수 있다. 시작 공백 또는 마지막 공백을 제거할 때는 TrimStart()와 TrimEnd() 메서드를 사용한다.

```cs
> string str = " Abc Def Fed Cba ";
> str.Trim()
"Abc Def Fed Cba"
> str.TrimStart()
"Abc Def Fed Cba "
> str.TrimEnd()
" Abc Def Fed Cba"
```

6 . Replace() 메서드는 매개변수 2개 중 첫 번째 매개변수를 문자열에서 검색한 후 있으면 두 번째 매개변수로 변경한 값을 반환한다. 

```cs
> string str = " Abc Def Fed Cba ";
> str.Replace("Def", "디이에프")
" Abc 디이에프 Fed Cba "
```

7 . 모든 문자열 처리 관련 메서드는 하나 이상을 연결해서 호출할 수 있다. 이를 메서드 체이닝이라고 한다.

```cs
> string str = " Abc Def Fed Cba ";
> str.Replace("Def", "디이에프").Replace("Fed", "XYZ").ToLower()
" abc 디이에프 xyz cba "
```

8 . IndexOf() 메서드는 문자열 앞부분부터 검색을 시작하여 지정된 문자의 위치(인덱스)를 알려준다. LastIndexOf() 메서드는 문자열 뒤에서부터 검색을 시작하여 지정된 문자의 위치(인덱스)를 구할 때 사용한다. 즉, 처음 요소의 인덱스는 IndexOf() 메서드를 사용하고, 마지막 요소의 인덱스는 LastIndexOf() 메서드를 사용하여 구한다.

```cs
> string str = " Abc Def Fed Cba ";
> str.IndexOf('e')
6
> str.LastIndexOf('e')
10
```

9 . Substring() 메서드는 Substring(5, 3) 형태로 다섯 번째 인덱스부터 세 글자를 읽어 올 수 있고, Substring(5) 형태로 다섯 번째 인덱스 이후로 나오는 모든 문자열을 반환할 수 있다. 

```cs
> string str = " Abc Def Fed Cba ";
> str.Substring(5, 3)
"Def"
> str.Substring(5)
"Def Fed Cba "
```

10 . Remove() 메서드는 매개변수로 지정한 위치의 모든 문자 또는 문자열을 제거하여 출력할 수도 있다.

```cs
> string str = " Abc Def Fed Cba ";
> str.Remove(5, 3)
" Abc  Fed Cba "
```

11 . 문자열 비교는 == 연산자, String.Compare() 메서드, String.Equals() 메서드 등을 사용하여 값을 비교할 수 있다.

```cs
> string str = " Abc Def Fed Cba ";
> str[2 - 1] == str[16 - 1]
false
> String.Compare("A", "C")
-1
> "A".CompareTo("C")
-1
> "Abc".Equals("Abc")
true
> String.Equals("Abc", "aBC")
false
```

12 . StartsWith() 메서드로 특정 문자열로 시작하는지 여부를 알 수 있고, EndsWith() 메서드로 특정 문자열로 끝나는지 여부를 알 수 있다.

```cs
> string str = " Abc Def Fed Cba ";
> "http://www.dotnetkorea.com".StartsWith("http")
true
> "http://www.dotnetkorea.com".EndsWith(".com")
true
```

13 . 문자열을 연결할 때는 더하기 연산자, String.Concat() 메서드, String.Format() 메서드 및 문자열 보간법 등을 사용한다.

```cs
> string str = " Abc Def Fed Cba ";
> var hi1 = "안녕";
> var hi2 = "하세요.";
> hi1 + hi2
"안녕하세요."
> String.Concat(hi1, hi2)
"안녕하세요."
> String.Format("{0} {1} {0}", hi1, hi2)
"안녕 하세요. 안녕"
> $"{hi1} {hi2}"
"안녕 하세요."
```

14 . String.Format() 메서드 및 문자열 보간법은 문자열에 지정된 숫자 값을 바탕으로 통화량(C) 또는 세 자리마다 콤마를 찍는 문자열을 출력하도록 할 수 있다.

```cs
> string str = " Abc Def Fed Cba ";
> String.Format("{0:C}", 1000)
"₩1,000"
> String.Format("{0:#,###}", 1000)
"1,000"
```

15 . Split() 메서드는 지정한 문자를 구분자로 하여 문자열에서 또 다른 문자열 배열을 뽑아낸다. str 변수는 공백을 기준으로 구분되어 있다. Split(' ') 형태로 공백 하나를 구분자로 해서 문자열 배열로 구분하여 strArray 배열을 채우면 Abc Def Fed Cba 순서로 배열 요소가 생성된다.

```cs
> string str = " Abc Def Fed Cba ";
> string[] strArray = str.Trim().Split(' ');
> foreach (string s in strArray)
. {
.     Console.WriteLine(s);
. }
Abc
Def
Fed
Cba
```

16 . 기타 Insert() 메서드로 문자열을 삽입하거나 Remove() 메서드로 문자열을 제거할 수 있다.

```cs
> string original = "Hello";
> string modified = original.Insert(5, "World");
> modified
"HelloWorld"
> string original = "HelloWorld";
> string modified = original.Remove(5);
> modified
"Hello"
```

17 . 문자열에 PadLeft()와 PadRight()를 사용하여 특정 문자를 왼쪽 또는 오른쪽에 채울 수 있다.

```cs
> string number = "1234";
> number.PadLeft(10, '0')
"0000001234"
> number.PadRight(10, '_')
"1234______"
```

# 3 StringBuilder 클래스를 사용하여 문자열 연결하기

>string 키워드로 선언된 문자열 변수는 더하기 연산자 등을 사용하여 문자열을 연결할 수 있다. System.Text 네임스페이스에 포함된 StringBuilder 클래스는 문자열을 추가 및 삭제하는 등 유용한 API를 제공함으로써 긴 문자열을 묶어 처리할 때 편리하게 사용할 수 있다. 

>StringBuilder 클래스는 Console.WriteLine() 또는 String.Format()과 달리 직접 StringBuilder.메서드(); 형태로 사용하지 않는다.

>StringBuilder 클래스의 주요 멤버들은 인스턴스 멤버이기에 클래스의 인스턴스인 개체를 생성한 후 호출할 수 있다. 클래스를 사용하려고 새로운 개체를 만드는 것을 인스턴스 생성이라고 한다. 간단한 구문은 다음과 형태가 같다.

```cs
클래스 개체 = new 클래스();
```

>StringBuilder 클래스를 사용하려면 다음과 같이 builder 등 새로운 이름의 개체(인스턴스)를 생성해야 한다.

```cs
> StringBuilder builder = new StringBuilder();
```

## 3.1 StringBuilder 클래스의 Append() 메서드로 문자열 연결하기

```cs
> using System.Text;
> StringBuilder sb = new StringBuilder(); // (1) StringBuilder 클래스의 인스턴스 생성
> 
> sb.Append("January\n");                 // (2) Append() 메서드로 문자열 추가
> sb.Append("February\n");
> sb.AppendLine("March");
> 
> sb
[January
February
March
]
> sb.ToString()                           // (3) ToString() 메서드로 문자열로 출력
"January\nFebruary\nMarch\r\n"
```

>StringBuilder 클래스는 인스턴스를 생성한 후 Append() 등 메서드를 사용하여 문자열을 추가한다. AppendLine() 메서드를 사용하면 문자열 끝에 \\r\\n을 추가한다.

>StringBuilder의 개체인 sb 변수는 그 자체가 StringBuilder이기에 이 안에 묶여 있는 문자열을 출력하려면 ToString() 메서드로 문자열을 변환한 후 사용 가능하다. 

## 3.2 메서드 체이닝으로 StringBuilder 클래스의 여러 메서드 호출하기

>StringBuilder 클래스도 메서드 체이닝을 사용하여 여러 메서드를 단계별로 호출할 수 있다.

```cs
> using System.Text;
> var message = new StringBuilder()
.     .AppendFormat("{0} 클래스를 사용한 ", nameof(StringBuilder))
.     .Append("메서드 ")
.     .Append("체이닝 ")
.     .ToString()
.     .Trim();
> message
"StringBuilder 클래스를 사용한 메서드 체이닝"
```

## 3.3 StringBuilder 클래스 사용하기

>StringBuilder 클래스는 긴 문자열을 묶을 때 효과적이다.

```cs
> using System.Text;
> StringBuilder sb = new StringBuilder();
> 
> sb.Append("<script>");
> sb.AppendFormat("window.alert(\"{0}\");", DateTime.Now.Year);
> sb.AppendLine("</script>");
> sb.ToString()
"<script>window.alert(\"2024\");</script>\r\n"
```

>StringBuilder 클래스의 인스턴스를 생성한 후 Append(), AppendFormat(), AppendLine() 등 메서드를 사용해서 문자열을 여러 방식으로 추가할 수 있다.

# 4 String과 StringBuilder 클래스의 성능 차이 비교하기

- StringPerformance.cs

```cs
using System;

class StringPerformance
{
    static void Main()
    {
        DateTime start = DateTime.Now;

        string msg = "";
        for (int i = 0; i < 10000; i++)
        {
            msg += "안녕하세요.";
        }

        DateTime end = DateTime.Now;
        double exec = (end - start).TotalMilliseconds;
        Console.WriteLine(exec);
    }
}
```

- 실행 결과

```cs
96.0769
```

>문자열 변수를 더하기 연산자로 묶는 작업을 1만 번 수행했을 때 해당 컴퓨터에서는 70~100밀리초 정도가 소비되었다.

- StringBuilderPerformance.cs

```cs
using System;
using System.Text;

class StringBuilderPerformance
{
    static void Main()
    {
        DateTime start = DateTime.Now;

        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < 10000; i++)
        {
            sb.Append("안녕하세요.");
        }

        DateTime end = DateTime.Now;
        double exec = (end - start).TotalMilliseconds;
        Console.WriteLine(exec);
    }
}
```

- 실행 결과

```cs
7.9214
```

>String 변수로 묶는 작업과 달리 StringBuilder를 사용했을 때는 10밀리초 이내 정도로 아주 빠르게 실행한다. 이처럼 많은 양의 문자열을 반복해서 묶는 작업이 필요할 때는 StringBuilder 클래스를 사용하면 효율적이다. 

- Note

>숫자 형식의 문자를 +, - 기호를 붙여 표현할 때는 ToString() 또는 String.Format() 메서드에 서식을 주어 표현할 수 있다.

```cs
> 10.ToString("+#;-#0") // 10 -> +10, -10 -> -10, 0 -> 0
"+10"
> 
> string.Format("{0:+#;-#;0}", -10)
"-10"
> 
> $"{10:+#;-#;0}"
"+10"
```

>ToString()과 string.Format() 메서드, 문자열 보간법 등에는 +#,-#;0 형식을 사용하여 숫자에 +, - 기호를 붙인다.

