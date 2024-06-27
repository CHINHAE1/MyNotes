### 1、String[#](https://www.cnblogs.com/deyo/p/17496096.html#1string)

- String的声明：final 、实现Comparable接口等
- String内部的属性：final char[] value (jdk8中)；final byte[] value(jdk9中)
- String的声明方式1：使用字面量的方式。需要使用字符串常量池。
- String的不可变性
- String的声明方式2：new
- String的特殊运算： +
    - 常量 + 常量；变量+ 常量 ； 变量+变量；concat()；intern()
- String的构造器、常用方法

### 2、与String相关的类：StringBuffer、StringBuilder[#](https://www.cnblogs.com/deyo/p/17496096.html#2%E4%B8%8Estring%E7%9B%B8%E5%85%B3%E7%9A%84%E7%B1%BBstringbufferstringbuilder)

- String、StringBuffer、StringBuilder三个的异同。
- StringBuffer、StringBuilder的常用方法：增、删、改、查、插、长度、反转
- 三者添加数据方面的执行效率：StringBuilder > StringBuffer > String

### 3、比较器[#](https://www.cnblogs.com/deyo/p/17496096.html#3%E6%AF%94%E8%BE%83%E5%99%A8)

开发中只要涉及到对象比较大小，都跟比较器打交道。

#### 3.1 自然排序：Comparable[#](https://www.cnblogs.com/deyo/p/17496096.html#31-%E8%87%AA%E7%84%B6%E6%8E%92%E5%BA%8Fcomparable)

```css
实现步骤：
1. 待排序的对象所说的类要实现Comaprable接口
2. 实现接口中的抽象方法：compareTo(Object obj),指明比较大小的规则
3. 创建待排序的多个对象，在相关的逻辑下进行排序操作即可。比如：Arrays.sort(Object[] objs)
```

#### 3.2 定制排序：Comparator[#](https://www.cnblogs.com/deyo/p/17496096.html#32-%E5%AE%9A%E5%88%B6%E6%8E%92%E5%BA%8Fcomparator)

```css
实现步骤：
1. 创建一个实现了Comparator接口的类SubComparator
2. 此SubComparator类重写compare(Object o1,Object o2)
   此方法中指明要比较类A的实例对象o1,o2的大小。
3. 创建多个类A的对象，在相关的逻辑下进行排序操作即可。比如：Arrays.sort(A[] objs,SubComparator的对象)
```

```makefile
对比两种方式：

Comparable:在声明好类的同时，就指明了默认的排序的方式。
           一旦声明，一劳永逸

Comparator: 比较灵活，可以在需要的具体场景下，灵活的指定排序的方式。
           每次在需要的时候，都得现创建一个Comparator实现类的对象。
```

### 4、日期时间相关的API[#](https://www.cnblogs.com/deyo/p/17496096.html#4%E6%97%A5%E6%9C%9F%E6%97%B6%E9%97%B4%E7%9B%B8%E5%85%B3%E7%9A%84api)

#### 4.1 jdk8之前相关API[#](https://www.cnblogs.com/deyo/p/17496096.html#41-jdk8%E4%B9%8B%E5%89%8D%E7%9B%B8%E5%85%B3api)

- System的currentTimeMillis()
- java.util.Date 和 java.sql.Date
    - getTime() \ toString()
- SimpleDateFormat：用来格式化、解析日期
    - 格式化：String format(Date date)
    - 解析：Date parse(String str)
- Calendar：日历类，抽象类
    - 实例化：getInstance()
    - 方法：get(int field) 、set(int field,...)、add(...)，Date getTime() 、 setTime(Date date)

#### 4.2 jdk8新增的API[#](https://www.cnblogs.com/deyo/p/17496096.html#42-jdk8%E6%96%B0%E5%A2%9E%E7%9A%84api)

- LocalDate、LocalTime、LocalDateTime --> 类似于Calendar
- Instant : 瞬时 ---> 类似于Date
- DateTimeFormatter ：类似于SimpleDateFormat。针对LocalDate、LocalTime、LocalDateTime的格式化或解析操作

### 5、其他api的使用[#](https://www.cnblogs.com/deyo/p/17496096.html#5%E5%85%B6%E4%BB%96api%E7%9A%84%E4%BD%BF%E7%94%A8)

```markdown
1. System类
2. Runtime类：单例设计模式，对应着一个java进程中运行时内存环境。
3. Math类：跟数学操作相关的api

4. BigInteger类和BigDecimal类
BigInteger类:如果在程序中，需要使用的整型数据超出了long的范围(最大值为2^63 -1 )，则可以使用BigInteger替换，
             可以表示任意精度范围的整数。
BigDecimal类：如果在程序中，想表示任意精度的浮点型值，则使用BigDecimal类替换double的使用。

5. Random类
```