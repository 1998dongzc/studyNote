# Java规范

#### 1.equals不比较一定相等、一定不想等和数组类型一定不相等的对象。

#### 2.父类不向子类转型，会抛出ClassCastException异常。

#### 3.对一个值进行操作时，必须先判断是否为null。

#### 4.避免使用null对象的调用方法。

#### 5.确保类型转型无误，否则抛出ClassCastException异常。

#### 6.使用equals和hashCode方法来对URL进行资源标识符解析时会引起堵塞，使用Java.net.URI。

#### 7.String的split方法传递的参数是正则表达式，正则表达式本身用到的字符需要转义，如：句点符号“.”，美元符号“$”，乘方符号“^”，大括号“{}”，方括号“[]”，圆括号“()” ，竖线“|”，星号“*”，加号“+”，问号“?”等等，这些需要在前面加上“\\”转义符。

#### 8.避免catch Throwable对象。

#### 9.奇偶判断不能用于负数。

#### 10.避免出现空的catch块，可以在catch块中记录日志；如果catch块中不需要任何操作建议将异常抛出。

#### 11.删除空的finally块。

#### 12.删除空代码块。

#### 13.使用StringBuffer或StringBuilder做字符串拼接。

#### 14.避免对对于明显有继承结构的类和对象使用instanceof。

#### 15.先判断变量是否为null然后再使用。

#### 16.使用%运算符时候避免%1。

#### 17.使用Arrays.equals（Object[],Object[]）比较数组。

#### 18.当用toArray()方法将集合转化成数组时，在传入参数数组时，建议将参数数组的长度指定为集合的大小。原因有2点，第一，如果传入参数数组的长度小于集合大小，就会第二次创建一个新的数组来存放集合中的值，浪费内存空间；第二，如果传入参数数组的长度大于集合的大小，那么数组中会使用null来填充。 

#### 19.流的关闭皆应该放到finally控制块中。

#### 20.数组遍历使用Array.toString(list)方法。

#### 21.删除集合元素不使用removeall(),使用clear()。

#### 22.集合不应该包含自身。

#### 23.调用了値可能为null的局部变量，可能会例外发生NullPointerException，建议在调用前追加null检查。

#### 24.覆盖了equals也应该覆盖hashCode。

#### 25.每一个case分支都要加上break或者return。

#### 26.equals()方法应该对null参数进行检测，当传入null值时应该返回false。

#### 27.尽量不在方法内创建对象，在方法外创建以便多次调用。

#### 28.serialVersionUID是在序列化对象中描述版本号信息的，必须是一个静态的。long型的终态值。正确写法是private static final long serialVersionUID = xxxxL。

#### 29.定义了compareTo(...),需要在类中定义equals和hashCode方法。

#### 30.最常用的整数类型是int 。它是有符号的32位类型，数的范围是-2,147,483,648～2,147,483,647，绝对值只能取16位。

#### 31.多线程同步常量池的数据或值可能会导致死锁。

#### 32.多线程同步对象的getClass()。

#### 33.多线程同步对象不能是基础类型的包装类。

#### 34.多线程，获得锁后，不应该使用Thread.sleep()，不会释放锁，应该使用wait(),释放锁。

#### 35.多线程，使用同步包裹的notify()。

#### 36.遍历Map，使用for-each遍历map的entry//for (Map.Entry<String,User> entry : map.entrySet())通过entry获取key和value。

#### 37.Calendar是线程不安全的，所以应该public void run(){    Calendar calendar = Calendar.getInstance()     }，在线程方法中单独获取对象。

#### 38.多线程调用notify或notifyall，必须要获取当前锁后才能调用，否则会抛出IllegalMonitorStateException异常。

#### 39.使用PreparedStatement时，sql语句不能使用非常量字符串进行拼接。

#### 40.JDBC连接数据库时，账号密码不能为空。

#### 41.使PreparedStatement预编译，不使用Statement。

#### 42.对方法返回值检测、判断后再进行类型转换。

#### 43.移除从不调用的私有方法。

#### 44.使用Integer.valueOf()替代new Integer。

#### 45.方法返回Boolean时，不能返回null。

#### 46.if-else必须使用{}。

#### 47.方法名、属性名首字母小写，采用驼峰式命名，如testMethod、testName。

#### 48.StringBuffer sb = new StringBuffer('c');使用'c'时，会将'c'转换成int值,设置为buffer的大小。

#### 49.避免捕获空指针异常：在正常情形下代码不应该捕获NullPointException，否则Catch块可能隐藏原始错误，导致其他更多微妙的错误。

#### 50.避免给参数重新赋值,建议使用临时本地变量来代替。

#### 51.避免在catch块中再次抛出同类型的异常新实例。

#### 52.避免抛出或捕获原始异常类型，如RuntimeException，Throwable，Exception等，建议使用自定义异常。

#### 53.避免数组循环拷贝：拷贝数组用System.arraycopy代替循环拷贝数组元素。

#### 54.StringBuffer是线程安全的，避免使用append方法。

#### 55.在循环语句中尽量避免使用空语句。

#### 56.不希望被外部修改的变量请添加final修饰符。

#### 57.建议重复2次以上的字符串，设为静态常量。

#### 58.用Integer.toString(x)代替Integer.valueOf(x).toString();

#### 59.避免局部变量与类变量同名。

#### 60.定义了clone方法的所有类都需要实现Cloneable接口。

#### 61.switch中的case处理的逻辑尽可能简单。

#### 62.不直接调用System.gc();

#### 63.尽可能使用日志记录代替替代System.out.println("....");。

#### 64.使用Arrays.asList方法代替循环拷贝（list复制给ArrayList）。

#### 65.String.indexOf(字符)，它执行的很快。不要使用indexOf(字符串)。

#### 66.应该保存对象的clone副本或copy副本。

#### 67.使用接口代替实现类。

#### 68.删除无用的方法重写。

#### 69.检查是否在返回boolean值时是否有使用冗余的地方。

#### 70.String str = new String();使用此语句创建空字符串时，java是在堆中新建一个空字符串对象，然后将其赋给引用str，浪费堆内存。在创建字符串时直接赋值即可。如：String str=""。

#### 71.不用String str = new String("abc");而用String str="abc";。

#### 72.在定义常量时，建议将常量定义成static final类型，常量才不会被随意修改。

#### 73.建议在定义Integer、Long、Double等数据类型常量的最大、最小值的时候，使用Java提供的方法。例如：Integer.MAX_VALUE、Integer.MIN_VALUE。

#### 74.读取类之前，对其进行初始化。

#### 75.用Map替换Hashtable: 如果不是在必须线程安全的环境下，考虑使用Map替换Hashtable。Map m = new HashMap<K, V>();

#### 76.工具类应该私有化构造方法。

#### 77.只有static final 成员是public的，其他的类成员都是private的。

#### 78.函数参数过多时，将方法参数封装成对象，或者想办法减少方法参数个数。

#### 79.检查返回return的个数,checkstyle默认每个方法中的return个数不超过2。

#### 80.检查布尔运算符在一条语句中允许出现的最大数目是否过大,checkstyle默认为3。

#### 81.关闭资源：确保这些资源(譬如：Connection,Statement,和ResultSet对象)总在使用后被关闭。

#### 82.克隆方法必须实现Cloneable接口：如果类实现Cloneable接口，clone()方法应该被实现为一个final的方法并且只抛出CloneNotSupportedException的异常。

#### 83.首字母小写，采用骆驼命名法，尽量见名知意，不要太长，尽量不要超过15个字符。

#### 84.方法名首字母小写，第一个词描述方法类型，增/删/改/查等，第二个词描述具体行为，后面可以根据情况在加入，但避免名称过长。

#### 85.检查类中是否有重复代码，重复代码行数不能超过8行。

#### 86.去掉类型转换括号中两边的空白。

#### 87.如果重写的finalize()方法是空的，那么它就不需要存在。

#### 88.Map禁止重用Entry和在iterator中重用entry。

#### 89.子类finalize()方法中要调用父类的finalize()方法。

#### 90.J2EE容器中不应该使用System.exit(0);

#### 91.字符串比较值不用==和!=，用equals()和equalsIgnoreCase()。

#### 92.synchronized 会对对象做是否为空的判断，如果为空则会抛出异常，所以接下来再对对象判空是毫无意义的。

#### 93.多线程不能使用空的代码块作为锁。

#### 94.数据类型不能装包后立即拆包，或者拆包后立即装包。

#### 95.switch分支过少时，采用if-else语句。

#### 96.需要返回值为数组时，返回空数组而不是null。

#### 97.检查修饰符的顺序，默认是public,protected,private,abstract,static,final,transient,volatile,synchronized,native,strictfp。

#### 98.由public 或 protected修饰的变量如果是成员变量，而成员变量，java会自动帮你初始化为null，调用的时候如果用到这个结果[如getStr().length()]，有可能为空指针异常,所以建议成员变量初始化

#### 99.行注释不能放在尾部，建议单独一行。

#### 100.在catch中不要使用Instanceof检测。

#### 101.非serializable类不能有一个可序列化的内部类。

#### 102.检查类和接口中的声明顺序，具体顺序为：优先生命public、其次portected、最后private。 
