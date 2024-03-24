# 简单工厂模式（静态工厂方法）
1. 内容：不直接向客户端暴露创建的实现细节，而是通过一个工厂类来负责创建产品类的实现
2. 角色：工厂角色、抽象产品角色、具体产品角色
3. 优点：隐藏了对象创建的实现细节；客户端不需要修改代码
4. 缺点：**违反了单一职责原则**，将创建逻辑集中到一个工厂类；当添加新产品时，需要修改工厂类代码，**违反了开闭原则**

## 类图
````mermaid
classDiagram
class Client
class Product
<<interface>> Product
Product : +do_something()
class ProductA
ProductA : +do_something()
class ProductB
ProductB : +do_something()
class SimpleFactory
SimpleFactory : +create_product() Product
ProductA ..|> Product
ProductB ..|> Product
SimpleFactory ..|> ProductA
SimpleFactory ..|> ProductB
Client ..|> Product
Client ..|> SimpleFactory
```