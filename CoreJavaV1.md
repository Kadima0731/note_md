# Java核心技术1

- [基础程序设计结构](#%e5%9f%ba%e7%a1%80%e7%a8%8b%e5%ba%8f%e8%ae%be%e8%ae%a1%e7%bb%93%e6%9e%84)
  - [基础数据类型](#%e5%9f%ba%e7%a1%80%e6%95%b0%e6%8d%ae%e7%b1%bb%e5%9e%8b)
  - [变量](#%e5%8f%98%e9%87%8f)
  - [运算符](#%e8%bf%90%e7%ae%97%e7%ac%a6)
  - [字符串](#%e5%ad%97%e7%ac%a6%e4%b8%b2)
  - [输入输出](#%e8%be%93%e5%85%a5%e8%be%93%e5%87%ba)
  - [大数值](#%e5%a4%a7%e6%95%b0%e5%80%bc)
  - [数组](#%e6%95%b0%e7%bb%84)
- [对象与类](#%e5%af%b9%e8%b1%a1%e4%b8%8e%e7%b1%bb)
  - [使用预定义类](#%e4%bd%bf%e7%94%a8%e9%a2%84%e5%ae%9a%e4%b9%89%e7%b1%bb)
  - [用户自定义类](#%e7%94%a8%e6%88%b7%e8%87%aa%e5%ae%9a%e4%b9%89%e7%b1%bb)
  - [静态域和静态方法](#%e9%9d%99%e6%80%81%e5%9f%9f%e5%92%8c%e9%9d%99%e6%80%81%e6%96%b9%e6%b3%95)
  - [方法参数](#%e6%96%b9%e6%b3%95%e5%8f%82%e6%95%b0)
  - [对象构造](#%e5%af%b9%e8%b1%a1%e6%9e%84%e9%80%a0)
  - [包](#%e5%8c%85)
  - [类路径](#%e7%b1%bb%e8%b7%af%e5%be%84)
  - [文档注释](#%e6%96%87%e6%a1%a3%e6%b3%a8%e9%87%8a)
  - [类设计技巧](#%e7%b1%bb%e8%ae%be%e8%ae%a1%e6%8a%80%e5%b7%a7)
- [继承](#%e7%bb%a7%e6%89%bf)
  - [类,超类和子类](#%e7%b1%bb%e8%b6%85%e7%b1%bb%e5%92%8c%e5%ad%90%e7%b1%bb)
  - [受保护的访问](#%e5%8f%97%e4%bf%9d%e6%8a%a4%e7%9a%84%e8%ae%bf%e9%97%ae)
  - [Object及其方法](#object%e5%8f%8a%e5%85%b6%e6%96%b9%e6%b3%95)
  - [ArrayList](#arraylist)
  - [参数可变的方法](#%e5%8f%82%e6%95%b0%e5%8f%af%e5%8f%98%e7%9a%84%e6%96%b9%e6%b3%95)
  - [枚举类](#%e6%9e%9a%e4%b8%be%e7%b1%bb)
  - [反射](#%e5%8f%8d%e5%b0%84)
  - [继承的设计技巧](#%e7%bb%a7%e6%89%bf%e7%9a%84%e8%ae%be%e8%ae%a1%e6%8a%80%e5%b7%a7)
- [接口, lambda表达式和内部类](#%e6%8e%a5%e5%8f%a3-lambda%e8%a1%a8%e8%be%be%e5%bc%8f%e5%92%8c%e5%86%85%e9%83%a8%e7%b1%bb)
  - [接口](#%e6%8e%a5%e5%8f%a3)
  - [lambda表达式](#lambda%e8%a1%a8%e8%be%be%e5%bc%8f)
  - [内部类](#%e5%86%85%e9%83%a8%e7%b1%bb)
  - [代理](#%e4%bb%a3%e7%90%86)
- [泛型程序设计](#%e6%b3%9b%e5%9e%8b%e7%a8%8b%e5%ba%8f%e8%ae%be%e8%ae%a1)
- [集合](#%e9%9b%86%e5%90%88)
  - [Java集合框架](#java%e9%9b%86%e5%90%88%e6%a1%86%e6%9e%b6)
  - [具体的集合类](#%e5%85%b7%e4%bd%93%e7%9a%84%e9%9b%86%e5%90%88%e7%b1%bb)
  - [具体的映射类](#%e5%85%b7%e4%bd%93%e7%9a%84%e6%98%a0%e5%b0%84%e7%b1%bb)
  - [视图与包装器](#%e8%a7%86%e5%9b%be%e4%b8%8e%e5%8c%85%e8%a3%85%e5%99%a8)
  - [alg](#alg)
  - [其他集合](#%e5%85%b6%e4%bb%96%e9%9b%86%e5%90%88)

## [第一章 基础程序设计结构](javacore/v1_ch01.md)

## 对象与类

---
类是产生对象的模板, 是Java语言的基石. 类是对事物的抽象,  类包含实例域, 静态域, 方法等部分, 实例域是类的数据, 方法是操纵数据的手段. 对象是类的实例. 实现封装的关键是不能让类中的方法直接访问其他类中的实例域. 面向对象的程序设计是以数据而非过程为中心的设计方式, 经验上来说是一个找名词找动词的过程.

对象要素:

- 对象的行为
- 对象的状态
- 对象标识

对象状态的改变必须调用对象的方法实现.

类之间的关系:

- 依赖关系(use-a)
- 包含关系(has-a)
- 继承关系(is-a)

### 使用预定义类

java中预定义了大量类可以用以创建对象, 对象是承载数据的实体, 对象变量不包含对象, 它只引用对象, 例如`LocalDate date`声明(创建)了一个对象变量但它不具有对象, 创建对象使用`new Class(params)`进行, 创建的对象可以直接用于方法, 也可以通过对象变量引用.  可以显式的将对象变量设置为`null`表示当前变量没有引用任何对象. **所有Java对象都存储在堆中.** 

对于对象操作的方法, 有的会改变对象的状态, 有的并不会改变,  例如`String`类对象的`subString()`方法, 返回的是一个新构建的对象, 而不会改变对象本身, 这种称为*访问器方法*; 有的方法则需要修改对象的状态. 根据是否对对象的状态进行修改, 可以将方法分为更改器方法和访问器方法.

> 注意不要编写返回引用可变对象的访问器方法. 其他类可以调用该对象的方法直接修改了本类的实例域. 例如返回`Date`类的实例域对象.

### 用户自定义类

用户自定义类使用和类相同的名称命名源文件. 在一个源文件中, 只能有一个公有类, 和任意数目的公有类. 对于多源文件的工程, 可以使用`javac file1.java file2.java ..`编译, 也可以只显式的编译含有需要运行`main`方法的类,编译器能够自动的查找到依赖的对应的源文件, 相当于c++中的make工具.

**构造器**

- 构造器域类同名
- 每个类可以有一个以上的构造器
- 构造器可以有0到多个参数
- 构造器总是伴随着`new`操作一起调用.

类方法的参数具有两个部分, 对象会作为隐式参数传入, 可以用`this`调用, 其他参数会通过函数的形参传入.
Java中所有方法都在类内定义, 是否内联由编译器决定.
类方法能够访问同类的任何一个对象的私有域. `public`修饰的方法可以被任何类访问, `private`修饰的方法仅可在类内访问. 类具有相似的访问权限, 不带修饰的类, 可以被同一个包的其他类访问.

**final实例域** 类中用`final`修饰的实例域在定义时进行初始化, 此后不能修改值. final修饰符大多应该应用于基本类型域或不可变类的域.(类中的方法都不能改变其对象, 如String)`final`仅限制了该变量只能够引用该对象不能够再引用别的对象, 但外部依然可以调用该对象的方法修改对象的状态.

### 静态域和静态方法

**静态域** 声明了`static`的类域, 不属于任何对象, 能够通过类名进行访问, 在类第一次被加载时执行初始化.

**静态常量** 声明了`final`的静态域, 这类域在声明时就进行初始化, 此后不能在更改, 常见的`Math.pi`就属于这一类. 静态常量可以声明为`public`, 因为它们通常不能再被修改.

> System类中的out是公有静态常量, 但是有一个`setOut`方法, 可以修改out为不同的流, 这个方法是一个本地方法不是用java语言实现.

**静态方法** 声明了`static`的方法, 这类方法不带有隐式参数, 可以通过类名或类的对象(不推荐)调用, 不需要创建对象就可以使用.

用静态方法的情况:

- 需要访问类的静态域
- 不需要访问对象的状态, 其所需要参数都通过显式参数提供.

**工厂方法** 工厂方法是一类用于产生对象的静态方法, 不用构造器而用工厂方法构造对象的原因是

1. 无法命名构造器. 构造器名只有一个, 但希望得到的实例使用不同的类名
2. 使用构造器时, 无法改变所构造的对象类型. 例如需要返回子类对象

**main方法** main方法是一种静态方法, 是程序的入口, 每个类可以有一个main方法, 也可以没有, 主力类源文件中通常使用main方法进行一些单元测试等.

### 方法参数

Java中的参数传递仅有值传递形式, 而不具有C++中的引用传递方式. 直观上理解, 形参创建了同类型的变量后, 引用了域实参相同的对象, 可以通过形参调用对象的方法改变该对象的状态, 但是不能够通过改变形参引用的对象来修改外部实参指向的对象. 即C++中常用的`swap(type &a, type &b)`在java中是无法实现的, 可以通过包装类的方式或其他方式进行交换.[参考资料](https://blog.csdn.net/bntx2jsqfehy7/article/details/83508006)

<img src="pictures/CoreJavaV1/ch4_1.jpg" width=60%>

方法中的参数使用情况总结:

- 一个方法不能修改一个基本数据类型的参数
- 一个方法可以改变一个对象参数的状态
- 一个方法不能让独享参数引用一个新的对象

### 对象构造

**重载** 多个方法, 具有相同的方法名和不同的参数列表称为重载.

**默认域初始化** 如果一个域在创建时没有赋值, 编译器会对他进行默认初始化, 数值型变量为0, 布尔变量为false, 其他变量为null.

**默认构造器**  如果一个类没有构造器, 编译器会给它创建一个无参数的构造器, 构造器将所有实例设置为默认值. (如果域声明显式赋值, 则按赋值) 但是对于至少具有一个构造器的方法, 编译器不再创建默认构造器, 此时如果需要, 需要自己定义不带参数的构造器.

**显式域初始化** 显式初始化包括两种方法, 一种是在声明时对域赋值, 初始值不一定是常量, 也可以调用方法对域进行初始化; 另一种是在构造器中对域进行赋值. 显式初始化是一种良好的程序设计.

**初始化块** 除了直接对域赋值, 也可以直接在类内添加`{ }`包围起的代码块称为初始化块, 在每次创建对象时, 该部分都会被首先调用. 同时 ,可以在块前声明`static`构建静态初始化块, 可以用于对静态域进行更加复杂的初始化操作, 该块在该类第一次被加载时被调用.

**调用另一个构造器**  可以在一个构造器的第一行使用`this(params)`调用另一个构造器, 其作用和C++中的初始列表中调用其他构造器的作用一致, 但是相比C++, java的类中不包含对象, 只包含对象指针, 因此不存在C++中构造前必须先调初始化列表的尴尬问题.

调用构造器步骤:

- 所有实例域初始化为0, false或null
- 按照在类声明中出现的顺序,依次执行所有域的初始化语句和初始化块
- 如果构造器的第一个行调用了第二个构造器, 执行第二个构造器的主体
- 执行构造器的主体

**finalize方法** 申明了finalize的方法会在对象被析构时调用, 但是不能够以来该方法,因为不能够确定对象何时被析构.

### 包

**类的导入** 一个类可以使用所属包内的所有类和其他包中的公有类. 可以使用包的全名访问其他包公有类 , 也可以使用`import`导入类.

- 可以通过`*`一次导入一个包, 但是不能一条语句同时导入一个包下的多个包.
- 引入的两个包中有同名的类, 为了确定使用的是哪个包中的这个类, 可以单独声明一下导入这个类.
- 如果两个类都要使用, 需要指明包名.

与类相似的, 类的静态方法和静态域也可以通过`import`导入.

为了将自己的类放入包中, 可以在源文件的第一行使用`package com.corejava.ch04;`的方法申明所在包名, 源文件的位置需要放在与包名一致的树状目录的基目录, 这里就是`/com/corejava/ch04/`, 而进行编译和虚拟机调用类时, 都应该在根目录进行. 如果没有在源文件中放置package语句, 源文件会被放入一个无名的默认包. 如果源文件不在对应的子目录下, 若其没有外部依赖可以正常编译, 但虚拟机找不到类, 不能正常运行.

**包作用域** 正如之前所说, 一个没有用访问权限修饰符修饰的类可以被所在包的所有方法使用

### 类路径

类路径即`CLASSPATH`, 是编译器和虚拟机查找类的依据, 类路径中所列出的目录和归档文件是搜索类的起点, 当没有指定类所在的包时, 编译器在类路径列出的位置开始搜索依赖的类, 若找到一个以上的类则会报错. 若自己通过`java -cp`设置类路径时, 如果没有设置当前路径, 虚拟机也不会在当前路径查看类. 类路径中放置的应当是包的根目录和jar包所在位置和当前位置.

### 文档注释

### 类设计技巧

- 数据必须私有化: 数据私有化是OOP的基础, 能够有效保护数据
- 数据都需要合适的初始化: 不要依赖默认初始化, 最好能够显式的进行初始化
- 尽量不要在类中使用过多的基本数据类型: 当存在过多的基本数据类型时, 应当用其他类代替, 进行进一步的抽象
- 不是所有域都需要独立的访问器和修改器
- 拆分职责过多的类
- 类名应和方法名应域它的职责一致
- 优先使用不可变类: 多线程友好

## 继承

---
### 类,超类和子类

超类, 子类和类的关系, 超类是类的父类, 类是子类的父类, 三者是继承关系, 可以通过`extends superClass`继承超类. java中的继承机制是单继承. 继承可以获得父类的域和方法, 但是类并不能够直接访问父类的私有域, 要借用父类的私有域的访问器方法和修改器方法对这部分域进行使用. 


继承后可以对父类的方法进行覆盖, 覆盖要求两者方法的签名完全一样, 此时依然可以通过`super.method`调用父类的方法.

`super`除了在父类方法调用中会被使用, 还可以在构造器中通过`super(parms)`调用父类的构造器, 和this一样要求在第一行. 如果没有显式的调用父类构造器, 则将会自动调用父类的默认构造器.

> super 和c++中的this概念不同, 它不是对象的引用, 不能够赋给另一个对象变量.`super.getSalary`相当于c++中的`Employee::getSalary`.

在实现继承时, 覆盖方法时, 签名必须完全相同, 但是返回类型可以是原方法返回类的子类.

可以使用`@override`标记重写的方法, 要求编译器进行类型检查.

**多态**: 超类变量可以引用超类, 也可以引用超类的子类, 它们对于超类变量来说是等价的, 但是在真正调用对象的方法时, 会根据对象的实际类型, 调用该类的方法(即可能是覆盖了超类的方法), 一个对象变量可以指向多种实际类型的象的现象称为*多态*.

**动态绑定:** 虚拟机在运行过程中能自动的选择调用哪个方法的现象

**静态绑定:** static方法, private方法, final方法和构造器在编译时就能够确定其调用的方法的现象.

继承层次: 由一个公共类派生出的所有类的集合成为继承的层次.

**方法调用的过程**
- 确定对象的声明类型和方法名, 列出当前类中该命名的方法和超类中声明为`public`的该名称方法.
- 检查调用方法时提供的参数类型, 如果有一个与提供的类型完全匹配就选择. 这称为*重载解析*.如果可以找到多个或找不到都会报错
- 如果方法是静态绑定的, 那就直接确定了.
- 如果方法是动态绑定的, 那么虚拟机会调用与变量所引用的类型最匹配的类的方法. 虚拟机用方法表记录每个类型的方法


**阻止继承**: 声明了`final`的类不能够被继承, 声明了`final`的方法在被继承时不可以被覆盖, 子类依然可以调用被`final`修饰的方法. 如果把一个类设为final, 类方法自动变为`final`而不包括域.

**强制转换**: 强制转换的前提是可以转换, 例如当对象本来是`class1`, 处理过程中将其转化成`Object`, 可以通过`(class1)`对其进行强制类型转换. 不能够将`Object`对象直接转化为子类对象.这一问题在数组操作中存在, 下面举一例.

> 进行类型转换的唯一原因是在忽略对象的实际类型之后, 使用对象的全部功能. 强制转换只能在继承层次间进行, 将超类转换成子类之前需要用`isInstanceOf`关键字进行检查.

```java
Employee[] es = new Manager[5];
es[0] = new Employee(); // 会报错, 数组会记录自己的实际类型, 并监督放入的引用都是可兼容的类型. 
//这样的操作缺少了Manager的实例域.
```

**抽象类**: 方法可以在访问表示符后通过申明`abstract`变为一个抽象方法, 含有一个以上抽象方法的类, 称为抽象类, 类也可以直接声明为抽象类, 抽象方法不需要实现, 抽象类不能够实例化, 但是可以声明这个类型的变量. 

- 抽象类是代码抽象的重要机制, 子类中的公共方法应当在抽象类中实现, 抽象类不应该实现方法的思想是错误的.
- 扩展抽象类的两种方法, 实现全部抽象方法, 子类就不是抽象的; 实现部分抽象方法, 子类也是抽象的.
- 类即使不含抽象方法, 也可以将类声明为抽象类.

### 受保护的访问

访问控制符声明为`protect`的成员可以被同一包或者子类访问, 默认访问控制符的成员可以被同一个包访问.

更详细的说, protected的规则如下:
- 包内可见,并对子类可见.
- 若子类和父类不在同一个包, 子类中子类实例可以访问从父类继承来的protected方法, 而不能访问父类实例的protected方法

> 引申: 若和父类不在同一个包中, 子类不能访问其他子类的父类protected方法. 也就是p227说的, 子类只能调用受保护的clone方法来克隆自己的对象的由来. 

举例:
```java
//Duck1.java
package playground;

public class Duck1 {
    public static void main(String[] args) {
        Duck1 d = new Duck1();
        d.testSelfClone();
        d.testOtherSubclassClone();
        d.testOtherSubclassWithPublicClone();
    }
    public void testSelfClone() {
        clone(); // 可以, 从父类继承来的
    }
    public void testOtherSubclassClone() {
        Duck2  d2 = new Duck2();
        d2.clone(); // 是要报错的, 不能在子类中调用其他子类的父类protected方法.
    }
    public void testOtherSubclassWithPublicClone() {
        Duck3 d3 = new Duck3();
        d3.clone(); // 可以, 该类开放了public
    }
}

//Duck2.java
package playground;

public class Duck2 { }

//Duck3.java
package playground;

public class Duck3 {
    public Duck3 clone() throws CloneNotSupportedException {
        return (Duck3) super.clone();
    }
}
```

但是如果子类和父类在同一个包中, 事情又不一样了. 因为在同一个包中, 父类的protected方法是可见的.因此, 子类可以访问别的子类的父类protected方法.
```java
//Bird.java
package playground;

public class Bird {
    protected void pFunc() {
        System.out.println("IN Bird.pFunc.");
    }
}
//Duck1.java
package playground;

public class Duck1 extends Bird{
    public static void main(String[] args) {
        Duck1 d = new Duck1();
        d.testSelfpFunc();
        d.testOtherSubclasspFunc();
        d.testOtherSubclassWithPublicpFunc();
    }
    public void testSelfpFunc() {
        pFunc(); // 可以, 从父类继承来的
    }
    public void testOtherSubclasspFunc() {
        Duck2  d2 = new Duck2();
        d2.pFunc(); // 可以, 因为在同一个包
    }
    public void testOtherSubclassWithPublicpFunc() {
        Duck3 d3 = new Duck3();
        d3.pFunc();
    }
}

//Duck2.java
package playground;
public class Duck2 extends Bird{ }
//Duck3.java
package playground;
public class Duck3 extends Bird { }
```


### Object及其方法

Object类是所有类的父类, 该类具有大量的方法能够供类使用, 其中有几种方法在实现时可能需要重载, 需要被重点记录.

> 只有基本类型不是Object的子类, 包括int, float, char, boolean. 所有数组类型不管是对象数组还是基本类型数组都扩展了Object类.

`equals`方法: 继承中该方法存在以下的问题: 如果子类能够拥有相等的概念, 则覆盖该方法时应该采用`getClass`方法; 如果由超类决定相等的概念, 那么就可以使用`instanceof`进行检测, 这样可以在不同的子类之间进行相等的比较.

具体的重写流程:
- 显式参数使用Object, 命名为otherObject, 稍后可能会进行转换
- 检测是否是同一对象
- 第一步判断null
- 第二步, 判断是否是同一类, 判断类时, 如果时前一种情况, 可以使用`isinstance`关键字进行判断; 如果是第二种情况, 应该用`.class`属性和`getClass()`判断.
- 如果前面的都相同, 对各个实例的对象域使用`equals`进行判断, 基本类型域用`==`进行判断. 数组类型可以使用`Arrays.equals`方法进行判断.

`hashCode`方法用于对该类实例进行hash时调用, 如果重写了`equals`就必须重写该方法, 保证`equals`相等的两个对象具有相同的`hashcode`. 编写`hashCode`方法时, 对于实例域的哈希可以调用它自己的`hashCode`, 更好的方法是使用`Object.hashCode`方法避免null引起的问题.

还有更好的办法, 可以调用`Object.hash`提供所有实例域作为参数, 该方法会调用各个实例域的`Object.hashCode`并将它们组合起来.

`toString`方法, 在调用print时会调用该对象的`toString`方法. 该方法的注意点是, 对于数组对象, 直接使用会输出奇奇怪怪的东西, 正确的方法是对Array对象使用`Arrays.toString`方法.

> 使用`equals`做比较时, 可能需要考虑对比的两个对象有null的情况, 这时应该使用`Object.equals`方法, 当两者均为null时, 返回`true`.

### ArrayList

**访问列表元素:** 使用`get`方法访问元素, `set`修改元素, `Add`添加元素. `set`只能修改已有的元素不能增加.

**构建列表:** 新的列表都应该使用泛型类型, 而不应该使用Object类型的.

ArrayList类中提供`ensureCapacity`方法, 如果使用`new ArrayList<>(100)`实例化一个对象的话, 该对象具有容纳100个元素的潜力, 但此时内部数组的大小还很小, 增加元素过程中需要重新申请内部数组然后复制过去. `ArrayList.ensureCapacity`方法则在一开始申请一个给定大小的内部数组, 在内部元素达到给定大小之前不用再重新申请空间. 两者的共同点是, 无论是初始化是给大小还是`ensureCapacity`方法给大小, `ArrayList`里在调用`Add`之前都是么有元素的. 


**ArrayList转换为Array:**
```java
X[] a = new X[list.size()];
list.toArray(a); // toArray方法要传入一个创建好的数组.
```
### 参数可变的方法

使用`Class...`作为方法的参数时, 能够接受变数量的参数, 其实相当于接受了一个`Class[]`的数组. 例如`main`可以写成`public static void main(String... args)`.

### 枚举类

在之前就看过, 枚举类型可以写成以下形式:
```java
public enum Size {SMALL, MEDIUM, LARGE, EXTRA_LARGE}; // 注意最后这个;
```
这样就可以定义一个`Size`类, 该类只具有4个实例, 新定义该类的变量时, 直接引用该类的对象, 而不能新建对象(事实上, `enum`类的构造器是`private`的).

所有的enum和class是相似的, 事实上`enum`类型的类都继承于`Enum`类, 该类定义了几个实用方法, 同时可以在上文的基础上对类进行修改.

`toString`方法: 该方法对`enum`对象转化为`String`对象, 默认是原对象名

`Enum.ValueOf(Class, String)`静态方法: 该方法是`toString`的逆方法, 从字符串返回对应的对象.

`values()`方法: 返回所有枚举对象.

可以对构造器进行重载, 也可以增加方法. 能够重载的方法只有`toString`方法.

```java
public enum Size {
  SMALL("small"), MEDIUM("medium"), LARGE("large"), EXTRA_LARGE("extra_large"); //注意这个分号不能少
  private String describe; 
  private Size(String s) {
    describe = s;
  }
  public String getDescribe() {
    return describe;
  }
}
```

### 反射

反射是java运行时分析的重要手段, 能够获得对象的类信息(包括类型, 方法, 域, 域值等).

反射的作用:
- 运行时分析类的能力
- 运行时查看对象, 例如编写适用于所有类型的函数
- 实现通用的数组操作代码.
- 适用Method类, 类似于函数指针

#### Class类

每个类本身是一个Class类, 该类维护了类的类名, 访问控制符, 域, 方法等实例域. 获得`Class`的方法有三种
- 对类直接取属性`Employee.class`
- 对对象获得其类型 `employee.getClass()`
- `Class.forName(String)` 在所有存储的类中查找类, 不论该类是否被该程序使用.

一个`Class`对象具有`getName`获得类名, `getModifiers`获得访问标识符, `getComponentType`获得元素类型(针对Array, 放在Class中有些奇怪)等方法.

`Class`对象具有的域都是`Field`类的实例, 可以通过`getField(String name)`--获得该名称的域, `getDeclaredFields()`--获得所有声明的域, `getFields()`--获得所有public的域

`Class`对象具有的方法都是`Method`类的实例, 和`Field`类似具有几个get方法, 但是需要注意, 因为同名的方法可能不止一个, 因此需要使用方法的签名作为参数, `getMethod(String name, Class<?>... Parameters)`.

>`forName`方法可能会引起已检查异常, 需要和`try`语句一起使用.
#### Field类

`Field`类的实例首先有名字, 可以通过`getName()`获得, 类可以通过`getType()`获得, 返回的是一个`Class`类对象,  重要的是, 现在得到的仅是类的一个域, 要获得这个域的值可以通过一系列get方法

- `get(Object obj) -> Object` 传入的是Class的实例,这个实例具有这个Field, 可以通过get得到
- `getInt(Object obj) -> int`
- `getDouble(Object obj) -> double`
- `getGenericType(Object obj) -> Type` 获得Field对应类型的对象.

但是直接获得, 只能够访问该类public的域, 为了访问到私有域需要首先设置`Accessible`. Field自己就具有`setAccessible(boolean)`, 其实也可以采用`AccessibleObject.setAccessible(Field[] array, boolean flag)`的方法批量的设置.

#### Method类

`Method`类中, 很多方法和之前大同小异, 而最关心的问题是,java中方法是否能够像c++中的函数指针一样被调用, `Method`中具有`invoke(Obj param1, Obj param2)`方法, 将参数传入可以得到返回Object的调用结果. 但是这种方式的运行速度较慢,并不主张使用.

### 继承的设计技巧

- 将公共的方法和域放在超类
- 不要使用受保护的域
- 使用继承实现`is-a`关系
- 除非所有方法都有意义否则不应使用继承
- 覆盖方法时不应改变其行为预期
- 占位
- 不要过多使用反射

## 接口, lambda表达式和内部类

---

### 接口

**概念:** 不是类, 而是对一种需求的描述, 提供了一种标准,供服务端和客户端进行协调.

**特性:**

- 所有方法都是`public`, 所有域都是`public static final`
- 不能有实例域
- 不能使用`new`创建对象
- 可以创建变量, 引用实现了接口的类的对象
- 可以使用`instanceof` 关键字判断一个对象是否实现了接口

Java8之后可以在接口中添加**静态方法**, 代替原本需要工具类来完成的工作, 静态方法在接口中起到实用工具的作用.

**默认方法**: 对方法申明`default`可以将方法声明为默认方法, 默认方法使得实现该接口的类只需要实现自己需要重写的方法, 而不用重写所有方法. 例如`Collection`接口中的`isEmpty()`方法就可以用默认方法实现.

默认方法产生冲突的情况:
- 继承的超类和实现的接口有相同签名的方法
- 实现的多个接口中有相同签名的默认方法

解决方法:
- 超类优先
- 多个接口的相同签名默认方法冲突时, 由实现类实现该方法来决定使用哪个默认方法. 多个接口的相同签名方法有至少一个声明成了默认方法, 就需要解决这种一致性的冲突.


**接口与抽象类对比:** 

- 抽象类可以实现普通方法, 抽象类可以有实例域, 接口不可以
- 抽象类是类, 接口不是
- 抽象类只能单继承, 接口可以实现多个, 达到多继承的目标
- 抽象类和接口都可以被其他抽象类/接口继承
- 抽象类和接口都可以用`instanceof`判断

接口能够避免多继承的复杂情况, 同时基本实现多继承的功能


### lambda表达式

lambda表达式的作用, 传递代码块, 一次或多次使用.

**语法:** lambda表达式的基本形式为`(Class param)->{sentence;}`, 需要注意的语法点包括:
- 不需要显式指定返回类型, 可以推导
- 当参数类型可以推导时, 也可以不指定参数类型, 例如`Comparator<String> com = (first, second)-> first.length() - second.length();`
- 当只有一句语句时, 花括号可以不用, 也不用加分号
- 小括号必须有, 即使没有参数时也需要有个空括号
- 返回类型可以为void, 在语句中没有返回值

**函数式接口**: 只有一个抽象方法的接口称为函数式接口, 例如`Comparator`, `ActionListener`都是函数式接口, 在需要函数式接口变量的参数位置, 可以使用lambda表达式进行替换. 注意只有一个抽象方法的接口与只有一个方法的接口不同, 只有一个方法的接口完全可以声明一个`Object`的方法. Java提供了很多有用的抽象函数接口可供使用, 例如断言等接口.

**方法引用**:方法引用可以将现成的方法转化为lambda表达式再转为函数式接口的实现类对象. 当希望用lambda表达式实现的动作已经有现成的方法实现时, 可以用方法引用代替.
```java
Timer t = new Timer(100, event->System.out.println(event)); // 可以用以下方法引用代替
Timer t = new Timer(100, System.out::println);
```
方法引用有以下几种形式:
- object::instanceMethod
- Class::staticMethod
- Class::instanceMethod

其中需要理解一下的是第三个, 当调用实例方法时, 第一个参数作为方法的对象, 即`(x, y)->x.instanceMethod(y)`

**构造器引用**: 构造器引用和方法引用类似, 只不过这里的方法名是`new`, 即 `Class::new`相当于`(x)->return new Class(x)`.

**lambda表达式中的变量作用域**: lambda可以引用外部的变量, 但是只能使用外部的不可变对象, 并且其作用域和外部是一致的, 即lambda表达式中用的变量不能和外部变量重名. lambda表达式转化的对象会隐式的保存引用的外部对象, 作用相当于**闭包**.

**编写函数接收lambda表达式**: 在需要接受lambda表达式的参数位置, 设置合适的函数式接口的变量就可以接受lambda表达式. Java提供了一系列实用函数式接口.

<img src="pictures/CoreJavaV1/ch6_1.jpg" width=80%>

**Comparator的实用静态方法:**

**comparing方法**

Comparator提供了一个更加实用的比较器构造器函数`Comparator.comparing`, 这个方法的参数可以是方法引用或lambda表达式, 用于获取对象的键. 例如:
```java
Arrays.sort(people, Comparator.comparing(Person::getName()));
// 按照名字对people中的person进行排序
```
**thenCompare方法**

该方法可以与`thenCompare`方法串联起来传入多个获取键的方法引用或lambda表达式, 当前者相等时,按照后面的键继续比较.
```java
Arrays.sort(people, Comparator.comparing(Person::getName()).thenCompare(Person.getAge()));
```

**Comparing, thenCompare方法变体**
- 为了避免自动装箱, 可以使用`ComparingInt`和`thenCompareInt`等变体
- 当获取键的方法可能获得null时, 需要指定这样的对象怎么排序, java提供了`Comparator.nullsFirst, Comparator.nullsLast`的适配器. 用法如下:
  ```java
  comparing(Person::getName(), Comparator.nullsFirst())
  ```

### 内部类

定义在另一个类中的类

**特性**:
- 可以访问该类定义所在作用域的数据, 包括私有数据
- 可对包中的其他类隐藏
- 当定义回调函数时, 可以很方便的使用匿名内部类.
- Java的内部类包含一个隐式引用, 指向实例化该内部对象的外部对象.[编译器修改内部类构造函数增加引用]
- 虽然定义在外部类当中, 但是并不表示外部类包含内部类的实例这样一个数据成员, 它的实例化依然是通过某个方法中对该类的对象的构造.
- 内部类可以定义成私有的, 而常规类只有包可见性和公开可见性.

举例: 
```java
class TalkingClock {
  private int interval;
  private boolean beep;

  public TalkingClock(int interval, boolean beep){
    ...
  }
  private void start() {
    ActionListener listener = new TimePrinter(); // 内部类实例
  }
  public class TimePrinter implements ActionListener
  {
    public void actionPerformed(ActionEvent event) {
      System.out.println("At the tone, the time is " + new Date());
      if (beep) { // 能够访问外部类的私有成员
        Toolkit.getDefaultToolkit().beep();
      }
    }
  }
}
```

**语法**:

在内部类中访问外部类中的变量, 更加明确的指定写法: `outClass.this`

在外部显式的调用内部类的构造器: `outClass.innerClass obj = outObject.new innerClass(params)`

```java
if (TalkingClock.this.beep) ... // 内部类中调用外部类实例的成员

ActionListener listener = this.new TimePrinter(); // 外部类中显式实例化一个内部类.
```

**有用?必要?安全?**

- 内部类的作用是更高的访问权限, 可以访问外部类的私有方法和数据成员
- 内部类的是编译器现象, 虚拟机层面没有内部类的概念, 内部类将被编译成特殊的普通类
- 内部类的实现是在内部类中增加`this$000`之类的特殊标识符的数据成员, 并在外部类中增加一个`access$000(obj)`的静态方法来实现. 包含`$`在Java中不是一个外部合法的标识符.
- 事实上可以通过某一些方法对上述的特殊成员变量和静态方法进行调用(通过十六进制编辑器修改标识符名)

#### 局部内部类

语法: 在某个代码块中, 例如成员方法中包含一个内部类

变量作用域: 局部内部类可以访问外部类的数据成员, 可以访问方法中的局部变量. 这种访问的实现通过编译器在局部内部类中添加带`$`特殊符号的数据成员, 保存局部变量. 局部内部类所引用的局部变量必须是**事实上final**的. 在Java8之前, 必须是final的.

访问控制: 局部内部类不能声明成`public`或`private`, 其只对当前代码块可见, 对外其他成员方法都不可见. 

用途: 回调函数

##### 匿名内部类

当创建的类只需要创建一个对象时, 适合使用匿名内部类

匿名类语法

```
new SuperType(construction params)
{
  inner class methods and data
};
```
`superType`可以是一个接口, 也可以是一个超类

```java
public void start(int interval, boolean beep) {
  ActionListener listener = new ActionListener()
  {
    public void actionPerformed(ActionEvent event) {
      System.out.println("At the tone, the time is " + new Date());
      if (beep) Toolkit.getDefaultToolkit().beep();
    }
  };
  Timer t = new Timer(interval, listener);
  t.start();
}
```

利用匿名类可以使用*双括号*技巧构造数组列表, 当这个数组列表只在一个参数的地方用到时可以这样写
```java
// 原写法
ArrayList<String> friends = new ArrayList<>();
friends.add("harry");
friends.add("Tony");
invite(friends);

// 匿名类的写法
invite(ArrayList<String>(){{add("Harry"); add("Tony");}}) // 外层的括号建立了ArrayList的匿名子类, 内层括号则是一个对象构造块(第4章)
```
在生成日志或调试消息时, 有时希望打印类名, 但是使用`getClass()`对于静态方法不奏效, 这里可以使用匿名类获得外部类的类名.
```java
new Object(){}.getClass().getEnclosingClass(); //获得静态方法的类名, getEnclosingClass方法获得外围类
```

##### 静态内部类

语法: 在定义内部类时, 加上`static`的关键字,即`public static class Pair`, 得到的就是静态内部类
- 只有内部类能够声明为static, 声明后, 内部类没有对外部类的引用, 其他和内部类一致
- 静态方法中构造内部类对象时, 必须使用静态内部类
- 在接口中的内部类自动变成`public`和`static`的类

### 代理
#### 静态代理&动态代理

## 异常

finally总结
- 不管有木有出现异常，finally块中代码都会执行；
- 当try和catch中有return时，finally仍然会执行；
- finally是在return后面的表达式运算后执行的（此时并没有返回运算后的值，而是先把要返回的值保存起来，管finally中的代码怎么样，返回的值都不会改变，任然是之前保存的值），所以函数返回值是在finally执行前确定的；
- finally中最好不要包含return，否则程序会提前退出，返回值不是try或catch中保存的返回值。


## IO模型

---


## [第八章 Collections类](javacore/v1_ch08.md)

## Java并发原理

pass

## 泛型程序设计

## 集合

### Java集合框架
Java集合框架给出了大量数据结构和算法的实现以供调用, 并且提供了相对统一和简洁的调用方式
- 接口与实现分离: 同一数据结构可能存在多种实现, 具有不同的性能表现, Java将抽象数据结构与具体的实现分离, 例如`Queue`接口就可以用`ArrayList`或`ArrayDeque`来实现队列的功能.
- 接口与实现分离的好处: 能够灵活的更换底层的实现结构
- 另外实现了一组以Abstract开头的类, 为类的实现者设计, 在实现接口时不必实现所有接口的方法.

Collection接口
- boolean add(E element); 添加元素, 确实改变了集合返回`true`否则返回`false`
- Iterator<E> iterator(); 返回一个集合的迭代器
- int size()
- boolean isEmpty()
- boolean contains(Object obj)
- boolean containsAll(Collection<?> c)
- boolean equals(Object other)
- boolean addAll(Collection<? extends E> from)
- boolean remove(Object obj)
- boolean removeAll(Collection<?> c)
- void clear()
- boolean retainAll(Collection<?> c) 删除所有与other集合中不同的元素 由于调用个改变了集合则返回true
- Object[] toArray()
- <T> T[] toArray(T[] arrayToFill)


Iterator接口
- E next(); 逐个访问集合中的每个元素, 到达末尾抛出`NoSuchElementException`
- boolean hasNext(); 可以用`hasNext`和`next`配合, 遍历所有元素, 但是更好的方法是用`foreach`语法 
- void remove(); 删除上次访问的对象 必须紧跟在next后执行, 若上次访问后集合发生改变, 则调用返回`IllegalStateException`
- default void forEachRemaining(Consumer<? super E> action);

`foreach`语法能够与实现了`Iterable`接口的类工作, `Iterable`接口只有一个抽象方法`Iterator`, 即`Collection`中的所有数据类型都扩展了该接口

另外, Java8之后, 可以使用`forEachRemaining`方法, 方法引入一个lambda表达式, 迭代处理每个元素

`iterator.forEachRemaining(element-> do somthing with element);`

> 与C++的区别: Java迭代器认为是位于两个元素之间的,当调用next时, 迭代器就越过下一个元素, 并且返回刚才越过的元素的引用. C++的迭代器则是根据数组索引建模的, 即指向某个位置的元素, 而非两个元素之间

`iterator`接口的`remove`方法
- 该方法删除的是上一个`next`返回的元素, 这与删除前先查看的思想是一致的, 但是删除某个位置的元素前, 也需要先越过该元素
- `remove`方法与`next`方法紧密依赖, 调用`remove`前没有调用`next`是不合法的 **注意删除连续的两个元素时的操作**

![]()

- 向集合插入元素可以用`add`, 但是对于Map接口, 需要用`V put(K key, V value)`和`V get(K key)`方法
- List类是有序集合, 支持随机访问, 定义了以下用于随机访问的方法
  - void add(int index, E element)
  - void remove(int index)
  - E get(int index)
  - E set(int index, E element)
- ListIterator是Iterator的子接口, 定义了`void add(Element)`方法在迭代器前面添加一个元素, 也可以通过`previous`和`hasPrevious`方法向前迭代
- 为了避免对链表完成随机访问的操作, 定义了`randomAccess`接口, 接口没有定义任何方法, 但可以用`instanceOf`检查是否可以高效随机访问
- LinkedList底层是链表, ArrayList底层是动态数组

### 具体的集合类

### 具体的映射类


### 视图与包装器

### alg

### 其他集合
