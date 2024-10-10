---
title: JAVA基础语法
date: 2024-10-09
categories: [JAVA]
tags: [JAVA]
---

JAVA基础语法笔记。

<!--more-->

# 杂项

## 文档注释

IDEA中输入`/**`回车，自动生成文档注释。

## byte  short  int double

short有符号，取值: -128-127

int 的取值范围在 -2,147,483,648（-2 ^ 31）和 2,147,483,647（2 ^ 31 -1）（含）之间。

```java
int i; // 声明一个 int 类型变量
i = 1000000; // 将值 1000000 赋给变量 i
int j = -2000000; // 声明并初始化一个 int 类型变量 j，赋值为 -2000000
```

long 的取值范围在(-2^63) 和 (2^63 -1)（含）之间。如果 int 存储不下，就用 long。

```java
long l; // 声明一个 long 类型变量
l = 100000000000L; // 将值 100000000000L 赋给变量 l（注意要加上 L 后缀）
long m = -20000000000L; // 声明并初始化一个 long 类型变量 m，赋值为 -20000000000L
```

float 是单精度的浮点数（单精度浮点数的有效数字大约为 6 到 7 位），32 位（4 字节），遵循 IEEE 754（二进制浮点数算术标准），取值范围为 1.4E-45 到 3.4E+38。float **不适合用于精确的数值，比如说金额**。

```java
float f; // 声明一个 float 类型变量
f = 3.14159f; // 将值 3.14159f 赋给变量 f（注意要加上 f 后缀）
float g = -2.71828f; // 声明并初始化一个 float 类型变量 g，赋值为 -2.71828f
```

double 是双精度浮点数（双精度浮点数的有效数字大约为 15 到 17 位），占 64 位（8 字节），也遵循 IEEE 754 标准，取值范围大约 ±4.9E-324 到 ±1.7976931348623157E308。double 同样不适合用于精确的数值，比如说金额。

```java
double myDouble = 3.141592653589793;
```

## 强制类型转换

### int转char

```java
int a = 65;
char c = (char) a;
System.out.println(c);
```

### 各种进制转char

可以使用 `Character.forDigit()` 方法将整型 int 转换为字符 char，参数 radix 为基数，十进制为 10，十六进制为 16。

```java
public static char forDigit(int digit,int radix)
Params:
digit – the number to convert to a character. radix – the radix.
Returns:
the char representation of the specified digit in the specified radix.
```

```java
int radix = 10;
int value_int = 6;
char value_char = Character.forDigit(value_int , radix);
System.out.println(value_char );
```

### char转int

直接赋值：

```java
int a = 'a';
```

### 数字字符转数字

```java
int a = Character.getNumericValue('1');
int a = Character.digit('1', 10);
```

## 包装器

- Byte（对应 byte）
- Short（对应 short）
- Integer（对应 int）
- Long（对应 long）
- Float（对应 float）
- Double（对应 double）
- Character（对应 char）
- Boolean（对应 boolean）

## 数字字符串转数字

```java
String text = "123";
int number = Integer.parseInt(text);
System.out.println(number);
```

## 堆和栈

![img](assets/basic-data-type-3d5b3e40-1abb-4624-8282-b83e58388825.png)

## 基本数据类型缓存池

- `new Integer(18)` 每次都会新建一个对象;
- `Integer.valueOf(18)` 会使⽤用缓存池中的对象，多次调用只会取同⼀一个对象的引用。

```java
Integer x = new Integer(18);
Integer y = new Integer(18);
System.out.println(x == y); //false

Integer z = Integer.valueOf(18);
Integer k = Integer.valueOf(18);
System.out.println(z == k); //true

Integer m = Integer.valueOf(300);
Integer p = Integer.valueOf(300);
System.out.println(m == p); //false
```

- Byte：-128~127，也就是所有的 byte 值
- Short：-128~127
- Long：-128~127
- Character：\u0000 - \u007F
- Boolean：true 和 false

## 位运算符

![img](assets/eleven-03.png)

```java
int a = 60, b = 13;
System.out.println("a 的二进制：" + Integer.toBinaryString(a)); // 111100
System.out.println("b 的二进制：" + Integer.toBinaryString(b)); // 1101

int c = a & b;
System.out.println("a & b：" + c + "，二进制是：" + Integer.toBinaryString(c));

c = a | b;
System.out.println("a | b：" + c + "，二进制是：" + Integer.toBinaryString(c));

c = a ^ b;
System.out.println("a ^ b：" + c + "，二进制是：" + Integer.toBinaryString(c));

c = ~a;
System.out.println("~a：" + c + "，二进制是：" + Integer.toBinaryString(c));

c = a << 2;
System.out.println("a << 2：" + c + "，二进制是：" + Integer.toBinaryString(c));

c = a >> 2;
System.out.println("a >> 2：" + c + "，二进制是：" + Integer.toBinaryString(c));

c = a >>> 2;
System.out.println("a >>> 2：" + c + "，二进制是：" + Integer.toBinaryString(c));
```

## 数组

```java
int[] a = new int[]{1, 2, 3, 4, 5};
for (int i = 0; i < a.length; i++) {
    System.out.println(a[i]);
}
for (int element : a) {
    System.out.println(element);
}
```

## 可变参数

`void varArgsMethod(String... args)`

## Arrays工具类

以下是 Java `Arrays` 工具类中常用方法的简要说明：

1. **`equals`**
   - **参数**: `boolean equals(Object[] a, Object[] b)`
   - **返回值**: `boolean`
   - **作用**: 比较两个数组是否相等。

2. **`toString`**
   - **参数**: `String toString(int[] a)`
   - **返回值**: `String`
   - **作用**: 返回数组内容的字符串表示形式。

3. **`fill`**
   - **参数**: `void fill(int[] a, int val)`
   - **返回值**: 无
   - **作用**: 用指定值填充整个数组。

4. **`sort`**
   - **参数**: `void sort(int[] a)`
   - **返回值**: 无
   - **作用**: 对数组进行升序排序。

5. **`binarySearch`**
   - **参数**: `int binarySearch(int[] a, int key)`
   - **返回值**: `int`
   - **作用**: 使用二分搜索查找指定值的索引。

# 面向对象

## 权限修饰符

Java类的权限修饰符有四种：`public`、`protected`、`default`（无修饰符）、`private`。以下是各修饰符在不同访问范围内的权限表：

| 修饰符      | 同一个类内 | 同一个包内 | 子类 | 其他包 |
| ----------- | ---------- | ---------- | ---- | ------ |
| `public`    | √          | √          | √    | √      |
| `protected` | √          | √          | √    | ×      |
| `default`   | √          | √          | ×    | ×      |
| `private`   | √          | ×          | ×    | ×      |

- **public**: 任何地方都能访问。
- **protected**: 本类、同包类、子类可以访问，其他包不能访问。
- **default**: 仅限于同一包内访问，跨包无法访问。
- **private**: 只能在本类内访问，其他地方都不能访问。

## 成员变量和静态变量的初始值

```java
public class LocalVar {
    private int a;
    static int b;

    public static void main(String[] args) {
        LocalVar lv = new LocalVar();
        System.out.println(lv.a);
        System.out.println(b);
    }
}

```

```java
输出：
0
0
```

| 数据类型 | 默认值   | 大小   |
| -------- | -------- | ------ |
| boolean  | false    | 不确定 |
| char     | '\u0000' | 2 字节 |
| byte     | 0        | 1 字节 |
| short    | 0        | 2 字节 |
| int      | 0        | 4 字节 |
| long     | 0L       | 8 字节 |
| float    | 0.0f     | 4 字节 |
| double   | 0.0      | 8 字节 |

## 成员变量和局部变量

1. **作用域**

- **成员变量：**
  - **实例变量**：属于类的对象，每个对象有自己独立的副本。
  - **静态变量**：属于整个类，所有对象共享一份静态变量。
  
- **局部变量：**
  局部变量是在方法、构造函数或代码块中定义的变量，它们只在该代码块或方法中可见。一旦离开该作用域，局部变量就会被销毁。

2. **生命周期**

- **成员变量：**
  - **实例变量**：当一个对象被创建时，实例变量被分配内存。当对象被销毁时，实例变量也随之销毁。
  - **静态变量**：在类被加载时分配内存，直到程序结束时才被销毁。

- **局部变量：**
  局部变量的生命周期是短暂的，它们只在方法或代码块执行时存在。方法执行结束后，局部变量就会被销毁，内存被释放。

3. **默认值**

- **成员变量：**
  成员变量在没有初始化的情况下会有默认值：
  - 数字类型（如 `int`, `double`）：默认值是 `0` 或 `0.0`
  - 布尔类型：默认值是 `false`
  - 引用类型：默认值是 `null`

- **局部变量：**
  **局部变量没有默认值，必须显式地初始化**，否则编译器会报错。

4. **存储位置**

- **成员变量：**
  成员变量存储在堆内存中（对于实例变量），或者在方法区中（对于静态变量）。

- **局部变量：**
  局部变量存储在栈内存中，方法执行时压栈，方法结束后出栈。

5. **修饰符**

- **成员变量：**
  成员变量可以使用访问修饰符（如 `private`, `public`, `protected`）以及其他修饰符（如 `static`, `final`）。它们的可见性可以通过这些修饰符进行控制。

- **局部变量：**
  局部变量不能使用访问修饰符，但可以使用 `final` 修饰符来表示它是不可更改的（即只赋值一次）。

```java
public class Example {
    // 成员变量（实例变量）
    private int instanceVar;

    // 成员变量（静态变量）
    private static int staticVar;

    public void method() {
        // 局部变量
        int localVar = 10;
        
        System.out.println("局部变量：" + localVar);
        System.out.println("实例变量：" + instanceVar);
        System.out.println("静态变量：" + staticVar);
    }
}
```

## 方法

在 Java 中，类方法的声明包括多个部分：访问修饰符、返回类型、方法名、参数列表和方法体。以下是 Java 类方法的标准格式和一些注意细节。

### 1. **方法声明格式**

```java
[修饰符] 返回类型 方法名(参数列表) {
    // 方法体
}
```

### 2. **方法声明的各个部分**

- **修饰符（Modifiers）**：
  修饰符决定方法的可见性和行为，常见的修饰符包括：
  
  - `public`: 方法可以被其他类访问。
  - `private`: 方法只能在定义它的类中访问。
  - `protected`: 方法可以在同一包中的类或子类中访问。
  - `static`: 静态方法属于类，而不是类的实例，静态方法可以通过类名直接调用。
  - `final`: 表示方法不能被子类重写。
  - `abstract`: 抽象方法没有方法体，必须在子类中实现。
  - `synchronized`: 表示方法是线程安全的，同一时间只能由一个线程访问。
- **返回类型（Return Type）**：
  - 方法必须指定返回类型，可以是基本数据类型（如 `int`, `boolean`），引用类型（如 `String`, `List`），或 `void`（表示方法不返回任何值）。
- **方法名（Method Name）**：
  - 方法名应使用小写字母开头，遵循驼峰命名法（camelCase），并且要描述方法的功能。
- **参数列表（Parameter List）**：
  - 方法可以接收零个或多个参数，每个参数必须有明确的类型和名称。
  - 参数之间用逗号分隔，且参数的类型和顺序不能颠倒。

### 3. **细节注意事项**

- **返回值**：
  - 如果方法有返回值，必须使用 `return` 语句返回与声明的返回类型一致的值。
  - 如果返回类型是 `void`，则不需要 `return` 语句，除非想提前结束方法。

- **静态方法**：
  - `static` 修饰的方法属于类，而不是类的实例。可以通过 `ClassName.methodName()` 调用，而不需要创建对象。
  
- **方法重载（Overloading）**：
  - Java 支持方法重载，即同一类中可以定义多个**方法名相同但参数不同**的方法（参数类型、数量或顺序不同）。

- **异常声明**：
  - 如果方法可能会抛出异常，必须在方法声明中使用 `throws` 关键字明确列出。例如：`public void readFile() throws IOException { }`。

- **访问修饰符的作用**：
  - 默认情况下，如果没有指定修饰符，方法的可见性是包级别，即同一个包内的类可以访问。
  
- **可变参数**：
  - Java 支持可变参数，可以在参数列表的最后一项使用 `...` 表示可变参数。例如：`public void print(String... messages)`。

### 4. **示例代码**

#### 无返回值的方法
```java
public void printMessage(String message) {
    System.out.println(message);
}
```

#### 带返回值的方法
```java
public int add(int a, int b) {
    return a + b;
}
```

#### 带静态修饰符的方法
```java
public static void printStaticMessage() {
    System.out.println("This is a static method.");
}
```

#### 带异常声明的方法
```java
public void readFile(String filePath) throws IOException {
    // 方法体内的代码可能会抛出 IOException
}
```

#### 带可变参数的方法
```java
public void printMessages(String... messages) {
    for (String message : messages) {
        System.out.println(message);
    }
}
```

### 5.方法重载(Method Overloading)

**方法重载**是在同一个类中定义**多个同名**的方法，但每个方法的**参数列表不同**。Java 通过参数的数量、类型、顺序来区分这些重载的方法。重载方法允许你使用相同的方法名处理不同类型或数量的输入，这样提高了代码的可读性和灵活性。

#### **方法重载的规则**

1. **参数数量不同**：方法的参数个数可以不同。
2. **参数类型不同**：即使参数个数相同，但参数的类型不同。
3. **参数顺序不同**：参数类型相同但顺序不同也可以构成重载。

#### **不属于方法重载的情况**
- **仅返回类型不同**：Java 不允许仅通过返回类型不同来区分方法重载，编译器无法仅依靠返回类型来识别调用的是哪个方法。
- **仅访问修饰符不同**：方法的可见性（`public`, `private`等）和是否是静态方法（`static`）不能作为方法重载的依据。
- **仅抛出异常不同**：抛出的异常类型不同也不能作为方法重载的条件。

#### **方法重载的好处**
- 提高了代码的可读性和简洁性，因为开发者可以通过同一个方法名处理不同类型或数量的输入。
- 使代码更具灵活性，可以适应多种输入情况而不需要为每种情况创建不同的方法名。

#### **方法重载示例**

```java
public class OverloadExample {
    // 重载方法1：接收两个整数并返回和
    public int add(int a, int b) {
        return a + b;
    }
    
    // 重载方法2：接收三个整数并返回和
    public int add(int a, int b, int c) {
        return a + b + c;
    }
    
    // 重载方法3：接收两个浮点数并返回和
    public double add(double a, double b) {
        return a + b;
    }

    // 重载方法4：接收一个整数和一个浮点数并返回和
    public double add(int a, double b) {
        return a + b;
    }
    
    public static void main(String[] args) {
        OverloadExample obj = new OverloadExample();
        System.out.println(obj.add(1, 2));          // 调用第一个方法
        System.out.println(obj.add(1, 2, 3));       // 调用第二个方法
        System.out.println(obj.add(1.5, 2.5));      // 调用第三个方法
        System.out.println(obj.add(1, 2.5));        // 调用第四个方法
    }
}
```

#### **注意**
- **返回类型**不同并不构成重载。例如，以下代码是无效的，因为 Java 无法通过返回类型区分重载的方法：

```java
// 错误示例
public int add(int a, int b) {
    return a + b;
}

public double add(int a, int b) {
    return a + b;
}
```

#### **自动类型转换与重载**
Java 支持自动类型转换（比如从 `int` 转为 `double`），如果方法的参数类型能通过类型转换匹配，Java 编译器会自动选择合适的重载方法。例如：
```java
public double add(double a, double b) {
    return a + b;
}

public static void main(String[] args) {
    OverloadExample obj = new OverloadExample();
    System.out.println(obj.add(1, 2));  // 自动将 int 转换为 double
}
```

在这种情况下，虽然传递的是两个整数，但由于没有匹配的 `int` 参数的重载方法，Java 会将 `int` 自动转换为 `double`，并调用 `add(double, double)`。

#### **总结**
- **方法重载**是通过定义多个相同方法名但参数不同的方法来实现的。
- 它提高了代码的可读性和灵活性。
- 方法重载不能仅依靠返回类型、访问修饰符或抛出异常来实现。
