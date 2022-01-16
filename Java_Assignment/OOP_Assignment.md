# OOP Assignment

1. 1.	Write a Singleton class. Confirm that singleton class cannot be inherited. Singleton class is a class that can have only one object at time.

```java
//Class name - Singleton


public class Singleton {
	
	private static Singleton single = null;
	public String str;
	
	private Singleton()
	{
		str = "My name is Subham";
	}
	
	public static Singleton getStr()
	{
		if(single == null)
		{
			single = new Singleton();
		}
		return single;
	}
}

```
```java
//class name - TestSingleton


public class TestSingleton {

	public static void main(String[] args) {

		Singleton a = Singleton.getStr();
		Singleton b = Singleton.getStr();
		
		b.str = (b.str).toUpperCase();
		
		System.out.println(a.str);
		System.out.println(b.str);
	}

}

```

Output:

```
MY NAME IS SUBHAM
MY NAME IS SUBHAM

```

2. Write a program that describes the hierarchy of an organization. Here we need to write 3 classes Employee, Manager & Labour where Manager & Labour are the sub classes of the Employee. Manager has incentive & Labour has over time. Add the functionality to calculate total salary of
all the employees. Use polymorphism i.e. method overriding.

```java
//class name - Labour


public class Labour extends Employee{

	public int overtime = 15;
	
	public int totalSalary()
	{
		int gross = 1000 * overtime;
		return gross;
	}

}

```

```java
//class name Manager

public class Manager extends Employee {

	public int incentives = 1000;
	
	public int totalSalary()
	{
		
		int gross = 54000 + incentives;
		return gross;
		
	}
}

```

```java
//class name - Employee


public class Employee {
	
	public int totalSalary()
	{
		return 0;
	}
	
	public static void main(String args[])
	{
		Manager m = new Manager();
		Labour l = new Labour();
		
		System.out.println("Salary of Manager : " + m.totalSalary());
		System.out.println("Salary of Labour : " + l.totalSalary());
		System.out.println("Total Salary : " + (m.totalSalary()+l.totalSalary()));
	}

}


```

Output:

```
Salary of Manager : 55000
Salary of Labour : 15000
Total Salary : 70000

```

3. Write a program to consider saving & current account in the bank. Saving account holder has Fixed Deposits' whereas Current account holder has cash credit. Apply polymorphism to find out total cash in the bank.

```java
//class name - SavingsAccount


public class SavingsAccount extends Bank {
	
	public int totalAmount(int fixedDep, int interest, int time)
	{
			double gross = fixedDep + ((fixedDep/100)*interest) * Math.floor(time/6) ; 
			Double d = new Double(gross);
			int gross_int = d.intValue();
			return gross_int;
	}
}

```

```java
//class name - CurrentAccount


public class CurrentAccount extends Bank{

	public int totalAmount(int cashcredit, int interest_credit, int time_credit)
	{
			double credit = cashcredit + ((cashcredit/100)*interest_credit) * Math.floor(time_credit/12) ; 
			Double d_credit = new Double(credit);
			int credit_int = d_credit.intValue();
			return credit_int;
	}
	
}

```

```java
//class name - Bank

import java.util.Scanner;

public class Bank {

	public static void main(String[] args) {
		
		Scanner scan = new Scanner(System.in);
		
		int credit, fixedDep, interest, time, interest_credit, time_credit;
		
		System.out.println("Enter Fixed Deposit Amount: ");
		fixedDep = scan.nextInt();
		
		System.out.println("Enter the interest rate in Fixed Deposit: ");
		interest = scan.nextInt();
		
		System.out.println("Enter the time period in months: ");
		time = scan.nextInt();
		
		SavingsAccount save = new SavingsAccount();
		System.out.println("Amount in Savings Account is: " + save.totalAmount(fixedDep, interest, time));
		
		System.out.println("Enter Cash Credit Amount: ");
		credit = scan.nextInt();
		
		System.out.println("Enter the interest rate in Cash Credit ");
		interest_credit = scan.nextInt();
		
		System.out.println("Enter the time period in months: ");
		time_credit = scan.nextInt();
		
		CurrentAccount current = new CurrentAccount();
		System.out.println(" Amount in Current Account is: " + current.totalAmount(credit, interest_credit, time_credit));
	
		System.out.println("Total Amount in Bank is: " + ( save.totalAmount(fixedDep, interest, time) + current.totalAmount(credit, interest_credit, time_credit)));
	}

}

```

Output:

```
Enter Fixed Deposit Amount: 
100000
Enter the interest rate in Fixed Deposit: 
7
Enter the time period in months: 
12
Amount in Savings Account is: 114000
Enter Cash Credit Amount: 
2340
Enter the interest rate in Cash Credit 
10
Enter the time period in months: 
4
 Amount in Current Account is: 2340
Total Amount in Bank is: 116340
```

4. Test the following principles of an abstract class:

 - If any class has any of its method abstract then you must declare entire class abstract. Abstract class cannot be instantiated.
 

```java
//class name - Demo

public class Demo extends Call {
	public void dispaly2()
	{
	
	System.out.println("HI");
	}
	public static void main(String[] args)
	{
			
			Demo d= new Demo();
			d.dispaly();
			
			
		}
	}

```

```java
//class name - Call

abstract class Call {
 void display()
{
	System.out.println("hello");
}
}

```

Output:

```
Not necessary that abstract class have abstract method and methods donot require  implementation for declaration
``` 
 - When we extend an abstract class, we must either override all the abstract methods in sub class or declare subclass as abstract.

```java
//class name - Demo

public class Demo extends Call {
	public void dispaly2()
	{
	
	System.out.println("HI");
	}
	public static void main(String[] args)
	{
			
			Demo d= new Demo();
			d.dispaly2();	
		}
	}

```

```java
//class name  - Call

abstract class call {
 void display()
{
	System.out.println("hello");
}
}

```

Output:

```
HI
```

 - Abstract class cannot be private.

```
Exception in thread "main" java.lang.Error: Unresolved compilation problem: 
	Implicit super constructor Call() is not visible for default constructor. Must define an explicit constructor

```
 - Abstract class cannot be final.

```
Yes it can’t be a final because final is not a access specifier
```
 - You can declare a class abstract without having any abstract method

```
Yes we can create abstract class without a method.
```

5. Write the classes Line, Rectangle, Cube etc. & make the Shape as their base class. Add an abstract draw() method in the class Shape & draw all shapes.

```java
//class name - Rectangle

class Rectangle extends Shapes {

  public void draw() {
    System.out.println("Drawing a rectangle...");
  }
}

```

```java
//class name - Cube

class Cube extends Shapes 
{
  public void draw() {
    System.out.println("Drawing a cube...");
  }
}
```

```java
//abstract class name - Shapes

abstract class Shapes 
{
		public abstract void draw();	
}
```

```java
//class name - BaseShape

public class BaseShape {
	
	 public static void drawShapes(Shapes[] list) {
		    for (int i = 0; i < list.length; i++) {
		      list[i].draw();
		    }
		  }

	 public static void main(String args[])
	 {
		 Shapes[] shapeList = new Shapes[2];
		 shapeList[0] = new Rectangle();
		 shapeList[1] = new Cube(); 
		 drawShapes(shapeList);
	 }
}

```

Output:

```
Drawing a rectangle...
Drawing a cube...

```

6. Write an abstract class 'Persistence' along with two sub classes 'FilePersistence' & 'DatabasePersistence'. The base class with have an abstract method persist() which will be overridden by its sub classes. Write a client who gets the Persistence object at runtime & invokes persist() method on it without knowing whether data is being saved in File or in Database.

```java
//abstract class name - Persistence

abstract class Persistence{
    abstract void persist();
}
```

```java
//class name - FilePersistence

class FilePersistence extends Persistence {
    void persist() {
        System.out.println("Data Saved in File");
    }
}
```

```java
//class name - DatabasePersistence

class DatabasePersistence extends Persistence {
    void persist() {
        System.out.println("Data Saved in Database");
    }
}
```

```java
//class name - Client

public class Client extends Persistence {
    
    public static void main(String[] args) {
        Persistence ob = new Client();
        ob.persist();
    }
    
    void persist() { 
        System.out.println("Persist Method from Client");
    }
}
```

Output:

```
Persist Method from Client
```
