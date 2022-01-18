# Collections Assignment

1. Given a Tree Map<Long, Contact> which has phone numbers for keys and contact objects for values.

 Write solutions to

 - Fetch all the keys and print them,
 - Fetch all the values and print them
 - Print all key-value pairs

 Note:

 - Contacts should be stored in descending order of phone number
 - Contact Class:
 
    PhoneNumer: <long>
    Name: <String>
    Email: <String>
    Gender: <Enum>
  
```java
//class name Tree1
	
import java.util.Collections;
import java.util.Map;
import java.util.Set;
import java.util.TreeMap;
import tree.contact.gender;
public class Tree1 {
	public static void main(String[] args)
	{
		Map<Long,Contact> map=new TreeMap<Long,Contact>();
		Contact c1=new Contact((long)89034567,"ram","ram@.com",gender.m);
		Contact c2=new Contact((long)12345679,"raj","raj@.com",gender.m);
		Contact c3=new Contact((long)67864747,"sam","sam@.com",gender.Fe);
		Contact c4=new Contact((long)45754757,"tom","tom@.com",gender.m);
		map.put((long)89034567, c1);
		map.put((long)12345679, c2);
		map.put((long)67864747, c3);
		map.put((long)45754757, c4);
		 for(Map.Entry<Long, Contact> entry:map.entrySet()){  
			 Long key=entry.getKey();  
		        Contact c=entry.getValue();  
		        System.out.println(key+" Details:");  
		        System.out.println(c.phoneno+" "+c.name+" "+c.email+" "+c.g);  
		 }
		 System.out.println("............");
		 System.out.println("After Sorted:");
		        Map<Long,Contact> sortedMapDesc = new TreeMap<>(
		                Collections.reverseOrder());
		        sortedMapDesc.putAll(map);
		        for(Map.Entry<Long,Contact> entry1 : sortedMapDesc.entrySet())
		        {
		        	 Long key=entry1.getKey();  
				        Contact c8=entry1.getValue();  
				        System.out.println(key+" Details:");
		        System.out.println(c8.phoneno+" "+c8.name+" "+c8.email+" "+c8.g);  
		        }     
		    
	}
}

```
	
```java
//class name - Contact
	
package tree;
import java.util.EnumSet;

public class Contact {
	long phoneno;
	String name,email;
	public enum gender {Fe,m}
	gender g;
	/**
	 * @param phoneno
	 * @param name
	 * @param email
	 * @param g
	 */
	public Contact(long phoneno, String name, String email, gender g) {
		super();
		this.phoneno = phoneno;
		this.name = name;
		this.email = email;
		this.g = g;
	}
	public long getPhoneno() {
		return phoneno;
	}
	public void setPhoneno(long phoneno) {
		this.phoneno = phoneno;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public String getEmail() {
		return email;
	}
	public void setEmail(String email) {
		this.email = email;
	}
	public gender getG() {
		return g;
	}
	public void setG(gender g) {
		this.g = g;
	}
}

```
  Output:
  
```
12345679 Details:
12345679 raj raj@.com m
45754757 Details:
45754757 tom tom@.com m
67864747 Details:
67864747 sam sam@.com Fe
89034567 Details:
89034567 ram ram@.com m
............
After Sorted:
89034567 Details:
89034567 ram ram@.com m
67864747 Details:
67864747 sam sam@.com Fe
45754757 Details:
45754757 tom tom@.com m
12345679 Details:
12345679 raj raj@.com m

```
  
2. Write an application to store 10 unique product objects. In case there is an attempt to add a duplicate product, it should be silently rejected.
  
```java
//class name - Function
  
public class Function implements Comparable<Function> 
{
	
	private String product_name;
	private int product_id;
	
	Function(String product_name, int product_id)
	{
		this.product_id = product_id;
		this.product_name = product_name;
	}
	
	private String getName()
	{
		return product_name;
	}
	
	public int getId()
	{
		return product_id;
	}
	
	public int compareTo(Function f)
	{
		if(product_id == f.getId())
		{
			return 0;
		}
		else if(product_name.compareTo(f.getName()) < 0)
		{
			return -1;
		}
		else
		{
			return -1;
		}
	}
	
	public String toString()
	{
		return product_name + " - " + product_id;
	}
	
}
```
```java
//class name - Duplicate

import java.util.TreeSet;

public class Duplicate {

	public static void main(String[] args) {
		
		TreeSet<Function> func = new TreeSet<>();
		
		func.add(new Function("iPhone",1));
		func.add(new Function("Samsung",2));
		func.add(new Function("Motorola",3));
		//adding a duplicate product name
		func.add(new Function("iPhone",4));
		//adding a duplicate product ID
		func.add(new Function("OnePlus",2));
		func.add(new Function("Redmi",5));
		
		for(Function f : func)
		{
			System.out.println(f);
		}
		
	}

}

```
Output:
	
```
Redmi - 5
iPhone - 4
Motorola - 3
Samsung - 2
iPhone - 1
```

3. Store atleast 10 Employee objects in a TreeSet<Employee>. When your application runs the user should be asked to selct one of the options upon which you will print the employee details in a sorted manner.
	
```java
//class name - Options


public class Options {
	
	private int id;
	private int salary;
	private String name;
	private String department;
	
	public Options(int id, int salary, String name, String department)
	{
		this.id = id;
		this.salary = salary;
		this.name = name;
		this.department = department;
	}
	
	public String getName()
	{
		return name;
	}
	public void setName(String name)
	{
		this.name = name;
	}
	public String getDep()
	{
		return department;
	}
	public void setDep(String department)
	{
		this.department = department;
	}
	
	public int getId()
	{
		return id;
	}
	public int getSalary()
	{
		return salary;
	}

}

```

```java
//class name - IdCompare
	
import java.util.Comparator;

public class IdCompare implements Comparator<Options>
{
	
	public int compare(Options o1, Options o2)
	{
		return o1.getId() - o2.getId();
	}

}

```
	
```java
//class name - NameCompare
	
import java.util.Comparator;

public class NameCompare implements Comparator<Options>
{
	
	public int compare(Options o1, Options o2)
	{
		return o1.getName().compareTo(o2.getName());
	}

}

```
	
```java
//class name - DepComapre
	
import java.util.Comparator;

public class DepComapre implements Comparator<Options>
{
	
	public int compare(Options o1, Options o2)
	{
		return o1.getDep().compareTo(o2.getDep());
	}

}

```
	
```java
//class name - SalaryCompare
	
import java.util.Comparator;

public class SalaryCompare implements Comparator<Options>{

	public int compare(Options o1, Options o2)
	{
		return o1.getSalary() - o2.getSalary();
	}
	
}

```
```java
//class name - TestCompare
	
import java.util.*;

public class TestCompare {

	public static void main(String[] args) {
		
		Scanner scan = new Scanner(System.in);
		System.out.println("You want to sort in order of \n\n1.ID\n2.Name\n3.Department\n4.Salary\n\nEnter your option: ");
		int option = scan.nextInt();
		
		switch(option)
		{
		case 1:
			TreeSet<Options> set = new TreeSet<Options>(new IdCompare());
			
			set.add(new Options(1,23000,"Subhasish","A"));
			set.add(new Options(2,32000,"Vedant","C"));
			set.add(new Options(3,13000,"Subham","F"));
			
			System.out.println(" Increasing Order with the Id : ");
			
			for(Options o : set)
			{
				System.out.print(o.getId()+","+o.getName()+","+o.getDep()+","+o.getSalary());
				System.out.println();
			}
			
			break;
			
		case 2:
			TreeSet<Options> setN = new TreeSet<Options>(new NameCompare());
			
			setN.add(new Options(1,23000,"Subhasish","A"));
			setN.add(new Options(2,32000,"Vedant","C"));
			setN.add(new Options(3,13000,"Subham","F"));
			
			System.out.println(" Increasing Order with the Name : ");
			
			for(Options o : setN)
			{
				System.out.print(o.getId()+","+o.getName()+","+o.getDep()+","+o.getSalary());
				System.out.println();
			}
			
			break;
		
		case 3:
			TreeSet<Options> setD = new TreeSet<Options>(new DepComapre());
			
			setD.add(new Options(1,23000,"Subhasish","A"));
			setD.add(new Options(2,32000,"Vedant","C"));
			setD.add(new Options(3,13000,"Subham","F"));
			
			System.out.println(" Increasing Order with the Department : ");
			
			for(Options o : setD)
			{
				System.out.print(o.getId()+","+o.getName()+","+o.getDep()+","+o.getSalary());
				System.out.println();
			}
			
			break;
			
		case 4:
			TreeSet<Options> setS = new TreeSet<Options>(new SalaryCompare());
			
			setS.add(new Options(1,23000,"Subhasish","A"));
			setS.add(new Options(2,32000,"Vedant","C"));
			setS.add(new Options(3,13000,"Subham","F"));
			
			System.out.println(" Increasing Order with the Salary : ");
			
			for(Options o : setS)
			{
				System.out.print(o.getId()+","+o.getName()+","+o.getDep()+","+o.getSalary());
				System.out.println();
			}
			
			break;
		
		}
		
		
	}

}
```

Output:
	
```
You want to sort in order of 

1.ID
2.Name
3.Department
4.Salary

Enter your option: 
4
 Increasing Order with the Salary : 
3,Subham,F,13000
1,Subhasish,A,23000
2,Vedant,C,32000

```
	
4. Given a Linked List of Objects representing date of birth's (use any inbuild java class to represent date), print the date's along with the message: Your date of Birth is DD-MM-YYYY, and it (was or was not) a leap year.

 - E.g. For the date 23-12-2000

   Your date of birth is 23-12-2000 and it was a leap year

```java
//class name - LeapYear
	
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;
import java.util.LinkedList;

public class LeapYear {

	public static void main(String[] args) {
		
		LocalDate date1 = LocalDate.of(2000, 07, 26);
		LocalDate date2 = LocalDate.of(2017, 11, 7);
		LocalDate date3 = LocalDate.of(1999, 10, 11);
		
		LinkedList<LocalDate> list = new LinkedList<LocalDate>();
		
		list.add(date1);
		list.add(date2);
		list.add(date3);
		
		for(LocalDate l : list)
		{
			String printDate = l.format(DateTimeFormatter.ofPattern("dd-MM-YYYY"));
			
			if(l.isLeapYear())
			{
				System.out.println("Your Date of Birth is " + printDate + " and it was a leap year");
			}
			else
			{
				System.out.println("Your Date of Birth is " + printDate + " and it was not a leap year");
			}
		}

	}

}

```
	
Output:
	
```
Your Date of Birth is 26-07-2000 and it was a leap year
Your Date of Birth is 07-11-2017 and it was not a leap year
Your Date of Birth is 11-10-1999 and it was not a leap year
```
