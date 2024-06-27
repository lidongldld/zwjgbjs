---
title: java Preconditions
tags: java
---
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


