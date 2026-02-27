### 变量和数据类型
- JavaScript 客户端部署语言 当前比较流行的语言
- 部署时有两种方法
  - 直接写在前端代码中
  ```bash
    <script>
       alert('这是一个弹窗！')
    <script/>
  ```
  - 写在.js文件里
  ```bash
    <script str=""><script/>
  ```
### 1.变量
- 声明和赋值的语法和python的语法相同（let）
- 常量声明（const）
### 2.数据类型（分为原始类型和对象类型）
- 原始类型（数字，字符串，布尔值，null空值，unfinished未定义）
  - 字符串（其中与python的不同点）`console.log("my name is ${name}")`
  - null空值 赋值了但内容为空`let a=""`
  - unfinished未定义 没有赋值的变量的数据类型
- 对象类型（object对象.array数组,function函数）
  - 数组的操作方法
  - | 增 | 删 | 改 | 查 |
    | :---: | :---: | :---: | :---: |
    | array.push() | delete array[] | array.splice(start,num,itme) | console.log(array[]) (也可以直接查看整个数组) |
---
