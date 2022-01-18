# Generics Assignment

1. Use a Hashset to hold employee objects. Upon running application, the details of the employees added to the HashSet should be displayed.

| Employee (class) |
|------------------|
| id | 
| name |
| salary |
| department |
| displayDetails() |

Feel free to add properties and methods to employee class

Note - If we try to store any object other than employee object in hashset, we should not be allowed to. 

```java
//class name - Hash

import java.util.HashSet;

public class Hash {
  
   public static void main(String[] args)
   {
      HashSet<Employee>set=new HashSet<Employee>();
      Employee e=new Employee(1,"SAM","TAX",25000.0);
      set.add(e);
      for(Employee e1:set)
      {
         e.Displaydetails();
      }
   }
  
}
```

```java
//class name - Employee

public class Employee {
  
    int id;
    String name,dep;
    double sal;
    public Employee(int id, String name, String dep, double sal) 
    {
        super();
        this.id = id;
        this.name = name;
        this.dep = dep;
    }
    public void Displaydetails() {
    	System.out.println(id+" "+name+" "+dep+" "+sal);
    }
}

```

Output:

```
1 SAM TAX 25000.0
```

2. Write an application to hold 10 random int values as key and random double values as values for HashMap. Print the data store in HashMap.

```java
//class name - Map

import java.util.HashMap;
public class Map {
     public static void main(String[] args)
     { 
	        Map<Integer,Double> m = new HashMap<>();
       
          m.put(34, 33.9);
          m.put(67, 67.7);
          m.put(96, 56.7);
          m.put(35, 3.5);
          m.put(11, 33.9);
          m.put(25, 5.9);
          m.put(99, 89.8);
          m.put(56, 23.5);
          m.put(84, 98.5);
          m.put(54, 87.6);
       
	        System.out.println(m);
	     
     }
}

```

Output:

```
{96=56.7, 34=33.9, 67=67.7, 35=3.5, 99=89.8, 84=98.5, 54=87.6, 56=23.5, 25=5.9, 11=33.9}
```

3.  Write a generic method to exchange the positions of two different elements in an array.

```java
//class name - Swap

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.List;


public class Swap {
		public static final <T> void swap (T[] a, int i, int j) {
			T t = a[i];
			a[i] = a[j];
			a[j] = t;
		}
		private static void test() {
				String [] arr = {"My", "Name", "Is", "Subham"};
				System.out.println("Original Array: "+Arrays.toString(arr));
				swap(arr, 0, 3);
				System.out.println("Swapped Array: "+Arrays.toString(arr));
		
		}
		public static void main(String...args)
		{
				test();
		}
}
```
Output:

```
Original Array: [My, Name, Is, Subham]
Swapped Array: [Subham, Name, Is, My]
```

4. Design a class named Pair which has two properties. The name of the first property is key and that of the second property Is value. When designing the class take case of the following scenarios:

 - Create an Object of Pair class to store String value for the property key and String value for the property value. Restriction Apart from String type no other types should be acceptable as Key or value Input

   e.g.

   myObj.setkey("1"); 
   myObj.setValue("Hello");
   
```java
import java.util.*;

	    public class Pair {
	    public static void main(String[] args)
	     {
		Map<String,String> map=new HashMap<>();
             	map.put("Hi", "8");
		map.put("hello", "9");
             	System.out.println(map);
		 
	     }
	}

```
Output:
```
{Hi=8, hello=9}
```

 - Create an object of the class Pair to store String value for the property key and java.util.Date as value for the property value

   myObj setKey("Today Is"); 
   myobl setValue(new java.util.Date());

   Note: In scenario a, no data apart from String should be used for key and value, in scenario b. no data apart from String for key and java.util.Date should be allowed
   
```java
import java.util.*;

	    public class pair1 
            {
	     	public static void main(String[] args)
	        {    
		  Map<String,Date> map=new HashMap<>();
		  map.put("Today is", new java.util.Date());
		  System.out.println(map);
				
              	}
            }

```

Output:

```
{Today is=Sat Jan 15 21:02:19 IST 2022}
```
