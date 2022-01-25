# Spring Core Assignment

1. Create an Address class with the following attributes:- street, city, state, zip, country Create an Customer class with the following attributes:- customerld, customer Name, customerContact, customerAddress. object and print details of Customer. Inject the Address bean into Customer bean using setter injection Create a Test class with main() method, get Customer bean from ApplicationContext 
Also write the JUnit Test cases for above program.

 - Modify the above application and inject the bean using constructor injection
 - Use XML based Configuraion.

```java
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
   </beans>
```

2.
