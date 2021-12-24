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

##### 3.注入空值和特殊符号

```Java
1.对于一个属性要注入空值，需要用到<null>标签
    <property name="address">
           <null></null>
    </property>
2.注入特殊符号，要用到CDATA结构（<![CDATA[需要的值]]），idea中CD快捷键一键生成。
    <property name="address">
           <value><![CDATA[<<beijing>>]]>
           </value>
    </property>
```

##### 4.注入外部bean

外部bean就是其他类的对象

```Java
1.创建需要注入的类的对象
    <bean id="userDaoImpl" class="com.learnjava.Dao.Impl.UserDaoImpl">
    	......
    </bean>
2.在需要注入的类里面设置属性和set()方法
3.在配置文件里面配置
    注入外部bean需要 ref属性。ref属性的值是注入对象的bean标签的id值。
    <bean id="userService" class="com.learnjava.service.UserService">
        <property name="userDao" ref="userDaoImpl"/>
    </bean>
```

##### 5.注入内部bean

```java
 <!--注入内部bean-->
    <bean id="employee" class="com.learnjava.demo.Employee">
        <property name="eName" value="Tom"/>
        <property name="gender" value="男"/>
        <property name="dept">
            <bean id="dept" class="com.learnjava.demo.Dept">
                <property name="dName" value="财务部"/>
            </bean>
        </property>
    </bean>
```

