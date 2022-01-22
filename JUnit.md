#JUnit笔记

### Junit4 的常用注解
```
@RunWith : 指定测试类使用某个运行器（TestRunner）
@Before：初始化方法 对于每一个测试方法都要执行一次
@After：释放资源 对于每一个测试方法都要执行一次
@Test：测试方法，在这里可以测试期望异常和超时时间
@Ignore ：忽略的测试方法
@BeforeClass ：针对所有测试，只执行一次，且必须为static void
@AfterClass ：针对所有测试，只执行一次，且必须为static void
@Parameters ： 指定测试类的测试数据集合
@Rule : 允许灵活添加或重新定义测试类中的每个测试方法的行为
@FixMethodOrder : 指定测试方法的执行顺序
@SuiteClasses ： 设置Suite包含的测试类集合
```
>单元测试用例执行顺序为 ： @BeforeClass -> @Before -> @Test -> @After -> @AfterClass

>单个测试方法的调用顺序为： @Before -> @Test -> @After