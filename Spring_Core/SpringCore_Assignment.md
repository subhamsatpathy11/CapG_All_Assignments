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