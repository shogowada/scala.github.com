---
layout: tutorial
title: Limitante Superior de Tipos

disqus: true

tutorial: scala-tour
categories: tour
num: 19
tutorial-next: lower-type-bounds
tutorial-previous: variances
language: pt-br
---

Em Scala, [parâmetros de tipos](generic-classes.html) e [tipos abstratos](abstract-types.html) podem ser restringidos por um limitante de tipo. Tal limitante de tipo limita os valores concretos de uma variável de tipo e possivelmente revela mais informações sobre os membros de determinados tipos. Um _limitante superiror de tipos_ `T <: A` declare que a variável tipo `T` refere-se a um subtipo do tipo `A`.
Aqui um exemplo que demonstra um limitante superior de tipo para um parâmetro de tipo da classe `Cage`:

```tut
abstract class Animal {
 def name: String
}

abstract class Pet extends Animal {}

class Gato extends Pet {
  override def name: String = "Gato"
}

class Cachorro extends Pet {
  override def name: String = "Cachorro"
}

class Leao extends Animal {
  override def name: String = "Leao"
}

class Jaula[P <: Pet](p: P) {
  def pet: P = p
}

object Main extends App {
  var jaulaCachorro = new Jaula[Cachorro](new Cachorro)
  var jaulaGato = new Jaula[Gato](new Gato)
  /* Não é possível colocar Leao em Jaula pois Leao não estende Pet. */
//  var jaulaLeao = new Jaula[Leao](new Leao)
}
```

Um instância da classe `Jaula` pode conter um animal, porém com um limite superior do tipo `Pet`. Um animal to tipo `Leao` não é um pet, pois não estende `Pet`, então não pode ser colocado em uma Jaula.

O uso de limitantes inferiores de tipo é discutido [aqui](lower-type-bounds.html). 
