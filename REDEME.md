# JS对象的基本语法

## 声明对象的两种方法

```javascript
//第一种：简略写法
let obj = {'name':'frank','age':18}

//第二种：规范写法
let obj = new Object({'name':'frank'})
```
* 键名是字符串不是标识符，可以包含任何字符
  
* 引号可以省略，省略之后值可以写标识符
  
* 省略引号键名依旧是字符串
  
## 属性名与属性值
  
属性名：每个key都是对象的属性名

属性值：每个value都是对象的属性值

## 对象的隐藏属性

* JS中每一个对象都有一个隐藏属性

* 这个隐藏属性储存着其共有属性组成的对象的地址
  
* 这个共有属性组成的对象叫做原型

* 也就是说，隐藏属性储存着原型的地址

## 如何删除对象的属性

```javascript
delete obj .xxx

delete obj['xxx']
//检验方法1不含属性名：
'xxx' in obj === flase

//检验方法2含有属性名，但值为undefined：
'xxx' in obj && obj.xxx === undefined
```

## 如何查看对象的属性

* 查看自身所有属性
  
  Object.keys(obj)

* 查看自身+共有属性
  
  console.log(obj) || 依次用Object.keys答应出obj.__proto__

* 判断一个属性是自身还是共有
  
  obj，hasOwnProperty('toString')

## 如何修改或增加对象的属性

* 直接赋值
  
```javascript
//name 是字符串
let obj = {name: 'frank'}
//name 是字符串
obj.name = 'frank'
//name 是字符串
obj['name'] = 'frank'
```

* 批量赋值

```javascript
//obj:赋值对象
Obj.assign（obj，{age：18， gender:'man'}）
```

* 修改或增加共有属性

一半情况下不推荐修改原型共有属性，会引起很多的问题

```javascript

//无法通过自身修改或增加共有属性

//obj与obj2共有toString
let obj = {}，obj2 = {}
//只会修改obj自身属性，obj2.toString还在原型上
obj.toString = 'xxx'
```
如果偏要修改或增加原型上的属性

```javascript
//不推荐用__proto__
obj.__proto__.toString = 'xxx'

Object.prototype.toString = 'xxx'
```
## 增删改查总结

删：

* delete obj['name']

查：

* Object.keys()obj
* console.dir()obj
* obj['name']
* obj.name————这里的name是字符串
* obj[name]————这里的那么是变量

改：

* 改自身：obj['name'] = 'jack'
* 批量改自身：Object。assign（objk,{age:18}）
* 改共有属性：Object.prototype['toString'] = 'xxx'
* 改原型：let obj = Object.create(common)

增：

* 基本同上，已有属性则改，没有属性则增

## 'name' in obj和obj.hasOwnProperty('name')区别

* 'name' in obj:用来判断obj对象不含某属性

* obj hasOwnProperty('name'):用来判断一个属性是obj自身的还是原型共有属性