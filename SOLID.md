![SOLID](https://hsto.org/r/w1560/getpro/habr/upload_files/b7a/12d/e5d/b7a12de5dee75c93513da0799b013099.jpg)

## Definitions and Prerequisites
[Inheritance and Subtyping](https://stackoverflow.com/a/36266550)
[Coupling and Cohesion](https://www.geeksforgeeks.org/software-engineering-differences-between-coupling-and-cohesion/)

## General
* Как правило разработчикам приходится реализовывать новую функциональность, а не менять старую. Так давайте писать код так, чтобы новое было легко писать, а старое — тяжело сломать


## Single Responsibility
> Every module, class or function in a computer program should have responsibility over a single part of that program’s functionality, and it should encapsulate that part (a class should have only one reason to change)

Суть этого принципа заключается в том, что функционал класса должен быть целостным, обладать высокой логической связностью. Если у класса много ответвенности (много функций "из разных сфер"), то и меняться он будет очень часто. Таким образом, если класс имеет больше одной ответственности, то это ведет к хрупкости дизайна и ошибкам в неожиданных местах при изменениях кода. Любой сложный класс должен быть разбит на несколько простых составляющих, отвечающих за определенный аспект поведения.

Основные правила:
* Объединение ответственностей является общепринятой практикой и в этом нет ничего плохого, до тех пор пока это легко обслуживать. То есть не нужно фанатично дробить классы – это усложняет работу с проектом точно так же, как и НЕ применение этого принципа
* Если у вы делаете игру и у вас только летающие птицы, то, конечно же, не имеет смысла делать подобное дробление как в примере
* Если размер вашего класса начинает разбухать, то стоит подумать а не нужно ли разделить этот класс на несколько классов
* Класс решает задачи разных уровней абстракции (например разбирает json-объект и анализирует его содержимое) – явный признак, что это идет не по принципу
* Интерфейс класса слишком разнороден и содержит методы, отвечающие за слабосвязанные логически операции
* Класс или интерфейс содержит несколько методов со схожей семантикой, которые используются разными клиентами

> Try asking yourself: what does this class do? If there is a list of actions, you'll probably violate SRP

Reasons to change:
  * Changes in relationship between classes
  * Changes in system requirements

 Examples of responsibilities:
 - Persistence
 - Validation
 - Notification
 - Error Handling
 - Logging
 - Class Selection/Instantiation
 - Formatting
 - Parsing
 - Mapping

Examples: [god object, active directory and product validation](https://blog.byndyu.ru/2009/10/blog-post.html), [three ways to violate SRP (iOS)](https://habr.com/en/post/330142/)

#### Useful Links
https://blog.byndyu.ru/2009/10/blog-post.html
http://wiki.c2.com/?OpenClosedPrinciple
[Single Responsibility Principle. Не такой простой, как кажется](https://habr.com/en/post/454290/)

## Interface Segregation
Принцип разделения интерфейса (interface segregation principle) — производный принцип от первой буквы, S. Дело в том, что сформулировать "единую ответственность" в терминах интерфейса бывает сложно, а этот принцип нам однозначно говорит: если какая-то реализация не использует некоторые методы интерфейса, то эти методы в интерфейсе лишние. Здесь проще всего показать на примере: в Java вот есть интерфейс Collection с методами в духе add(), remove() и так далее. И в неизменяемых реализациях коллекций эти методы, ясное дело, не нужны. Поэтому, согласно принципу I, интерфейс стоит разделить на Collection и его наследника, MutableCollection (как сделано в Kotlin, например). Цель у этого всего опять-таки одна: чем меньше методов в интерфейсе, тем реже его придется менять (и тем меньше шанс что-нибудь сломать). Ну и дописывать новые интерфейсы проще, чем дописывать методы в существующие интерфейсы.

#### Useful Links

## Open-Closed
> Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification
* You should be able to extend a classes behavior, without modifying it (extend in this case doesn't necessarily mean that you should subclass the actual class that needs the new behavior)
* "If you will add a new function, create a new class extending an existing one, rather than changing it."

#### Useful Links


## Liskov Substitution
#### Useful Links
https://habr.com/en/post/521258/

## Dependency Inversion
#### Useful Links

## Addendum
SRP vs ISP [this](https://stackoverflow.com/questions/14388358/in-solid-what-is-the-distinction-between-srp-and-isp-single-responsibility-pr) and [this](https://stackoverflow.com/questions/8099010/is-interface-segregation-principle-only-a-substitue-for-single-responsibility-pr)
OCP vs LSP [this](https://softwareengineering.stackexchange.com/questions/178488/lsp-vs-ocp-liskov-substitution-vs-open-close) and [this](https://www.codeproject.com/Articles/587404/Understand-Single-Responsibility-and-Interface-Seg)

## References
[Простым языком + хорошие примеры](https://didemeren.medium.com/solid-principles-in-practice-a9771a746f6c)
[Серия статей о SOLID от Александра Бындю](https://blog.byndyu.ru/2009/10/solid.html)
[Хорошое пояснение на русском языке](https://ru.stackoverflow.com/a/900456)
[Practical Usage](https://www.quora.com/How-can-I-use-SOLID-principles-in-my-code)
[Uncle Bob defends SOLID](https://blog.cleancoder.com/uncle-bob/2020/10/18/Solid-Relevance.html)