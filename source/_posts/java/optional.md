---
title: java optional
tags: java
---
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
