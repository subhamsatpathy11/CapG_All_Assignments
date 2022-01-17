# Collections Assignment

1. Given a Tree Map<Long, Contact> which has phone numbers for keys and contact objects for values.

Write solutions to

 - Fetch all the keys and print them,
 - Fetch all the values and print them
 - Print all key-value pairs

Note:

 - Contacts should be stored in descending order of phone number
 - Contact Class:
  - PhoneNumer: <long>
  - Name: <String>
  - Email: <String>
  - Gender: <Enum>
  
  ```java
  ```
  Output:
  
  ```
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
