# Java中的API与字符串
## API概述
1. 什么是API
   * 应用程序接口
2. 为什么需要API
   * 别人已经开发好，形成类库
   * 需要时调用，方便开发，提高效率
3. 常用API包结构
   * ![常用API包结构](https://github.com/zhaohui-nanjing/Java-SE/blob/main/API_And_String/%E5%B8%B8%E7%94%A8API%E5%8C%85%E7%BB%93%E6%9E%84.png)
## 文档注释
1. 什么是文档注释
	* 以/**开始，*/结束的注释
	* Java系统自带命令，按照文档注释内容生成Java文档；
2. 为什么需要文档注释
	* 只有文档注释的内容才能通过Java系统自带的javadoc命令写入文档
	* 普通注释只能在代码中看到
3. 怎么使用文档注释
	* 在三个地方使用：类，方法，属性，常量
	* 在类上使用，用于说明类的设计目的，功能等
	* @author 作者
	* @since  最低运行在哪个java版本上 JDK1.8
	* @version 当前类版本1.0
	* @see 该类中用到哪些相关类java.lang.String
	* 在方法上使用，说明参数和返回值
	* @param
	* @return
4. 使用eclipse生成Java Doc
	* File----Export----JavaDoc
## String字符串
1. 什么是String
	* 字符串类型
	* 引用数据类型
2. 为什么需要字符串
	* 字符就是文字，是传输信息必要载体
	* char只能保存一个字节
	* String，一个对象可以保存多个文字
3. 字符串概述
	* String类被final修饰
    	* 不能作为父类被继承
		* 只能被赋值一次，一旦赋值，不能修改
	* String类本质是一个char数组
	* String特殊的赋值方式 String a = "abc";
	* String是不可变对象
	* String是Unicode编码
    	* 编码 将字符转为数字（0，1），解码 将数字转为字符（0，1）
		* char0~65535 a--97 A--65
		* utf-8，2字节编码，几乎包含所有语言字符
4. 字符串常量池
	* 属于堆的内容
	* 可以一定程度上减少内存上的消耗
	* 可以解释它是不可变对象
	* 双引号中引用，一定会在字符串常量池中存一份；
	* ![字符串常量池](https://github.com/zhaohui-nanjing/Java-SE/blob/main/API_And_String/%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%B8%B8%E9%87%8F%E6%B1%A0.png)
	* 字符串是不可变对象，内容一旦创建不可修改
	* 若改变，一定是创建（引用）新对象
	* Java中推荐使用“字符串对象”来直接赋值方法，即字面量直接赋值给变量，好处 是会在字符串常量池中创建，对象可以被重用
	* 使用new方式创建String对象（不推荐），不在字符串常量池中创建，值一样时不能被重用
	* 比较字符串时，需要比较字符串中的内容，使用equals，需要比较地址，使用==
	* Java编译器有个特性：凡是能在编译期确定的计算结果，一定会在编译期运行计算，将编译结果直接保存编译成class文件，不会每次运行时计算，以提高运行效率；
	* 单引号和双引号含义完全不同
    	* 单引号用+连接，会计算对应ASCII码
    	* 双引号用+连接，会组合为新的字符串
## String常用API
1. length（）方法
   * 返回当前字符串对象中字符个数，
   * 实际是char类型数组的长度
   * 数组，length属性返回字符个数
2. indexOf（String str）方法
   * 查找给定字符串在当前字符串中的位置，若存在返回索引位置，若不存在返回-1
   * indexOf（"str", index）从index位置开始找
   * lastIndexOf()找最后出现的字符位置
3. substring（int start，int end）方法
   * 截取域名，两个参数时，留前不留后
   * 一个参数，表示从该位置开始截取到末尾
   * 返回截取到的内容
4. trim（）方法
   * 去掉当前字符串左右两边的空格
5. charAt（）方法
   * 返回指定索引位置的字符
6. startsWith（String str），endsWith（String str）方法
   * 判断当前字符串是否以给定的字符开始或结束
7. toUpperCase（），toLowerCase（）方法
   * 将当前字符串中英文字母转换成全大写或小写
   * 对中文无效
   * 字符串是不变对象，调用该方法，返回值和原字符串值不同
8. 基本数据类型与String的转换
   * 基本数据类型-->String类型：String.valueOf(123)将指定基本数据类型的值转换为String类型
   * String s3 = 123 + “abc”；效率低
## StringBuilder可变长度的字符串
1. 什么是可变长度字符串
	* StringBuilder类是在java.lang包下，该类维护一个可变长度的字符串
	* 本身不是字符串，而是提供维护字符串功能的API
2. 为什么需要StringBuilder
	* 因为String类型对象不可变，在频繁修改时性能低下，内存开销大
	* 频繁修改字符串时，需要避免使用String类型
3. StringBuilder的API类
	* 追加：append（String str）
	* 修改：replace（）三个参数，前两个是替换的区间，遵循留前不留后
	* 删除：delete，两个参数，留前不留后
	* 插入：insert（）向字符串中间加入新字符
4. StringBuffer类
	* 线程安全
	* StringBuilder线程不安全

