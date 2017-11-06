# ECMAScript2015678

> 全新的JavaScript语法

### let、const：

```js
  let : 块级作用域
  const ： 定义常量
```

### 解构赋值：

```js
  //array
  let [a,b,c] = ['aaa','bbb','ccc'];
  console.log(a);
  console.log(b);
  console.log(c);

  //object
  let obj = {
    a:a,
    b:b,
    c:c
  } = {
    a:'10',
    b:true,
    c:100000000000
  }
  console.log(obj.a);
  console.log(obj.b);
  console.log(obj.c);

  //object2
  let obj2 = {
    a,
    b,
    c
  } = {
    a:'10',
    b:true,
    c:100000000000
  }
  console.log(obj2.a);
  console.log(obj2.b);
  console.log(obj2.c);

```

### 模板字符串：

```js
  var eating = 'cake',
      drink = 'milk';

  //传统拼接字符串
  var breakfast = '今天早上吃的是:' + eating + ',喝的是：' + drink;
  console.log(breakfast);

  //es6模板字符串
  var breakfast2 = `今天早上吃的是：${eating},喝的是：${drink}`;
  console.log(breakfast2);
```

### 默认参数：

```js
  function add(x,y=1000) {
    return x + y;
  }

  console.log(add(200));
  console.log(add(200,300));
```

### 展开操作符：

```js
  let arr = ['你好',true,100000,'fjdiso'];
  let newArr = [...arr,'新的数组1','新的数组2'];
  console.log(newArr); //["你好", true, 100000, "fjdiso", "新的数组1", "新的数组2"];
```

### 剩余操作符：

```js
  function fn(a,b,c,...d) {
    console.log(a,b,c,...d);
  }

  fn(100,'fds','fjksd',20000);
```

### 函数的名字：

```js
  let fn = function(arg){

  }
  console.log(fn.name); //fn
```

### 箭头函数：
> 有人说js函数 function 没有什么实际作用，所以去掉 function。

```js
  let fnn = (a,b) => {
    return a + b ;
  }

  console.log(fnn(1,3));
```

### 对象表达式：

```js
  let a = 'hello',
      b = 100000,
      c = function(){
        console.log('c');
      }

  let obj = {
      a,
      b,
      c
  }

  console.log(obj);
  obj.c();
```

### 对比两个值是否相等：

```js
  console.log(Object.is(100,'100'));

  console.log(Object.is(NaN,'12'));

  console.log(Object.is(NaN,NaN)); //true
```

### 把对象的值复制到另一个对象里：
> 相当于jquery中的extend

```js
  let obj = {a:200};

  Object.assign(
    obj,
    {a:1000,b:'fjdskhk'},
    {a:50000000}
  );

  console.log(obj); //{a: 50000000, b: "fjdskhk"}
```

### 设置对象的prototype  __proto__：

```js
  let obj1 = {
    getA(){
      return 'a';
    },
    a:1000
  }

  let obj2 = {
    getB(){
      return 'b';
    }
  }

  let c = Object.create(obj1);

  console.log(c.getA()); //a
  console.log(Object.getPrototypeOf(c)); //obj1

  Object.setPrototypeOf(c,obj2);
  console.log(c.getB());
  console.log(Object.getPrototypeOf(c)); //obj2

  // __proto__ ES6对这个进行了支持
  let c = {
    __proto__:obj1
  }
  console.log(c.getA()); //a
  console.log(Object.getPrototypeOf(c)); //obj1

```

### super 调取父级的东西：

```js
  let obj1 = {
    getA(){
      return 'a';
    }
  }

  let obj2 = {
    getA(){
      return 'b';
    }
  }

  let c = {
    __proto__: obj2,
    getA(){
      return 'c'
    },
    getB(){
      return super.getA();
    }
  }

  console.log(c.getA());
  console.log(c.getB());
```

### class类 类的定义和继承：

```js
  class People {
    constructor(name,age){
      this.__name = name;
      this.__age = age;
    }

    getName(){
      return this.__name;
    }

    //静态方法
    static getAge(){
      console.log('age');
    }

  }

  let xiaoming = new People('xiaoming',12);
  console.log(xiaoming);
  let n = xiaoming.getName();
  console.log(n);

  //类方法
  People.getAge();


  //*继承
  class Chengxuyuan extends People {
    constructor(name,age,salary) {
      super(name,age);
    }

    getAge(){
      console.log(this.age);
    }

  }


  let xiaohui = new Chengxuyuan('xiaohui',22);
  console.log(xiaohui.getName());
```

### Set:

```js
  let s = new Set('abcd');
  console.log(s); // {"a", "b", "c", "d"}

  let s1 = new Set(['dsa',100,'hsdfkj']);
  console.log(s1); //{"dsa", 100, "hsdfkj"}

  console.log(s1.size); //3
  console.log(s1.has(100)); //true
  s1.delete('dsa');
  console.log(s1); //{100, "hsdfkj"}

  s1.forEach(i => {
    console.log(i);
  }); //i 是形参 100 "hsdfkj"

```

### Map:

```js
  let m = new Map(); //k-v

  m.set('a',1000000);
  m.set('b','fjkdsljkfl');

  console.log(m);

  console.log(m.get('b')); //fjkdsljkfl

```

### ES6模块化开发 （最重要的部分）:

```js

   export default

   import a from './a.js'

```
