# Spring MVC Assignment

1. Design and develop a Spring MVC web application as follows:

 - Create index.jsp page having one hyperlink. When user dicks on that hyperlink, it should call HelloWorldController.
 - Design HelloWorldController class that returns a view helloWorld.jsp
 - Design a hello World jsp page that displays "Hello World" message.

```java
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller

public class HelloController {

	@RequestMapping("/hello")
	public String redirect() {
		return "helloWorld";
	}}
```

```jsp
<!--HelloWorld.jsp--> 

<?xml version="1.0" encoding="ISO-8859-1" ?>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
	pageEncoding="ISO-8859-1"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<!-- <meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" /> -->
<title>Insert title here</title>
</head>

<body>
	<h2>
		HeLLo World
		<h2>
</body>
</html>
```

```jsp
<!--index.jsp-->

<?xml version="1.0" encoding="ISO-8859-1" ?>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
<title>Insert title here</title>
</head>
<body>
<a href="hello">Click here...</a> 
</body>
</html>
```

```xml
<!--servlet-dispatcher.xml-->

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"  
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns:context="http://www.springframework.org/schema/context"  
    xmlns:mvc="http://www.springframework.org/schema/mvc"  
    xsi:schemaLocation="  
        http://www.springframework.org/schema/beans  
        http://www.springframework.org/schema/beans/spring-beans.xsd  
        http://www.springframework.org/schema/context  
        http://www.springframework.org/schema/context/spring-context.xsd  
        http://www.springframework.org/schema/mvc  
        http://www.springframework.org/schema/mvc/spring-mvc.xsd">  
  
    <!-- Provide support for component scanning -->  
    <context:component-scan base-package="com.javatpoint" />  
  
    <!--Provide support for conversion, formatting and validation -->  
    <mvc:annotation-driven/>  
<!-- Define Spring MVC view resolver -->  
<bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver">  
        <property name="prefix" value="/WEB-INF/"></property>  
        <property name="suffix" value=".jsp"></property>          
     </bean>  
</beans>
```

```xml
<!--web.xml-->

<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://java.sun.com/xml/ns/javaee" xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd" id="WebApp_ID" version="3.0">  
  <display-name>SpringMVC</display-name>  
   <servlet>    
    <servlet-name>spring</servlet-name>    
    <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>    
    <load-on-startup>1</load-on-startup>      
</servlet>    
<servlet-mapping>    
    <servlet-name>spring</servlet-name>    
    <url-pattern>/hello</url-pattern>    
</servlet-mapping>    
</web-app>
```

2. Design and develop a Spring MVC web application as follows

 - Design simplelnterest jsp to capture principal amount, no. of years and rate of interest
 - Simpleinterest Controller will receive these inputs and calculates simple interest.
 - Simpleinterest Controller shoulukaturn a view that contains simple interest.

```java
package com.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.ModelAttribute;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.servlet.ModelAndView;

@Controller
public class SimpleInterestController {
	
	@RequestMapping(value = "/getvalues.html", method = RequestMethod.GET)
	public ModelAndView getForm()
	{
		ModelAndView model = new ModelAndView("Values");
		return model;
	}

	@RequestMapping(value = "/submitvalues.html", method = RequestMethod.POST)
	public ModelAndView acceptForm(@RequestParam("amount") Double amount, @RequestParam("rate") Double rate, @RequestParam("time") int time)
	{
		ModelAndView model = new ModelAndView("Calculate");
		model.addObject("message", "Simple Interest : " + "(" + amount + "*" + rate + "*" + time + ")/100 = " + (amount*rate*time)/100);
		return model;
	}
	
}
```

```xml
<!--web.xml-->

<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd" id="WebApp_ID" version="4.0">
  <display-name>SpringMVC</display-name>
 
 <servlet>
 	<servlet-name>spring-dispatcher</servlet-name>
 		<servlet-class>
 			org.springframework.web.servlet.DispatcherServlet
 		</servlet-class>
 </servlet>
 
 <servlet-mapping>
 	<servlet-name>spring-dispatcher</servlet-name>
 	<url-pattern>/</url-pattern>
 </servlet-mapping>
 
 
</web-app>
```

```xml
<!--spring-servlet.xml-->

<?xml version="1.0" encoding="UTF-8"?>
 
<beans xmlns="http://www.springframework.org/schema/beans"
xmlns:context="http://www.springframework.org/schema/context"
xmlns:mvc="http://www.springframework.org/schema/mvc" 
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="
    http://www.springframework.org/schema/beans     
    http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
    http://www.springframework.org/schema/context 
    http://www.springframework.org/schema/context/spring-context-3.0.xsd
    http://www.springframework.org/schema/mvc
    http://www.springframework.org/schema/mvc/spring-mvc-3.0.xsd">



   <mvc:annotation-driven/>	
   <context:component-scan base-package = "com.controller"/>
 
 
    <bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name = "prefix">
            <value>/WEB-INF/</value>
        </property>
          <property name = "suffix">
              <value>.jsp</value>
          </property>
    </bean> 
</beans>
```

```jsp
<!--Values.jsp-->

<html>
<body>
	
	<h1>Student Application Form</h1>
	
	<form action = "/AssignmentQ2/submitvalues.html" method = "post">
	
		<p> Amount : <input type = "number" name = "amount"/></p>
		<p> Rate : <input type = "number" name = "rate"/></p>
		<p> Years : <input type = "number" name = "time"/></p>
		<input type = "submit" value = "Submit"/>
	
	</form>

</body>

```

```jsp
<!--Calculate.jsp-->

<html>
<body>
	<h1>Simple Interest</h1>
	<h2>${message}</h2>
</body>
</html>
```

3. Design and develop a Spring MVC web application as follows:

 - Design a' User model class having attributes username, password & email.
 - Design login.jsp to capture username and password (Use ModelAttribute)
 - UserController should receive the credentials and return "success" view if user is authenticated successfully, else retum "error" view.
 - Design success jsp and error jsp

```java
//UserController.java

package com.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.validation.BindingResult;
import org.springframework.web.bind.annotation.ModelAttribute;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.servlet.ModelAndView;

@Controller
public class UserController {
	
	@RequestMapping(value = "/getdetails.html", method = RequestMethod.GET)
	public ModelAndView getForm()
	{
		ModelAndView model = new ModelAndView("Details");
		return model;
	}
	
	@ModelAttribute
	public void addCommonObjects(Model model)
	{
		model.addAttribute("message", "Logged In");
	}
	
	@RequestMapping(value = "/submitdetails.html", method = RequestMethod.POST)
	public ModelAndView acceptForm(@ModelAttribute("detail1") Detail detail1, BindingResult result)
	{
		if(result.hasErrors())
		{
			ModelAndView model = new ModelAndView("Details");
			return model;
		}
		
		ModelAndView model = new ModelAndView("Page");
		return model;
	}

}
```
```java
//Detail.java

package com.controller;

public class Detail {
	
	private String username;
	private String password;
	private String email;
	
	public String getUsername()
	{
		return username;
	}
	public void setUsername(String username)
	{
		this.username = username;
	}
	
	public String getPassword()
	{
		return password;
	}
	public void setPassword(String password)
	{
		this.password = password;
	}
	
	public String getEmail()
	{
		return email;
	}
	public void setEmail(String email)
	{
		this.email = email;
	}

}
```
```xml
<!--web.xml-->

<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd" id="WebApp_ID" version="4.0">
  <display-name>SpringMVC</display-name>
 
 <servlet>
 	<servlet-name>spring-dispatcher</servlet-name>
 		<servlet-class>
 			org.springframework.web.servlet.DispatcherServlet
 		</servlet-class>
 </servlet>
 
 <servlet-mapping>
 	<servlet-name>spring-dispatcher</servlet-name>
 	<url-pattern>/</url-pattern>
 </servlet-mapping>
 
 
</web-app>
```
```xml
<!--spring-servlet.xml-->

<?xml version="1.0" encoding="UTF-8"?>
 
<beans xmlns="http://www.springframework.org/schema/beans"
xmlns:context="http://www.springframework.org/schema/context"
xmlns:mvc="http://www.springframework.org/schema/mvc" 
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="
    http://www.springframework.org/schema/beans     
    http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
    http://www.springframework.org/schema/context 
    http://www.springframework.org/schema/context/spring-context-3.0.xsd
    http://www.springframework.org/schema/mvc
    http://www.springframework.org/schema/mvc/spring-mvc-3.0.xsd">



   <mvc:annotation-driven/>	
   <context:component-scan base-package = "com.controller"/>
 
 
    <bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name = "prefix">
            <value>/WEB-INF/</value>
        </property>
          <property name = "suffix">
              <value>.jsp</value>
          </property>
    </bean> 
</beans>
```
```jsp
<!--Details.jsp-->

<html>
<body>
	
	<form:errors path = "detail1.*/"/>
	
	<form action = "/AssignmentQ3/submitdetails.html" method = "post">
	
		<p> Username : <input type = "text" name = "username"/></p>
		<p> Password : <input type = "password" name = "password"/></p>
		<p> Email : <input type = "email" name = "email"/></p>
		<input type = "submit" value = "Submit"/>
	
	</form>

</body>
</html>
```
```jsp
<!--Page.jsp-->

<html>
<body>
	<h1>Logged In</h1>
	<h2>${message}</h2>
	
	<table>
	
	<tr>
		<td>User name : </td>
		<td>${detail1.username}</td>
	</tr>
	<tr>
		<td>Email : </td>
		<td>${detail1.email}</td>
	</tr>
	
	</table>
</body>
</html>
```

4. Design and develop a Spring MVC web application as follows 
 
 - Design a User model class having attributes username, password & email,
 - Design registration.jsp to capture username, password and email. (Use ModelAttribute)
 - UserController should receive the details and store into a database. (Use JdbcTemplate). 
 - After successful registration, it should return login view.
 - Design login jsp to capture username and password (Use ModelAttribute) 
 - UserController should receive the credentials and return "success" view if user is authenticated successfully, else return "error" view f Design success jap and error sp

```java
//UserController.java

package com.controller;

import java.util.ArrayList;
import java.util.List;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.ModelAttribute;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.servlet.ModelAndView;

@Controller
public class UserController {
	
	
	List<Userdetails> list = new ArrayList<Userdetails>();
	
	@RequestMapping(value = "/registerSuccess.html", method=RequestMethod.POST)
	public String newusers(@RequestParam("usname") String unm,@RequestParam("uspwd") String pwd,@RequestParam("usmail") String mail) {
		Userdetails user1 = new Userdetails(unm,pwd,mail);
		list.add(user1);
		return "redirect:/login.html";
	}
	
	@RequestMapping(value = "/login.html")
	public ModelAndView tryagain(@ModelAttribute("user1") Userdetails user1) {
		
		ModelAndView model = new ModelAndView("loginpage");
		model.addObject(user1);
		return model;
		
	}
	
	@RequestMapping(value = "/Authdetails.html", method=RequestMethod.POST)
	public ModelAndView getvalues(@ModelAttribute("user1") Userdetails user1) {
		for(int i=0;i<list.size();i++) {
			if(list.get(i).getUsname().equals(user1.usname) && list.get(i).getUspwd().equals(user1.uspwd)) {
				ModelAndView model = new ModelAndView("success");
				model.addObject(user1);
				return model;
				}else {
					ModelAndView model = new ModelAndView("Error");
					model.addObject(user1);
					return model;
				}
		}
		return null;
		
	}
}
```

```java
//Userdetails.java

package come.controller;

public class Userdetails {
	String usname,uspwd,usmail;
public Userdetails() {}
	
	public Userdetails(String usname, String uspwd, String usmail) {
		super();
		this.usname = usname;
		this.uspwd = uspwd;
		this.usmail = usmail;
	}

	public String getUsname() {
		return usname;
	}

	public void setUsname(String usname) {
		this.usname = usname;
	}

	public String getUspwd() {
		return uspwd;
	}

	public void setUspwd(String uspwd) {
		this.uspwd = uspwd;
	}

	public String getUsmail() {
		return usmail;
	}

	public void setUsmail(String usmail) {
		this.usmail = usmail;
	}

}
```

```xml
<!--web.xml-->

<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd" id="WebApp_ID" version="4.0">
  <display-name>SpringMVC</display-name>
 
 <servlet>
 	<servlet-name>spring-dispatcher</servlet-name>
 		<servlet-class>
 			org.springframework.web.servlet.DispatcherServlet
 		</servlet-class>
 </servlet>
 
 <servlet-mapping>
 	<servlet-name>spring-dispatcher</servlet-name>
 	<url-pattern>/</url-pattern>
 </servlet-mapping>
 
 
</web-app>
```

```xml
<!--spring-servlet.xml-->

<?xml version="1.0" encoding="UTF-8"?>
 
<beans xmlns="http://www.springframework.org/schema/beans"
xmlns:context="http://www.springframework.org/schema/context"
xmlns:mvc="http://www.springframework.org/schema/mvc" 
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="
    http://www.springframework.org/schema/beans     
    http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
    http://www.springframework.org/schema/context 
    http://www.springframework.org/schema/context/spring-context-3.0.xsd
    http://www.springframework.org/schema/mvc
    http://www.springframework.org/schema/mvc/spring-mvc-3.0.xsd">



   <mvc:annotation-driven/>	
   <context:component-scan base-package = "com.controller"/>
 
 
    <bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name = "prefix">
            <value>/WEB-INF/</value>
        </property>
          <property name = "suffix">
              <value>.jsp</value>
          </property>
    </bean> 
</beans>
```

```jsp
<!--login.jsp-->

<html>
<body>
	
	<form action = "/AssignmentQ3/Authdetails.html" method = "post">
	
		<p> Username : <input type = "text" name = "username"/></p>
		<p> Password : <input type = "password" name = "password"/></p>
		<p> Email : <input type = "email" name = "email"/></p>
		<input type = "submit" value = "Submit"/>
	
	</form>

</body>
</html>
```

```jsp
<!--success.jsp-->

<html>
<body>
	<h1>Logged In</h1>
	<h2>${message}</h2>
	
	<table>
	
	<tr>
		<td>User name : </td>
		<td>${user1.usname}</td>
	</tr>
	<tr>
		<td>Email : </td>
		<td>${user1.usmail}</td>
	</tr>
	
	</table>
</body>
</html>
```
