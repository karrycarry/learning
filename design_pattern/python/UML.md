# 1. UML
UML图形一共有十种，分为静态模型图和动态模型图。其中静态模型图主要描述系统的静态结构，动态模型主要描述系统行为的各个方面
1. 静态模型图：类图、对象图、包图、组件图、部署图
2. 动态模型图：用例图、时序图、协作图、状态图、活动图

# 2. UML类图

## 2.1 泛化
1. 是一种继承关系，表示is-a的关系，是对象之间耦合度最大的一种关系，子类继承父类的所有细节。指向方（符号左）子类，被指向方（符号右）为父类。在UML类图中，泛化关系由带空心三角形的实线箭头表示。
2. 示例：
    ```mermaid
    classDiagram
    class MammalAnimal
    MammalAnimal: + feature()
    class Cat
    Cat: +feature()
    Cat: +catchingMouse()
    class Cattle
    Cattle: +feature()
    Cattle: +farmland()
    Cat --|> MammalAnimal
    Cattle --|> MammalAnimal
    ```

## 2.2 实现
1. 是一种类与接口的关系，表示类是接口所有特征和行为的实现。指向方（符号左）为实现类，被指向方（符号右）为接口类，实现关系由带空心三角形的虚线箭头表示。
2. 代码示例
    ```mermaid
    classDiagram
    class Flyable
    <<interface>> Flyable
    Flyable: +flying()
    class Bat
    Bat: +flying()
    Bat ..|> Flyable
    ```

## 2.3 依赖
1. 对象之间最弱的一种关联方式，是临时性的关联。代码中一般指由局部变量、函数参数、返回值建立的对于其他对象的调用关系。一个类调用被依赖类中的某些方法得以完成这个类的一些职责，即一个类的实现需要另一个类的协助。依赖关系由带箭头的虚线表示。
2. 代码示例
    ```mermaid
    classDiagram
    class Animal
    class Food
    Animal ..> Food
    ```

## 2.4 关联
1. 对象之间一种引用关系，它使一个类知道另一个类的属性和方法。这种关系通常使用类的属性表达。在类图中有带箭头的实现表示。关联可以是双向的，也可以是单向的。如：一本书可以有多个读者，一个读者也可能会有多本书，书和读者是一种双向的关系（也就是多对多的关系）
2. 示例
    ```mermaid
    classDiagram
    class Reader
    class Book
    class Author
    Reader -- Book
    Book --> Author

    ```

## 2.5 聚合
1. 表示has-a的关系，是一种不稳定的包含关系。较强于一般的关联，由整体与局部的关系，并且没有了整体，局部也可单独存在。在类图使用空心的菱形表示，菱形从局部指向整体。
2. 示例
    ```mermaid
    classDiagram
    class Company
    class Employee
    Employee --o Company
    ```

## 2.6 组合
1. 表示contains-a，是一种强烈的包含关系，组合类负责被组合类的生命周期，是一种更强的聚合关系。部分不能脱离整体存在。在类图中使用实心的菱形表示，菱形从局部执行整体。
2. 示例
    ```mermaid
    classDiagram
    class Computer
    class CPU
    class Mainbord
    class HardDisk
    class MemeryCard
    CPU --* Computer
    Mainbord --* Computer
    HardDisk --* Computer
    MemeryCard --* Computer
    ```

