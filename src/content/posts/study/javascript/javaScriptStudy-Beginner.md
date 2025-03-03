---
title: JavaScript 入门
published: 2025-02-18
description: ''
image: ''
tags: ['JavaScript', 'study']
category: JavaScript
draft: false 
lang: ''
---
# 一．基础

## 基本规则

在 JavaScript 中，指令被称为语句，并用分号（;）进行分隔。

:::tip
如果一条语句独占一行的话，那么分号是可以省略的。
但如果一行中有多条语句，那么这些语句必须用分号进行分隔。
:::

JavaScript 是区分大小写的，并使用 Unicode 字符集
```javascript
var 变量 = 666;
console.log(变量)
//输出
666
```

## 注释
注释语法和 C++ 以及许多其他语言的注释语法一样：
```javascript
// 单行注释

/* 这是一个更长的，
 * 多行注释
 */
```

# 二．变量
变量的名字又叫做标识符，其需要遵守一定的规则。

JavaScript 标识符通常以字母、下划线（_）或者美元符号（$）开头；后续的字符也可以是数字（0-9）。

## 声明变量

1. **var**

    声明一个变量

    变量默认为undefined

    ```javascript
    var a;
    console.log(a);
    //输出
    undefined
    ```
    也可将其初始化为一个值
    ```javascript
    var a = 666;
    console.log(a);
    //输出
    666
    ```
2. **let**

    声明一个块级作用域的本地变量

    ```javascript
    let x = 1;
    if (x === 1) {
        let x = 2;
        console.log(x);
    }
    console.log(x);
    //输出
    2
    1
    ```

    更多let详情查看[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/let)

3. **const**

    声明一个只读的命名常量

    ```javascript
    const number = 123;
    try {
      number = 99;
    } catch (err) {
      console.log(err);
      // 预期输出：TypeError:对常量'number'的赋值无效
      // 注意：确切的输出可能取决于浏览器
    }
    console.log(number);
    //输出
    TypeError: Assignment to constant variable.
    123
    ```
   
    更多const详情查看[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/const)

:::tip
全局变量会在浏览器关闭后才销毁,局部变量用完后自动销毁
:::

## 数据结构
### 数据类型
js有8种数据类型
- String(字符串)
- Number(数值)
- Boolean(布尔值)
- Null(空值)
- Undefind(未定义)
- BigInt(任意精度的整数)
- Symbol(其实例是唯一且不可变的数据类型)
- Object(对象)

#### String(字符串)
字符串用于表示和操作字符序列

1. 创建字符串

    字符串字面量可以使用单引号或者双引号指定，它们的处理方式相同，或者使用反引号字符 `。

    反引号的形式指定了模板字符串，可以在其中插入表达式

    ```javascript
    const string1 = "A string primitive";
    const string2 = 'Also a string primitive';
    const string3 = `Yet another string primitive`;
    const string4 = new String("A String object");
    ```

    String单双引号嵌套

    ```javascript
    var a = '我:"艹!"'
    console.log(a)
    var a = "我:'艹!'"
    console.log(a)
    //输出
    我:"艹!"
    我:'艹!'
    ```

    :::tip
    typeof会返回变量的数据类型,返回的数据类型是String
    :::

    ```javascript
    var a = "s"
    console.log(typeof a)
    var b = typeof a
    console.log(typeof b)
    //输出
    string
    string
    ```

2. 访问字符
    
    有两种方式访问字符串中的单个字符。首先是 charAt() 方法：

    ```javascript
    var g = "good".charAt(1)
    console.log(g)
    //输出
    o
    ```
    
    另一个方式是将字符串视为类数组对象，其中各个字符对应于一个数字索引：

    ```javascript
    var g = "good"[1]
    console.log(g)
    //输出
    o
    ```
    :::warning
    当使用方括号表示法进行字符串访问时，尝试删除或为其赋值的行为将不成功。
    涉及的属性既不可写（writable）也不可配置（configurable）
    :::

3. 比较字符串

    使用小于和大于运算符来比较字符串：

    ```javascript
    const a = "a";
    const b = "b";
    if (a < b) {
    // true
        console.log(`${a} 小于 ${b}`);
    } else if (a > b) {
        console.log(`${a} 大于 ${b}`);
    } else {
        console.log(`${a} 和 ${b} 相等`);
    }
    //输出
    a 小于 b
    ```
   
4. 字符串强制转换

    String()方法,转换null和undefined时会返回本身

    ```javascript
    a = String(233)
    console.log(typeof a)
    console.log(String(null))
    console.log(String(undefined))
    //输出
    string
    null
    undefined
    ```

5. 实例属性
    - **String.prototype.constructor**
      
      创建实例对象的构造函数

    - **String.prototype.length**

      字符串的长度(只读)

   这些属性在 String.prototype 上定义，由所有 String 实例共享

6. 实例方法
   - **String.prototype.at()**

     返回指定索引处的字符
   
   - **String.prototype.charAt()**
     
     返回指定位置的字符

   - **String.prototype.includes()**

     字符串是否包含某个子串

   - **String.prototype.indexOf()**

     返回某个子串在字符串中首次出现的位置，未找到返回-1

   - **String.prototype.lastIndexOf()**

     返回某个子串在字符串中最后一次出现的位置，未找到返回-1

   - **String.prototype.match()**

     返回一个数组，数组的成员是字符串中满足正则表达式的所有部分

   - **String.prototype.replace()**

     替换字符串中符合正则表达式的部分

   - **String.prototype.replaceAll()**

     替换字符串中所有符合正则表达式的部分

   - **String.prototype.substring()**

     裁切并返回一个新的字符串
     







# 参考链接:
 - [MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Grammar_and_types)