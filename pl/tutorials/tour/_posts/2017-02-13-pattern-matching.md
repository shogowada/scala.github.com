---
layout: tutorial
title: Dopasowanie wzorców (Pattern matching)

disqus: true

tutorial: scala-tour
categories: tour
num: 11
language: pl
tutorial-next: singleton-objects
tutorial-previous: case-classes
---

Scala posiada wbudowany mechanizm dopasowania wzorców. Umożliwia on dopasowanie dowolnego rodzaju danych, na podstawie zasady że zwracamy zawsze pierwsze dopasowanie. Przykład dopasowania liczby całkowitej:

```tut
object MatchTest1 extends App {
  def matchTest(x: Int): String = x match {
    case 1 => "one"
    case 2 => "two"
    case _ => "many"
  }
  println(matchTest(3))
}
```

Blok kodu z wyrażeniami `case` definiuje funkcję, która przekształca liczby całkowite na łańcuchy znaków. Słowo kluczowe `match` pozwala w wygodny sposób zastosować dopasowanie wzorca do obiektu.

Wzorce można także dopasowywać do różnych typów wartości:

```tut
object MatchTest2 extends App {
  def matchTest(x: Any): Any = x match {
    case 1 => "one"
    case "two" => 2
    case y: Int => "scala.Int"
  }
  println(matchTest("two"))
}
```

Pierwszy przypadek jest dopasowany, gdy `x` jest liczbą całkowitą równą `1`. Drugi określa przypadek, gdy `x` jest równe łańcuchowi znaków `"two"`. Ostatecznie mamy wzorzec dopasowania typu. Jest on spełniony gdy `x` jest dowolną liczbą całkowitą oraz gwarantuje, że `y` jest (statycznie) typu liczby całkowitej.

Dopasowanie wzorca w Scali jest najbardziej użyteczne z wykorzystaniem typów algebraicznych modelowanych przez [klasy przypadków](case-classes.html).
Scala także pozwala też na używanie wzorców niezależnie od klas przypadków, używając metody `unapply` definiowanej przez [obiekty ekstraktorów](extractor-objects.html).
