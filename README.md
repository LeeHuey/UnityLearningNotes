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





