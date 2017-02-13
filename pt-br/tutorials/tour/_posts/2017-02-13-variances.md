---
layout: tutorial
title: Variâncias

disqus: true

tutorial: scala-tour
categories: tour
num: 18
tutorial-next: upper-type-bounds
tutorial-previous: generic-classes
language: pt-br
---

Scala suporta anotações de variância de parâmetros de tipo de [classes genéricas](generic-classes.html). Em contraste com o Java 5, as anotações de variância podem ser adicionadas quando uma abstração de classe é definida, enquanto que em Java 5, as anotações de variância são fornecidas por clientes quando uma abstração de classe é usada.

Na página sobre [classes genéricas](generic-classes.html) foi dado um exemplo de uma pilha de estado mutável. Explicamos que o tipo definido pela classe `Stack [T]` está sujeito a subtipos invariantes em relação ao parâmetro de tipo. Isso pode restringir a reutilização da abstração de classe. Derivamos agora uma implementação funcional (isto é, imutável) para pilhas que não tem esta restrição. Por favor, note que este é um exemplo avançado que combina o uso de [métodos polimórficos](polymorphic-methods.html), [limites de tipo inferiores](lower-type-bounds.html) e anotações de parâmetros de tipos covariantes em um estilo não trivial. Além disso, fazemos uso de [classes internas](inner-classes.html) para encadear os elementos da pilha sem links explícitos.

```tut
class Stack[+A] {
  def push[B >: A](elem: B): Stack[B] = new Stack[B] {
    override def top: B = elem
    override def pop: Stack[B] = Stack.this
    override def toString() = elem.toString() + " " +
                              Stack.this.toString()
  }
  def top: A = sys.error("no element on stack")
  def pop: Stack[A] = sys.error("no element on stack")
  override def toString() = ""
}

object VariancesTest extends App {
  var s: Stack[Any] = new Stack().push("hello");
  s = s.push(new Object())
  s = s.push(7)
  println(s)
}
```

A anotação `+T` declara o tipo `T` para ser usado somente em posições covariantes. Da mesma forma, `-T` declara que `T` pode ser usado somente em posições contravariantes. Para os parâmetros de tipo covariante obtemos uma relação de sub-tipo covariante em relação ao parâmetro de tipo. Em nosso exemplo, isso significa que `Stack [T]` é um subtipo de `Stack [S]` se `T` for um subtipo de `S`. O oposto é válido para parâmetros de tipo que são marcados com um `-`.

No exemplo da pilha teríamos que usar o parâmetro de tipo covariante `T` em uma posição contravariante para podermos definir o método `push`. Uma vez que queremos sub-tipagem covariante para pilhas, usamos um truque e abstraímos o tipo de parâmetro do método `push`. Então temos um método polimórfico no qual usamos o tipo de elemento `T` como um limite inferior da variável de tipo da função `push`. Isso faz com que a variância de `T` fique em acordo com sua declaração, como um parâmetro de tipo covariante. Agora as pilhas são covariantes, mas a nossa solução permite que, por exemplo, seja possível inserir uma string em uma pilha de inteiros. O resultado será uma pilha do tipo `Stack [Any]`; Assim detectamos o error somente se o resultado for usado em um contexto onde esperamos uma pilha de números inteiros. Caso contrário, nós apenas criamos uma pilha com um tipo de elemento mais abrangente.