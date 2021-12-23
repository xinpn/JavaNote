# IOC操作bean管理

### 什么是bean管理？

bean管理包括**创建对象**和**注入属性**。有两种方式进行bean管理：**xml配置文件**、**注解**。

### 基于xml创建对象

```Java
1、在配置文件中进行配置
    <bean id="user" class="com.learnjava.Dao.Impl.UserDaoImpl"></bean>
    其中，id标签表示唯一标识，class标签表示类的全路径
2.通过getBean()获取对象
    //获取配置文件
	ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
    //获得配置创建的对象
	UserDao user = (UserDao) context.getBean("user");
创建对象时，默认使用无参构造器。
```

### 基于xml方式注入属性

DI：依赖注入，就是注入属性。是IOC的一种具体实现方式。 

注入属性在创建对象的基础上完成。

##### 1.通过set()方法注入属性

```Java
1.在类中创建要注入的属性
2.在类中实现属性的set()方法
3.在配置文件中配置属性的值
    name标签表示属性名，value标签表示属性值。
    <bean id="user" class="com.learnjava.Dao.Impl.UserDaoImpl">
        <property name="name" value="Tom"/>
        <property name="age" value="18"/>
    </bean>
4，通过对象来测试是否注入成功
```

##### 2.通过有参构造器注入属性

```java
1.在类中创建要注入的属性
2.创建有参构造器
3、配置文件中进行配置
    constructor-arg标签表示有参构造器参数。
    <bean id="user" class="com.learnjava.Dao.Impl.UserDaoImpl">
        <constructor-arg name="name" value="Jerry"/>
        <constructor-arg name="age" value="25"/>
    </bean>
```

