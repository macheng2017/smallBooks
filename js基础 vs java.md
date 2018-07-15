js 当中数据类型 所有的数据类型 定义仅通过一个 var x; 即可定义
但是 js 还是分为以下几种数据类型 :
整数 实数
字符串 (单双引号)
布尔值
null
undefined
对象
数组

在 java 当中的数据类型定义必须严格的写出来,需要声明变量的类型

```java
// java primitive type
boolean flag = false;
char x = null;
byte d = 0;
short a = 0;
int count = 0;
long count = 0L;
float cost = 0.0f;
double cost = o.od;
```

另外 java 当中也有复合类型

java 当中的对象和 js 当中的对象一样吗?

java 当中先有类 class 然后才有对象 new 一个对象, 而 js 当中直接可以定义对象

例如:

```js
var book = {
  topic: 'javaScript',
  fat: true
}
// 使用book类中的属性
book.topic
book['fat']
console.log(book.topic)
```

java 当中

```java
// 定义一个java类
class Book {
    String topic = "javaScript";
    boolean fat = true;
}
// 在另外一个类中使用Book类创建对象
public class HelloWord {
    public static void main (String [] args){
        Book book = new Book()
        System.out.println(book.topic)
    }
}
```

1.  区别 js 当中可以在运行时直接为对象添加属性,java 当中这种事根本就不要想了,类设计好了就不能更改 了,而对象是根据定义好的类 new 出来的
2.  js

js 动态的添加对象属性,太方便了

```js
book.author = 'David Flanagan'
```
