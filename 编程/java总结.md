## **一、Java基础**

### **1. 基本数据类型**

#### **概念**

Java中直接存储值的8种原始数据类型。

#### **定义**

- `byte`（1字节）、`short`（2字节）、`int`（4字节）、`long`（8字节）
- `float`（4字节）、`double`（8字节）
- `char`（2字节，Unicode）、`boolean`（true/false）

#### **语法**

java

复制

```
int age = 25;          // 整数
double price = 99.95;  // 浮点数
char grade = 'A';      // 字符
boolean isOpen = true; // 布尔值
```

#### **作用**

定义变量类型，限制数据范围和内存占用。

#### **案例**

计算商品总价：

java

复制

```
int quantity = 3;
double price = 29.99;
double total = quantity * price; // 输出：89.97
```

------

### **2. 引用数据类型**

#### **概念**

存储对象内存地址的数据类型。

#### **定义**

- 类（如`String`、自定义类）
- 接口、数组

#### **语法**

java

复制

```
String name = "Java";           // String类
int[] numbers = new int[5];     // 数组
Student stu = new Student();    // 自定义类
```

#### **作用**

操作复杂数据结构，支持面向对象编程。

#### **案例**

创建学生对象数组：

java

复制

```
Student[] students = new Student[3];
students[0] = new Student("Alice");
students[1] = new Student("Bob");
```

------

### **3. 运算符**

#### **概念**

用于数据运算的符号。

#### **定义**

- 算术：`+`, `-`, `*`, `/`, `%`
- 比较：`==`, `!=`, `>`, `<`
- 逻辑：`&&`, `||`, `!`
- 位运算：`&`, `|`, `^`, `<<`, `>>`

#### **语法**

java

复制

```
int a = 10, b = 20;
boolean result = (a > b) && (a != 0); // false
int c = a << 2; // 左移两位，结果40
```

#### **作用**

实现数学计算和逻辑判断。

#### **案例**

判断闰年：

java

复制

```
int year = 2024;
boolean isLeap = (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0); // true
```

------

### **4. 流程控制：if-else**

#### **概念**

根据条件执行不同代码分支。

#### **定义**

java

复制

```
if (条件1) {
    // 代码块1
} else if (条件2) {
    // 代码块2
} else {
    // 默认代码块
}
```

#### **语法**

java

复制

```
int score = 85;
if (score >= 90) {
    System.out.println("优秀");
} else if (score >= 60) {
    System.out.println("及格"); // 输出：及格
} else {
    System.out.println("不及格");
}
```

#### **作用**

实现条件逻辑分支。

#### **案例**

用户权限判断：

java

复制

```
String role = "admin";
if ("admin".equals(role)) {
    System.out.println("显示管理菜单");
} else {
    System.out.println("显示普通菜单");
}
```

------

### **5. 流程控制：for循环**

#### **概念**

重复执行代码块固定次数。

#### **定义**

java

复制

```
for (初始化; 终止条件; 迭代) {
    // 循环体
}
```

#### **语法**

java

复制

```
for (int i = 0; i < 5; i++) {
    System.out.println(i); // 输出0到4
}
```

#### **作用**

处理重复性任务（如遍历数组）。

#### **案例**

计算数组元素和：

java

复制

```
int[] nums = {1, 2, 3, 4};
int sum = 0;
for (int num : nums) {
    sum += num; // sum = 10
}
```

------

### **6. 面向对象：封装**

#### **概念**

隐藏对象内部实现细节，通过方法暴露操作。

#### **定义**

- 使用 `private` 修饰成员变量
- 通过 `public` 的 getter/setter 访问

#### **语法**

java

复制

```
public class Student {
    private String name;
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
}
```

#### **作用**

保护数据完整性，防止非法修改。

#### **案例**

限制年龄范围：

java

复制

```
public class Person {
    private int age;
    public void setAge(int age) {
        if (age < 0 || age > 150) {
            throw new IllegalArgumentException("非法年龄");
        }
        this.age = age;
    }
}
```

------

### **7. 面向对象：继承**

#### **概念**

子类继承父类属性和方法。

#### **定义**

使用 `extends` 关键字：

java

复制

```
class Animal {
    void eat() { System.out.println("进食"); }
}
class Dog extends Animal {
    void bark() { System.out.println("吠叫"); }
}
```

#### **语法**

java

复制

```
Dog dog = new Dog();
dog.eat();  // 调用父类方法
dog.bark(); // 调用子类方法
```

#### **作用**

代码复用，实现多态。

#### **案例**

扩展图形类：

java

复制

```
class Shape { void draw() {} }
class Circle extends Shape {
    @Override
    void draw() { System.out.println("画圆形"); }
}
```

------

### **8. 面向对象：多态**

#### **概念**

同一方法在不同对象中有不同实现。

#### **定义**

- 编译时类型（父类） vs 运行时类型（子类）
- 方法重写（Override）

#### **语法**

java

复制

```
Animal animal = new Dog(); // 向上转型
animal.eat(); // 调用Dog类的eat方法（若被重写）
```

#### **作用**

提高代码扩展性和灵活性。

#### **案例**

统一处理不同支付方式：

java

复制

```
interface Payment {
    void pay();
}
class Alipay implements Payment {
    @Override
    public void pay() { System.out.println("支付宝支付"); }
}
class WechatPay implements Payment {
    @Override
    public void pay() { System.out.println("微信支付"); }
}
```

------

### **9. 抽象类**

#### **概念**

包含抽象方法的类，不能实例化。

#### **定义**

使用 `abstract` 关键字：

java

复制

```
abstract class Shape {
    abstract void draw(); // 抽象方法
    void print() { System.out.println("形状"); } // 普通方法
}
```

#### **语法**

子类必须实现抽象方法：

java

复制

```
class Circle extends Shape {
    @Override
    void draw() { System.out.println("画圆形"); }
}
```

#### **作用**

定义规范，强制子类实现特定行为。

#### **案例**

模板方法模式：

java

复制

```
abstract class Game {
    abstract void initialize();
    abstract void start();
    abstract void end();
    public final void play() { // 模板方法
        initialize();
        start();
        end();
    }
}
```

------

### **10. 接口**

#### **概念**

完全抽象的类，定义方法规范。

#### **定义**

使用 `interface` 关键字：

java

复制

```
interface Flyable {
    void fly(); // 默认public abstract
    default void land() { // Java 8默认方法
        System.out.println("着陆");
    }
}
```

#### **语法**

类通过 `implements` 实现接口：

java

复制

```
class Bird implements Flyable {
    @Override
    public void fly() { System.out.println("鸟飞"); }
}
```

#### **作用**

实现多继承，解耦代码。

#### **案例**

USB设备接口：

java

复制

```
interface USB {
    void connect();
    void transferData();
}
class Mouse implements USB {
    @Override
    public void connect() { System.out.println("鼠标连接"); }
    // 其他方法实现...
}
```

------

（由于篇幅限制，此处仅展示部分内容。完整版需覆盖以下所有知识点：集合框架、泛型、异常处理、多线程、IO/NIO、反射、注解、Lambda、Java Web基础、Servlet、JSP、Filter、Session、JDBC、MVC等，每个知识点均按上述格式独立展开）



#### **11. 集合框架：HashMap**

**概念**
基于哈希表实现的键值对存储结构。
**定义**

- 允许`null`键和`null`值
- 非线程安全，扩容机制为2的幂次
  **语法**

java

复制

```
Map<String, Integer> map = new HashMap<>();
map.put("apple", 10); // 添加键值对
int count = map.get("apple"); // 获取值
```

**作用**
高效存储和查询键值数据。
**案例**
统计单词频率：

java

复制

```
String text = "apple banana apple orange";
Map<String, Integer> frequency = new HashMap<>();
for (String word : text.split(" ")) {
    frequency.put(word, frequency.getOrDefault(word, 0) + 1);
}
// 结果：{apple=2, banana=1, orange=1}
```

------

#### **12. 异常处理：try-catch**

**概念**
捕获和处理程序运行时的错误。
**定义**

- `try`：包裹可能抛出异常的代码
- `catch`：捕获指定类型异常并处理
  **语法**

java

复制

```
try {
    int result = 10 / 0; // 抛出ArithmeticException
} catch (ArithmeticException e) {
    System.out.println("除数不能为0");
} finally {
    System.out.println("清理资源");
}
```

**作用**
防止程序因异常崩溃，保证健壮性。
**案例**
文件读取异常处理：

java

复制

```
try (BufferedReader reader = new BufferedReader(new FileReader("file.txt"))) {
    String line = reader.readLine();
} catch (IOException e) {
    e.printStackTrace();
}
```

------

### **Java Web完整知识点（部分示例）**

#### **1. Servlet请求转发**

**概念**
将请求在服务器端转发到其他资源（如JSP）。
**定义**

- 使用`RequestDispatcher`对象
- URL不变，共享`request`作用域
  **语法**

java

复制

```
RequestDispatcher dispatcher = request.getRequestDispatcher("welcome.jsp");
dispatcher.forward(request, response);
```

**作用**
实现服务器端跳转，隐藏资源路径。
**案例**
用户登录后跳转到主页：

java

复制

```
if (loginSuccess) {
    request.getRequestDispatcher("home.jsp").forward(request, response);
} else {
    response.sendRedirect("login.jsp");
}
```

------

#### **2. JDBC数据库连接**

**概念**
Java操作关系型数据库的标准API。
**定义**

- 步骤：加载驱动 → 创建连接 → 执行SQL → 处理结果 → 关闭资源
  **语法**

java

复制

```
Class.forName("com.mysql.cj.jdbc.Driver");
Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb", "user", "password");
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM users");
```

**作用**
实现Java程序与数据库的交互。
**案例**
查询用户信息：

java

复制

```
String sql = "SELECT username FROM users WHERE id = ?";
try (PreparedStatement pstmt = conn.prepareStatement(sql)) {
    pstmt.setInt(1, 1001);
    ResultSet rs = pstmt.executeQuery();
    if (rs.next()) {
        System.out.println(rs.getString("username"));
    }
}
```

------

### **后续内容覆盖范围**

- **Java基础**：泛型、反射、多线程同步、NIO、Lambda表达式、Stream API
- **Java Web**：Filter链、Session分布式存储、JSTL标签、RESTful API设计、MyBatis整合
- **项目实战**：电商购物车、博客系统（含数据库设计图与代码）



### **13. 泛型（Generics）**

#### **概念**

在编译时检查类型安全，避免运行时类型转换错误。

#### **定义**

- 类型参数化（如`List<String>`）
- 可应用于类、接口、方法

#### **语法**

java

复制

```
// 泛型类
class Box<T> {
    private T data;
    public void setData(T data) { this.data = data; }
    public T getData() { return data; }
}

// 使用
Box<String> box = new Box<>();
box.setData("Hello");
String value = box.getData(); // 无需强制类型转换
```

#### **作用**

提高代码复用性，避免`ClassCastException`。

#### **案例**

泛型方法实现数组交换：

java

复制

```
public static <T> void swap(T[] array, int i, int j) {
    T temp = array[i];
    array[i] = array[j];
    array[j] = temp;
}

// 使用
Integer[] nums = {1, 2, 3};
swap(nums, 0, 2); // nums变为 [3, 2, 1]
```

------

### **14. 反射（Reflection） 14.反射（Reflection）**

#### **概念**

在运行时动态获取类信息并操作对象。

#### **定义**

- 核心类：`Class`, `Method`, `Field`, `Constructor`
- 可突破封装性（如访问私有方法）

#### **语法**

java

复制

```
Class<?> clazz = Class.forName("com.example.Student"); // 获取Class对象
Object obj = clazz.newInstance(); // 创建实例
Method method = clazz.getMethod("setName", String.class); // 获取方法
method.invoke(obj, "Alice"); // 调用方法
```

#### **作用**

框架设计（如Spring）、动态代理、注解处理。

#### **案例**

通过反射调用私有方法：

java

复制

```
class Test {
    private void secret() { System.out.println("私有方法被调用"); }
}

// 反射调用
Class<?> clazz = Test.class;
Method method = clazz.getDeclaredMethod("secret");
method.setAccessible(true); // 突破私有限制
method.invoke(clazz.newInstance()); // 输出：私有方法被调用
```

------

### **15. 多线程同步：synchronized**

#### **概念**

确保同一时间只有一个线程访问共享资源。

#### **定义**

- 修饰方法或代码块
- 基于对象监视器（Monitor）实现锁机制

#### **语法**

java

复制

```
// 同步方法
public synchronized void increment() {
    count++;
}

// 同步代码块
public void add() {
    synchronized (lockObject) { // 显式锁对象
        count++;
    }
}
```

#### **作用**

解决多线程环境下的数据竞争问题。

#### **案例**

线程安全的计数器：

java

复制

```
class Counter {
    private int count = 0;
    public synchronized void add() { count++; }
    public int getCount() { return count; }
}

// 多线程测试
Counter counter = new Counter();
Runnable task = () -> {
    for (int i = 0; i < 1000; i++) {
        counter.add();
    }
};
Thread t1 = new Thread(task);
Thread t2 = new Thread(task);
t1.start();
t2.start();
t1.join();
t2.join();
System.out.println(counter.getCount()); // 正确输出2000
```

------

### **16. NIO（Non-blocking I/O） 16.NIO（无阻塞 I/O）**

#### **概念**

基于通道（Channel）和缓冲区（Buffer）的高性能I/O模型。

#### **定义**

- 核心组件：`Channel`, `Buffer`, `Selector`
- 非阻塞模式适合高并发场景

#### **语法**

java

复制

```
// 文件复制示例
try (FileChannel src = FileChannel.open(Paths.get("source.txt"), StandardOpenOption.READ);
     FileChannel dest = FileChannel.open(Paths.get("dest.txt"), StandardOpenOption.WRITE)) {
    ByteBuffer buffer = ByteBuffer.allocate(1024);
    while (src.read(buffer) != -1) {
        buffer.flip(); // 切换为读模式
        dest.write(buffer);
        buffer.clear(); // 清空缓冲区
    }
}
```

#### **作用**

提升I/O操作效率，支持网络高并发。

#### **案例**

使用Selector实现多路复用：

java

复制

```
Selector selector = Selector.open();
ServerSocketChannel serverChannel = ServerSocketChannel.open();
serverChannel.bind(new InetSocketAddress(8080));
serverChannel.configureBlocking(false);
serverChannel.register(selector, SelectionKey.OP_ACCEPT);

while (true) {
    selector.select(); // 阻塞直到有事件
    Set<SelectionKey> keys = selector.selectedKeys();
    for (SelectionKey key : keys) {
        if (key.isAcceptable()) {
            // 处理新连接
        } else if (key.isReadable()) {
            // 处理读事件
        }
    }
    keys.clear();
}
```

------

## **四、Java Web（续）**

### **3. Filter链 3. 过滤器链**

#### **概念**

多个过滤器按配置顺序依次处理请求。

#### **定义**

- 在`web.xml`中定义`<filter-mapping>`顺序
- 或通过注解`@WebFilter`的`urlPatterns`和`order`属性

#### **语法**

xml

复制

```
<!-- web.xml配置 -->
<filter>
    <filter-name>LogFilter</filter-name>
    <filter-class>com.example.LogFilter</filter-class>
</filter>
<filter-mapping>
    <filter-name>LogFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>
```



运行 HTML

#### **作用**

实现责任链模式，如日志 → 编码 → 权限校验。

#### **案例**

多过滤器顺序执行：

java

复制

```
@WebFilter(urlPatterns = "/*", filterName = "EncodingFilter", order = 1)
public class EncodingFilter implements Filter {
    @Override
    public void doFilter(ServletRequest req, ServletResponse res, FilterChain chain) {
        req.setCharacterEncoding("UTF-8");
        chain.doFilter(req, res);
    }
}

@WebFilter(urlPatterns = "/*", filterName = "AuthFilter", order = 2)
public class AuthFilter implements Filter {
    @Override
    public void doFilter(ServletRequest req, ServletResponse res, FilterChain chain) {
        HttpServletRequest request = (HttpServletRequest) req;
        if (request.getSession().getAttribute("user") == null) {
            response.sendRedirect("/login.jsp");
            return;
        }
        chain.doFilter(req, res);
    }
}
```

------

### **4. Session分布式存储**

#### **概念**

在集群环境中共享Session数据。

#### **定义**

- 方案：Redis存储、数据库存储、Session复制
- 使用Spring Session等框架简化实现

#### **语法**

java

复制

```
// 配置Redis存储Session（Spring Boot）
@Configuration
@EnableRedisHttpSession
public class SessionConfig {
    @Bean
    public LettuceConnectionFactory connectionFactory() {
        return new LettuceConnectionFactory(new RedisStandaloneConfiguration("localhost", 6379));
    }
}
```

#### **作用**

解决多服务器间Session不一致问题。

#### **案例**

从Redis读取Session：

java

复制

```
HttpSession session = request.getSession();
session.setAttribute("user", "Alice"); // 存储到Redis
String user = (String) session.getAttribute("user"); // 从Redis读取
```

------

### **5. JSTL标签**

#### **概念**

JSP标准标签库，简化JSP中的逻辑代码。

#### **定义**

- 核心标签：`<c:if>`, `<c:forEach>`
- 格式化标签：`<fmt:formatDate>`

#### **语法**

jsp

复制

```
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<c:if test="${not empty user}">
    <p>欢迎, ${user.name}</p>
</c:if>

<c:forEach items="${users}" var="user" varStatus="status">
    <tr>
        <td>${status.index + 1}</td>
        <td>${user.name}</td>
    </tr>
</c:forEach>
```

#### **作用**

替代JSP脚本，提升代码可读性。

#### **案例**

格式化日期：

jsp

复制

```
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
<fmt:formatDate value="${now}" pattern="yyyy-MM-dd HH:mm:ss" />
```

------

### **6. RESTful API设计**

#### **概念**

基于HTTP协议的API设计风格。

#### **定义**

- 资源URI：`/users/{id}`
- HTTP方法语义：GET（查询）、POST（新增）、PUT（更新）、DELETE（删除）

#### **语法**

java

复制

```
@WebServlet("/api/users/*")
public class UserServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) {
        String pathInfo = req.getPathInfo(); // 解析路径如 /1
        // 返回用户数据
    }
    
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) {
        // 创建新用户
    }
}
```

#### **作用**

统一接口规范，提高前后端协作效率。

#### **案例**

使用Java实现RESTful端点：

java

复制

```
// 获取用户列表：GET /api/users
// 创建用户：POST /api/users
// 删除用户：DELETE /api/users/1
```

------

### **7. MyBatis整合**

#### **概念**

ORM框架，通过XML或注解配置SQL映射。

#### **定义**

- 核心组件：`SqlSessionFactory`, `Mapper`接口
- 动态SQL：`<if>`, `<foreach>`标签

#### **语法**

xml

复制

```
<!-- Mapper XML -->
<mapper namespace="com.example.UserMapper">
    <select id="selectUserById" resultType="User">
        SELECT * FROM users WHERE id = #{id}
    </select>
</mapper>
```



运行 HTML

#### **作用**

简化JDBC操作，实现对象-关系映射。

#### **案例**

MyBatis查询用户：

java

复制

```
try (SqlSession session = sqlSessionFactory.openSession()) {
    UserMapper mapper = session.getMapper(UserMapper.class);
    User user = mapper.selectUserById(1);
    System.out.println(user.getName());
}
```

------

## **五、项目实战**

### **1. 电商购物车模块**

#### **技术栈**

- 前端：JSP + AJAX
- 后端：Servlet + MyBatis
- 数据库：MySQL

#### **核心功能**

- 商品列表展示（分页）
- 购物车增删改查（Session或Redis存储）
- 订单生成与支付模拟

#### **代码片段**

java

复制

```
// 添加商品到购物车
public void addToCart(HttpServletRequest request, int productId, int quantity) {
    HttpSession session = request.getSession();
    Map<Integer, Integer> cart = (Map<Integer, Integer>) session.getAttribute("cart");
    if (cart == null) {
        cart = new HashMap<>();
        session.setAttribute("cart", cart);
    }
    cart.put(productId, cart.getOrDefault(productId, 0) + quantity);
}
```

------

### **2. 博客系统**

#### **技术栈**

- 前端：Thymeleaf + Bootstrap
- 后端：Spring Boot + JPA
- 搜索：Elasticsearch

#### **核心功能**

- Markdown文章编辑与渲染
- 评论与回复（嵌套结构）
- 全文搜索（Elasticsearch集成）

#### **数据库设计**

sql

复制

```
CREATE TABLE articles (
    id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255),
    content TEXT,
    author_id INT,
    created_at DATETIME
);
```

------

**剩余知识点**（持续补充中）：

- Java 8 Lambda表达式与Stream API
- 动态代理与AOP原理
- Web安全（XSS/CSRF防御）
- WebSocket实时通信
- 微服务基础概念





## **六、Java 8 新特性**

### **1. Lambda表达式**

#### **概念**

匿名函数，简化代码编写，实现函数式编程。

#### **定义**

- 语法：`(参数列表) -> { 代码块 }`
- 需函数式接口（仅含一个抽象方法）支持

#### **语法**

java

复制

```
// 无参数
Runnable task = () -> System.out.println("Hello Lambda");

// 带参数
Comparator<Integer> comparator = (a, b) -> a.compareTo(b);
```

#### **作用**

简化匿名内部类，提升代码简洁性。

#### **案例**

集合遍历：

java

复制

```
List<String> list = Arrays.asList("Java", "Python", "C++");
list.forEach(str -> System.out.println(str));
```

------

### **2. Stream API 2.流应用程序接口**

#### **概念**

对集合数据进行函数式操作（过滤、映射、归约）。

#### **定义**

- 中间操作（如filter, map）
- 终止操作（如collect, forEach）

#### **语法**

java

复制

```
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> squares = numbers.stream()
                               .filter(n -> n % 2 == 0)
                               .map(n -> n * n)
                               .collect(Collectors.toList());
// 结果：[4, 16]
```

#### **作用**

简化集合处理，支持链式操作和并行处理。

#### **案例**

统计员工薪资：

java

复制

```
List<Employee> employees = ...;
double totalSalary = employees.stream()
                              .mapToDouble(Employee::getSalary)
                              .sum();
```

------

## **七、高级特性**

### **1. 注解（Annotation）**

#### **概念**

为代码添加元数据，影响编译或运行时行为。

#### **定义**

- 内置注解：`@Override`, `@Deprecated`
- 元注解：`@Target`, `@Retention`

#### **语法**

java

复制

```
// 自定义注解
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface Loggable {
    String value() default "操作日志";
}

// 使用注解
class Service {
    @Loggable("用户登录")
    public void login() { ... }
}
```

#### **作用**

框架配置（如Spring）、代码生成（如Lombok）。

#### **案例**

通过反射读取注解：

java

复制

```
Method method = Service.class.getMethod("login");
Loggable loggable = method.getAnnotation(Loggable.class);
System.out.println(loggable.value()); // 输出：用户登录
```

------

### **2. 动态代理**

#### **概念**

运行时动态创建代理类，增强目标对象功能。

#### **定义**

- JDK动态代理（基于接口）
- CGLIB代理（基于类继承）

#### **语法**

java

复制

```
// JDK动态代理
interface UserService {
    void save();
}

class UserServiceImpl implements UserService {
    public void save() { System.out.println("保存用户"); }
}

InvocationHandler handler = (proxy, method, args) -> {
    System.out.println("前置处理");
    Object result = method.invoke(new UserServiceImpl(), args);
    System.out.println("后置处理");
    return result;
};

UserService proxy = (UserService) Proxy.newProxyInstance(
    UserService.class.getClassLoader(),
    new Class[]{UserService.class},
    handler
);
proxy.save(); 
// 输出：前置处理 → 保存用户 → 后置处理
```

#### **作用**

实现AOP（如日志、事务管理）。

#### **案例**

Spring AOP中的方法增强：

java

复制

```
@Aspect
@Component
public class LogAspect {
    @Before("execution(* com.example.service.*.*(..))")
    public void before(JoinPoint joinPoint) {
        System.out.println("方法执行前记录日志");
    }
}
```

------

## **八、Web安全**

### **1. XSS防御**

#### **概念**

跨站脚本攻击，恶意脚本注入网页。

#### **定义**

- 存储型XSS：恶意脚本存储到数据库
- 反射型XSS：通过URL参数注入

#### **防御方法**

- 输入过滤：移除`<script>`标签
- 输出转义：使用`HtmlUtils.htmlEscape()`

#### **案例**

Spring中转义HTML：

java

复制

```
import org.springframework.web.util.HtmlUtils;

String userInput = "<script>alert('XSS');</script>";
String safeOutput = HtmlUtils.htmlEscape(userInput);
// 输出：&lt;script&gt;alert('XSS');&lt;/script&gt;
```

------

### **2. SQL注入防御**

#### **概念**

通过输入恶意SQL破坏数据库查询逻辑。

#### **定义**

- 攻击方式：`' OR '1'='1`
- 防御方法：使用预编译语句（PreparedStatement）

#### **语法**

java

复制

```
String sql = "SELECT * FROM users WHERE username = ? AND password = ?";
PreparedStatement pstmt = conn.prepareStatement(sql);
pstmt.setString(1, username);
pstmt.setString(2, password);
ResultSet rs = pstmt.executeQuery();
```

#### **作用**

防止恶意SQL篡改查询逻辑。

#### **案例**

MyBatis中防注入：

xml

复制

```
<select id="findUser" resultType="User">
    SELECT * FROM users 
    WHERE username = #{username} AND password = #{password}
</select>
```



运行 HTML

------

## **九、实时通信**

### **1. WebSocket 1. 网络套接字**

#### **概念**

全双工通信协议，实现服务端主动推送消息。

#### **定义**

- 替代方案：轮询、长轮询
- 注解：`@ServerEndpoint`, `@OnMessage`

#### **语法**

java

复制

```
@ServerEndpoint("/chat")
public class ChatEndpoint {
    @OnOpen
    public void onOpen(Session session) {
        System.out.println("连接建立: " + session.getId());
    }

    @OnMessage
    public void onMessage(String message, Session session) {
        session.getBasicRemote().sendText("回复: " + message);
    }
}
```

#### **作用**

实时聊天、在线游戏、股票行情推送。

#### **案例**

前端连接WebSocket：

javascript

复制

```
const socket = new WebSocket('ws://localhost:8080/chat');
socket.onmessage = event => {
    console.log('收到消息:', event.data);
};
socket.send('Hello WebSocket');
```

------

## **十、微服务基础**

### **1. 服务发现（Eureka）**

#### **概念**

管理微服务实例的注册与发现。

#### **定义**

- Eureka Server：注册中心
- Eureka Client：服务提供者与消费者

#### **语法**

java

复制

```
// 启动类注解
@SpringBootApplication
@EnableEurekaServer
public class EurekaServerApplication { ... }

// 客户端配置
eureka:
  client:
    service-url:
      defaultZone: http://localhost:8761/eureka
```

#### **作用**

动态扩展服务实例，实现负载均衡。

#### **案例**

消费者调用服务：

java

复制

```
@RestController
public class ConsumerController {
    @Autowired
    private RestTemplate restTemplate;

    @GetMapping("/user/{id}")
    public User getUser(@PathVariable Long id) {
        return restTemplate.getForObject("http://user-service/user/" + id, User.class);
    }
}
```

------

**持续补充提示**：

- 如需更多模块（如Spring Cloud配置中心、熔断器Hystrix），请具体说明。
- 项目实战部分可扩展数据库设计、API文档（Swagger）等内容。





## **十一、设计模式**

### **1. 单例模式（Singleton）**

#### **概念**

确保一个类只有一个实例，并提供全局访问点。

#### **定义**

- 私有构造方法
- 静态方法提供实例

#### **语法**

java

复制

```
public class Singleton {
    private static Singleton instance;
    private Singleton() {} // 私有构造
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
// 使用
Singleton obj = Singleton.getInstance();
```

#### **作用**

节省资源，如数据库连接池、配置管理。

#### **案例**

日志工具类单例：

java

复制

```
public class Logger {
    private static Logger instance;
    private Logger() {}
    public static synchronized Logger getInstance() {
        if (instance == null) {
            instance = new Logger();
        }
        return instance;
    }
    public void log(String message) {
        System.out.println("[LOG] " + message);
    }
}
```

------

### **2. 工厂模式（Factory）**

#### **概念**

通过工厂类创建对象，隐藏具体实现细节。

#### **定义**

- 简单工厂：一个方法创建多种对象
- 工厂方法：每个产品对应一个工厂

#### **语法**

java

复制

```
interface Shape {
    void draw();
}
class Circle implements Shape {
    public void draw() { System.out.println("画圆形"); }
}
class ShapeFactory {
    public Shape createShape(String type) {
        if ("circle".equals(type)) {
            return new Circle();
        }
        return null;
    }
}
// 使用
Shape shape = new ShapeFactory().createShape("circle");
```

#### **作用**

解耦对象创建与使用，增强扩展性。

#### **案例**

数据库连接工厂：

java

复制

```
public class ConnectionFactory {
    public static Connection getConnection(String dbType) {
        if ("mysql".equals(dbType)) {
            return DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb");
        } else if ("oracle".equals(dbType)) {
            return DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:orcl");
        }
        throw new IllegalArgumentException("不支持的数据库类型");
    }
}
```

------

## **十二、测试框架**

### **1. JUnit单元测试**

#### **概念**

Java标准单元测试框架，用于验证代码逻辑正确性。

#### **定义**

- 测试方法使用`@Test`注解
- 断言方法：`assertEquals`, `assertTrue`

#### **语法**

java

复制

```
public class CalculatorTest {
    @Test
    public void testAdd() {
        Calculator calc = new Calculator();
        assertEquals(5, calc.add(2, 3));
    }
}
```

#### **作用**

自动化测试，确保代码修改后功能正常。

#### **案例**

测试字符串反转：

java

复制

```
@Test
public void testReverse() {
    String input = "hello";
    String reversed = StringUtils.reverse(input);
    assertEquals("olleh", reversed);
}
```

------

### **2. Mockito模拟测试**

#### **概念**

模拟依赖对象的行为，隔离测试目标代码。

#### **定义**

- `@Mock`：创建模拟对象
- `@InjectMocks`：注入依赖

#### **语法**

java

复制

```
public class UserServiceTest {
    @Mock
    private UserDao userDao;
    @InjectMocks
    private UserService userService;
    
    @Before
    public void setup() {
        MockitoAnnotations.initMocks(this);
    }
    
    @Test
    public void testFindUser() {
        Mockito.when(userDao.findById(1)).thenReturn(new User("Alice"));
        User user = userService.findUser(1);
        assertEquals("Alice", user.getName());
    }
}
```

#### **作用**

解决测试中的外部依赖问题，提升测试速度。

#### **案例**

模拟数据库查询异常：

java

复制

```
@Test(expected = RuntimeException.class)
public void testFindUserWithException() {
    Mockito.when(userDao.findById(1)).thenThrow(new RuntimeException("数据库错误"));
    userService.findUser(1);
}
```

------

## **十三、构建工具**

### **1. Maven依赖管理**

#### **概念**

自动化构建工具，管理项目依赖和生命周期。

#### **定义**

- `pom.xml`：定义项目依赖、插件、仓库
- 生命周期：`clean`, `compile`, `package`, `install`

#### **语法**

xml

复制

```
<!-- pom.xml示例 -->
<dependencies>
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>8.0.25</version>
    </dependency>
</dependencies>
```



运行 HTML

#### **作用**

自动下载和管理Jar包，统一项目结构。

#### **案例**

构建Spring Boot项目： 构建 Spring Boot 项目：

xml

复制

```
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.5.4</version>
</parent>
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
</dependencies>
```



运行 HTML

------

### **2. Gradle构建脚本**

#### **概念**

基于Groovy的灵活构建工具，支持增量编译。

#### **定义**

- `build.gradle`：定义任务、依赖、插件
- 语法简洁，执行效率高

#### **语法**

groovy 古怪

复制

```
plugins {
    id 'java'
}
repositories {
    mavenCentral()
}
dependencies {
    implementation 'com.google.guava:guava:30.1.1-jre'
}
```

#### **作用**

替代Maven，适用于复杂项目构建。

#### **案例**

创建可执行Jar：

groovy 古怪

复制

```
jar {
    manifest {
        attributes 'Main-Class': 'com.example.Main'
    }
}
```

------

## **十四、日志框架**

### **1. Log4j2配置 1. 部署 log4j2**

#### **概念**

高性能日志记录工具，支持多种输出格式和级别。

#### **定义**

- 日志级别：`TRACE`, `DEBUG`, `INFO`, `WARN`, `ERROR`, `FATAL`
- 输出目标：控制台、文件、数据库

#### **语法**

xml

复制

```
<!-- log4j2.xml配置 -->
<Configuration>
    <Appenders>
        <Console name="Console" target="SYSTEM_OUT">
            <PatternLayout pattern="%d{HH:mm:ss} [%t] %-5level %logger{36} - %msg%n"/>
        </Console>
    </Appenders>
    <Loggers>
        <Root level="info">
            <AppenderRef ref="Console"/>
        </Root>
    </Loggers>
</Configuration>
```



运行 HTML

#### **作用**

记录程序运行状态，便于调试和监控。

#### **案例**

记录异常日志：

java

复制

```
public class UserService {
    private static final Logger logger = LogManager.getLogger(UserService.class);
    public void saveUser(User user) {
        try {
            // 业务代码
        } catch (Exception e) {
            logger.error("保存用户失败", e);
        }
    }
}
```

------

## **十五、Spring框架基础**

### **1. IoC（控制反转）**

#### **概念**

将对象创建和依赖注入交给容器管理。

#### **定义**

- `@Component`, `@Service`, `@Repository`
- `@Autowired`自动注入依赖

#### **语法**

java

复制

```
@Service
public class UserService {
    @Autowired
    private UserRepository userRepo;
    // 业务方法
}
```

#### **作用**

解耦组件依赖，提升可维护性。

#### **案例**

XML配置方式：

xml

复制

```
<bean id="userService" class="com.example.UserService">
    <property name="userRepo" ref="userRepository"/>
</bean>
<bean id="userRepository" class="com.example.UserRepositoryImpl"/>
```



运行 HTML

------

### **2. AOP（面向切面编程）**

#### **概念**

通过切面横向增强业务方法（如日志、事务）。

#### **定义**

- 切点（Pointcut）：定义拦截规则
- 通知（Advice）：前置、后置、环绕等增强逻辑

#### **语法**

java

复制

```
@Aspect
@Component
public class LogAspect {
    @Before("execution(* com.example.service.*.*(..))")
    public void logBefore(JoinPoint joinPoint) {
        System.out.println("方法执行前: " + joinPoint.getSignature().getName());
    }
}
```

#### **作用**

分离横切关注点，避免代码重复。

#### **案例**

事务管理切面：

java

复制

```
@Around("@annotation(org.springframework.transaction.annotation.Transactional)")
public Object manageTransaction(ProceedingJoinPoint pjp) throws Throwable {
    try {
        beginTransaction();
        Object result = pjp.proceed();
        commitTransaction();
        return result;
    } catch (Exception e) {
        rollbackTransaction();
        throw e;
    }
}
```

------

## **十六、项目实战扩展**

### **1. 电商系统订单模块**

#### **技术栈**

- 分布式事务：Seata
- 消息队列：RocketMQ保证最终一致性

#### **核心逻辑**

java

复制

```
public void createOrder(Order order) {
    // 1. 扣减库存（调用库存服务）
    // 2. 生成订单（本地事务）
    // 3. 发送支付消息到MQ
    // 4. 支付服务消费消息，更新订单状态
}
```

------

### **2. 博客系统全文搜索**

#### **技术栈**

- Elasticsearch
- Spring Data Elasticsearch

#### **代码示例**

java

复制

```
@Document(indexName = "articles")
public class Article {
    @Id
    private String id;
    @Field(type = FieldType.Text, analyzer = "ik_max_word")
    private String content;
    // Getters and Setters
}

public interface ArticleRepository extends ElasticsearchRepository<Article, String> {
    List<Article> findByContent(String keyword);
}
```

------

**后续补充方向**：

- **微服务架构**：Spring Cloud Alibaba（Nacos, Sentinel）
- **容器化部署**：Dockerfile编写、Kubernetes Pod配置
- **性能优化**：JVM调优、数据库索引设计
- **安全进阶**：OAuth2.0认证、JWT令牌刷新机制





## **十七、高级框架整合**

### **1. Spring Boot自动配置**

#### **概念**

简化Spring应用初始搭建和配置，约定优于配置。

#### **定义**

- 启动类注解`@SpringBootApplication`
- 自动配置原理：`spring.factories` + `@Conditional`

#### **语法**

java

复制

```
@SpringBootApplication
public class MyApp {
    public static void main(String[] args) {
        SpringApplication.run(MyApp.class, args);
    }
}
```

#### **作用**

快速创建独立运行、生产级的Spring应用。

#### **案例**

整合MyBatis：

yaml

复制

```
# application.yml
mybatis:
  mapper-locations: classpath:mapper/*.xml
  configuration:
    map-underscore-to-camel-case: true
```

------

### **2. Spring Security安全控制 2.弹簧安全控制**

#### **概念**

提供身份验证（Authentication）和授权（Authorization）功能。

#### **定义**

- 核心过滤器链：`UsernamePasswordAuthenticationFilter`、`BasicAuthenticationFilter`
- 权限注解：`@PreAuthorize`, `@PostAuthorize`

#### **语法**

java

复制

```
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http.authorizeRequests()
            .antMatchers("/admin/**").hasRole("ADMIN")
            .anyRequest().authenticated()
            .and().formLogin();
    }
}
```

#### **作用**

保护Web接口，防止未授权访问。

#### **案例**

自定义用户认证：

java

复制

```
@Service
public class UserDetailsServiceImpl implements UserDetailsService {
    @Autowired
    private UserRepository userRepo;
    
    @Override
    public UserDetails loadUserByUsername(String username) {
        User user = userRepo.findByUsername(username);
        return new org.springframework.security.core.userdetails.User(
            user.getUsername(), 
            user.getPassword(), 
            AuthorityUtils.createAuthorityList("ROLE_USER")
        );
    }
}
```

------

## **十八、缓存技术**

### **1. Redis缓存集成**

#### **概念**

内存数据存储，支持高速读写和多种数据结构。

#### **定义**

- 数据类型：String, Hash, List, Set, SortedSet
- 缓存策略：TTL过期、LRU淘汰

#### **语法**

java

复制

```
@Autowired
private RedisTemplate<String, Object> redisTemplate;

public void cacheUser(User user) {
    redisTemplate.opsForValue().set("user:" + user.getId(), user, 30, TimeUnit.MINUTES);
}

public User getUser(Long id) {
    return (User) redisTemplate.opsForValue().get("user:" + id);
}
```

#### **作用**

减轻数据库压力，提升高频数据访问速度。

#### **案例**

缓存商品详情：

java

复制

```
@Cacheable(value = "products", key = "#productId")
public Product getProductById(Long productId) {
    return productRepository.findById(productId).orElse(null);
}
```

------

### **2. 缓存雪崩解决方案**

#### **概念**

大量缓存同时失效，导致请求直接冲击数据库。

#### **定义**

- 随机过期时间：避免同一时间失效
- 熔断降级：Hystrix或Sentinel保护数据库

#### **语法**

java

复制

```
// 设置缓存时添加随机过期时间
int expireTime = 3600 + new Random().nextInt(300); // 3600~3900秒
redisTemplate.expire(key, expireTime, TimeUnit.SECONDS);
```

#### **作用**

保障系统高可用性，防止级联故障。

#### **案例**

使用Sentinel限流：

java

复制

```
@SentinelResource(value = "productQuery", blockHandler = "handleBlock")
public Product queryProduct(Long id) {
    // 查询逻辑
}
public Product handleBlock(Long id, BlockException ex) {
    return new Product("默认商品"); // 降级响应
}
```

------

## **十九、消息队列**

### **1. RabbitMQ消息收发**

#### **概念**

AMQP协议实现的消息中间件，支持消息路由和持久化。

#### **定义**

- 核心概念：Exchange（交换机）、Queue（队列）、Binding（绑定）
- 消息确认机制：ACK/NACK

#### **语法**

java

复制

```
// 发送消息
rabbitTemplate.convertAndSend("order.exchange", "order.create", order);

// 接收消息
@RabbitListener(queues = "order.queue")
public void handleOrder(Order order) {
    // 处理订单
}
```

#### **作用**

解耦系统组件，实现异步处理和削峰填谷。

#### **案例**

订单超时取消：

java

复制

```
// 下单时发送延迟消息
rabbitTemplate.convertAndSend(
    "order.exchange", 
    "order.delay", 
    order, 
    message -> {
        message.getMessageProperties().setDelay(30 * 60 * 1000); // 30分钟延迟
        return message;
    }
);
```

------

### **2. Kafka高吞吐处理**

#### **概念**

分布式流处理平台，适用于大数据实时处理。

#### **定义**

- 主题（Topic）、分区（Partition）、消费者组（Consumer Group）
- 副本机制保障高可用

#### **语法**

java

复制

```
// 生产者
@Autowired
private KafkaTemplate<String, String> kafkaTemplate;
kafkaTemplate.send("log.topic", "用户登录：" + username);

// 消费者
@KafkaListener(topics = "log.topic", groupId = "log-group")
public void processLog(String message) {
    System.out.println("收到日志：" + message);
}
```

#### **作用**

处理日志收集、实时监控等大数据场景。

#### **案例**

用户行为追踪：

java

复制

```
// 前端埋点发送事件
navigator.sendBeacon('/track', JSON.stringify({
    event: 'click',
    element: 'buy_button',
    userId: '123'
}));

// 后端写入Kafka
@PostMapping("/track")
public void trackEvent(@RequestBody Event event) {
    kafkaTemplate.send("user_behavior", event.getUserId(), event);
}
```

------

## **二十、容器化与部署**

### **1. Docker容器打包**

#### **概念**

轻量级虚拟化技术，打包应用及其依赖环境。

#### **定义**

- 镜像（Image）：只读模板
- 容器（Container）：镜像的运行实例

#### **语法**

dockerfile docker 文件

复制

```
# Dockerfile示例
FROM openjdk:11-jre-slim
COPY target/myapp.jar /app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

#### **作用**

实现环境一致性，简化部署流程。

#### **案例**

构建并运行镜像：

bash 敲击

复制

```
docker build -t myapp:1.0 .
docker run -d -p 8080:8080 myapp:1.0
```

------

### **2. Kubernetes集群管理**

#### **概念**

容器编排系统，实现自动化部署、扩缩容。

#### **定义**

- Pod：最小调度单元，包含一个或多个容器
- Service：定义Pod访问策略

#### **语法**

yaml

复制

```
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: myapp
        image: myapp:1.0
        ports:
        - containerPort: 8080
```

#### **作用**

管理微服务集群，保障高可用和弹性伸缩。

#### **案例**

滚动更新策略：

yaml

复制

```
spec:
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25%
```

------

## **二十一、前端技术整合**

### **1. Vue.js前后端分离**

#### **概念**

前端框架，通过API与Java后端交互。

#### **定义**

- 核心特性：数据绑定、组件化、路由（Vue Router）
- 状态管理：Vuex

#### **语法**

javascript

复制

```
// API调用示例
axios.get('/api/users')
  .then(response => {
    this.users = response.data;
  })
  .catch(error => {
    console.error('请求失败:', error);
  });
```

#### **作用**

构建响应式单页应用（SPA），提升用户体验。

#### **案例**

用户列表展示：

vue 观

复制

```
<template>
  <ul>
    <li v-for="user in users" :key="user.id">{{ user.name }}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      users: []
    };
  },
  mounted() {
    this.fetchUsers();
  },
  methods: {
    fetchUsers() {
      axios.get('/api/users').then(res => this.users = res.data);
    }
  }
};
</script>
```

------

### **2. Webpack构建优化**

#### **概念**

前端资源模块化打包工具。

#### **定义**

- Loader：处理CSS、图片等非JS资源
- Plugin：扩展功能（如代码压缩）

#### **语法**

javascript

复制

```
// webpack.config.js
module.exports = {
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader']
      }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({ template: './src/index.html' })
  ]
};
```

#### **作用**

优化前端资源加载，支持模块化开发。

#### **案例**

代码分割提升性能：

javascript

复制

```
optimization: {
  splitChunks: {
    chunks: 'all',
    cacheGroups: {
      vendor: {
        test: /[\\/]node_modules[\\/]/,
        name: 'vendors'
      }
    }
  }
}
```

------

## **二十二、持续集成与交付**

### **1. Jenkins流水线**

#### **概念**

自动化构建、测试、部署的CI/CD工具。

#### **定义**

- Pipeline脚本：`Jenkinsfile`定义构建流程
- 阶段（Stage）：构建、测试、部署

#### **语法**

groovy 古怪

复制

```
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }
    }
}
```

#### **作用**

实现自动化软件交付流程。

#### **案例**

邮件通知构建结果：

groovy 古怪

复制

```
post {
    always {
        emailext body: '构建详情：${BUILD_URL}',
                 subject: '构建通知: ${JOB_NAME} - ${BUILD_STATUS}',
                 to: 'dev-team@example.com'
    }
}
```

------

### **2. SonarQube代码检查**

#### **概念**

静态代码分析平台，检测代码质量。

#### **定义**

- 检测项：代码重复率、复杂度、安全漏洞
- 质量阈：设定通过标准

#### **语法**

xml

复制

```
<!-- pom.xml配置 -->
<plugin>
    <groupId>org.sonarsource.scanner.maven</groupId>
    <artifactId>sonar-maven-plugin</artifactId>
    <version>3.9.1.2184</version>
</plugin>
```



运行 HTML

#### **作用**

提升代码可维护性，遵循最佳实践。

#### **案例**

运行代码分析：

bash 敲击

复制

```
mvn sonar:sonar -Dsonar.projectKey=my_project
```

------

## **二十三、扩展学习建议**

1. **源码阅读**
   - JDK核心类库（如HashMap、ArrayList）
   - Spring框架核心模块（如IoC容器、AOP实现）
2. **性能调优**
   - JVM参数优化（堆内存、GC策略）
   - SQL执行计划分析与索引优化
3. **架构设计**
   - DDD（领域驱动设计）
   - CQRS（命令查询职责分离）
4. **新技术跟踪**
   - GraalVM原生镜像
   - Quarkus微服务框架



## **二十四、Java模块系统（JPMS）**

### **1. 模块化概念**

#### **概念**

Java 9引入的模块系统，用于封装和明确依赖关系。

#### **定义**

- **模块**：包含代码和资源的独立单元，通过`module-info.java`声明。
- **导出包**：明确模块对外暴露的API。

#### **语法**

java

复制

```
// module-info.java
module com.example.myapp {
    requires java.base;          // 依赖基础模块
    requires java.sql;           // 依赖SQL模块
    exports com.example.myapp.api; // 导出API包
}
```

#### **作用**

增强封装性，减少类路径冲突，优化启动性能。

#### **案例**

创建模块化应用：

1. 项目结构：

   复制

   ```
   src/
     com.example.myapp/
       module-info.java
       com/example/myapp/Main.java
   ```

2. 编译运行：

   bash 敲击

   复制

   ```
   javac -d out --module-source-path src -m com.example.myapp
   java --module-path out -m com.example.myapp/com.example.myapp.Main
   ```

------

## **二十五、响应式编程**

### **1. Reactor框架 1.反应堆框架**

#### **概念**

基于Reactive Streams规范的响应式编程库，支持非阻塞异步数据流处理。

#### **定义**

- **Mono**：0-1个元素的异步序列。
- **Flux**：0-N个元素的异步序列。

#### **语法**

java

复制

```
Flux<String> flux = Flux.just("Java", "Python", "C++")
                        .filter(s -> s.startsWith("J"))
                        .map(String::toUpperCase);

flux.subscribe(
    data -> System.out.println("收到数据: " + data), // 成功处理
    error -> System.err.println("错误: " + error),  // 错误处理
    () -> System.out.println("流处理完成")           // 完成回调
);
```

#### **作用**

提升高并发场景下的资源利用率，适用于实时数据处理。

#### **案例**

WebFlux构建非阻塞API：

java

复制

```
@RestController
public class UserController {
    @GetMapping("/users")
    public Flux<User> getUsers() {
        return userRepository.findAll(); // 返回响应式流
    }
}
```

------

## **二十六、RESTful API进阶设计**

### **1. HATEOAS（超媒体驱动）**

#### **概念**

API响应中嵌入资源链接，客户端通过链接导航。

#### **定义**

- 使用`Link`对象描述资源关系。
- 遵循HAL（Hypertext Application Language）格式。

#### **语法**

java

复制

```
@GetMapping("/users/{id}")
public EntityModel<User> getUser(@PathVariable Long id) {
    User user = userService.findById(id);
    EntityModel<User> model = EntityModel.of(user);
    model.add(linkTo(methodOn(UserController.class).getUser(id)).withSelfRel());
    model.add(linkTo(methodOn(UserController.class).getAllUsers()).withRel("users"));
    return model;
}
```

#### **作用**

提升API可发现性和自描述性，降低客户端耦合。

#### **案例**

响应示例：

json

复制

```
{
  "id": 1,
  "name": "Alice",
  "_links": {
    "self": { "href": "/users/1" },
    "users": { "href": "/users" }
  }
}
```

------

## **二十七、微服务监控**

### **1. Spring Boot Actuator 1.Spring Boot 执行器**

#### **概念**

提供生产级监控端点，暴露应用健康信息、指标等。

#### **定义**

- **端点**：`/actuator/health`, `/actuator/metrics`等。
- **定制端点**：自定义监控指标。

#### **语法**

yaml

复制

```
# application.yml
management:
  endpoints:
    web:
      exposure:
        include: "*"  # 开放所有端点
```

#### **作用**

实时监控应用状态，快速定位问题。

#### **案例**

自定义健康检查：

java

复制

```
@Component
public class CustomHealthIndicator implements HealthIndicator {
    @Override
    public Health health() {
        boolean isHealthy = checkServiceStatus();
        if (isHealthy) {
            return Health.up().withDetail("Service", "Available").build();
        }
        return Health.down().withDetail("Error", "Service Unavailable").build();
    }
}
```

------

### **2. Prometheus集成 2.普罗米修斯集成**

#### **概念**

开源监控系统，通过拉取机制收集指标数据。

#### **定义**

- **Metrics**：应用性能指标（如请求数、耗时）。
- **Grafana**：可视化监控数据。

#### **语法**

xml

复制

```
<!-- Maven依赖 -->
<dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-registry-prometheus</artifactId>
</dependency>
```



运行 HTML

#### **作用**

实现多维度的应用性能监控（APM）。

#### **案例**

配置Prometheus抓取数据：

yaml

复制

```
# prometheus.yml
scrape_configs:
  - job_name: 'spring-app'
    metrics_path: '/actuator/prometheus'
    static_configs:
      - targets: ['localhost:8080']
```

------

## **二十八、数据库高级主题**

### **1. 事务管理（ACID）**

#### **概念**

确保数据库操作的原子性、一致性、隔离性、持久性。

#### **定义**

- **声明式事务**：通过`@Transactional`注解管理。
- **传播行为**：如`REQUIRED`, `REQUIRES_NEW`。

#### **语法**

java

复制

```
@Transactional(propagation = Propagation.REQUIRED, isolation = Isolation.READ_COMMITTED)
public void transferMoney(Account from, Account to, BigDecimal amount) {
    from.debit(amount);
    to.credit(amount);
}
```

#### **作用**

保障复杂业务操作的数据一致性。

#### **案例**

分布式事务（Seata）：

java

复制

```
@GlobalTransactional
public void placeOrder(Order order) {
    reduceStock(order);  // 调用库存服务
    createOrder(order);  // 本地事务
}
```

------

## **二十九、安全进阶**

### **1. OAuth2.0授权**

#### **概念**

开放授权标准，允许第三方应用有限访问用户资源。

#### **定义**

- **授权模式**：授权码模式、密码模式、客户端模式。
- **角色**：资源服务器、授权服务器、客户端。

#### **语法**

java

复制

```
@Configuration
@EnableAuthorizationServer
public class AuthServerConfig extends AuthorizationServerConfigurerAdapter {
    @Override
    public void configure(ClientDetailsServiceConfigurer clients) throws Exception {
        clients.inMemory()
            .withClient("client-id")
            .secret("{noop}client-secret")
            .authorizedGrantTypes("authorization_code", "refresh_token")
            .scopes("read", "write");
    }
}
```

#### **作用**

实现安全的第三方应用授权机制。

#### **案例**

获取授权码流程：

1. 用户访问授权端点：`/oauth/authorize?response_type=code&client_id=client-id&redirect_uri=...`

2. 授权后重定向到回调地址，附带`code`参数。

3. 客户端使用`code`换取访问令牌：

   bash 敲击

   复制

   ```
   curl -X POST -u "client-id:client-secret" \
        -d "grant_type=authorization_code&code=xxx&redirect_uri=..." \
        http://localhost:8080/oauth/token
   ```

------

## **三十、扩展学习资源**

1. **书籍推荐**
   - 《Effective Java》—— Joshua Bloch
     《高效 Java》-- Joshua Bloch
   - 《Spring实战》—— Craig Walls
   - 《微服务架构设计模式》—— Chris Richardson
2. **在线课程**
   - Coursera: Java Programming and Software Engineering Fundamentals
     Coursera：Java 编程和软件
   - Udemy: Spring Boot Microservices with Spring Cloud
     Udemy：使用 Spring Cloud 的 Spring Boot 微服务
3. **开源项目**
   - Spring PetClinic（Spring官方示例）
   - Apache Shiro（安全框架）
   - Elasticsearch（搜索与分析引擎）
4. **社区与论坛**
   - Stack Overflow 堆栈溢出
   - GitHub Discussions GitHub 讨论
   - Reddit的r/java和r/programming板块