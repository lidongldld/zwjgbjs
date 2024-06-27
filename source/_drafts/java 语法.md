---
title: java 语法
tags: java
---

# 1、optional类
Optional 类提供了一种优雅的方式来处理可能为空的值。
可以减少if else 的使用
``` java
class PriceNullException extends RuntimeException{
    public PriceNullException(String message){
        super(message);
    }
}
Double price = null;
Double finalPrice = Optional.ofNullable(price)
    .orElseThrow(()->new PriceNullException("价格为空"));

```
上述代码中，如果 price 为空，则会抛出自定义的 PriceNullException 异常。

## 判断 Optional 是否存在值、获取 Optional 的值
可以通过调用 Optional 对象的 get() 方法来获取其值。但是在调用 get() 方法之前，最好先通过 isPresent() 方法来判断 Optional 是否存在值。因为如果 Optional 为空，调用 get() 方法会抛出 NoSuchElementException 异常。
``` java
if (optionalName.isPresent()) {
    System.out.println("姓名为：" + optionalName.get());
} else {
    System.out.println("姓名为空");

}
```


# Preconditions的用法
源码分析：
``` java
//检查参数（expression）是否合法，若为false，抛出IllegalArgumentException异常
public static void checkArgument(boolean expression) {
   if (!expression) {
     throw new IllegalArgumentException();   
   }
}

//检查入参，带异常信息
public static void checkArgument(boolean expression, @Nullable Object errorMessage) {
   if (!expression) {
     throw new IllegalArgumentException(String.valueOf(errorMessage));
  }
}
//检查入参，errorMessageTemplate表示异常信息模板，errorMessageArgs将被替换为信息模板中的参数
public static void checkArgument(
  boolean expression,
  @Nullable String errorMessageTemplate,
  @Nullable Object... errorMessageArgs) {
  if (!expression) {
     throw new IllegalArgumentException(format(errorMessageTemplate, errorMessageArgs));
  }
}
```
示例1：
``` java
Preconditions.checkArgument(demo,"demo不能为false");
```
输出：
``` text 
Exception in thread "main" java.lang.IllegalArgumentException: demo不能为false
   at com.google.common.base.Preconditions.checkArgument(Preconditions.java:122)
   at demo.PreconditionsDemo.main(PreconditionsDemo.java:8)
```
示例2：
``` java
Preconditions.checkArgument(demo,"该参数为%s",demo);
```
输出：
``` text 
Exception in thread "main" java.lang.IllegalArgumentException: 该参数为false
   at com.google.common.base.Preconditions.checkArgument(Preconditions.java:191)
   at demo.PreconditionsDemo.main(PreconditionsDemo.java:8)
```
