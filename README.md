<div align="left">
<img alt="Liu Jie" src="https://s2.loli.net/2021/12/16/rxjhMFtGElVIuyz.png" width=50 />
</div>
*I'm LiuJie, a Front-end technical lunatics.*

[Github](https://github.com/laoer536)



# JS错题集

`number与new Number` 

![image-20211230104805912](https://s2.loli.net/2021/12/30/LXKZyqHgjsEx1hJ.png)



函数也是对象（所有对象都有原型 除了null  因为它就是原型链的顶层 ）

![image-20211230105430629](https://s2.loli.net/2021/12/30/ioKhWu9sxRAHeVX.png)



var 可以多次声明 但let const不行

![image-20211230112047296](https://s2.loli.net/2021/12/30/4wZVvlUzKAXCcFW.png)



对象的键和集合的键有所不同

![image-20211230112554474](https://s2.loli.net/2021/12/30/aCP53Zpb2U6Fqgv.png)



对象中存在同名键  后面的同名键会覆盖前面的同名键 但是最终位置不变 只是键值更新

![image-20211230113023144](https://s2.loli.net/2021/12/30/WImhQnwoV3P6H4x.png)



对象作为键时 因为键key都会转化为字符串 对象转化为字符串都是“[object object]”  所以相当于连续两次的给这个键赋值  最终结果为456

![image-20211230114708696](https://s2.loli.net/2021/12/30/zYNt3P6ErmUiKpZ.png)



js事件处理程序默认是在冒泡阶段执行  所以默认是从里向外的执行的  

![image-20211230135859527](https://s2.loli.net/2021/12/30/DXqsE8lTROWnBAH.png)



call bind apply  (在this指向改变的情况下，bind是返回一个函数，而不是改变this指向执行，这一点区别很大)

![image-20211230140507489](https://s2.loli.net/2021/12/30/GXL96yPbqhzgOdC.png)



数组的空槽部分表示为null还是empty---当然是empty

![image-20211230141817740](https://s2.loli.net/2021/12/30/sxYjrZA9k5QvX2i.png)



关于函数参数的作用域仅属于函数内部

`以下catch接收到的x不是整个函数上下文的x 而是内部块级重新声明的x  印证 函数传入的参数 就相当于内部用let声明了一次 是块级的变量`

![image-20211230143145703](https://s2.loli.net/2021/12/30/tOCTb3VR2xPNFzu.png)

```js
function getName (firstName,lastName){

	return firstName+lastName;

}

//近似于

function getName (firstName,lastName){

	let firstName = firstName;  //注意 如果传入的参数是对象或者数组 还是存在拷贝问题(引用传递)  如果不是 则其实就是一个块级作用域变                                //   量 不影响外部的参数值  

	let lastName = lastName;   
    
	return firstName+lastName;  //这里执行的话返回NaN

}
```

类似

![image-20211231095353741](https://s2.loli.net/2021/12/31/fhp2ePaQS8gKAL3.png)

![image-20211231100958882](https://s2.loli.net/2021/12/31/3hXxT17RI4g29z5.png)

`总结一下：关于值之间的对比变化 以及相互关系的影响 一看引用类型 二看作用域 总的理解就是用C++的指针类比`





JS任何事物的组成

基本类型：boolean、null、unidefined、bigint、number、string、symbol

引用类型（Object）：Function、Object、Array、Date、RegExp、Boolean、String、Number

![image-20211214164042568](https://s2.loli.net/2021/12/14/2lKwhRvyrxa1CUn.png)

![image-20211230145039904](https://s2.loli.net/2021/12/30/aDm7AFB9kN81ojd.png)

`原始类型是没有任何属性或方法的，但是为什么又可以直接使用一些方法，原因上面已经写得很清楚了：简单的说就是试图访问属性或者方法时，JS会隐式地使用其可对应的封装类（包装类）来对其进行封装，从而扩展了他的能力，null和undefined除外。`



array.reduce基础

![image-20211230151308895](https://s2.loli.net/2021/12/30/LNoy3VhiPfj1tA5.png)

拓展：array.reduce((acc,cur,index,array=>{return ------),initialValue)  (acc必传 代表累计器值)

> 累加器的值等于回调函数先前返回的值。若没有返回则为undefined

```js
arr.reduce(callback(accumulator, currentValue[, index[, array]])[, initialValue])
```

1. Accumulator (acc) (累计器)

2. Current Value (cur) (当前值)

3. Current Index (idx) (当前索引)

4. Source Array (src) (源数组)

   

`!!`转换数据为布尔类型

![image-20211230152509511](https://s2.loli.net/2021/12/30/jHDqwWtplaJsfCr.png)



setInterval返回一个执行的唯一id

![image-20211230153108600](https://s2.loli.net/2021/12/30/LFA4l3uZbNtHIjh.png)

![image-20211230153313853](https://s2.loli.net/2021/12/30/6ylOLoNVCF4t39I.png)

`执行clearInterval后Hi变不再打印`



这种情况不存在拷贝

![](https://s2.loli.net/2021/12/30/YsnWC6kqMgzUcVP.jpg)



这里对比一下就可以看出为什么了

![image-20211230155929783](https://s2.loli.net/2021/12/30/aFoqcHklgDh9z87.png)

意思就是说改变person并没有改变对象`{name:'Lydia'}`本身。关于这种拷贝问题，主要的关注点就是被引用的对象是否改变了，没改变就不变。本问题中person=null;只是将person的引用指向换了，换成了null，所以并没有改到对象本身，所以member[0]也并未改变。这里类似于C++的指针。



for in 遍历键名key（注意区分与for of遍历item 用于数组，不能用于对象）

![image-20211230163129390](https://s2.loli.net/2021/12/30/2Dj1TidspRP5vwV.png)

![image-20211230161753987](https://s2.loli.net/2021/12/30/xzewUycWMNHKdnu.png)

`在数组中也是如此`

![image-20211230162418553](https://s2.loli.net/2021/12/30/qOTAwHLyo3InJPc.png)



`+`号运算的关联性是从左到右的

3+4+‘5’并不等于345，前面的要先运算

![image-20211230163637270](https://s2.loli.net/2021/12/30/QbHmWjnVSEFNhk1.png)



扩展一下parseInt

![image-20211230164709792](https://s2.loli.net/2021/12/30/oC9x4UVkhReLf5E.png)



函数return；截止的话相当于function():void{}    void表示无返回值    即undefined

![image-20211230165457390](https://s2.loli.net/2021/12/30/tcWbCBum3ZiSI9e.png)



throw--抛出错误：throw一旦调用即抛出错误并直接进入catch部分

![image-20211231102654342](https://s2.loli.net/2021/12/31/DIxFmkGQ7fLybiC.png)



针对构造函数存在return返回值的情况：

> 如果返回基本类型：则return近似无效 构造函数体生效 new之后得到其本身内容
>
> 如果返回引用类型：则return有效 构造函数体无效 new之后得到其return部分

![image-20211231103506168](https://s2.loli.net/2021/12/31/3n61EKZXN52rTGy.png)

```js
function Car() {
  this.make = "Lamborghini";
  return [{ make: "Maserati" }];
}

const myCar = new Car();
console.log(myCar);    // 输出 [ { make: 'Maserati' } ]
```

```js
function Car() {
  this.make = "Lamborghini";
  return { make: "Maserati" };
}

const myCar = new Car();
console.log(myCar);  //输出 { make: 'Maserati' }
```

```js
function Car() {
  this.make = "Lamborghini";
  return /sdsd/;
}

const myCar = new Car();
console.log(myCar);  //   /sdsd/
```

```js
function Car() {
  this.make = "Lamborghini";
  return 111111;
}

const myCar = new Car();
console.log(myCar);  // Car { make: 'Lamborghini' }
```

```js
function Car() {
  this.make = "Lamborghini";
  return "11111111";
}

const myCar = new Car();
console.log(myCar);  // Car { make: 'Lamborghini' }
```



探究在顶层声明变量和在函数作用域中声明变量的区别

![image-20211231145957461](https://s2.loli.net/2021/12/31/Pczpd7LVsZSEDtb.png)

![image-20211231151119630](https://s2.loli.net/2021/12/31/gxoXnp2JWFD5jZC.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=no,viewport-fit=cover">
    <title>Title</title>
</head>
<body>

<script>
  a=2;
  console.log('window.y',window.a);

  let b = 2;
  console.log('window.b',window.b);

  var c= 2;
  console.log('window.c',window.c);
</script>
</body>
</html>
```

结果：

![image-20211231151932428](https://s2.loli.net/2021/12/31/k7OKrM968UosXtu.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=no,viewport-fit=cover">
    <title>Title</title>
</head>
<body>

<script>
/*  a=2;
  console.log('window.y',window.a);

  let b = 2;
  console.log('window.b',window.b);

  var c= 2;
  console.log('window.c',window.c);*/

  function set(){
      a=2;
      console.log('window.y',window.a);

      let b = 2;
      console.log('window.b',window.b);

      var c= 2;
      console.log('window.c',window.c);
  }

set();

  console.log(a);
  console.log(b);
  console.log(c);



  // window.set();
</script>
</body>
</html>
```

结果：

![image-20211231152844770](https://s2.loli.net/2021/12/31/DNMb2PCzgnS89e3.png)

总结一下：

> 顶层声明：
>
> var 和 直接不用关键字声明的方式 都会添加到window上。let 和const不会。
>
> 
>
> 在函数作用域中声明：
>
> var在函数作用域声明的话也是只作用于这个函数的 以前的理解存在错误  函数作用域用关键字var let const声明的变量常量，只在函数作用域中有效，外部不能访问。特例就是不用关键字声明，如上图直接`a=2`，这种方式声明的话，不作用于局部，而是作用于全局对象（浏览器中的window，Node中的global）添加了一个属性。



delete关键字不仅可以删除对象中的属性，也可以删除原型上的属性。

![image-20211231155026281](https://s2.loli.net/2021/12/31/i5Z2lpX9R7VKyrx.png)

delete关键字成功删除返回true 否则返回false

不能删除由var let const声明的变量/常量

以下第二个为`true`的原因是 `delete age`相当于`delete window.age`

![image-20211231162058150](https://s2.loli.net/2021/12/31/2FGZB3MOyWPnwgj.png)



关于js中模块导入导出，以及读取修改问题：

> 导入的模块只读
> 只有导出的才能修改

![image-20211231161318016](https://s2.loli.net/2021/12/31/FT31LtlhMfVvu2c.png)



数组解构:当解构数量左右不一致时，则按顺序取值。

![image-20211231163823129](https://s2.loli.net/2021/12/31/lHGm3bq9AWU1BEt.png)



使用defineProperty给对象添加新的属性，或修改现有属性（这种方式默认不可枚举）

![image-20211231164632731](https://s2.loli.net/2021/12/31/U7rDB4fERub9Zwv.png)



扩展：

该方法是es5的方法（千万不要以为是es6的哦），作用是直接在一个对象上定义一个新属性，或者修改一个对象的现有属性， 并返回这个对象。（**切记只能用在对象身上不能用在数组身上**）

1、语法

```js
Object.defineProperty(obj, prop, descriptor)
```

2、参数说明：

- obj：必需。目标对象 
- prop：必需。需定义或修改的属性的名字
- descriptor：必需。目标属性所拥有的特性

3、属性使用案例

修改某个属性的值时，给这个属性添加一些特性。

```js
let person = {}; 
Object.defineProperty(person, 'name', {   
    writable: true || false,   
    configurable: true || false,   
    enumerable: true || false,  
    value:'gjf' 
});
```

属性详解：

- writable：是否可以被重写，true可以重写，false不能重写，默认为false。
- enumerable：是否可以被枚举（使用for...in或Object.keys()）。设置为true可以被枚举；设置为false，不能被枚举。默认为false。
- value：值可以使任意类型的值，默认为undefined
- configurable：是否可以删除目标属性或是否可以再次修改属性的特性（writable, configurable, enumerable）。设置为true可以被删除或可以重新设置特性；设置为false，不能被可以被删除或不可以重新设置特性。默认为false。

4、存取器描述（get和set）

- **注意：当使用了getter或setter方法，不允许使用writable和value这两个属性**

```js
let person = {};
let n = 'gjf';
Object.defineProperty(person, 'name', { 
    configurable: true,  
    enumerable: true, 
    get() {    
        //当获取值的时候触发的函数    
        return n  
    },  
    set(val) {    
        //当设置值的时候触发的函数,设置的新值通过参数val拿到    
        n = val;  
    }
});
console.log(person.name) //gjf
person.name = 'newGjf'
console.log(person.name) //newGif
```

[Object.defineProperty的用法详解 - 掘金 (juejin.cn)](https://juejin.cn/post/6844903759802286088)



JSON.stringfy可以配置其转化

> JSON.stringfy不仅有将我们的数据转化为JSON字符串对象的能力，我们还可以对其转化进行配置

> `JSON.stringify()`将值转换为相应的JSON格式：
>
> - 转换值如果有 toJSON() 方法，该方法定义什么值将被序列化。
> - 非数组对象的属性不能保证以特定的顺序出现在序列化后的字符串中。
> - 布尔值、数字、字符串的包装对象在序列化过程中会自动转换成对应的原始值。
> - `undefined`、任意的函数以及 symbol 值，在序列化过程中会被忽略（出现在非数组对象的属性值中时）或者被转换成 `null`（出现在数组中时）。函数、undefined 被单独转换时，会返回 undefined，如`JSON.stringify(function(){})` or `JSON.stringify(undefined)`.
> - 对包含循环引用的对象（对象之间相互引用，形成无限循环）执行此方法，会抛出错误。
> - 所有以 symbol 为属性键的属性都会被完全忽略掉，即便 `replacer` 参数中强制指定包含了它们。
> - Date 日期调用了 toJSON() 将其转换为了 string 字符串（同Date.toISOString()），因此会被当做字符串处理。
> - NaN 和 Infinity 格式的数值及 null 都会被当做 null。
> - 其他类型的对象，包括 Map/Set/WeakMap/WeakSet，仅会序列化可枚举的属性。

![](https://s2.loli.net/2022/01/04/gruSs3otEB9kph6.png)



number++   首先返回变化之前的值  和C++类似

![image-20220104152059773](https://s2.loli.net/2022/01/04/P68Rytw1DG52EkC.png)





默认参数会被分配一个空间 这时不存在引用问题

![image-20220104153014617](https://s2.loli.net/2022/01/04/7Dj6axVK1Ln9MFf.png)



类的继承（扩展类继承产生的重写特性）

![image-20220104204559384](https://s2.loli.net/2022/01/04/PlZwXaYyE9JCeqB.png)

```typescript
(function () {
    class Animal {
        name: string;

        constructor(name: string) {
            this.name = name;
        }

        sayHello() {
            console.log('动物在叫~');
        }
    }

    class Dog extends Animal{

        age: number;

        constructor(name: string, age: number) {
            // 如果在子类中写了构造函数，在子类构造函数中必须对父类的构造函数进行调用（因为存在重写 子类的constructor会覆盖掉父类的constructor 所以这里必须使用super 即使父类没有书写constructor（父类存在隐式的constructor生成））
            //即同名方法的重写
            super(name); // 调用父类的构造函数
            //super();   //如果父类没有需要要传入参数的情况 也要手动调用super()
            this.age = age;
        }

        sayHello() {
            // 在类的方法中 super就表示当前类的父类
            //super.sayHello();

            console.log('汪汪汪汪！');
        }

    }

    const dog = new Dog('旺财', 3);
    dog.sayHello();
})();
```



![image-20220104212010025](https://s2.loli.net/2022/01/04/N8UoAHYwejbh19F.png)







































