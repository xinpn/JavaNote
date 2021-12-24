# IOC概述

### IOC概念

1. IOC的意思是反转控制（Inverse of control），它把对象的创建和对象之间的调用交给spring进行管理。
2. 使用IOC的目的：降低耦合度

### IOC的实现

**IOC的实现需要三个技术：xml解析、工厂模式、反射**

**IOC过程：**

```Java
1.有一个配置文件，例如applicationContext.xml
    <bean id="user" class="com.learnjava.UserDao"></bean>
2.有两个类：UserService、UserDao。在UserService需要使用UserDao的对象
	这时候需要创建一个工厂类：class UserFactory{
        public static UserDao getDao{
            //1.解析xml文件
            String classValue = xml文件中class的属性值;
            //2.通过反射获得对象
        	Class clazz = Class.forName(classValue);
            return (UserDao)clazz.newInstance();
        }
    }
```

##### **IOC思想基于IOC容器实现，IOC容器底层就是对象工厂**

```Java
spring提供了IOC容器的两种实现方式：
1、BeanFactory ，是spring内部的使用接口，一般不提供给开发人员使用
2.ApplicationContext，BeanFactory的子接口，提供更多强大的功能，开发人员使用
```

