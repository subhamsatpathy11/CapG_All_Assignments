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

 - Write a program where answers is of type List<String> or String[] 	
 - Write a program where answers is of type Set<String>
 - Write a program where answers is of type Map<Integer, String>. In case of Map, Integer value represents answer's sequence number.
 - Create a Test class with main() method, get Question bean from ApplicationContext object and print question and its answers. e. Also write the JUnit Test cases for above program.
	
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

	
Use XML based configuration.
	

	
