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

