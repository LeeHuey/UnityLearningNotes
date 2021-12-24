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
  stirng的创建方式：
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

  

  

  

  

  

  

​	

