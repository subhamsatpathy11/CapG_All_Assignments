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
//HelloWorld.jsp 

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
//index.jsp

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
srvlet-dispatcher.xml

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
//web.xml

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
