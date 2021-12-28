# UnityLearningNotes

## 1. C#基础

- #### 数据类型

  1. 值类型

  2. 引用类型：指向内存位置

     （1）内置

     - Object：值类型转换成Object为装箱，Object转换为值类型为拆箱
     - Dynamic：运行期类型检查
     - String：

     （2）用户定义

     - class
     - interface
     - deletage

  3. 指针类型

- #### 流程控制

  1. 判断

     if、switch和三元运算符

  2. 循环

     - while循环

     ```
     while(condition)
     {
        statement(s);
     }
     ```

     - for循环

     ```
     for ( init; condition; increment )
     {
        statement(s);
     }
     ```

     - foreach循环

       借助foreach，只能一一取得数组中的元素，**<u>并不能利用这种语句改变</u>**数组所存储的元素

     - do while循环

     ```
     do
     {
        statement(s);
     
     }while( condition );
     ```

- #### C#封装

  - public：所有对象都可以访问
  - private：对象本身在对象内部可以访问
  - protected：只有该类对象及其子类对象可以访问
  - ==internal：<u>同一个程序集的对象可以访问</u>==
  - protected internal：访问限于当前程序集或派生自包含类的类型

- #### C#方法

  别的类似于C/C++，主要是参数传递，包括值参数、引用参数和输出参数三种：

  - 值参数

    复制一份实参给形参

  - 引用参数

    对变量内存位置的引用，使用关键字==ref==声明引用参数

  - 输出参数

    使用输出参数，从函数返回多个值，使用关键字==out==声明输出参数

  - 数组也可当作参数传递给函数，不带索引的数组名称来给函数传递一个指向数组的指针。

  - <u>参数数组</u>，用于传递未知数量的参数给函数

    ```
    public 返回类型 方法名称( params 类型名称[] 数组名称 )
    
    要点补充：
     1.带 params 关键字的参数类型必须是一维数组，不能使用在多维数组上；
     2.不允许和 ref、out 同时使用；
     3.带 params 关键字的参数必须是最后一个参数，并且在方法声明中只允许一个 params 关键字。
     4.不能仅使用 params 来使用重载方法。
     5.没有 params 关键字的方法的优先级高于带有params关键字的方法的优先级
    ```

- #### C#可空类型

  C# 提供了一个特殊的数据类型，**nullable** 类型（可空类型），可空类型可以表示其基础值类型正常范围内的值，再加上一个 null 值。

  ```
  < data_type> ? <variable_name> = null;
  ？单问号用于对 **int、double、bool** 等无法直接赋值为 null 的数据类型进行 null 的赋值，意思是这个数据类型是 Nullable 类型的。
  
  double num3 = num1 ?? 5.34;	//num1为null的时候，返回5.34
  ?? 双问号用于判断一个变量在为 null 的时候返回一个指定的值，类似三元运算符的简化
  ```

- #### C#数组

  - 多维数组

    例如二维数组，区别于C/C++/Java中的二维数组，C#中更类似于矩阵。数组中的每个元素是使用形式为 a[ i , j ] 的元素名称来标识的，其中 a 是数组名称，i 和 j 是唯一标识 a 中每个元素的下标。

    ```
    int [,] a = new int [3,4] {
     {0, 1, 2, 3} ,   /*  初始化索引号为 0 的行 */
     {4, 5, 6, 7} ,   /*  初始化索引号为 1 的行 */
     {8, 9, 10, 11}   /*  初始化索引号为 2 的行 */
    };
    ```

  - 交错数组

    一维数组，是数组的数组。

    ```
    int[][] scores = new int[2][]{new int[]{92,93,94},new int[]{85,66,87,88}};
    scores 是一个由两个整型数组组成的数组 -- scores[0] 是一个带有 3 个整数的数组，scores[1] 是一个带有 4 个整数的数组。
    ```

    ==<u>区别交错数组和多维数组</u>==

  - Array类是C#中所有数组的基类

- #### C#字符串

  ```
  string的创建方式：
  1. 通过给 String 变量指定一个字符串 
  2. 通过使用 String 类构造函数
  	char[] letters = { 'H', 'e', 'l', 'l','o' };
  	string greetings = new string(letters);
  3. 通过使用字符串串联运算符（ + ）
  4. 通过检索属性或调用一个返回字符串的方法
  	string[] sarray = { "Hello", "From", "Tutorials", "Point" };
    string message = String.Join(" ", sarray);
  5. 通过格式化方法来转换一个值或对象为它的字符串表示形式
  	DateTime waiting = new DateTime(2012, 10, 10, 17, 58, 1);
    string chat = String.Format("Message sent at {0:t} on {0:D}", waiting);
  ```

  

- #### C#结构体

  - 结构可带有方法、字段、索引、属性、运算符方法和事件。
  - 可以定义构造函数，不能定义析构函数和无参构造函数
  - 不能继承，不能作为基础结构体
  - 可以实现多个接口
  - 可以不使用new来初始化，但是需要把所有字段都初始化后才能使用
  - 结构成员不能指定为 abstract、virtual 或 protected
  - <u>结构体是值类型，类是引用类型</u>。类的对象是存储在堆空间中，结构存储在栈中。堆空间大，但访问速度较慢，栈空间小，访问速度相对更快。故而，当我们描述一个轻量级对象的时候，结构可提高效率，成本更低。

- #### C#枚举

  ```
  enum <enum_name>
  { 
      enumeration list 
  };
  ```

  枚举列表中的每个符号代表一个整数值，一个比它前面的符号大的整数值。默认情况下，第一个枚举符号的值是 0。

- #### ==C#类==

  - 我们可以使用 **static** 关键字把类成员定义为静态的。当我们声明一个类成员为静态时，意味着无论有多少个类的对象被创建，只会有一个该静态成员的副本。

- #### C#继承

  与C、C++等无区别，不支持多重继承，但是可以通过接口实现多重继承。

- #### C#多态

  - 静态多态

    编译期：

    1. 函数重载

       同一个范围内，相同函数名多个定义。

    2. 运算符重载

       重载运算符是具有特殊名称的函数，是通过关键字 **operator** 后跟运算符的符号来定义的。与其他函数一样，重载运算符有返回类型和参数列表。

  - 动态多态

    - 使用关键字 **abstract** 创建抽象类。

      - 不能创建一个抽象类的实例。

      - 不能在一个抽象类外部声明一个抽象方法。

      - 通过在类定义前面放置关键字 **sealed**，可以将类声明为**密封类**。当一个类被声明为 **sealed** 时，它不能被继承。抽象类不能被声明为 sealed。

    - 使用关键字virtual声明虚函数。

      - 定义在类中的方法需要在继承类中实现。
      - 虚函数的调用在运行期发生。

- #### C#接口

  接口定义了所有类继承接口时应遵循的语法合同。接口定义了语法合同 **"是什么"** 部分，派生类定义了语法合同 **"怎么做"** 部分。

- #### C#异常处理

  C# 异常处理时建立在四个关键词之上的：**try**、**catch**、**finally** 和 **throw**。

- #### C#正则表达式

  [(https://www.runoob.com/regexp/regexp-tutorial.html)]	

- #### C#特性

  **特性（Attribute）**是用于在运行时传递程序中各种元素（比如类、方法、结构、枚举、组件等）的行为信息的声明性标签。

  ```
  [attribute(positional_parameters, name_parameter = value, ...)]
  element
  ```

  .Net 框架提供了两种类型的特性：*预定义*特性和*自定义*特性。

  - 预定义特性

    - AttributeUsage：描述了如何使用一个自定义特性类，自定义特性的时候使用。

      ```
      规定的语法结构：
      [AttributeUsage(
         validon, 
         AllowMultiple=allowmultiple, 
         Inherited=inherited 
      )]
      参数的含义：
      //参数 validon 规定特性可被放置的语言元素。它是枚举器 AttributeTargets 的值的组合。默认值是 AttributeTargets.All。
      //参数 allowmultiple（可选的）为该特性的 AllowMultiple 属性（property）提供一个布尔值。如果为 true，则该特性是多用的。默认值是 false（单用的）。
      //参数 inherited（可选的）为该特性的 Inherited 属性（property）提供一个布尔值。如果为 true，则该特性可被派生类继承。默认值是 false（不被继承）。
      例子：
      [AttributeUsage(AttributeTargets.Class |
      AttributeTargets.Constructor |
      AttributeTargets.Field |
      AttributeTargets.Method |
      AttributeTargets.Property, 
      AllowMultiple = true)]
      ```

    - Conditional：标记了一个条件方法，其执行依赖于指定的预处理标识符。

      ```
      规定的语法结构：
      [Conditional(
         conditionalSymbol
      )]
      eg.
      #define DEBUG
      //......
      [Conditional("DEBUG")]
      void XXXclass() {......}
      预定义且被标记的方法会被执行，相当于#if #end预定义的封装。
      ```

    - Obsolete：（过时的）标记了不应被使用的程序实体。

      ```
      [Obsolete(
         message,
         iserror
      )]
      eg.
      [Obsolete("Don't use OldMethod, use NewMethod instead", true)]
      static void OldMethod() {
      	Console.WriteLine("It is the old method");
      }
      ```
      
      - 参数 *message*，是一个字符串，描述项目为什么过时以及该替代使用什么。
      - 参数 *iserror*，是一个布尔值。如果该值为 true，编译器应把该项目的使用当作一个错误。默认值是 false（编译器生成一个警告）。

  - 自定义特性

    用于存储声明性的信息，且可在运行时被检索。包含4个步骤：

    - 声明自定义特性
    
      一个新的自定义特性应派生自 **System.Attribute** 类。
    
      eg.
    
      ```
      // 一个自定义特性 BugFix 被赋给类及其成员
      [AttributeUsage(AttributeTargets.Class |
      AttributeTargets.Constructor |
      AttributeTargets.Field |
      AttributeTargets.Method |
      AttributeTargets.Property,
      AllowMultiple = true)]
      
      public class DeBugInfo : System.Attribute
      ```
    
    - 构建自定义特性
    
      构建一个名为 *DeBugInfo* 的自定义特性，该特性将存储调试程序获得的信息。
    
      例子见：[](https://www.runoob.com/csharp/csharp-attribute.html)
    
    - 在目标程序元素上应用自定义特性
    
      通过把特性放置在紧接着它的目标之前，来应用该特性。
    
    - 通过反射访问特性

- #### C#反射 Reflection

  - 程序可以访问、检测和修改它本身状态或行为的一种能力。用途：

    - 它允许在运行时查看特性（attribute）信息。
    - 它允许审查集合中的各种类型，以及实例化这些类型。
    - 它允许延迟绑定的方法和属性（property）。
    - 它允许在运行时创建新类型，然后使用这些类型执行一些任务。

  - 查看元数据

    **System.Reflection** 类的 **MemberInfo** 对象需要被初始化，用于发现与类相关的特性（attribute）。

    - 遍历类特性

      Type type = typeof(MyClass)

       **foreach** (**Object** attributes **in** type.GetCustomAttributes(**false**))

    - 遍历方法特性

       **foreach** (MethodInfo m **in** type.GetMethods())
            **foreach** (Attribute a **in** m.GetCustomAttributes(**true**))

  



​	

​	

