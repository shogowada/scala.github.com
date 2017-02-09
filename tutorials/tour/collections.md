---
layout: tutorial
title: Collections

disqus: true

tutorial: scala-tour
num: 3
next-page: basics
previous-page: unified-types
---

## Lists

Lists preserve order and allow duplication.

```
val numbers = List(1, 2, 3, 2)
println(numbers.mkString(", ")) // 1, 2, 3, 2
println(numbers(1)) // 2
```

`mkString` is a predefined function which joins elements with a given string.

## Arrays

Arrays preserve order and allow duplication. Arrays also allow mutation of elements.

```
val numbers = Array(1, 2, 3)
numbers(1) = 4
println(numbers.mkString(", ")) // 1, 4, 3
println(numbers(1)) // 4
```

## Sets

Sets do not preserve order and do not allow duplication.

```
val numbers = Set(1, 2, 3, 2)
println(numbers.mkString(", ")) // 1, 2, 3
```

## Maps

Maps hold key-value pairs. Maps do not preserve order and do not allow duplication of keys.

```
val numbersByString = Map(
	"A" -> 1,
	"B" -> 2,
	"C" -> 3
)
println(numbersByString.mkString(", ")) // A -> 1, B -> 2, C -> 3
println(numbersByString("B")) // 2
```

## Tuples

```
val hostAndPort = ("localhost", 80)
println(hostAndPort) // (localhost,80)
```

## Options
