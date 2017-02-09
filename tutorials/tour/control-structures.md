---
layout: tutorial
title: Control Structures

disqus: true

tutorial: scala-tour
num: 3
next-page: unified-types
previous-page: basics
---

## If Expressions

```
val LegalAge = 21
val myAge = 22
if (myAge >= LegalAge) {
  println("I am legal.")
} else {
  println("I am illegal.")
}
// I am legal.
```

You can use them as expressions too.

```
val LegalAge = 21
val myAge = 22
val message = if (myAge >= LegalAge) {
  "I am legal."
} else {
  "I am illegal."
}
println(message) // I am legal.
```

## Match Expressions

```
val name = "John"
name match {
  case "John" => "Mr. John"
  case "Amy" => "Ms. Amy"
  case _ => "whoever you are"
}
```

## For Expressions

```
for (index <- ) {
}
```

## Try Expressions

## While Loop

## Do While Loop
