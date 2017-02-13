---
layout: tutorial
title: Control Structures

disqus: true

tutorial: scala-tour
num: 3
next-page: unified-types
previous-page: basics
---

You can use control structures to perform different actions based on conditions.

## If Expressions

`if` expressions perform actions if given conditions are met.

```
val x = 1
if (x == 1) {
  println("x is 1")
}
// x is 1
```

You can combine `if` and `else` to execute other actions in case given conditions are not met.

```
val x = 1
if (x == 1) {
  println("x is 1")
} else {
  println("x is not 1")
}
// x is 1
```

You can chain them as many as you want.

```
val x = 1
if (x == 1) {
  println("x is 1")
} else if (x == 2) {
  println("x is 2")
} else if (x == 3) {
  println("x is 3")
} else {
  println("x is not 1 or 2 or 3")
}
// x is 1
```

You can also use them as expressions.

```
val x = 1
val message = if (x == 1) {
  "x is 1"
} else {
  "x is not 1"
}
println(message) // x is 1
```

If expressions are trivial, you may omit `{}`.

```
val x = 1
val message = if (x == 1) "x is 1" else "x is not 1"
println(message) // x is 1
```

## Match Expressions

`match` expressions can do everything `if` expressions can do, but `match` expressions support much more complex control structures.

You can match on values.

```
val x = 1
val message = x match {
  case 1 => "x is 1"
  case 2 => "x is 2"
  case _ => "x is not 1 or 2" // In Scala, "_" means "I don't care."
}
println(message) // x is 1
```

You can match with guards.

```
val x = 1
val message = x match {
  case _ if x == 1 => "x is 1"
  case _ if x == 2 => "x is 2"
  case _ => "x is not 1 or 2"
}
println(message) // x is 1
```

You can match on types.

```
val x: Any = 1
val message = x match {
  case _: Int => "x is a value of Int type"
  case _: Double => "x is a value of Double type"
  case _ => "I don't know what x is"
}
println(message) // x is a value of Int type
```

You can match on case classes.

```
case class Car(maker: String, year: Int)

val ford2010 = Car("Ford", 2010)
val message = ford2010 match {
  case Car("Ford", _) => "The car is made by Ford"
  case _ => "I don't know who made this car"
}
println(message) // The car is made by Ford
```

## For Expressions

```
for (index <- 1 to 3) {
  println(index)
}
```

## Try Expressions

```
try {
} catch {
  case 
}
```

## While Loop

```
while () {
}
```

## Do While Loop

```
do {
} while ()
```
