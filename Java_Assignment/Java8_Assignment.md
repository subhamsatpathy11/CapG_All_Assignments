# Java 8 Assignment

1. Write an application to perform basic arithmetic operations like add, subtract, multiply and divide. You need to define a functional interface first.

```java
package lam;
public class exp {
	public static void main(String[] args) {
		arthmetic mylambda= (int a,int b) ->a+b;
			System.out.println("Addition:"+(mylambda.foo(10,10)) );
			arthmetic mylambda1= (int a,int b) ->a-b;
			System.out.println("Subtraction:"+(mylambda1.foo(20, 10)));
			arthmetic mylambda2= (int a,int b) ->a*b;
			System.out.println("Multiplication:"+(mylambda2.foo(20, 10)));
			arthmetic mylambda3= (int a,int b) ->a/b;
			System.out.println("Division:"+(mylambda3.foo(20, 10)));
	}
  interface arthmetic{
    	  int foo(int a, int b);  
  } 
}

```

Output:

```
Addition:20
Subtraction:10
Multiplication:200
Division:2

```

2. Write an application using lambda expressions to print Orders having 2 criteria implemented 
 - Order price more than 10000
 - Order  status is ACCEPTED or COMPLETED

```java
import java.util.Scanner;

public class exp1 {
	public static void main(String[] args)
	{
		
		order mylambda = (int a) -> {
			if(a >10000) 
				{
				System.out.println("Accepted"); 
				}
				else
				{
					System.out.println("Not Accepted");
				}
			return a;
		};
		System.out.println("order amount:" +(mylambda.foo(100000)));
	}
     interface order
     {
    	 int foo(int a);
     }
}

```

Output:

```
Accepted
order amount:100000

```

3. Use the functional interfaces Supplier, consumer, Predicate and Function to invoke built-in Methods  from java API.

```java
import java.util.ArrayList;
import java.util.function.Consumer;
import java.util.function.Predicate;
import java.util.function.Supplier;

public class exp3 {
public static void main(String[] args)
{
	//predicate
	Predicate<Integer>gt=a->(a>10);
	System.out.println("predicate:" + gt.test(20));
	//supplier
	String str="HI";
	Supplier<Integer> supplier=()->str.length();
	System.out.println("Supplier:" +supplier.get());
	//Consumer
	Consumer<String>print=a->System.out.println("Consumer:"+a);
	print.accept("HI");
}	
}	

```

Output:

```
predicate:true
Supplier:2
Consumer:HI

```

4. Remove the words that have odd lengths from the list. HINT : Use one of the new methods from JDK 8. Use remove() method from Collection interface

```java
package lam;
import java.util.ArrayList;
public class exp4 {
	public static void main(String[] args)
	{
		ArrayList<String>words=new ArrayList<String>();
		words.add("hi");
		words.add("Hey");
		words.add("Hello");
		words.add("good");
		words.add("bad");
		words.add("three");
		words.removeIf(n->(n.length()%2!=0));
		for(String i:words)
		{
			System.out.println(i);
		}
	}

}

```

Output:

```
hi
good

```

5. Create a string that consists of the first letter of each word in the list of Strings provide. HINT : Use Consumer interface and a StringBulider to construct the results.

```java
package lam;
import java.util.ArrayList;
import java.util.function.Consumer;

public class exp5 {
	public static void main(String[] args)
	{
		ArrayList<String>words=new ArrayList<String>();
		words.add("hi");
		words.add("Hey");
		words.add("Hello");
		words.add("good");
		words.add("bad");
		words.add("three");
		Consumer <String> print=(str)->System.out.println("the first letter of strings:"+str.charAt(0));
		words.forEach(print);
		
   }
}

```

Output:

```
the first letter of strings:h
the first letter of strings:H
the first letter of strings:H
the first letter of strings:g
the first letter of strings:b
the first letter of strings:t

```

6. Replace every word in the list with its upper case equivalent. Use replaceAll() method and UnaryOperator interface.

```java
import java.util.ArrayList;
import java.util.function.UnaryOperator;
class Op implements UnaryOperator<String> {
   public String apply(String str) {
      return str.toUpperCase();
   }
}
public class Test {
   public static void main(String[] args) throws CloneNotSupportedException {
      ArrayList<String> list = new ArrayList<>();
      list.add("Java");
      list.add("JavaScript");
      list.add("CoffeeScript");
      list.add("HBase");
      list.add("OpenNLP");
      System.out.println("Contents of the list: "+list);
      list.replaceAll(new Op());
      System.out.println("Contents of the list after replace operation: \n"+list);
   }
}
```

Output:

```
Contents of the list: [Java, JavaScript, CoffeeScript, HBase, OpenNLP]
Contents of the list after replace operation:[JAVA, JAVASCRIPT, COFFEESCRIPT, HBASE, OPENNLP]
```

7. Convert every key-value pair of the map into a string and append them all into a single string, in iteration order. HINT : Use Map.entrySet() method & a StringBulider to construct the result String.

```java
package org.lambda.app;
import java.util.HashMap;
import java.util.Map;
import java.util.stream.Collectors;

public class MapToString {
    public static void main(String[] cmd_lineParams) {
        Map<String, String> map = new HashMap<>(5);
        map.put("Harshita", "1");
        map.put("Lutika", "2");
        map.put("Subhasish", "3");
        map.put("Vedant", "6");
        map.put("Subham", "5");
        String s = map.entrySet().stream().map((entry) ->
                        "" + entry.getKey() + " \"" + entry.getValue().replaceAll("\"", "\\\\\"") + "\"")
                .collect(Collectors.joining(" "));
        System.out.println(s);

    }
}

```

Output:

```
Harsita "1" Subhasish "3" Subham "5" Lutika "2" Vedant "6"
```

8. Create a new thread that prints the numbers from the list. Use class Thread & interface Consumer

```java
package org.lambda.app;
import java.util.ArrayList;
import java.util.List;
public class ListToString {

    public static void main(String[] args)
    {
    	
    		List<Integer> n=new ArrayList<Integer>()
    		{{
                add(15);
                add(65);
                add(73);
                add(99);
                add(89);
    		} };
            
            Thread mylambda = new Thread(()->System.out.println(n));
            mylambda.run();
    	}
    }

```

Output:

```
[15, 65, 73, 99, 89]
```
