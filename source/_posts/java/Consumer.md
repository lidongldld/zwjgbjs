---
title: Consumer
tags: java
---
## 使用Lambda表达式创建Consumer
例1 基础类型操作
``` java
import java.util.ArrayList;
import java.util.List;
import java.util.function.Consumer;
 
public class ConsumerLambda1 {
  public static void main(String[] args) {
	List<Integer> oddList = new ArrayList<>();
	List<Integer> evenList = new ArrayList<>();
	
	Consumer<Integer> storeNumber = n -> {
	   if (n % 2 == 0) {
		 evenList.add(n);
	   } else {
		 oddList.add(n);
	   }
	};
	
	Consumer<List<Integer>> printList = list -> list.forEach(n -> System.out.println(n));
	
	storeNumber.accept(10);
	storeNumber.accept(15);
	storeNumber.accept(25);
	storeNumber.accept(30);
	
	System.out.println("--- Odd number ---");
	
	printList.accept(oddList);
	
	System.out.println("--- Even number ---");
	
	printList.accept(evenList);
  }
}
```
输出结果
``` text
--- Odd number ---
15
25
--- Even number ---
10
30 
```
例2 对象类型操作
``` java
import java.util.function.Consumer;
 
public class ConsumerLambda2 {
  public static void main(String[] args) {
     Consumer<Citizen> electionConsumer = c -> {
       if (c.getAge() < 18) {
    	 System.out.println(c.getName() + " is not eligible to vote.");
       } else {
    	 System.out.println(c.getName() + " can vote.");
       }
     };
     
     electionConsumer.accept(new Citizen("Ritesh", 15));
     
     electionConsumer.accept(new Citizen("Shreya", 20));
  }
}
 
class Citizen {
  private String name;
  private int age;
 
  public Citizen(String name, int age) {
	this.name = name;
	this.age = age;
  }
 
  public String getName() {
	return name;
  }
 
  public int getAge() {
	return age;
  }
}
```
输出结果
``` text 
Ritesh is not eligible to vote.
Shreya can vote.
```
## 使用方法引用创建Consumer
示例：
``` java
import java.util.HashMap;
import java.util.Map;
import java.util.function.Consumer;
 
public class ConsumerMethodRef {
  public static void main(String[] args) {
	Map<Integer, String> persons = new HashMap<Integer, String>();
	persons.put(101, "Mahesh");
	persons.put(102, "Krishna");
 
	Consumer<Map<Integer, String>> updatePersons = Utility::updateData;
 
	Consumer<Map<Integer, String>> displayPersons = Utility::displayData;
 
	updatePersons.accept(persons);
 
	displayPersons.accept(persons);
  }
}
 
class Utility {
  static void updateData(Map<Integer, String> persons) {
	persons.replaceAll((k, v) -> "Shree ".concat(v));
  }
 
  static void displayData(Map<Integer, String> persons) {
	for (Map.Entry<Integer, String> entry : persons.entrySet()) {
	  System.out.println(entry.getKey() + " - " + entry.getValue());
	}
  }
}
```
输出结果
``` text
101 - Shree Mahesh
102 - Shree Krishna
```