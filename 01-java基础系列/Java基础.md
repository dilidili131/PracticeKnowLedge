# Java基础

## 1.JDK和JRE有什么区别

- JDK：Java development Kit ，Java开发工具包，提供java开发环境和运行环境。

- JRE：Java Runtime Environment ，为java运行提供所需环境。


​		具体来说 JDK 其实包含了 JRE，同时还包含了编译 Java 源码的编译器 Javac，还包含了很多 Java 程序调试和分析的工具。简单来说：如果你需要运行 Java 程序，只需安装 JRE 就可以了，如果你需要编写 Java 程序，需要安装 JDK。

## 2.==和equals()的区别是什么



## 3.两个对象的 hashCode() 相同，则 equals() 也一定为 true，对吗？



## 4.final在java中有什么作用

- final修饰的类叫做最终类，不能被继承
- final修饰的方法不能被重写
- final修饰的变量叫常量，常量必须初始化，初始化之后至不能被修改。

## 5.Java中的Math.round()函数取整规则

 		四舍五入

- Math.round(-1.4) = -1
- Math.round(-1.5) = -1
- Math.round(-1.6) = -2
- Math.round(1.4) = 1
- Math.round(1.5) = 2
- Math.round(1.6) = 2

## 6.String属于基础数据类型吗

​		不属于，String属于类

​		基础数据类型有八种：byte boolean char short long int float double

## 7.Java中操作字符串都有哪些类

​		String： String声明的是不可变的对象，每次操作都会生成新的对象，然后将指针指向新的String对象，StringBuffer和StringBuilder可以再原有对象的基础上进行操作，所以经常改变字符串内容的情况下最好不要使用String。

​		StringBuffer：（线程安全的）

​		StringBuilder：（线程不安全的）

​		但是StringBuilder的心更难高于StringBuffer，所以单线程环境下推荐使用StringBuilder，多线程推荐使用StringBuffer。

## 8.String str="i"与 String str=new String("i")一样吗？

​		不一样，因为内存的分配方式不一样。String str="i"的方式，Java 虚拟机会将其分配到常量池中；而 String str=new String("i") 则会被分到堆内存中。

## 9.字符串反转

​		使用 StringBuilder 或者 stringBuffer 的 reverse() 方法。

```java
/ StringBuffer reverse
StringBuffer stringBuffer = new StringBuffer();
stringBuffer. append("abcdefg");
System. out. println(stringBuffer. reverse()); // gfedcba
// StringBuilder reverse
StringBuilder stringBuilder = new StringBuilder();
stringBuilder. append("abcdefg");
System. out. println(stringBuilder. reverse()); // gfedcba
```

## 10.String 类常用的方法。

- indexOf()：返回指定字符的索引
- charAt()：返回指定索引的字符
- replace()：字符串替换
- trim()：去除字符串两端空白
- split()：分割字符串，返回一个分隔后的字符串数组
- getBytes()：返回字符串的Byte类型数组
- length()：返回字符串长度
- toUpperCase()：字符串转换成大写
- toLowerCase()：字符串转换成小写
- subString()：截取字符串
- equals()：字符串比较

## 11. 抽象类必须要有抽象方法吗？

​		不需要，抽象类不一定非要有抽象方法。

​		示例代码：抽象类并没有抽象方法但完全可以正常运行。

```java
abstract class Cat {
    public static void sayHi() {
        System. out. println("hi~");
    }
}
```

## 12. 普通类和抽象类有哪些区别？

- 普通类不能包含抽象方法，抽象类可以包含抽象方法。
- 抽象类不能直接实例化，普通类可以直接实例化。

## 13.抽象类能使用 final 修饰吗？

​		不能，定义抽象类就是让其他类继承的，如果定义为 final 该类就不能被继承，这样彼此就会产生矛盾，所以 final 不能修饰抽象类，如下图所示，编辑器也会提示错误信息：

## 14. 接口和抽象类有什么区别？

- 定义抽象类的关键字是abstract class，而定义接口的关键字是interface
- 继承抽象类的关键字是extends，而实现接口的关键字是implements
- 继承抽象类支持单继承，而实现接口可以多实现
- 抽象类中可以有构造方法，而接口中不可以有构造方法
- 抽象类中可以有成员变量，而接口中只能有常量
- 抽象类中可以有成员方法，而接口中只能有抽象方法
- 抽象类中增加方法可以不影响子类，而接口中增加方法通常都影响子类
- 接口中的方法默认使用 public 修饰；抽象类中的方法可以是任意访问修饰符。
- 从jdk1.8开始允许接口中出现非抽象方法，但需要使用default关键字修饰。

##  15. Java 中 IO 流分为几种？

​		按功能来分：输入流（input）、输出流（output）。

​		按类型来分：字节流和字符流。

​		字节流和字符流的区别是：字节流按 8 位传输以字节为单位输入输出数据，字符流按 16 位传输以字符为单位输入输出数据。

## 16. BIO、NIO、AIO 有什么区别？

- BIO：Block IO 同步阻塞式 IO，就是我们平常使用的传统 IO，它的特点是模式简单使用方便，并发处理能力低。
- NIO：Non IO 同步非阻塞 IO，是传统 IO 的升级，客户端和服务器端通过 Channel（通道）通讯，实现了多路复用。
- AIO：Asynchronous IO 是 NIO 的升级，也叫 NIO2，实现了异步非堵塞 IO ，异步 IO 的操作基于事件和回调机制。

## 17. Files的常用方法都有哪些？

- Files. exists()：检测文件路径是否存在。
- Files. createFile()：创建文件。
- Files. createDirectory()：创建文件夹。
- Files. delete()：删除一个文件或目录。
- Files. copy()：复制文件。
- Files. move()：移动文件。
- Files. size()：查看文件个数。
- Files. read()：读取文件。
- Files. write()：写入文件。

# 容器

## 1. Java 容器都有哪些？

- collection
  - List
    - ArrayList
    - LinkedList
    - Vector
    - Stack
  - Set
    - HashSet
    - LinkedHashSet
    - TreeSet
- Map
  - HashMap
    - LinkedHashMap
  - TreeMap
  - ConcurrentHashMap
  - HashTable

## 2. Collection 和 Collections 有什么区别？

- Collection 是一个集合接口，它提供了对集合对象进行基本操作的通用接口方法，所有集合都是它的子类，比如 List、Set 等。
- Collections 是一个包装类，包含了很多静态方法，**不能被实例化**，就像一个工具类，比如提供的排序方法： Collections. sort(list)。

## 3. List、Set、Map 之间的区别是什么？

|      |             | 元素有序           | 允许元素重复             |
| ---- | ----------- | ------------------ | ------------------------ |
| List |             | 是                 | 是                       |
| Set  | AbstractSet | 否                 | 否                       |
|      | HashSet     | 否                 | 否                       |
|      | TreeSet     | 是（用二叉树排序） | 否                       |
| Map  | AbstractMap | 否                 | key必须唯一，value可重复 |
|      | HashMap     | 否                 | key必须唯一，value可重复 |
|      | TreeMap     | 是（用二叉树排序） | key必须唯一，value可重复 |

## 4. HashMap 和 Hashtable 有什么区别？

- 存储：HashMap 允许 key 和 value 为 null，而 Hashtable 不允许。
- 线程安全：Hashtable 是线程安全的，而 HashMap 是非线程安全的。
- 推荐使用：在 Hashtable 的类注释可以看到，**Hashtable 是保留类不建议使用**，**推荐在单线程环境下使用 HashMap 替代，如果需要多线程使用则用 ConcurrentHashMap 替代**。

## 5. 如何决定使用 HashMap 还是 TreeMap？

​		对于在 Map 中插入、删除、定位一个元素这类操作，HashMap 是最好的选择，因为相对而言 HashMap 的插入会更快，但如果你要对一个 key 集合进行有序的遍历，那 TreeMap 是更好的选择。

## 6. 说一下 HashMap 的实现原理？

​		HashMap 基于 Hash 算法实现的，我们通过 put(key,value)存储，get(key)来获取。当传入 key 时，HashMap 会根据 key. hashCode() 计算出 hash 值，根据 hash 值将 value 保存在 bucket 里。当计算出的 hash 值相同时，我们称之为 hash 冲突，HashMap 的做法是用链表和红黑树存储相同 hash 值的 value。当 hash 冲突的个数比较少时，使用链表否则使用红黑树。

## 7. 说一下 HashSet 的实现原理？

​		HashSet 是基于 HashMap 实现的，HashSet 底层使用 HashMap 来保存所有元素，因此 HashSet 的实现比较简单，相关 HashSet 的操作，基本上都是直接调用底层 HashMap 的相关方法来完成，HashSet 不允许重复的值。

## 8. ArrayList 和 LinkedList 的区别是什么？

- 数据结构实现：ArrayList 是动态数组的数据结构实现，而 LinkedList 是双向链表的数据结构实现。
- 随机访问效率：ArrayList 比 LinkedList 在随机访问的时候效率要高，因为 LinkedList 是线性的数据存储方式，所以需要移动指针从前往后依次查找。
- 增加和删除效率：在非首尾的增加和删除操作，LinkedList 要比 ArrayList 效率要高，因为 ArrayList 增删操作要影响数组内的其他数据的下标。

​		综合来说，在需要频繁读取集合中的元素时，更推荐使用 ArrayList，而在插入和删除操作较多时，更推荐使用 LinkedList。

## 9. 如何实现数组和 List 之间的转换？

- 数组转 List：使用 Arrays. asList(array) 进行转换。
- List 转数组：使用 List 自带的 toArray() 方法。

代码示例：

```java
// list to array
List<String> list = new ArrayList<String>();
list. add("王磊");
list. add("的博客");
list. toArray();
// array to list
String[] array = new String[]{"王磊","的博客"};
Arrays. asList(array);
```

## 10. ArrayList 和 Vector 的区别是什么？

- 线程安全：Vector 使用了 Synchronized 来实现线程同步，是线程安全的，而 ArrayList 是非线程安全的。
- 性能：ArrayList 在性能方面要优于 Vector。
- 扩容：ArrayList 和 Vector 都会根据实际的需要动态的调整容量，只不过在 Vector 扩容每次会增加 1 倍，而 ArrayList 只会增加 50%。

## 11. Array 和 ArrayList 有何区别？

- **Array 可以存储基本数据类型和对象**，**ArrayList 只能存储对象**。
- Array 是指定固定大小的，而 ArrayList 大小是自动扩展的。
- Array 内置方法没有 ArrayList 多，比如 addAll、removeAll、iteration 等方法只有 ArrayList 有。

## 12. 在 Queue 中 poll()和 remove()有什么区别？

- 相同点：都是返回第一个元素，并在队列中删除返回的对象。
- 不同点：如果没有元素 poll()会返回 null，而 remove()会直接抛出 NoSuchElementException 异常。

## 13. 哪些集合类是线程安全的？

​		Vector、Hashtable、Stack 都是线程安全的，而像 HashMap 则是非线程安全的，不过在 JDK 1.5 之后随着 Java. util. concurrent 并发包的出现，它们也有了自己对应的线程安全类，比如 HashMap 对应的线程安全类就是 ConcurrentHashMap。

## 14. 迭代器 Iterator 是什么？

​		Iterator 接口提供遍历任何 Collection 的接口。我们可以从一个 Collection 中使用迭代器方法来获取迭代器实例。迭代器取代了 Java 集合框架中的 Enumeration，迭代器允许调用者在迭代过程中移除元素。

## 15. Iterator 怎么使用？有什么特点？

```java
List<String> list = new ArrayList<>();
Iterator<String> it = list. iterator();
while(it. hasNext()){
  String obj = it. next();
  System. out. println(obj);
}
```

​		Iterator 的特点是更加安全，因为它可以确保，在当前遍历的集合元素被更改的时候，就会抛出 ConcurrentModificationException 异常。

## 16. Iterator 和 ListIterator 有什么区别？

- Iterator 可以遍历 Set 和 List 集合，而 ListIterator 只能遍历 List。
- Iterator 只能单向遍历，而 ListIterator 可以双向遍历（向前/后遍历）。
- ListIterator 从 Iterator 接口继承，然后添加了一些额外的功能，比如添加一个元素、替换一个元素、获取前面或后面元素的索引位置。

## 17. 怎么确保一个集合不能被修改？

​		可以使用 Collections. unmodifiableCollection(Collection c) 方法来创建一个只读集合，这样改变集合的任何操作都会抛出 Java. lang. UnsupportedOperationException 异常。

示例代码如下：

```java
List<String> list = new ArrayList<>();
list. add("x");
Collection<String> clist = Collections. unmodifiableCollection(list);
clist. add("y"); // 运行时此行报错
System. out. println(list. size());
```

# 多线程

## 1.并行和并发有什么区别？

- 并行：多个处理器或多核处理器同时处理多个任务。
- 并发：多个任务在同一个 CPU 核上，按细分的时间片轮流(交替)执行，从逻辑上来看那些任务是同时执行。

## 2.线程和进程的区别？

​		一个程序下至少有一个进程，一个进程下至少有一个线程，一个进程下也可以有多个线程来增加程序的执行速度。

## 3.守护线程是什么？

​		守护线程是运行在后台的一种特殊进程。它独立于控制终端并且周期性地执行某种任务或等待处理某些发生的事件。在 Java 中垃圾回收线程就是特殊的守护线程。

## 4.创建线程有哪几种方式？

创建线程有三种方式：

- 继承 Thread 重写 run 方法；
- 实现 Runnable 接口；
- 实现 Callable 接口。

## 5. 说一下 runnable 和 callable 有什么区别？

​		runnable 没有返回值，callable 可以拿到有返回值，callable 可以看作是 runnable 的补充。

## 6.线程有哪些状态？

线程的状态：

- NEW 尚未启动
- RUNNABLE 正在执行中
- BLOCKED 阻塞的（被同步锁或者IO锁阻塞）
- WAITING 永久等待状态
- TIMED_WAITING 等待指定的时间重新被唤醒的状态
- TERMINATED 执行完成

## 7.sleep() 和 wait() 有什么区别？

- 类的不同：sleep() 来自 Thread，wait() 来自 Object。
- 释放锁：sleep() 不释放锁；wait() 释放锁。
- 用法不同：sleep() 时间到会自动恢复；wait() 可以使用 notify()/notifyAll()直接唤醒。

。。。

。。。

。。。还有好多

# 反射(多线程还有好多)



## 1.什么是反射？

​		反射是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种动态获取的信息以及动态调用对象的方法的功能称为 Java 语言的反射机制。

## 2.什么是 Java 序列化？什么情况下需要序列化？

​		Java 序列化是为了保存各种对象在内存中的状态，并且可以把保存的对象状态再读出来。

​		以下情况需要使用 Java 序列化：

- 想把的内存中的对象状态保存到一个文件中或者数据库中时候；
- 想用套接字在网络上传送对象的时候；
- 想通过RMI（远程方法调用）传输对象的时候。

## 3.动态代理是什么？有哪些应用？

​		动态代理是运行时动态生成代理类。

​		动态代理的应用有 spring aop、hibernate 数据查询、测试框架的后端 mock、rpc，Java注解对象获取等。

## 4.怎么实现动态代理？

​		JDK 原生动态代理和 cglib 动态代理。JDK 原生动态代理是基于接口实现的，而 cglib 是基于继承当前类的子类实现的。

# 对象拷贝

## 1. 为什么要使用克隆？

​		克隆的对象可能包含一些已经修改过的属性，而 new 出来的对象的属性都还是初始化时候的值，所以当需要一个新的对象来保存当前对象的“状态”就靠克隆方法了。

## 2. 如何实现对象克隆？

- 实现 Cloneable 接口并重写 Object 类中的 clone() 方法。
- 实现 Serializable 接口，通过对象的序列化和反序列化实现克隆，可以实现真正的深度克隆。

## 3. 深拷贝和浅拷贝区别是什么？

- 浅克隆：当对象被复制时只复制它本身和其中包含的值类型的成员变量，而引用类型的成员对象并没有复制。
- 深克隆：除了对象本身被复制外，对象所包含的所有成员变量也将复制。

## 4.Java对象拷贝分类

- **对象拷贝**：这种方式会重新生成一个新的对象，生成的新对象与原来的对象没有任何关联。

- **引用拷贝**：和对象拷贝的不同之处在于，引用拷贝只会生成一个新的对象引用地址，但两个地址其最终指向的还是同一个对象

​		引用拷贝也就是我们常用的对象赋值，这种方式不会生成新的对象，只会在原对象上增加了一个新的对象引用，两个引用指向的对象还是是同一个；

​		java 对象默认的赋值方式都是引用拷贝，比如说下面代码对象赋值的过程就是引用拷贝：

```java
User user1 = new User();
User user2 = user1;
```

# Java Web

## 1. JSP 和 servlet 有什么区别？

​		JSP 是 servlet 技术的扩展，本质上就是 servlet 的简易方式。servlet 和 JSP 最主要的不同点在于，servlet 的应用逻辑是在 Java 文件中，并且完全从表示层中的 html 里分离开来，而 JSP 的情况是 Java 和 html 可以组合成一个扩展名为 JSP 的文件。JSP 侧重于视图，servlet 主要用于控制逻辑。

## 2.JSP 有哪些内置对象？作用分别是什么？

​		JSP 有 9 大内置对象：

- request：封装客户端的请求，其中包含来自 get 或 post 请求的参数；
- response：封装服务器对客户端的响应；
- pageContext：通过该对象可以获取其他对象；
- session：封装用户会话的对象；
- application：封装服务器运行环境的对象；
- out：输出服务器响应的输出流对象；
- config：Web 应用的配置对象；
- page：JSP 页面本身（相当于 Java 程序中的 this）；
- exception：封装页面抛出异常的对象。

## 3. 说一下 JSP 的 4 种作用域？

- page：代表与一个页面相关的对象和属性。
- request：代表与客户端发出的一个请求相关的对象和属性。一个请求可能跨越多个页面，涉及多个 Web 组件；需要在页面显示的临时数据可以置于此作用域。
- session：代表与某个用户与服务器建立的一次会话相关的对象和属性。跟某个用户相关的数据应该放在用户自己的 session 中。
- application：代表与整个 Web 应用程序相关的对象和属性，它实质上是跨越整个 Web 应用程序，包括多个页面、请求和会话的一个全局作用域。

## 4. session 和 cookie 有什么区别？

- 存储位置不同：session 存储在服务器端；cookie 存储在浏览器端。
- 安全性不同：cookie 安全性一般，在浏览器存储，可以被伪造和修改。
- 容量和个数限制：cookie 有容量限制，每个站点下的 cookie 也有个数限制。
- 存储的多样性：session 可以存储在 Redis 中、数据库中、应用程序中；而 cookie 只能存储在浏览器中。

## 5. 说一下 session 的工作原理？

​		session 的工作原理是客户端登录完成之后，服务器会创建对应的 session，session 创建完之后，会把 session 的 id 发送给客户端，客户端再存储到浏览器中。这样客户端每次访问服务器时，都会带着 sessionid，服务器拿到 sessionid 之后，在内存找到与之对应的 session 这样就可以正常工作了。

## 6. 如果客户端禁止 cookie 能实现 session 还能用吗？

​		可以用，session 只是依赖 cookie 存储 sessionid，如果 cookie 被禁用了，可以使用 url 中添加 sessionid 的方式保证 session 能正常使用。

## 7. spring mvc 和 struts 的区别是什么？

- 拦截级别：struts2 是类级别的拦截；spring mvc 是方法级别的拦截。
- 数据独立性：spring mvc 的方法之间基本上独立的，独享 request 和 response 数据，请求数据通过参数获取，处理结果通过 ModelMap 交回给框架，方法之间不共享变量；而 struts2 虽然方法之间也是独立的，但其所有 action 变量是共享的，这不会影响程序运行，却给我们编码和读程序时带来了一定的麻烦。
- 拦截机制：struts2 有以自己的 interceptor 机制，spring mvc 用的是独立的 aop 方式，这样导致struts2 的配置文件量比 spring mvc 大。
- 对 ajax 的支持：spring mvc 集成了ajax，所有 ajax 使用很方便，只需要一个注解 @ResponseBody 就可以实现了；而 struts2 一般需要安装插件或者自己写代码才行。

## 8. 如何避免 SQL 注入？

- 使用预处理 PreparedStatement。
- 使用正则表达式过滤掉字符中的特殊字符。

## 9. 什么是 XSS 攻击，如何避免？

​		XSS 攻击：即跨站脚本攻击，它是 Web 程序中常见的漏洞。原理是攻击者往 Web 页面里插入恶意的脚本代码（css 代码、Javascript 代码等），当用户浏览该页面时，嵌入其中的脚本代码会被执行，从而达到恶意攻击用户的目的，如盗取用户 cookie、破坏页面结构、重定向到其他网站等。

预防 XSS 的核心是必须对输入的数据做过滤处理。

## 10. 什么是 CSRF 攻击，如何避免？

​		CSRF：Cross-Site Request Forgery（中文：跨站请求伪造），可以理解为攻击者盗用了你的身份，以你的名义发送恶意请求，比如：以你名义发送邮件、发消息、购买商品，虚拟货币转账等。

防御手段：

- 验证请求来源地址；
- 关键操作添加验证码；
- 在请求地址添加 token 并验证。

# 异常

## 1. throw 和 throws 的区别？

- throw：是真实抛出一个异常。
- throws：是声明可能会抛出一个异常。

## 2. final、finally、finalize 有什么区别？

- final：是修饰符，如果修饰类，此类不能被继承；如果修饰方法和变量，则表示此方法和此变量不能在被改变，只能使用。
- finally：是 try{} catch{} finally{} 最后一部分，表示不论发生任何情况都会执行，finally 部分可以省略，但如果 finally 部分存在，则一定会执行 finally 里面的代码。
- finalize： 是 Object 类的一个方法，在垃圾收集器执行的时候会调用被回收对象的此方法。

## 3. try-catch-finally 中哪个部分可以省略？

try-catch-finally 其中 catch 和 finally 都可以被省略，但是不能同时省略，也就是说有 try 的时候，必须后面跟一个 catch 或者 finally。

## 4. try-catch-finally 中，如果 catch 中 return 了，finally 还会执行吗？

finally 一定会执行，即使是 catch 中 return 了，catch 中的 return 会等 finally 中的代码执行完之后，才会执行。

## 5. 常见的异常类有哪些？

- NullPointerException 空指针异常
- ClassNotFoundException 指定类不存在
- NumberFormatException 字符串转换为数字异常
- IndexOutOfBoundsException 数组下标越界异常
- ClassCastException 数据类型转换异常
- FileNotFoundException 文件未找到异常
- NoSuchMethodException 方法不存在异常
- IOException IO 异常
- SocketException Socket 异常

# 网络

## 1. http 响应码 301 和 302 代表的是什么？有什么区别？

301：永久重定向。

302：暂时重定向。

它们的区别是，301 对搜索引擎优化（SEO）更加有利；302 有被提示为网络拦截的风险。

## 2. forward 和 redirect 的区别？

forward 是转发 和 redirect 是重定向：

- 地址栏 url 显示：foward url 不会发生改变，redirect url 会发生改变；
- 数据共享：forward 可以共享 request 里的数据，redirect 不能共享；
- 效率：forward 比 redirect 效率高。

## 3. 简述 tcp 和 udp的区别？

tcp 和 udp 是 OSI 模型中的运输层中的协议。tcp 提供可靠的通信传输，而 udp 则常被用于让广播和细节控制交给应用的通信传输。

两者的区别大致如下：

- tcp 面向连接，udp 面向非连接即发送数据前不需要建立链接；
- tcp 提供可靠的服务（数据传输），udp 无法保证；
- tcp 面向字节流，udp 面向报文；
- tcp 数据传输慢，udp 数据传输快；

## 4. tcp 为什么要三次握手，两次不行吗？为什么？

如果采用两次握手，那么只要服务器发出确认数据包就会建立连接，但由于客户端此时并未响应服务器端的请求，那此时服务器端就会一直在等待客户端，这样服务器端就白白浪费了一定的资源。若采用三次握手，服务器端没有收到来自客户端的再此确认，则就会知道客户端并没有要求建立请求，就不会浪费服务器的资源。

## 5. 说一下 tcp 粘包是怎么产生的？

tcp 粘包可能发生在发送端或者接收端，分别来看两端各种产生粘包的原因：

- 发送端粘包：发送端需要等缓冲区满才发送出去，造成粘包；
- 接收方粘包：接收方不及时接收缓冲区的包，造成多个包接收。

## 6. OSI 的七层模型都有哪些？

- 物理层：利用传输介质为数据链路层提供物理连接，实现比特流的透明传输。
- 数据链路层：负责建立和管理节点间的链路。
- 网络层：通过路由选择算法，为报文或分组通过通信子网选择最适当的路径。
- 传输层：向用户提供可靠的端到端的差错和流量控制，保证报文的正确传输。
- 会话层：向两个实体的表示层提供建立和使用连接的方法。
- 表示层：处理用户信息的表示问题，如编码、数据格式转换和加密解密等。
- 应用层：直接向用户提供服务，完成用户希望在网络上完成的各种工作。

## 7. get 和 post 请求有哪些区别？

- get 请求会被浏览器主动缓存，而 post 不会。
- get 传递参数有大小限制，而 post 没有。
- post 参数传输更安全，get 的参数会明文限制在 url 上，post 不会。
