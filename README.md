# Type Hints

Éttore Leandro Tognoli - ettore.leandro.tognoli@gmail.com

---

# Éttore Leandro Tognoli

## Formação

Bacharelado em Ciência da Computação - UNIVEM

Mestrado em Ciência da Computação - UFSCar

## Experiência

Programador/Desenvolvedor em algumas empresas em Marília

Consultor e Freelancer

Pesquisador CIAg \*

Prof. Fatec \*

---

# Minha Opinião

Não estou aqui representando o CIAg ou a FATEC

---

# Bibliografia

Clean Architecture - Robert C Martin

Clean Code - Robert C Martin

Clean Coder - Robert C Martin ( Uncle Bob )

Design Patterns - GoF

Domain Drive Design - Eric Evans

SCRUM A Arte de Fazer o Dobro do Trabalho na Metade do Tempo - Jeff
Sutherland & J.J. Sutherland

A Startup Enxuta - Eric Ries

---

# Publico alvo

O importante é estar funcionando!? =(

Algo que não está funcionando posso fazer funcionar, já algo que não consigo alterar não vai me atender para sempre.

---

# Motivação

Startups Pivotam, logo são necessárias metodolias ageis

- Refatoração Continua ( Tipagem facilita muito refatorações )
- Legibilidade (Tipagem contribui com a expressividade do código )

---

# Sobre o Tema

"I found TypeScript is actually incredibly useful, so we're adding a similar idea to Python, we're adding it in a slightly different way because we have different context," he said.

"...the TypeScript behavior he was talking about was optional type checking..."

Guido van Rossum 16/04/2019

https://www.techrepublic.com/article/the-creator-of-python-on-how-the-programming-language-is-learning-from-typescript/

---

# Tipagem

Linguagens compiladas geralmente utilizam tipagem estatica e linguagens interpretadas geralmente utilizam tipagem dinamica.

## C/C++

```c
int i = 1;
```

## Python

```
i = 1;
```

## TypeScript

```
const i : number = 1;
```

---

# Duck Typing

"If it walks like a duck and it quacks like a duck, then it must be a duck"

O tipo do objeto não importa, mas sim a existência de certas propriedades

Os exemplos a seguir consideram tudo que faz "quack" um "pato"

---

# Java

```java
interface Duck {
  void quack();
}

class DuckClient {
  void consumeDuck(Duck duck) {
    duck.quack();
  }
}

class RubberDuck implements Duck {
  @Override
  void quack() { /*...*/ }
}

class FakeDuck {
  void quack() { /*...*/ }
}
```

---

# Java =(

```java
DuckClient client = new DuckClient();
client.consumeDuck(new RubberDuck()); // ok
client.consumeDuck(new FakeDuck()); // error
```

---

# Python 2

```python
class Duck:
  def quack(self):
    raise NotImplementedError()


class DuckClient:
  def cosumeDuck(self, duck):
    duck.quack()

class RubberDuck(Duck):
  def quack(self):
    pass

class FakeDuck:
  def quack(self):
    pass
```

---

# Python 2 =)

```python
client = DuckClient()
client.consumeDuck(RubberDuck()) # ok
client.consumeDuck(FakeDuck()) # ok!
```

---

# TypeScript

```typescript
interface Duck {
  quack: () => void;
}

class DuckClient {
  public consumeDuck(duck: Duck) {
    duck.quack();
  }
}

class RubberDuck implements Duck {
  public quack() {
    /* ... */
  }
}

class FakeDuck {
  public quack() {
    /* ... */
  }
}
```

---

# TypeScript =)

```typescript
const client = new DuckClient();
client.quack(new RubberDuck()); // ok
client.quack(new FakeDuck()); // ok!
```

---

# PHP

```php
interface Duck {
  function quack();
}

class DuckClient {
  function consumeDuck( $duck ) {
    $duck->quack();
  }
}

class RubberDuck implements Duck {
  function quack() { /* ... */ }
}

class FakeDuck {
  function quack() { /* ... */ }
}
```

---

# PHP =)

```
$client = new DuckClient();
$client->consumeDuck(new RubberDuck()); // ok
$client->consumeDuck(new FakeDuck()); // ok
```

---

# TypeHint

---

# Python 3

```python
class Duck:
  def quack(self):
    raise NotImplementedError()


class DuckClient:
  def cosumeDuck(self, duck : Duck):
    duck.quack()

class RubberDuck(Duck):
  def quack(self):
    pass

class FakeDuck:
  def quack(self):
    pass
```

---

# Python 3 =)

```python
client = DuckClient()
client.consumeDuck(RubberDuck()) # ok
client.consumeDuck(FakeDuck()) # ok!
```

---

# PHP & Interfaces

Existe uma verificação em tempo de execução

- Custo em tempo de execução
- Tchau duck types

---

# PHP

```php
interface Duck {
  function quack();
}

class DuckClient {
  function consumeDuck(Duck $duck ) {
    $duck->quack();
  }
}

class RubberDuck implements Duck {
  function quack() { }
}

class FakeDuck {
  function quack() { }
}
```

---

# PHP =(

```
$client = new DuckClient();
$client->consumeDuck(new RubberDuck()); // ok
$client->consumeDuck(new FakeDuck()); // error =O
```

---

# ORMs

Ninguém gosta de alterar uma "tabela" e ter que alterar o código dos modelos depois das views e etc...

DRY - Don't Repeat Yourself

Geração de Bancos de Dados

Migração de Bancos de Dados

---

# JPA & Hibernate

```java
import javax.persistence.*;

@Entity
@Table(name = "EMPLOYEE")
public class Employee {
   @Id @GeneratedValue
   @Column(name = "id")
   private int id;

   @Column(name = "first_name")
   private String firstName;

   @Column(name = "last_name")
   private String lastName;

   @Column(name = "salary")
   private int salary;

   /** getters and setters **/
  
}
```
---

# DRY & Java

S2 Kotlin

---

# Doctrine

```php
/**
 * @Entity
 * @Table(name="products")
 **/
class Product
{
    /**
    * @Id
    * @Column(type="integer")
    * @GeneratedValue
    **/
    protected $id;
    /**
    * @Column(type="string")
    **/
    protected $name;
}
```
---

# ORM & Tipagem

A tipagem fornece meta dados importantes para os ORMs

Existem ORMs que não utilizam isso, Eloquent (Laravel)

---


# Meta Programação

Injeção de Dependencia

---

# Python Moderno

Python 3.7

- dataclasses

Pipenv

- lockfile
