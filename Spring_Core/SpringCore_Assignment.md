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

 - @repository
	
```java
public interface BankCardDAO {
    
    public BankCardDTO insertBankCard(String bankName, String cardNumber, String createDate);
}	
```
```java
// Annotated this object as a DAO function bean.
@Repository("bcDao")
public class BankCardDAOImpl implements BankCardDAO {
    @Override
    public BankCardDTO insertBankCard(String bankName, String cardNumber, String createDate) {
        BankCardDTO ret = new BankCardDTO();
        ret.setBankName(bankName);
        ret.setCardNumber(cardNumber);
        ret.setCreateDate(createDate);
        
        System.out.println("Bank card has been inserted by BankCardDAOImpl. Bank name : " + bankName + " , card number : " + cardNumber + " , create date : " + createDate);
        return ret;
    }
}	
```
	
 - @Service
	
```java
public interface BankCardManager {
    public BankCardDTO createBankCard(String bankName, String cardNumber, String createDate);
    
}	
```
```java
// Annotated this object as a service bean.
@Service("bcManager")
public class BankCardManagerImpl implements BankCardManager {
    @Autowired
    private BankCardDAO bankCardDao;
    
    @Override
    public BankCardDTO createBankCard(String bankName, String cardNumber, String createDate) {
        
        System.out.println("Bank card has been created by BankCardManagerImpl. Bank name : " + bankName + " , card number : " + cardNumber + " , create date : " + createDate);
        return this.bankCardDao.insertBankCard(bankName, cardNumber, createDate);
    }
}	
```
	
 - @controller
	
```java
// Annotated this object as a controller bean.
@Controller("bcController")
public class BankCardController {
    @Autowired
    private BankCardManager bcManager;
    
    public BankCardDTO createBankCard(String bankName, String cardNumber, String createDate)
    {
        return this.bcManager.createBankCard(bankName, cardNumber, createDate);
    }
}
```
```java
public class TestAutowireUseAnnotation {

    public static void main(String[] args) {
           // Initiate Spring application context.
        ApplicationContext springAppCtx = new ClassPathXmlApplicationContext("AutowireByAnnotationBeanSettings.xml");

                // Get @Controller annotated bean by id.
        BankCardController bcController = (BankCardController)springAppCtx.getBean("bcController");
        
        bcController.createBankCard("Bank Of China", "BOC888888", "2017/08/08");
    }

}	
```
	
Taking another example for @autowired, @configuration

 - @autowired
	
```java

import org.springframework.beans.factory.annotation.Autowired;

public class TextEditor {
   @Autowired
   private SpellChecker spellChecker;

   public TextEditor() {
      System.out.println("Inside TextEditor constructor." );
   }
   public SpellChecker getSpellChecker( ){
      return spellChecker;
   }
   public void spellCheck(){
      spellChecker.checkSpelling();
   }
}	
```
	
```xml
<?xml version = "1.0" encoding = "UTF-8"?>

<beans xmlns = "http://www.springframework.org/schema/beans"
   xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
   xmlns:context = "http://www.springframework.org/schema/context"
   xsi:schemaLocation = "http://www.springframework.org/schema/beans
   http://www.springframework.org/schema/beans/spring-beans.xsd
   http://www.springframework.org/schema/context
   http://www.springframework.org/schema/context/spring-context.xsd">

   <context:annotation-config/>

   <!-- Definition for textEditor bean -->
   <bean id = "textEditor" class = "io.third.TextEditor">
   </bean>

   <!-- Definition for spellChecker bean -->
   <bean id = "spellChecker" class = "io.third.SpellChecker">
   </bean>

</beans>	
```

 - @configuration
	
```java
DemoManager.java and DemoManagerImpl.java
public interface DemoManager {
    public String getServiceName();
}
 
public class DemoManagerImpl implements DemoManager
{
    @Override
    public String getServiceName()
    {
        return "My first service with Spring 3";
    }
}	
```
	
```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
 
import com.howtodoinjava.core.beans.DemoManager;
import com.howtodoinjava.core.beans.DemoManagerImpl;
 
@Configuration
public class ApplicationConfiguration {
 
    @Bean(name="demoService")
    public DemoManager helloWorld() 
    {
        return new DemoManagerImpl();
    }
}	
```
	
```java

import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
 
import com.howtodoinjava.core.beans.DemoManager;
import com.howtodoinjava.core.config.ApplicationConfiguration;
 
public class VerifySpringCoreFeature
{
    public static void main(String[] args)
    {
        ApplicationContext context = new AnnotationConfigApplicationContext(ApplicationConfiguration.class);
 
        DemoManager  obj = (DemoManager) context.getBean("demoService");
 
        System.out.println( obj.getServiceName() );
    }
}
```
	
 - @configuration example
	
```java
@Configuration
public class ApplicationContextTestResourceNameType {

    @Bean(name="namedFile")
    public File namedFile() {
        File namedFile = new File("namedFile.txt");
        return namedFile;
    }
}	
```
	
5. Write a program to demonstrate use of @Resource, @inject, @Required annotations
	
 - @resource
	
```java
@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(
  loader=AnnotationConfigContextLoader.class,
  classes=ApplicationContextTestResourceNameType.class)
public class FieldResourceInjectionIntegrationTest {

    @Resource(name="namedFile")
    private File defaultFile;

    @Test
    public void givenResourceAnnotation_WhenOnField_ThenDependencyValid(){
        assertNotNull(defaultFile);
        assertEquals("namedFile.txt", defaultFile.getName());
    }
}
@Configuration
class ApplicationContextTestResourceNameType {

    @Bean(name="namedFile")
    public File namedFile() {
        File namedFile = new File("namedFile.txt");
        return namedFile;
    }
}
```
 - @inject
	
```java
@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(
  loader=AnnotationConfigContextLoader.class,
  classes=ApplicationContextTestInjectQualifier.class)
public class FieldQualifierInjectIntegrationTest {

    @Inject
    private ArbitraryDependency defaultDependency;

    @Inject
    private ArbitraryDependency namedDependency;

    @Test
    public void givenInjectQualifier_WhenOnField_ThenDefaultFileValid(){
        assertNotNull(defaultDependency);
        assertEquals("Arbitrary Dependency",
          defaultDependency.toString());
    }

    @Test
    public void givenInjectQualifier_WhenOnField_ThenNamedFileValid(){
        assertNotNull(defaultDependency);
        assertEquals("Another Arbitrary Dependency",
          namedDependency.toString());
    }
}	
```
 - We can take a separate example to show how @required works within code implementation
	
```java
import org.springframework.beans.factory.annotation.Required;

public class Student {
   private Integer age;
   private String name;

   @Required
   public void setAge(Integer age) {
      this.age = age;
   }
   public Integer getAge() {
      return age;
   }
   
   @Required
   public void setName(String name) {
      this.name = name;
   }
   public String getName() {
      return name;
   }
}	
```
```java
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class MainApp {
   public static void main(String[] args) {
      ApplicationContext context = new ClassPathXmlApplicationContext("Beans.xml");
      
      Student student = (Student) context.getBean("student");
      System.out.println("Name : " + student.getName() );
      System.out.println("Age : " + student.getAge() );
   }
}	
```
	
```xml
<beans xmlns = "http://www.springframework.org/schema/beans"
   xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
   xmlns:context = "http://www.springframework.org/schema/context"
   xsi:schemaLocation = "http://www.springframework.org/schema/beans
   http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
   http://www.springframework.org/schema/context
   http://www.springframework.org/schema/context/spring-context-3.0.xsd">

   <context:annotation-config/>

   <!-- Definition for student bean -->
   <bean id = "student" class = "io.fifth.Student">
      <property name = "name" value = "Zara" />

      <!-- try without passing age and check the result -->
      <!-- property name = "age"  value = "11"-->
   </bean>

</beans>
```
	
Output:
	
```
Property 'age' is required for bean 'student'
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
