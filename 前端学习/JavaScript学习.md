## 一、变量和数据类型
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
### 3.转换
- 隐性转换 +两边只要有一个数据类型是字符串那么结果是两个字符串相加、-/*的话都会把数据转化为数字类型
- 显性转换 Number() parseInt() parseFloat() string() 
---
## 二、判断，循环，函数
### 1.判断
- 判断（包括逻辑运算和比较运算）（===表示两边的值和类型都相等、其他的符号都与python语法相同）
- 条件判断（if else）
### 2.循环
- while
- for（遍历数组）
- break和contine关键字
### 3.函数
- 系统函数`console.log() parseInt()`
- 自定义函数`function 函数名(实参){}`
- 匿名函数`let fn=function(实参){}`
- 箭头函数`let fn=(实参)=>{}`
- 高阶函数(接受另一个函数作为参数)
  - filter数组过滤
  ```bash
    let array=[1,2,3,4]
    const new=array.filter(function(num){
      return num%2
    })
    console.log(new)
  ```
  - foreach数组遍历
  ```bash
    let a=[1,2,3,4]
    a.forEach(function(num){
    console.log(num)
    })
  ```
  ---
## 三、对象、DOM操作
### 1.对象（无序的）
```bash
  let a={
    name:"吉祥",
    "now-age":19
    age:18,
    gender:"男"
    hi:function(){
      console.log('欢迎！')
    }
  }
```
| 增 | 删 | 改 | 查 |
| :---: | :---: | :---: | :---: |
| object.height(属性：值) | delete object.属性 | object.属性=值  object['属性']=值|console.log(object.属性) |
- 遍历对象
```bash
for(let k in a){
  console.log(a[k])
}
```
### 2.DOM操作（核心思想是把网页当作对象来处理）
- 什么是DOM（DOM是html与javascript之间的'翻译官'，充当一个接口的作用）
  - 浏览器会根据html标签生成js对象（修改对象的属性会自动映射到标签上）
  - document是DOM里的一个对象，网页的元素都在document里
- 获取DOM元素
  - `document.querySelector('CSS选择器')`
  - 补充伪元素（有索引号，但没有pop()、push()等函数方法）`document.querySeletorAll('CSS选择器')`
- 操作元素内容
  - innertext将文本内容添加到标签位置
  - innerHTML将文本内容添加到标签位置同时可以解析网页标签（如加粗<strong><strong/>）
- 事件监听（绑定）
```bash
const object=document.querySelector('CSS选择器')
objext.addEleventLIstener('click',function(){alert('这是一个弹窗！')})
```
- 事件类型<br>
  <img src="事件类型.png" title='监听事件类型' width=300px height=auto><br>
- 事件对象（相当于事件触发之后，浏览器塞给你的一个对象'信息包'）
  - type(触发的事件类型) clientX/Y(鼠标距离浏览器左上角的坐标) offsetX/Y(相对事件标签)`object.addEvenListener('keydown',function(e){console.log(e.key)})`
### 3.DOM操作的补充
- math（）方法
  - Math.random() 产生0-1的随机数包含0但不包含1
  - Math.floor() 向下取整
- 定时器
  - 间歇定时器 `let var=setinterval(fn,interval[单位是毫秒])` `clearinterval(var)`
  - 延迟定时器 `let var=settimeout(fn,delay)` `cleartimeout(var)`
- 操作元素属性
  - 操作一般属性 var.src='链接'（一般属性常用的有href/src/title）可以通过改变src改变图片
  - 操作元素样式 var.style.width="30px"注意：如果属性有-连接符，需要转换为小驼峰命名法
- class属性
  - 元素.className="css选择器" 新值直接会覆盖旧值
  - 元素.classList.add("类名")
  - 元素.classList.remove("类名")
  - 元素.classList.toggle("类名")
- 添加与删除DOM
  - 创建和插入 let object=document.createElement("div)
    - 追加到父元素的末尾 `父级元素.appendChild('object')`
    - 插入到指定的位置
  ```bash
     let parentNode=document.querySelector("获取父级元素")
     let childNode=document.querySelector("父级元素中的一个子级元素")
     let newItem=document.createElement("span")
     newItem.textContent='插入的内容'
     parentNode.InsertBefore(newItem,chileNode)
  ```
  - 删除DOM
    - 元素.remove()
    - 删除整个父元素 元素.parentNode.remove()
### 4.本地储存
- 数据只能以字符串的形式储存、来保存不频繁更改的数据、避免储存敏感信息
- 持久性/不同域名下不能共享访问
- 建立储存信息  localstorage.setItem('key','value')
- 获取储存的信息 const username=localstorage.getItem('username')
- 删除储存信息 localstorage.remove('username')
- 清空储存 localstorage.clear()
- 遍历储存的数据
```bash
for(let i=0;i<=localstorage.length;i++){
let key=localstorage.key(i)
let value=localstorage.getItem(key)
console.log('${key}:${value}')
}
```
- 注意！如果储存数组或者对象等复杂数据类型，需要先转化为JSON形式
```bash
let object={吉祥:23，如意:12}
localstorage.setItem('key',JSON.stringify(object))
const data=JSON.parse(localstorage.getItem('key'))
```
 - 案例1、现在实现一个功能给网页设计白天黑夜白和浅两种模式，修改后并且保存下次登录网页还是会保存这个设置。
 - 案例2、保存用户的购物车数据
---
## 四、网络请求和BOM（浏览器对象模型）操作
- BOM模型
  - 获取窗口大小`console.log(windows.innerWidth/windows.innerHeight/windows.outerWidth/wondows.outerHeight)`
  - 滚动操作 `windows.scrollTO(x,y)`
  - 获取滚动位置 `console.log(windows.scrollX/windows.scrollY)`
  - 页面 windows.onload(function(){console.log('加载完毕！')})
  - 返回元素的大小及其与浏览器边界位置 元素.getBoundingCliendRect()
- 监听事件补充
  - 窗口大小变化（隐藏目录栏）resize
  - 鼠标的移动、移入和移出 mousemove mouseenter mouseleave
  - 页面滚动 scroll
- 网络请求
  - 
