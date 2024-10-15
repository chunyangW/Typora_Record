# 第一章 JAVA环境搭建

## 常用windows组合键

- win + R 
  - 打开运行窗口
- win + E
  - 打开资源管理器
- win + L
  - 锁
- win + D 
  - 回到桌面
- alt + tab
  - 切换窗口

## DOS命令

- win + R cmd = command

- 当前路径是黑色窗口之前的一串比如C:\Users\lenovo

- cd .. 
  - 回退路径到上面一级

- mkdir test
  - 新建一个目录

- 常用DOS命令
  - dir :列出当前文件夹下目录

  - cls: clear screen 清屏

  - exit:退出DOS窗口

  - d:     切换到d盘符, 

    - c: 会到 c:\User\lenovo

  - del : 直接接文件名就能删除， 

    - 然后 del *.txt 删除所有带有.txt的文件

  - ipconfig : 查看ip   而ipconfig/all 可以查看 mac 地址

  - ping : 可以看两台电脑之间能不能正常通信，相当于打乒乓球可以交流了， 
    - 而ping ip -t 可以一直请求数据包可以判断网络问题

  - 然后在DOS中强行停止可以使用 ctrl + c

  - 上下方向键可以翻到以前的命令

  - mkdir abc  

    - 创建目录abc

  - rd abc

    - 删除目录abc

  - ren abc xyz

    - 重命名为xyz

  - cd   作用是：切换目录 change directory

    - 路径包括相对路径与绝对路径
      - 前面带   盘符的是绝对路径 如：C:\Users\lenovo\xyz
      - 相对路径  如  xyz/ok  相对的是当前的位置，以当前的位置来找 .\xyz
    - cd .. 
      - 回到上一个路径  .. 代表的是上级目录
      - 一个点代表当前路径 cd .
    - cd / 
      - 回到根目录
    - cd 后敲一个字母，可以自动补全后面的（table）再按可以切换成其他的

  - 可以直接在想要的目录然后输入cmd 直接进入到很深的目录

  - type + 文件名 可以查看文件内容

  - copy con + 文件名 可以新建文件

  - 然后 ctrl Z 保存

  - shutdown ：关机

    - shutdown -s -t 3600 （3600秒后自动关机)


- 批处理

  - .bat 文件

  - 然后在其中编写大量的DOS命令

  - 然后双击执行（执行是在当前的盘符除非其中先改写盘符位置，然后cd到要操作的位置）

    - ```bat
      c:
      cd 绝对路径
      del *.java  
      ```

    - 删除当前的路径中的.java

## 通用的文本编辑快捷键

- ctrl Z 撤销
- ctrl Y 重做也就是反撤销
-  home 键回到行首 shift + home 全选到home, ctrl home 回到文件头
- end 同上
- ctrl shift 左箭头能选中一个单词  test
- ctrl f 搜索

## Java语言的加载与执行

![image-20240926092928636](C:\Users\lenovo\Desktop\typora\开发\第一章 JAVA环境搭建.assets\image-20240926092928636-1727314181191-1-1727314182923-3.png)

- javac编译我们编写产生的源代码.java然后产生字节码文件.class（不是机器码，因为机器码会直接被PC读懂）后面通过java程序使得JVM（java virtual mechine）中运行(命令为  java (类名).class )。

- java既是编译型语言也是解释型语言

- 不同系统下的解释器能够解释出的机器码能被对应系统看懂

## PATH环境变量

- path环境变量不是JAVA 的而是属于window
- path环境变量的作用是什么 -- 指路的
  - 在path中环境变量是多个路径，不同路径用分号隔开
  - 在DOS命令窗口中输入一个dos命令后会优先在cmd当前路径中中寻找命令的路径
  - 如果找不到，则会去path中寻找命令的地址

## 编写第一个JAVA程序

在任何位置新建一个Java源文件起名HelloWorld

```java
public class HelloWorld{
    public static void main(String[] args){
        System.out.println("Hello World!");
    }
}
```

## 编译第一个Java程序

- 先使用Javac命令来编译通过
- javac 怎么使用
  - javac   .java源文件路径
  - javac   .java源文件相对绝对路径
  - 在 Java 中，如果一个类被声明为 `public`，那么它必须定义在与类名相同的文件中。

## 运行

- 使用java文件运行
- **java + 类名**
- !!!!!!!!!!!!!!!  java命令后面跟的不是文件路径，java**后面跟的是类名**
  - test.class 的类名是 test
- <font color =red>要使用java命令，dos命令窗口必须切到class文件所在位置</font>（因为还没有配置classpath环境变量，否则默认在当前路径下）

## JDK 包含 JRE 包含 JVM，JVM与OS交互

jvm 能看懂字节码然后变成机器码才能使用

## 掌握环境变量CLASSPATH

- class path环境变量是隶属于Java语言的，不是Windows操作系统的，和path环境变量完全不同
- class path环境变量是给class loader（类加载器）指路的
- Java A执行后，先启动JVM，JVM启动classloader，classloader去硬盘上通过class path找A.class文件。找到则执行，找不到则报错。
- 如果class path没有配置的话，默认在当前文件夹下找类
- 如何配置 class path：需要去系统变量哪里去新建一个classpath 
- 如果直接配置在桌面上的话，那classloader只去桌面上找.class，而不去当前路径去找除非将.class文件放到桌面上
  - 但是有一个好方法：classpath上添加一个路径：.  （这个表示当前路径）

## 关于编码时的乱码问题

- 文件编译器使用的汉字编译的不同，Java编译器使用的是UTF-8
-  有两个解决方案：
  - 第一种：javac -encoding GBK helloworld.java (改成相应的编码语言)
  - 第二种：将文件编译器的编码语言改成utf-8
- 

## 注释

- javadoc注释（下面的形式）

  - javadoc -d docs - author -version HelloWorld2.java （先生成一个目录docs放帮助文档，然后提取version与author等等）

  - 然后在 index.html中查看

  - ```java
    /**
    * 先要有总体的关键说明
    * @author 吴春阳
    * @version 1.0
    * @since 10.1
    */
    
    // public 表示公开的
    // class 表示定义一个类
    // helloworld2是给这个类起个名
    public class HelloWorld2{  // 定义一个公开的类，名字叫做HelloWorld2
    	
        // 类体
        
    	/**
    	* 这是main方法的关键说明
    	* @param args 这个是参数
    	*/
        // 1. 这是main方法，也叫主方法
        // 2. main方法是JVM规定的，固定写法。照抄，程序就是从这个位置进来执行的，这是程序的入口
        // 3. 对于main方法来说能修改的就是args这个变量名，其他不能dong
        // 4. public 公开 staic 表示静态的 void不返回数据
        // 5. 
        public static void main(String[] args){
            
            //方法体
            // 方法体中一行行Java语句组成
            // 任何java语句以分号结尾
            // 也是逐行执行的
            // 没有ln是不换行的
            // 双引号分号也是不能使用中文双引号的，
            System.out.println("华中科技大象");// 这行代码会将类容输出到控制台中并且会换行: ln
            
        }
        
        
        // 类体
        
        // System.out.println("这里能写这样的java语句吗")//类体中不能
    }
    ```

- 不是注释越多越好：点睛之笔：不要贪多

## 基本元素

-  public表示公开的 

- class 表示 定义一个类‘

- 类体中不能直接编写java语句

  如上代码注释

## public class 与class 区别

- 一个Java文件中可以定义多个class，但是实际的开发中，一个软件只有一个类一个入口
  - 每定义一个class会生成一个类文件
- **如果定义了一个公开的类，java源文件的名字应该和公共类名保持一致**
  - public 的类可以没有，但是如果有也只能有一个
- 每个类中都可以编写一个主函数的入口方法，想要执行相应的类中的主方法直接使用 java 类名就好了

\t 是制表符号可以输出

- java 语言既是是编译型语言，因为它的源代码在运行前需要被编译成字节码（`.class` 文件），然后这些字节码可以在任何安装了 Java 虚拟机（JVM）的设备上运行。然而，Java 的运行过程也涉及到解释执行，因为 JVM 通常会将字节码解释执行。所以，Java 语言结合了编译和解释的特点，有时也被称作“编译型解释型语言”。

- 所以java语言是混合型语言

  