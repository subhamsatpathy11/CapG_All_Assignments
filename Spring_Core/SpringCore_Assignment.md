# Spring Core Assignment

1. Create an Address class with the following attributes:- street, city, state, zip, country Create an Customer class with the following attributes:- customerld, customer Name, customerContact, customerAddress. object and print details of Customer. Inject the Address bean into Customer bean using setter injection Create a Test class with main() method, get Customer bean from ApplicationContext 
Also write the JUnit Test cases for above program.

 - Modify the above application and inject the bean using constructor injection
 - Use XML based Configuraion.

```java
//class name - Address 

package io.first;

public class Address {
 
    private Long id;
    protected String street; 
    protected String city;
    protected String state;
    protected String zip;
    protected String country;
    
    public Address() { 
    	
    	this.id = id;
    	this.street = street;
    	this.city = city;
    	this.state = state;
    	this.zip = zip;
    	this.country = country;
    }
    
    public Long getId()
    {
    	return id;
    }
    public void setId()
    {
    	this.id = id;
    }
    
    public String getStreet()
    {
    	return street;
    }
    public void setStreet()
    {
    	this.street = street;
    }
    
    public String getCity()
    {
    	return city;
    }
    public void setCity()
    {
    	this.city = city;
    }
    
    public String getState()
    {
    	return state;
    }
    public void setState()
    {
    	this.state = state;
    }
    
    public String getZip()
    {
    	return zip;
    }
    public void setZip()
    {
    	this.zip = zip;
    }
    
    public String getCountry()
    {
    	return country;
    }
    public void setCountry()
    {
    	this.country = country;
    }
    
    public void displayAdd()
    {
    	System.out.println("Addresss = " + this.street + this.city + this.state + this.zip + this.country);
    }
}
```

```java
//class name - Customer

package io.first;

public class Customer {
    
    protected int customer_id;
    protected String customer_name;
    protected Address customer_address;
    protected String customer_contact;
    
    public Customer() {
    	
    	this.customer_id = customer_id;
    	this.customer_name = customer_name;
    	this.customer_address = customer_address;
    	this.customer_contact = customer_contact;
    }
    
    public int getCustomerId()
    {
    	return customer_id;
    }
    public void setCustomerId()
    {
    	this.customer_id = customer_id;
    }
    
    public String getCustomerName()
    {
    	return customer_name;
    }
    public void setCustomerName()
    {
    	this.customer_name = customer_name;
    }
    
    public Address getCustomerAddress()
    {
    	return customer_address;
    }
    public void setCustomerAddress()
    {
    	this.customer_address = customer_address;
    }
    
    public String getCustomerContact()
    {
    	return customer_contact;
    }
    public void setCustomerContact()
    {
    	this.customer_contact = customer_contact;
    }
    
    public void display()
    {
    	System.out.println("Customer Details - " + this.customer_name + this.customer_id + this.customer_contact);
    }
}

```

```java
//class name - Test

package io.first;

public class Test {

	public static void main(String[] args) {
		ApplicationContext context=new ClassPathXmlApplicationContext("customerbean.xml");
		Customer customer = (Customer) context.getBean("Customer");
		customer.display();
	}

}

```

```xml
<bean id = "Customer"  class="io.first.Customer">
   <property name="customer_id" value="1"/>
   <property name="customer_name" value="Mark Zuckerburg"/>
   <property name="customer_contact" value="783893"/>
   <property name="street" ref="customer_address"/>
   <property name="city" ref="customer_address"/>
   <property name="state" ref="customer_address"/>
   <property name="zip" ref="customer_address"/>
   <property name="country" ref="customer_address"/>
</bean>
   <bean id="customer_address" class="io.first.Address">
   <property name="street" value="8"/>
   <property name="city" value="Bhubaneswar"/>
   <property name="state" value="Odisha"/>
   <property name="zip" value="751003"/>
   <property name="country" value="India"/> 
</bean>
```

Output:

```
id:1 name:Mark Zuckerburg Contact:783893
Customeraddress: 8
Bhubaneswar
Odisha
751003
India

```

2. Example of Injecting collections (List, Set and Map)

Create a class Question with following attributes: questionid, question, answers. There are 3 cases for above program.

 - Write a program where answers is of type List<String> or String[] 	
 - Write a program where answers is of type Set<String>
 - Write a program where answers is of type Map<Integer, String>. In case of Map, Integer value represents answer's sequence number.
 - Create a Test class with main() method, get Question bean from ApplicationContext object and print question and its answers. e. Also write the JUnit Test cases for above program.
	
Use XML based configuration.

```java
//class name - Question

package com.io.second;  
import java.util.Iterator;  
import java.util.List;  
  
public class Question {  
private int id;  
private String name;  
private List<String> answers_list;  
private Set<String> answers_set;  
private Map<Integer, String> answers_map;  
  
public int getId()
{
	return id;
}
public void setId()
{
	this.id = id;
}
public String getName()
{
	return name;
}
public void setName()
{
	this.name = name;
}
public ArrayList<Object>getList() 
{
	return answers_list;
}
public void setList(ArrayList<Object> answers_list) 
{
	this.answers_list = answers_list;
} 
public Set<Object>getSet() 
{
	return answers_set;
}
public void setSet(Set<Object> answers_set) 
{
	this.answers_set = answers_set;
} 
public Map<Integer, String>getMap() 
{
	return answers_map;
}
public void setList(Map<Integer, String> answer_map) 
{
	this.answers_map = answers_map;
} 

public void displayList(){  
    System.out.println(id+" "+name);  
    System.out.println("answers are:");  
    Iterator<String> itr=answers_list.iterator();  
    while(itr.hasNext()){  
        System.out.println(itr.next());  
    }  
}  

public void displaySet(){  
    System.out.println(id+" "+name);  
    System.out.println("answers are:");  
    Iterator<String> iter = answers_set.iterator();  
    while(iter.hasNext()){  
        System.out.println(iter.next());  
    }  
}  

public void displayMap()
{
	answers_map.forEach((key, value) -> System.out.println(id + ":" + answers_map));
}
  
}  
```


	
```java
	```java
package io.second;  
  
import org.springframework.beans.factory.BeanFactory;  
import org.springframework.beans.factory.xml.XmlBeanFactory;  
import org.springframework.core.io.ClassPathResource;  
import org.springframework.core.io.Resource;  
  
public class Test {  
public static void main(String[] args) {  
    Resource r=new ClassPathResource("applicationContext.xml");  
    BeanFactory factory=new XmlBeanFactory(r);  
      
    Question q=(Question)factory.getBean("q");  
    q1.displayList(); 
    Question q1=(Question)factory.getBean("q1");  
    q1.displaySet(); 
    Question q2=(Question)factory.getBean("q2);  
    q1.displayMap();  
      
}  
}  	
```
```xml
<?xml version="1.0" encoding="UTF-8"?>  
<beans  
    xmlns="http://www.springframework.org/schema/beans"  
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
    xmlns:p="http://www.springframework.org/schema/p"  
    xsi:schemaLocation="http://www.springframework.org/schema/beans   
http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">  
  
<bean id="q" class="io.second.Question">  
<property name="id" value="1"></property>  
<property name="name" value="What is Java?"></property>  
<property name="answers">  
<list>  
<value>Java is a programming language</value>  
<value>Java is a platform</value>  
<value>Java is an Island</value>  
</list>  
</property>  
</bean>  
	
<bean id="q1" class="io.second.Question">  
<property name="id" value="2"></property>  
<property name="name" value="Java is a platform"></property>  
<property name="answers">  
<list>  
<value>Java is a programming language</value>  
<value>Java is a platform</value>  
<value>Java is an Island</value>  
</list>  
</property>  
</bean>  
	
<bean id="q2" class="io.second.Question">  
<property name="id" value="3"></property>  
<property name="name" value="Java is an Island"></property>  
<property name="answers">  
<list>  
<value>Java is a programming language</value>  
<value>Java is a platform</value>  
<value>Java is an Island</value>  
</list>  
</property>  
</bean>  
  
</beans> 	
```

	
4. Example on @Controller, @Service, @Repository, @Autowired, @Configuration and @Bean. Modify the above application, use annotations and java based configuration.

 - @Bean
```java
package spring_ex4;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

//@Configuration
public class ApplicationConfiguration {
	@Bean(name="demoService")
    public DemoManager helloWorld() 
    {
        return new DemoManagerImpl();
    }
}
```
```java
package spring_ex4;

public interface DemoManager {
	 public String getServiceName();
}
package spring_ex4;

public class DemoManagerImpl implements DemoManager
{
    public String getServiceName()
    {
        return "Hello!!!!";
    }
}
```
```java
package spring_ex4;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class VerifySpringCoreFeature {
	    public static void main(String[] args)
	    {
	        ApplicationContext context = new AnnotationConfigApplicationContext(ApplicationConfiguration.class);
	 
	        DemoManager  obj = (DemoManager) context.getBean("demoService");
	 
	        System.out.println( obj.getServiceName() );
	    }
}
```
Output:
```
Addition of first and second = 4
```
 - @contoller
```java
package spring_exp4;

import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class SpringMainClass {
	public static void main(String[] args) {
		AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext();
		context.scan("spring_exp4");
		context.refresh();
		MathController ms = context.getBean(MathController.class);
		int result = ms.add(2, 2);
		System.out.println("Addition of first and second = " + result);
		context.close();
	}
}
```
```java
package spring_exp4;
package spring_exp4;
import org.springframework.stereotype.Controller;
import org.springframework.stereotype.Service;

//@Service("ms")
@Controller
public class MathController {
	public int add(int x, int y) {
		return x + y;
	}
}
```
Output:
```
Addition of first and second = 4
```
 - @Service
```java
package spring_exp4;

import org.springframework.stereotype.Component;
import org.springframework.stereotype.Service;

@Service("ms")
//@Component
public class MathService {
	public int add(int x, int y) {
		return x + y;
	}
}
```
```java
package spring_exp4;

import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class SpringMainClass {
	public static void main(String[] args) {
		AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext();
		context.scan("spring_exp4");
		context.refresh();
		MathService ms = context.getBean(MathService.class);
		int result = ms.add(2, 2);
		System.out.println("Addition of first and second = " + result);
		context.close();
	}
}
```
	
Output:
```
Addition of first and second = 4
```
 - @Autowired
```java
package maths_example;

import org.springframework.beans.factory.BeanFactory;
// org.springframework.beans.factory.xml.XmlBeanFactory;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
import org.springframework.stereotype.Repository;
//import org.springframework.core.io.FileSystemResource;
//@Repository
public class Mainbean {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		//BeanFactory factory= new XmlBeanFactory(new FileSystemResource("spring.xml"));
		 ApplicationContext context=new ClassPathXmlApplicationContext("spring.xml");
		  Shape shape=(Shape)context.getBean("circle");
		    shape.draw();

	}

}
```
```java
package maths_example;

public class Triangle implements Shape {
	private Point PointA;
	private Point PointB;
	private Point PointC;
	public Point getPointA() {
		return PointA;
	}
	public void setPointA(Point pointA) {
		PointA = pointA;
	}
	public Point getPointB() {
		return PointB;
	}
	public void setPointB(Point pointB) {
		PointB = pointB;
	}
	public Point getPointC() {
		return PointC;
	}
	public void setPointC(Point pointC) {
		PointC = pointC;
	}
	public void draw()
	{
		System.out.println("Draw triangle");
		System.out.println(getPointA().getX()+ " "+getPointA().getY());
		System.out.println(getPointB().getX()+ " "+getPointB().getY());
		System.out.println(getPointC().getX()+ " "+getPointC().getY());
	}
	


}
```
```java
package maths_example;

public interface Shape {
	public void draw();

}
package maths_example;

public class Point {
	private int x;
	private int y;
	public int getX() {
		return x;
	}
	public void setX(int x) {
		this.x = x;
	}
	public int getY() {
		return y;
	}
	public void setY(int y) {
		this.y = y;
	}

}
```
```java
import org.springframework.beans.factory.annotation.Required;
import org.springframework.stereotype.Component;
import org.springframework.stereotype.Repository;

//@Component
//@Repository
public class Circle implements Shape {
	private Point center;

	public void draw()
	{
		System.out.println("draw circle");
		System.out.println("circle point" +center.getX() +center.getY());
	}
	public Point getCenter() {
		return center;
	}

//@Autowired
	public void setCenter(Point center) {
		this.center = center;
	}

}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns = "http://www.springframework.org/schema/beans"

xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation = "http://www.springframework.org/schema/beans
   http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">
<bean id = "triangle"  class="maths_example.Triangle">
	<property name="PointA" ref="pointA"/>
<property name="PointB" ref="pointB"/>
<property name="PointC" ref="pointC"/>
</bean>
<bean id = "pointA"  class="maths_example.Point">
<property name="x" value="0"/>
<property name="y" value="10"/>
</bean>
<bean id = "pointB"  class="maths_example.Point">
<property name="x" value="10"/>
<property name="y" value="10"/>
</bean>
<bean id = "pointC"  class="maths_example.Point">
<property name="x" value="20"/>
<property name="y" value="10"/>
</bean> 
<bean id = "center"  class="maths_example.Point">
<property name="x" value="20"/>
<property name="y" value="10"/>
</bean> 

 <bean id = "circle"  class="maths_example.Circle">
 <!-- <property names="center" ref="pointA"/> -->
</bean> 
 <bean class="org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor">
	</bean>

	
</beans>
```
	
Output:
```

draw circle
circle point2010
```

	
5. Write a program to demonstrate use of @Resource, @inject, @Required annotations
	
 - @Required
```java
package assignment5;

import org.springframework.beans.factory.annotation.Required;

public class employee {
	 private String name;    
	    private String designation;
	    private String company;
	 
	    @Required
	    public void setName(String name) {
	        this.name = name;
	    }
	    public String getName() {
	        return name;
	    }
	 
	    @Required
	    public void setDesignation(String designation) {
	        this.designation = designation;
	    }
	    public String getDesignation() {
	        return designation;
	    }
	 
	    public void setCompany(String company) {
	        this.company = company;
	    }
	    public String getCompany() {
	        return company;
	    }
	 
	    @Override
	    public String toString() {
	        return "Employee [name=" + name + ", designation=" + designation + ", company=" + company + "]";
	    }

}
```
```java
package springrequiredannotation;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

import assignment5.employee;

public class AppMain {
	  @SuppressWarnings("resource")
	    public static void main(String[] args) {        
	        ApplicationContext ac = new ClassPathXmlApplicationContext("required-annotation.xml");
	 
	        employee emp = ac.getBean("myemployee", employee.class);
	        System.out.println(emp.toString());
	    }

}
```
```xml

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:context="http://www.springframework.org/schema/context"
	xsi:schemaLocation="
        http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">

	
	<context:annotation-config />

	<bean id="myemployee" class="com.spring.pojo.Employee">
		<!-- Required property -->
		<property name="name" value="Charlotte O' Neil" />
		<!-- Required property -->
		<property name="designation" value="Technical Leader" />
		<property name="company" value="Test Ltd." />
	</bean>
</beans>

```

 - @resource 
```java
package com.spring.pojo;

public class Company {
	 private String name;
	    private String location;
	 
	    public String getName() {
	        return name;
	    }
	    public void setName(String name) {
	        this.name = name;
	    }
	    public String getLocation() {
	        return location;
	    }
	    public void setLocation(String location) {
	        this.location = location;
	    }
	 
	    @Override
	    public String toString() {
	        return "Company [name=" + name + ", location=" + location + "]";
	    }
}
```
```java
package com.spring.pojo;
import javax.annotation.Resource;


public class Employee {

    private String id;
    private String name;
 
    @Resource(name="mycompany")
    private Company company;
 
    public String getId() {
        return id;
    }
    public void setId(String id) {
        this.id = id;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public Company getCompany() {
        return company;
    }
    public void setCompany(Company company) {
        this.company = company;
    }
 
    @Override
    public String toString() {
        return "Employee [id=" + id + ", name=" + name + ", company=" + company.toString() + "]";
    }

}
```
```java
package com.spring.util;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

import com.spring.pojo.Employee;

public class AppMain {
	@SuppressWarnings("resource")
    public static void main(String[] args) {
 
        ApplicationContext ac = new ClassPathXmlApplicationContext("resource-annotation.xml");
 
        Employee emp = ac.getBean("myemployee", Employee.class);
        System.out.println(emp.toString());

}
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:context="http://www.springframework.org/schema/context"
    xsi:schemaLocation="
        http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
 
    <!-- To activate the '@Resource' annotation in the spring framework -->
    <context:annotation-config />
 
    <bean id="mycompany" class="com.spring.pojo.Company">
        <property name="name" value="Test Pvt. Ltd." />
        <property name="location" value="India" />
    </bean>
 
    <bean id="myemployee" class="com.spring.pojo.Employee">
        <property name="id" value="123456" />
        <property name="name" value="Charlotte O' Neil" />
    </bean>
</beans>
```
 - @insert
```java
package com.springexample;
 
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
 
public class RunMyProgram {
    public static void main(String[] args) {
        ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml");
        StudentHolder studentHolder = (StudentHolder) context.getBean("studentHolder");
            studentHolder.displayStudentDetails();
    }
}

```
```java
package com.springexample;
 
import javax.inject.Inject;
 
public class StudentHolder {
     
    /* Inject annotation wires the property byType by default */
    @Inject
    Student student;
     
    public Student getStudent() {
        return student;
    }
 
    public void setStudent(Student student) {
        this.student = student;
    }   
     
    public void displayStudentDetails(){
        System.out.println("Student Details");
        System.out.println("---------------");
        System.out.println("Student No: "+student.getStudentNo());
        System.out.println("Student Name: "+student.getStudentName());
    }
}

```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
        http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-3.0.xsd">
 
    <bean id="stu" class="com.springexample.Student">
        <property name="studentNo" value="1001" />
        <property name="studentName" value="John Peter" />
    </bean>
     
    <bean id="studentHolder" class="com.springexample.StudentHolder" />
    <context:annotation-config />
</beans>

```
```java

package com.springexample;
 
public class Student {
    private int studentNo;
    private String studentName;
     
    public int getStudentNo() {
        return studentNo;
    }
    public void setStudentNo(int studentNo) {
        this.studentNo = studentNo;
    }
    public String getStudentName() {
        return studentName;
    }
    public void setStudentName(String studentName) {
        this.studentName = studentName;
    }   
}

```

7. Write a Java program to demonstrate SPEL (Spring Expression language)
	
```java
import org.springframework.expression.Expression;  
import org.springframework.expression.ExpressionParser;  
import org.springframework.expression.spel.standard.SpelExpressionParser;  
  
public class Test {  
public static void main(String[] args) {  
ExpressionParser parser = new SpelExpressionParser();  
  
Expression exp = parser.parseExpression("'Hello SPEL'");  
String message = (String) exp.getValue();  
System.out.println(message);  
//OR  
//System.out.println(parser.parseExpression("'Hello SPEL'").getValue());  
}  
}  	
```
8. Write a Java program to demonstrate InitializingBean and DisposableBean.

   Try Different ways:

 - (Use init-method and destroy-method in xml config file)
	
```java
package QuestionEight;

import org.springframework.beans.factory.DisposableBean;
import org.springframework.beans.factory.InitializingBean;

public class CustomerService implements InitializingBean, DisposableBean {
	private String msg;

	public String getMsg() {
		return msg;
	}

	public void setMsg(String msg) {
		this.msg = msg;
	}

	public void destroy() throws Exception {

		// TODO Auto-generated method stub
		System.out.println("Spring Container is destroy! Customer clean up");
	}

	public void afterPropertiesSet() throws Exception {
		// TODO Auto-generated method stub
		System.out.println("Init method after properties are set : " + msg);
	}}
	
```
```java
package QuestionEight;

import org.springframework.beans.factory.DisposableBean;
import org.springframework.beans.factory.InitializingBean;

public class CustomerService implements InitializingBean, DisposableBean {
	private String msg;

	public String getMsg() {
		return msg;
	}

	public void setMsg(String msg) {
		this.msg = msg;
	}

	public void destroy() throws Exception {

		// TODO Auto-generated method stub
		System.out.println("Spring Container is destroy! Customer clean up");
	}

	public void afterPropertiesSet() throws Exception {
		// TODO Auto-generated method stub
		System.out.println("Init method after properties are set : " + msg);
	}}

```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/beans
	http://www.springframework.org/schema/beans/spring-beans-2.5.xsd">

       <bean id="customerService" class="QuestionEight.CustomerService">
		<property name="msg" value="i'm property message" />
       </bean>
		
</beans>

```
Output:
	
```
Init method after properties are set : i'm property message
Spring Container is destroy! Customer clean up

```
 - (Use @PostConstruct and @PreDestroy)
	
```java
package EightB;

import javax.annotation.PostConstruct;
import javax.annotation.PreDestroy;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;

@Component
public class MyBean {

	public MyBean() {
		System.out.println("MyBean instance created");
	}

	@PostConstruct
	private void init() {
		System.out.println("Verifying Resources");
	}

	@PreDestroy
	private void shutdown() {
		System.out.println("Shutdown All Resources");
	}

	public void close() {
		System.out.println("Closing All Resources");
	}
}

```
```java
package EightB;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.Scope;

@Configuration
public class MyConfiguration {

	@Bean
	@Scope(value = "singleton")
	public MyBean myBean() {
		return new MyBean();
	}

}

```
```java
package EightB;

import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class SpringApp {

	public static void main(String[] args) {
		AnnotationConfigApplicationContext ctx = new AnnotationConfigApplicationContext();
		ctx.register(MyConfiguration.class);
		ctx.refresh();

		MyBean mb1 = ctx.getBean(MyBean.class);
		System.out.println(mb1.hashCode());

		MyBean mb2 = ctx.getBean(MyBean.class);
		System.out.println(mb2.hashCode());

		ctx.close();
	}

}
	
```
	
Output:
	
```
MyBean instance created
Verifying Resources
2145970759
2145970759
Shutdown All Resources
Closing All Resources
```

9. Write a Java program to demonstrate Complete Bean Life cycle.
	
```java
package lifecycle.beans;

public class Hello 
{
	 public void init() throws Exception
	    {
	        System.out.println(
	            "Welcome to SpringCore ");
	    }
	 
	    // This method executes
	    // when the spring container
	    // is closed
	    public void destroy() throws Exception
	    {
	        System.out.println(
	            "Destroy method created");
	           
	    }
	}
	
```

```java
package lifecycle.beans;
import org.springframework
.context
.ConfigurableApplicationContext;

import org.springframework
.context.support
.ClassPathXmlApplicationContext;
public class Main {
    public static void main(String[] args)
        throws Exception
    {
 
        // Loading the Spring XML configuration
        // file into the spring container and
        // it will create the instance of
        // the bean as it loads into container
 
        ConfigurableApplicationContext cap
            = new ClassPathXmlApplicationContext(
                "spring9.xml");
 
        // It will close the spring container
        // and as a result invokes the
        // destroy() method
        cap.close();
    }
}
	
```
	
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns = "http://www.springframework.org/schema/beans"

xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation = "http://www.springframework.org/schema/beans
   http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">
    <bean id="hw" class="lifecycle.beans.Hello"
            init-method="init" destroy-method="destroy"/>
            </beans>
	
```
	
Output:
	
```
Welcome to SpringCore 
Destroy method created
```

10. Write a java program to demonstrate ApplicationContextAware interface.
	
```java
package AplicationContextAware;

public class Employee {
	private String Name;

	public String getName() {
		return Name;
	}

	public void setName(String name) {
		Name = name;
	}

	@Override
	public String toString() {
		return "employee [Name=" + Name + "]";
	}
}
	
```
	
```java
package AplicationContextAware;

import org.springframework.beans.BeansException;
import org.springframework.context.ApplicationContext;
import org.springframework.context.ApplicationContextAware;

public class AppContextAwareImpl implements ApplicationContextAware {
	private ApplicationContext applicationContext;

	public void setApplicationContext(ApplicationContext applicationContext) throws BeansException {
		// TODO Auto-generated method stub
		System.out.println("set Application Context method is called by the spring container");
		this.applicationContext = applicationContext;
	}

	public void displayEmployeeDetails() {
		Employee employee = applicationContext.getBean("employee", Employee.class);
		System.out.println("Got employee object from the applicationContext(Spring Container)=" + employee);

	System.out.println("is employee object Singleton =" + applicationContext.isSingleton("employee"));
	}
}
	
```
	
```java
package AplicationContextAware;

import org.springframework.context.support.ClassPathXmlApplicationContext;

public class App {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		ClassPathXmlApplicationContext applicationContext= new ClassPathXmlApplicationContext("applicationContext.xml");
		AppContextAwareImpl applicationContextAwareImpl= applicationContext.getBean("applicationContextAware",AppContextAwareImpl.class);
         applicationContextAwareImpl.displayEmployeeDetails();
         applicationContext.close();
	}

}
	
```
	
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://www.springframework.org/schema/beans
 http://www.springframework.org/schema/beans/spring-beans.xsd">
 
    <bean id="employee" class="AplicationContextAware.Employee">
           <property name="name" value ="peter" />
           </bean>
     <bean id="applicationContextAware"  class="AplicationContextAware.AppContextAwareImpl"></bean>
</beans>
	
```
	
Output:
	
```
set Application Context method is called by the spring container
Got employee object from the applicationContext(Spring Container)=employee [Name=peter]
is employee object Singleton =true

```
