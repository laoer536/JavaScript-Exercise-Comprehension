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



import和require的一个区别：一个是提升到顶层 一个是运行时按需加载（优先级不会被提升）

![image-20220105091358136](https://s2.loli.net/2022/01/05/H1SoXRYj7bqBpx5.png)



Symbol创建唯一值  与传入的参数无关

![image-20220105092147722](https://s2.loli.net/2022/01/05/2DdoQNxnPFmaSkJ.png)

特殊符号处理为字符串 可以正常输出

![image-20220105093204025](https://s2.loli.net/2022/01/05/KODdzshvB1YJipN.png)

这样就不行：

![image-20220105093344357](https://s2.loli.net/2022/01/05/LznI4Albfe1dk3J.png)



生成器函数`function*`

![image-20220105094312215](https://s2.loli.net/2022/01/05/hEnRGW4ad5pcHsV.png)

扩展：

 [语法]

```
function* name([param[, param[, ... param]]]) { statements }
```

- `name`

  函数名

- `param`

  要传递给函数的一个参数的名称，一个函数最多可以有255个参数。

- `statements`

  普通JS语句。

[描述]

**生成器函数**在执行时能暂停，后面又能从暂停处继续执行。

调用一个**生成器函数**并不会马上执行它里面的语句，而是返回一个这个生成器的 **迭代器** **（ [iterator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#iterator) ）对象**。当这个迭代器的 `next() `方法被首次（后续）调用时，其内的语句会执行到第一个（后续）出现[`yield`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/yield)的位置为止，[`yield`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/yield) 后紧跟迭代器要返回的值。或者如果用的是 [`yield*`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/yield*)（多了个星号），则表示将执行权移交给另一个生成器函数（当前生成器暂停执行）。

`next()`方法返回一个对象，这个对象包含两个属性：value 和 done，value 属性表示本次 `yield `表达式的返回值，done 属性为布尔类型，表示生成器后续是否还有` yield `语句，即生成器函数是否已经执行完毕并返回。

调用 `next()`方法时，如果传入了参数，那么这个参数会传给**上一条执行的 yield语句左边的变量**，例如下面例子中的` x `：

```js
function *gen(){
    yield 10;
    x=yield 'foo';
    yield x;
}

var gen_obj=gen();
console.log(gen_obj.next());// 执行 yield 10，返回 10
console.log(gen_obj.next());// 执行 yield 'foo'，返回 'foo'
console.log(gen_obj.next(100));// 将 100 赋给上一条 yield 'foo' 的左值，即执行 x=100，返回 100
console.log(gen_obj.next());// 执行完毕，value 为 undefined，done 为 true
```

当在生成器函数中显式 `return `时，会导致生成器立即变为完成状态，即调用 `next()` 方法返回的对象的 `done `为 `true`。如果 `return `后面跟了一个值，那么这个值会作为**当前**调用 `next()` 方法返回的 value 值。



`yield*` 可以移交执行权

```js
function* anotherGenerator(i) {
  yield i + 1;
  yield i + 2;
  yield i + 3;
}

function* generator(i){
  yield i;
  yield* anotherGenerator(i);// 移交执行权
  yield i + 10;
}

var gen = generator(10);

console.log(gen.next().value); // 10
console.log(gen.next().value); // 11
console.log(gen.next().value); // 12
console.log(gen.next().value); // 13
console.log(gen.next().value); // 20
```



String.raw()  （可以忽略字符串中的转义字符的影响）

> 在大多数情况下, `String.raw()`是用来处理模版字符串的.

![image-20220105100503579](https://s2.loli.net/2022/01/05/syMzt5DGnrRShcV.png)

```js
String.raw`Hi\n${2+3}!`;
// 'Hi\\n5!'，Hi 后面的字符不是换行符，\ 和 n 是两个不同的字符

String.raw `Hi\u000A!`;
// "Hi\\u000A!"，同上，这里得到的会是 \、u、0、0、0、A 6个字符，
// 任何类型的转义形式都会失效，保留原样输出，不信你试试.length

let name = "Bob";
String.raw `Hi\n${name}!`;
// "Hi\nBob!"，内插表达式还可以正常运行


// 正常情况下，你也许不需要将 String.raw() 当作函数调用。
// 但是为了模拟 `t${0}e${1}s${2}t` 你可以这样做:
String.raw({ raw: 'test' }, 0, 1, 2); // 't0e1s2t'
// 注意这个测试, 传入一个 string, 和一个类似数组的对象
// 下面这个函数和 `foo${2 + 3}bar${'Java' + 'Script'}baz` 是相等的.
String.raw({
  raw: ['foo', 'bar', 'baz']
}, 2 + 3, 'Java' + 'Script'); // 'foo5barJavaScriptbaz'
```



async返回的是一个Promise对象 

![image-20220105101346125](https://s2.loli.net/2022/01/05/oxMmduZgRnqyz1f.png)



Object.freeze 冻结对象 （误选为D 严格模式启用了才选D）

> 关于严格模式的更多信息查看：[JS中「严格模式」与「非严格模式」有什么区别？ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/362078508)

![image-20220105102528223](https://s2.loli.net/2022/01/05/bzC7Jj49RY6INPl.png)



```js
var obj = {
  prop: function() {},
  foo: 'bar'
};

// 新的属性会被添加, 已存在的属性可能
// 会被修改或移除
obj.foo = 'baz';
obj.lumpy = 'woof';
delete obj.prop;

// 作为参数传递的对象与返回的对象都被冻结
// 所以不必保存返回的对象（因为两个对象全等）
var o = Object.freeze(obj);

o === obj; // true
Object.isFrozen(obj); // === true

// 现在任何改变都会失效
obj.foo = 'quux'; // 静默地不做任何事
// 静默地不添加此属性
obj.quaxxor = 'the friendly duck';

// 在严格模式，如此行为将抛出 ReferenceError
function fail(){
  'use strict';
  obj.foo = 'sparky'; // throws a ReferenceError
  delete obj.quaxxor; // 返回true，因为quaxxor属性从来未被添加
  obj.sparky = 'arf'; // throws a ReferenceError
}

fail();

// 试图通过 Object.defineProperty 更改属性
// 下面两个语句都会抛出 TypeError.
Object.defineProperty(obj, 'ohai', { value: 17 });
Object.defineProperty(obj, 'foo', { value: 'eit' });

// 也不能更改原型
// 下面两个语句都会抛出 TypeError.
Object.setPrototypeOf(obj, { x: 20 })
obj.__proto__ = { x: 20 }
```

补充：

**ReferenceError：**

相较于TypeError，ReferenceError 其实更容易被理解，他的错误就是字面意思，引用错误。这意味着在尝试引用一个不存在当前作用域中的变量/常量时产生的错误。

```js
let a = b; // ReferenceError，因为 b 未被定义
console.log(c) // ReferenceError，因为 c 未被定义
```

**TypeError：**

TypeError 会发生在值的类型不符合预期时。换句话说，在对值的操作方法不存在或并未正确的定义时，TypeError 就会被返回。

```js
let a; // a = undefined
console.log(a.b) // TypeError,无法从 undefined 这个类型上读取属性

let c = 1;
console.log(c()) // TypeError，c并不是一个函数
```



关于解构中重命名的问题

![image-20220105141400237](https://s2.loli.net/2022/01/05/JOaUGs4lvXg9LV3.png)



Pure Function (纯函数)

> 纯函数是满足如下条件的函数：
>
> - 相同输入总是会返回相同的输出。
> - 不产生副作用。
> - 不依赖于外部状态。

![image-20220105142311067](https://s2.loli.net/2022/01/05/f9niUYoRVgZwJHy.png)



函数中如果传入的值有计算 则会先进行计算在传入函数

![image-20220105145812204](https://s2.loli.net/2022/01/05/bDujPLIGHYWVTSf.png)

扩展：

`in`关键字
如果指定的属性在指定的对象或其原型链中，则in 运算符返回true。

```js
// 数组
var trees = new Array("redwood", "bay", "cedar", "oak", "maple");
0 in trees        // 返回true
3 in trees        // 返回true
6 in trees        // 返回false
"bay" in trees    // 返回false (必须使用索引号,而不是数组元素的值)

"length" in trees // 返回true (length是一个数组属性)

Symbol.iterator in trees // 返回true (数组可迭代，只在ES2015+上有效)


// 内置对象
"PI" in Math          // 返回true

// 自定义对象
var mycar = {make: "Honda", model: "Accord", year: 1998};
"make" in mycar  // 返回true
"model" in mycar // 返回true
```

补充一下 只要涉及到表达式、运算 运行时JS都会将其先执行了 再输出

![image-20220105150401966](https://s2.loli.net/2022/01/05/PC958LvyuklX1Zr.png)



选成了A  啊我的天  即使是undefined 也是要输出的大哥

![image-20220105151232978](https://s2.loli.net/2022/01/05/6whXRsOfI8olWmC.png)



以下只是起调用 并没有修改对象  调用`person.city`并不会引发属性的创建 

![image-20220105152255902](https://s2.loli.net/2022/01/05/2V5OSMGrwmet8yd.png)



块级作用域啊  大哥  （亏）

![image-20220105174333601](https://s2.loli.net/2022/01/05/t8C3edDaFvwxEmq.png)



异步处理中` .then`中如果有返回值 那么下一个` .then`接收到的参数值就是上一个` .then`的返回值

![image-20220106174216733](https://s2.loli.net/2022/01/06/ow1CgrB9EPOtbJK.png)



扩展：

fetch: [使用 Fetch - Web API 接口参考 | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API/Using_Fetch)

```js
// Example POST method implementation:
async function postData(url = '', data = {}) {
  // Default options are marked with *
  const response = await fetch(url, {
    method: 'POST', // *GET, POST, PUT, DELETE, etc.
    mode: 'cors', // no-cors, *cors, same-origin
    cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
    credentials: 'same-origin', // include, *same-origin, omit
    headers: {
      'Content-Type': 'application/json'
      // 'Content-Type': 'application/x-www-form-urlencoded',
    },
    redirect: 'follow', // manual, *follow, error
    referrerPolicy: 'no-referrer', // no-referrer, *no-referrer-when-downgrade, origin, origin-when-cross-origin, same-origin, strict-origin, strict-origin-when-cross-origin, unsafe-url
    body: JSON.stringify(data) // body data type must match "Content-Type" header
  });
  return response.json(); // parses JSON response into native JavaScript objects
}

postData('https://example.com/answer', { answer: 42 })
  .then(data => {
    console.log(data); // JSON data parsed by `data.json()` call
  });
```



函数参数默认值可以与先前声明的参数建立引用关系

![image-20220110100130590](https://s2.loli.net/2022/01/10/L7cuKfThxViGFAk.png)



default是导出产生对象的一个属性，属性名为‘default’  

![image-20220110103357444](https://s2.loli.net/2022/01/10/QnLTPxw4HKWb8vu.png)

![image-20220110105758532](https://s2.loli.net/2022/01/10/bvlgaI2WOhA9T1n.png)



箭头函数没有原型 所以功能上有些不能用

> [箭头函数 - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

![image-20220110112230594](https://s2.loli.net/2022/01/10/zyWp2Yg4Fui5Te7.png)

![image-20220110113438504](https://s2.loli.net/2022/01/10/MK8oBsFGnOEkzYy.png)

> 1、通过 call 或 apply 调用
>
> 由于 箭头函数没有自己的this指针，通过 `call()` *或* `apply()` 方法调用一个函数时，只能传递参数（不能绑定this---译者注），他们的第一个参数会被忽略。（这种现象对于bind方法同样成立---译者注）即改变指向无效
>
> 2、[没有单独的`this`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions#没有单独的this)
>
> 在箭头函数出现之前，每一个新函数根据它是被如何调用的来定义这个函数的this值：
>
> - 如果该函数是一个构造函数，this指针指向一个新的对象
> - 在严格模式下的函数调用下，this指向undefined
> - 如果该函数是一个对象的方法，则它的this指针指向这个对象
> - 等等
>
> `This`被证明是令人厌烦的面向对象风格的编程。
>
> ✨箭头函数不会创建自己的`this,它只会从自己的作用域链的上一层继承this`。
>
> 3、[不绑定`arguments`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions#不绑定arguments)
>
> 箭头函数不绑定[Arguments 对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/arguments)。因此，在本示例中，`arguments`只是引用了封闭作用域内的arguments：
>
> ```js
> var arguments = [1, 2, 3];
> var arr = () => arguments[0];
> 
> arr(); // 1
> 
> function foo(n) {
>   var f = () => arguments[0] + n; // 隐式绑定 foo 函数的 arguments 对象. arguments[0] 是 n,即传给foo函数的第一个参数
>   return f();
> }
> 
> foo(1); // 2
> foo(2); // 4
> foo(3); // 6
> foo(3,2);//6
> ```
>
> 4、[使用 `new` 操作符](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions#使用_new_操作符)
>
> 箭头函数不能用作构造器，和 `new`一起用会抛出错误。
>
> ```js
> var Foo = () => {};
> var foo = new Foo(); // TypeError: Foo is not a constructor
> ```
>
> 5、[使用 `yield` 关键字](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions#使用_yield_关键字)
>
>  `yield` 关键字通常不能在箭头函数中使用（除非是嵌套在允许使用的函数内）。因此，箭头函数不能用作函数生成器。
>
> 6、[使用`prototype`属性](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions#使用prototype属性)
>
> ```js
> var Foo = () => {};
> console.log(Foo.prototype); // undefined
> ```
>
> 7、返回对象
>
> ```js
> var func = () => ({foo: 1});
> ```



剩余参数只能放在函数的最后一个位置 

![image-20220110141129367](https://s2.loli.net/2022/01/10/e7NVAgkTrS6Jvfq.png)



JS引擎会自动在语句后添加分号  如果代码不规范 这个特性会产生意外的BUG

![image-20220110142244346](https://s2.loli.net/2022/01/10/mAw6Th4jfnSIe3u.png)

![image-20220110142150319](https://s2.loli.net/2022/01/10/3uKaW4LtcODh9qZ.png)

扩展：关于花括号的简写

```js
var a = 10,b = 20;
/**
 * if 简写
 */
if(a > b) console.log('a大');
if(a < b) console.log('b大');
/**/
if(a > b) console.log('a大');
else console.log('b大');

/**
 * for简写
 */
for(var i=0; i<10; ++i) console.log(i);

/**
 * while简写
 */
while (i > 10) console.log(i);
```

一个网上的例子

![image-20220110143433776](https://s2.loli.net/2022/01/10/1mKRzeCvlO8ogM7.png)



![image-20220110144047278](https://s2.loli.net/2022/01/10/sLxeKzi7Solf1kN.png)

![image-20220110144727720](https://s2.loli.net/2022/01/10/TejCn3orwlHGxWa.png)

一个是类一个是构造函数 也可以相互替换 不必对应

![image-20220110145252432](https://s2.loli.net/2022/01/10/XJxQF6CYl7j3iLW.png)



Symbol()作为键名时 用Object.key()遍历时 将不可见

![image-20220110150817866](https://s2.loli.net/2022/01/10/MwCRXINknPJKgci.png)

Symbol还是很妙的，参考：[javascript中symbol类型的应用场景（意义）和使用方法 - 前端开发博客 (nblogs.com)](https://www.nblogs.com/archives/489/)



&&运算符的使用

![image-20220110153934440](https://s2.loli.net/2022/01/10/e4MsUPOwlGkJ8Wn.png)



同步>异步(先微后宏)

![image-20220110155929693](https://s2.loli.net/2022/01/10/trBovp8yY5KaNRI.png)



加号运算符会将非数字转化为string类型 相当于调用toString()方法

![image-20220110171933895](https://s2.loli.net/2022/01/10/IWXaRb6rZU5gfhp.png)

对象比较：依据是引用地址 地址相等即相等

像字符串以及数值这种基本类型是依据它们的值进行比较的；但像数组、日期以及简单对象这类object是根据它们的引用进行判断的。依据引用的判断会检查所给的object是否指向内存中的相同地址。

![image-20220119172830553](https://s2.loli.net/2022/01/19/GObTxwHUdIgXQVh.png)

扩展：

> [比较 JavaScript | 中的两个对象技术喜悦 (techiedelight.com)](https://www.techiedelight.com/compare-two-objects-javascript/#:~:text=This post will discuss how to compare two,comparison%2C and all their properties are equal. 1.)



对象中通过`.`和`[]`访问元素的区别与进一步认识

![image-20220119175256589](https://s2.loli.net/2022/01/19/yNMxo5XlbcQYJ7I.png)

由此可见，这个里面根本就没有`colors`的属性 所以直接报错了



表情比较：

> 背景：表情在JS引擎下表现形式为Unicode

相同的表情有相同的unicode 所以相等

![image-20220119175845054](https://s2.loli.net/2022/01/19/GsbcVlDQO1fEwtS.png)



`slice`不会改变原数组

`splice`会改变原数组

![image-20220120203040527](https://s2.loli.net/2022/01/20/hxIad6A9DbByJu3.png)



let和const有暂存性死区

var有变量提升

![image-20220120211652525](https://s2.loli.net/2022/01/20/pZLB4CKAFojU2hz.png)

var 提升

![image-20220120212508533](https://s2.loli.net/2022/01/20/PEQmMkz3d4FHxRe.png)





对生成器函数中`yield`和`yield*`的区别

![image-20220120215511685](https://s2.loli.net/2022/01/20/K8MbotVOWdaH6Qk.png)

扩展：

> [(93条消息) yield 和 yield*_陈开心的博客-CSDN博客_yield和yeild](https://blog.csdn.net/u013565133/article/details/102974537)

![image-20220120221900740](https://s2.loli.net/2022/01/20/j4wDP5SsfHlGtOm.png)



垃圾回收机制的一个原因是 是否建立了引用关系

![image-20220121095036638](https://s2.loli.net/2022/01/21/qMVY9vHNAj54PsG.png)

清除定时器只能用对应的清除方法实现   等于null 是不行的 无论这里写的是箭头函数 还是普通函数

![image-20220121095621927](https://s2.loli.net/2022/01/21/z9gZYLHMqREAsuD.png)



Map存值  key是原封不动的存  

![image-20220121100346098](https://s2.loli.net/2022/01/21/hkzZ12GgbwIFJsB.png)

![image-20220121100650436](https://s2.loli.net/2022/01/21/noiJPN2MY4yCLdK.png)



关键点：默认参数  扩展运算符的使用效果

![image-20220121101127603](https://s2.loli.net/2022/01/21/2H8rbuX1UtFx5qg.png)

再来见识一下扩展运算符的威力  这种在一些场景下很有用  例如array2.push(...[]);等

![image-20220121101611496](https://s2.loli.net/2022/01/21/tZRds9NcrMfaKpX.png)



计算属性

![image-20220121101830791](https://s2.loli.net/2022/01/21/1jnQA4ZIbom79SO.png)

扩展一下： 存值取值都可以   非常自由   

```js
var profix="foo"
		var myObject={
			[profix+"bar"]:"hello",
			[profix+"baz"]:"word"
		}
		console.log(myObject.foobar);
		console.log(myObject.foobaz);
```



认识一下可选链 以及this指向温习

![image-20220121103322115](https://s2.loli.net/2022/01/21/f1kSxI2Wv49PCYT.png)



indexOf在数组中找到了对应的value 则返回其下标 否则返回-1

![image-20220121104335004](https://s2.loli.net/2022/01/21/NeDz5Yn4IXclfsb.png)

indexOf在字符串中

![image-20220121104706016](https://s2.loli.net/2022/01/21/jbahwJ3YZCm8clI.png)

每个字符被当做个体  若涉及多个 能找到的话 就返回找到这个块的首字母所在的index  找不到也是返回-1



js中的get和set(用于对象，用直接赋值的方式传入参数)

因为没有使用`config.language = 'xxxxx'`赋值传入参数   返回就是undefined

![image-20220121105345016](https://s2.loli.net/2022/01/21/cTtBhGpoZdC1gr9.png)

set(setter)

> **`set`**语法将对象属性绑定到要在尝试设置该属性时调用的函数

在 JavaScript 中，每当尝试更改指定的属性时，都可以使用 setter 来执行函数。Setter 最常与 getter 结合使用，以创建一种类型的伪属性。不可能同时在保存实际值的属性上具有 setter。

使用语法时，请注意以下事项：`set`

- 它可以有一个标识符，它是一个数字或一个字符串;
- 它必须只有一个参数（请参见[不兼容的 ES5 更改：文本 getter 和 setter 函数现在必须正好有 0 个或 1 个参数](https://whereswalden.com/2010/08/22/incompatible-es5-change-literal-getter-and-setter-functions-must-now-have-exactly-zero-or-one-arguments/)了解更多信息）;
- 它不能与另一个对象文本一起出现在对象文本中，也不能与同一属性的数据条目一起出现。（ 并且是禁止的 ）`set``{ set x(v) { }, set x(v) { } }``{ x: ..., set x(v) { } }`

```js
const language = {
  set current(name) {
    this.log.push(name);
  },
  log: []
};

language.current = 'EN';
language.current = 'FA';

console.log(language.log);
// expected output: Array ["EN", "FA"]
```

get(getter)

> **`get`**语法将对象属性绑定到一个函数，该函数将在查找该属性时调用。

有时，需要允许访问返回动态计算值的属性，或者您可能希望反映内部变量的状态，而无需使用显式方法调用。在JavaScript中，这可以通过使用*getter*来完成。

不可能同时将 getter 绑定到属性并让该属性实际保存一个值，*尽管可以结合使用*getter 和 setter 来创建一种类型的伪属性。

使用语法时，请注意以下事项：`get`

- 它可以有一个标识符，它是一个数字或一个字符串;
- 它必须具有正好为零的参数（请参见[不兼容的 ES5 更改：文本 getter 和 setter 函数现在必须正好有 0 个或 1 个参数](https://whereswalden.com/2010/08/22/incompatible-es5-change-literal-getter-and-setter-functions-must-now-have-exactly-zero-or-one-arguments/)了解更多信息）;
- 它不得与另一个对象一起出现在对象文本中，例如，禁止以下内容
- ![image-20220121110241701](https://s2.loli.net/2022/01/21/2r4MnXGFOBstjfl.png)

```js
const obj = {
  log: ['a', 'b', 'c'],
  get latest() {
    if (this.log.length === 0) {
      return undefined;
    }
    return this.log[this.log.length - 1];
  }
};

console.log(obj.latest);
// expected output: "c"
```



> **`Intl`** 对象是 ECMAScript 国际化 API 的一个命名空间，它提供了精确的字符串对比、数字格式化，和日期时间格式化。[`Collator`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Intl/Collator)，[`NumberFormat`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat) 和 [`DateTimeFormat`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat) 对象的构造函数是 `Intl` 对象的属性。

![image-20220122214830318](https://s2.loli.net/2022/01/22/vCOnTdktBLP37wU.png)



这是一个解构后再赋值的例子（左边是对象或者数组 右边也是对应的对象或者数组  它是解构操作）

![image-20220122220606374](https://s2.loli.net/2022/01/22/NSWa1r4VoFHp8xL.png)



这里我一直误解了`Number.isNaN`的功能   才发现我理解他的功能其实是`isNaN`的  哎  我人傻了

![image-20220122230508926](https://s2.loli.net/2022/01/22/J67p3QdmWPMgS8b.png)



async函数中也可以使用`finally` 

![image-20220122231508219](https://s2.loli.net/2022/01/22/HPA19GysjXEcIki.png)



进一步认识`++`和`--`这种操作符的效果

![image-20220122234118244](https://s2.loli.net/2022/01/22/8H1G2zD4MrFlTEY.png)

![image-20220122234016486](https://s2.loli.net/2022/01/22/zacJuEwTIt149y2.png)



eventLoop所有会执行的语句都要一起考虑

![image-20220123125557315](https://s2.loli.net/2022/01/23/T5wkxshWL1YRE9H.png)

![image-20220124090505082](https://s2.loli.net/2022/01/24/7eEDykP69Y8MFtR.png)

![image-20220124125108630](https://s2.loli.net/2022/01/24/AtRuWxfQ6NkVCd2.png)

一个比较好的例子：
[对微任务和宏任务的执行顺序的个人理解 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/257069622)

```js
console.log('1');

setTimeout(function() {
    console.log('2');
    process.nextTick(function() {
        console.log('3');
    })
    new Promise(function(resolve) {
        console.log('4');
        resolve();
    }).then(function() {
        console.log('5')
    })
})
process.nextTick(function() {
    console.log('6');
})
new Promise(function(resolve) {
    console.log('7');
    resolve();
}).then(function() {
    console.log('8')
})

setTimeout(function() {
    console.log('9');
    process.nextTick(function() {
        console.log('10');
    })
    new Promise(function(resolve) {
        console.log('11');
        resolve();
    }).then(function() {
        console.log('12')
    })
})

//打印顺序 1 7 6 8 2 4 3 5 9 11 10 12
//每一次的执行都会先把同步和微任务先执行了 最后执行宏任务
//另外需要注意一下 async
```

await之前的代码被视为同步操作  之后的代码视为微任务

![image-20220124134058862](https://s2.loli.net/2022/01/24/9eR3wz1VuXphKHx.png)



这里顺带引出一下`requestAnimationFrame()`

> > **`window.requestAnimationFrame()`** 告诉浏览器——你希望执行一个动画，并且要求浏览器在下次重绘之前调用指定的回调函数更新动画。该方法需要传入一个回调函数作为参数，该回调函数会在浏览器下一次重绘之前执行
>
> 所以，**requestAnimationFrame的回调时机也是在当前的tick中，所以不属于宏任务，但也不是微任务，排在微任务之后。**
>
> 作者：Reed
> 链接：https://juejin.cn/post/6844903814508773383







`import *`这种情况的导入的原文件`export defaut`内容没有被`.default`处理  这里所以这里`*`代表被导出的对象

![image-20220123143132821](https://s2.loli.net/2022/01/23/bWCNL9V7Af1gMmd.png)

![image-20220123143244821](https://s2.loli.net/2022/01/23/fREKIHzcXU64JYw.png)

1. 引入 export default 导出的模块不用加 {},引入非 export default 导出的模块需要加 {}。

```text
import fileSystem, {readFile} from 'fs'
```

2. 一个文件只能导出一个 default 模块。



Proxy

![image-20220123145739377](https://s2.loli.net/2022/01/23/ir3N5uQaSAqEvZ4.png)

扩展Proxy详见：[Proxy - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy)

> 这里为了创建一个完整的 traps 列表示例，我们将尝试代理化一个非原生对象

```js
/*
  var docCookies = ... get the "docCookies" object here:
  https://developer.mozilla.org/zh-CN/docs/DOM/document.cookie#A_little_framework.3A_a_complete_cookies_reader.2Fwriter_with_full_unicode_support
*/

var docCookies = new Proxy(docCookies, {
  "get": function (oTarget, sKey) {
    return oTarget[sKey] || oTarget.getItem(sKey) || undefined;
  },
  "set": function (oTarget, sKey, vValue) {
    if (sKey in oTarget) { return false; }
    return oTarget.setItem(sKey, vValue);
  },
  "deleteProperty": function (oTarget, sKey) {
    if (sKey in oTarget) { return false; }
    return oTarget.removeItem(sKey);
  },
  "enumerate": function (oTarget, sKey) {
    return oTarget.keys();
  },
  "ownKeys": function (oTarget, sKey) {
    return oTarget.keys();
  },
  "has": function (oTarget, sKey) {
    return sKey in oTarget || oTarget.hasItem(sKey);
  },
  "defineProperty": function (oTarget, sKey, oDesc) {
    if (oDesc && "value" in oDesc) { oTarget.setItem(sKey, oDesc.value); }
    return oTarget;
  },
  "getOwnPropertyDescriptor": function (oTarget, sKey) {
    var vValue = oTarget.getItem(sKey);
    return vValue ? {
      "value": vValue,
      "writable": true,
      "enumerable": true,
      "configurable": false
    } : undefined;
  },
});

/* Cookies 测试 */

alert(docCookies.my_cookie1 = "First value");
alert(docCookies.getItem("my_cookie1"));

docCookies.setItem("my_cookie1", "Changed value");
alert(docCookies.my_cookie1);
```



也可以代理数组

> 示例展示：通过属性查找数组中的特定对象 

```js
let products = new Proxy([
  { name: 'Firefox'    , type: 'browser' },
  { name: 'SeaMonkey'  , type: 'browser' },
  { name: 'Thunderbird', type: 'mailer' }
], {
  get: function(obj, prop) {
    // 默认行为是返回属性值， prop ?通常是一个整数
    if (prop in obj) {
      return obj[prop];
    }

    // 获取 products 的 number; 它是 products.length 的别名
    if (prop === 'number') {
      return obj.length;
    }

    let result, types = {};

    for (let product of obj) {
      if (product.name === prop) {
        result = product;
      }
      if (types[product.type]) {
        types[product.type].push(product);
      } else {
        types[product.type] = [product];
      }
    }

    // 通过 name 获取 product
    if (result) {
      return result;
    }

    // 通过 type 获取 products
    if (prop in types) {
      return types[prop];
    }

    // 获取 product type
    if (prop === 'types') {
      return Object.keys(types);
    }

    return undefined;
  }
});

console.log(products[0]); // { name: 'Firefox', type: 'browser' }
console.log(products['Firefox']); // { name: 'Firefox', type: 'browser' }
console.log(products['Chrome']); // undefined
console.log(products.browser); // [{ name: 'Firefox', type: 'browser' }, { name: 'SeaMonkey', type: 'browser' }]
console.log(products.types); // ['browser', 'mailer']
console.log(products.number); // 3
```



Object.seal()  封闭对象(操作后只能修改值)

> 通常，一个对象是[可扩展的](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/isExtensible)（可以添加新的属性）。密封一个对象会让这个对象变的不能添加新属性，且所有已有属性会变的不可配置。属性不可配置的效果就是属性变的不可删除，以及一个数据属性不能被重新定义成为访问器属性，或者反之。但属性的值仍然可以修改。尝试删除一个密封对象的属性或者将某个密封对象的属性从数据属性转换成访问器属性，结果会静默失败或抛出[`TypeError`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/TypeError)（在[严格模式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Strict_mode) 中最常见的，但不唯一）

![image-20220123153118662](https://s2.loli.net/2022/01/23/gvwDsRdotpM85ym.png)

> 除了属性值以外的任何变化，都会失败.!!!!!!!!!!!!

```js
var obj = {
  prop: function() {},
  foo: 'bar'
};

// 可以添加新的属性
// 可以更改或删除现有的属性
obj.foo = 'baz';
obj.lumpy = 'woof';
delete obj.prop;

var o = Object.seal(obj);

o === obj; // true
Object.isSealed(obj); // === true

// 仍然可以修改密封对象的属性值
obj.foo = 'quux';


// 但是你不能将属性重新定义成为访问器属性
// 反之亦然
Object.defineProperty(obj, 'foo', {
  get: function() { return 'g'; }
}); // throws a TypeError

// 除了属性值以外的任何变化，都会失败.!!!!!!!!!!!!
obj.quaxxor = 'the friendly duck';
// 添加属性将会失败
delete obj.foo;
// 删除属性将会失败

// 在严格模式下，这样的尝试将会抛出错误
function fail() {
  'use strict';
  delete obj.foo; // throws a TypeError
  obj.sparky = 'arf'; // throws a TypeError
}
fail();

// 通过Object.defineProperty添加属性将会报错
Object.defineProperty(obj, 'ohai', {
  value: 17
}); // throws a TypeError
Object.defineProperty(obj, 'foo', {
  value: 'eit'
}); // 通过Object.defineProperty修改属性值
```

对比Object.freeze()  冻结对象（操作后啥都不能改）   Object.seal()还可以修改值

```js
var obj = {
  prop: function() {},
  foo: 'bar'
};

// 新的属性会被添加, 已存在的属性可能
// 会被修改或移除
obj.foo = 'baz';
obj.lumpy = 'woof';
delete obj.prop;

// 作为参数传递的对象与返回的对象都被冻结
// 所以不必保存返回的对象（因为两个对象全等）
var o = Object.freeze(obj);

o === obj; // true
Object.isFrozen(obj); // === true

// 现在任何改变都会失效
obj.foo = 'quux'; // 静默地不做任何事
// 静默地不添加此属性
obj.quaxxor = 'the friendly duck';

// 在严格模式，如此行为将抛出 TypeErrors
function fail(){
  'use strict';
  obj.foo = 'sparky'; // throws a TypeError
  delete obj.quaxxor; // 返回true，因为quaxxor属性从来未被添加
  obj.sparky = 'arf'; // throws a TypeError
}

fail();

// 试图通过 Object.defineProperty 更改属性
// 下面两个语句都会抛出 TypeError.
Object.defineProperty(obj, 'ohai', { value: 17 });
Object.defineProperty(obj, 'foo', { value: 'eit' });

// 也不能更改原型
// 下面两个语句都会抛出 TypeError.
Object.setPrototypeOf(obj, { x: 20 })
obj.__proto__ = { x: 20 }
```

但是  这个冻结是浅层的 深层的可以修改

![image-20220123153955621](https://s2.loli.net/2022/01/23/SY7ziG4gXfbpVA2.png)



ES2020 在类中使用`#`操作符 相当于Typescript的`private`声明  表示类私有   

![image-20220123154421128](https://s2.loli.net/2022/01/23/ZSfhUEnkKX5NzQ9.png)



注意const声明的数组或者对象 里面的属性可以改  但是这个数组或者对象整体不能改。

![image-20220126125328955](https://s2.loli.net/2022/01/26/uVH3QXPcbizN8sh.png)



对象默认不可迭代 可以使用Symbol赋予

![image-20220126130451331](https://s2.loli.net/2022/01/26/CXZOE2yw31hIlA4.png)



不存在返回‘undefined’并非null   不过数组中有empty 注意一下

![image-20220126131346096](https://s2.loli.net/2022/01/26/CtT9jBQKihsbWfA.png)



constructor里面声明和之外声明？？？

![image-20220126141904106](https://s2.loli.net/2022/01/26/HtnSjVgDMBiqCKz.png)

![image-20220126163108323](https://s2.loli.net/2022/01/26/wf47aI58PLgxMZQ.png)



array.splice()

注意添加元素是在开始索引之后添加 但是删除元素的话就是从当前指定索引开始删除  而非当前索引之后的元素开始删除

> ### [参数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/splice#参数)
>
> - `start`
>
>   指定修改的开始位置（从0计数）。如果超出了数组的长度，则从数组末尾开始添加内容；如果是负值，则表示从数组末位开始的第几位（从-1计数，这意味着-n是倒数第n个元素并且等价于`array.length-n`）；如果负数的绝对值大于数组的长度，则表示开始位置为第0位。
>
> - `deleteCount` 可选
>
>   整数，表示要移除的数组元素的个数。
>
>   如果 `deleteCount` 大于 `start` 之后的元素的总数，则从 `start` 后面的元素都将被删除（含第 `start` 位）。
>
>   如果 `deleteCount` 被省略了，或者它的值大于等于`array.length - start`(也就是说，如果它大于或者等于`start`之后的所有元素的数量)，那么`start`之后数组的所有元素都会被删除。
>
>   如果 `deleteCount` 是 0 或者负数，则不移除元素。这种情况下，至少应添加一个新元素。
>
> - `item1, item2, *...*` 可选
>
>   要添加进数组的元素,从`start` 位置开始。如果不指定，则 `splice()` 将只删除数组元素。
>
> ### [返回值](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/splice#返回值)
>
> 由被删除的元素组成的一个数组。如果只删除了一个元素，则返回只包含一个元素的数组。如果没有删除元素，则返回空数组。
>
> ## [描述](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/splice#描述)
>
> 如果添加进数组的元素个数不等于被删除的元素个数，数组的长度会发生相应的改变。

![image-20220127094747882](https://s2.loli.net/2022/01/27/tK1bcdSFYIgMQkv.png)

![image-20220127094652405](https://s2.loli.net/2022/01/27/SXel1DUaFE2oZ3P.png)

![image-20220127095318697](https://s2.loli.net/2022/01/27/8R7yYFcjJx3iewX.png)



`谁调用就指向谁`这个说法可以被箭头函数突破  箭头函数指向上一级

> 箭头函数不会创建自己的`this,它只会从自己的作用域链的上一层继承this`。

![image-20220127100939513](https://s2.loli.net/2022/01/27/TnqOVF2grLpiZwA.png)

如果不使用箭头函数（this指向了这个对象）

![image-20220127102138572](https://s2.loli.net/2022/01/27/Iu84d3KhQBrfMTv.png)

扩展：

箭头函数递归

```js
var fact = (x) => ( x==0 ?  1 : x*fact(x-1) );
fact(5);       // 120
```

使用三目

```js
var simple = a => a > 15 ? 15 : a;
simple(16); // 15
simple(10); // 10

let max = (a, b) => a > b ? a : b;
```



Promise的一些方法扩展：

![image-20220127105128861](https://s2.loli.net/2022/01/27/Hs7x2w49gGt3bJh.png)

Promise.all()

> Promise.all() 方法接收一个promise的iterable类型（注：Array，Map，Set都属于ES6的iterable类型）的输入，并且只返回一个[`Promise`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise)实例， 那个输入的所有promise的resolve回调的结果是一个数组。这个[`Promise`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise)的resolve回调执行是在所有输入的promise的resolve回调都结束，或者输入的iterable里没有promise了的时候。它的reject回调执行是，只要任何一个输入的promise的reject回调执行或者输入不合法的promise就会立即抛出错误，并且reject的是第一个抛出的错误信息。

> Promise.all 的快速返回失败行为
> Promise.all 在任意一个传入的 promise 失败时返回失败。例如，如果你传入的 promise中，有四个 promise 在一定的时间之后调用成功函数，有一个立即调用失败函数，那么 Promise.all 将立即变为失败。

![image-20220127105044550](https://s2.loli.net/2022/01/27/ufPVliEUaw6psmj.png)

Promise.any()

> `Promise.any()` 接收一个[`Promise`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise)可迭代对象，只要其中的一个 `promise` 成功，就返回那个已经成功的 `promise` 。如果可迭代对象中没有一个 `promise` 成功（即所有的 `promises` 都失败/拒绝），就返回一个失败的 `promise `和[`AggregateError`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/AggregateError)类型的实例，它是 [`Error`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Error) 的一个子类，用于把单一的错误集合在一起。本质上，这个方法和[`Promise.all()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)是相反的

> 这个方法用于返回第一个成功的 `promise` 。只要有一个 `promise` 成功此方法就会终止，它不会等待其他的 `promise` 全部完成。
>
> 不像 [Promise.all()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/all) 会返回一组完成值那样（resolved values），我们只能得到一个成功值（假设至少有一个 `promise` 完成）。当我们只需要一个 `promise` 成功，而不关心是哪一个成功时此方法很有用的。
>
> 同时, 也不像 [Promise.race()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/race) 总是返回第一个结果值（resolved/reject）那样，这个方法返回的是第一个 *成功的* 值。这个方法将会忽略掉所有被拒绝的 `promise`，直到第一个 `promise` 成功。

> 成功（Fulfillment）：
> 当任何一个被传入的 promise 成功的时候, 无论其他的 promises 成功还是失败，此函数会将那个成功的 promise 作为返回值 。
>
> 如果传入的参数是一个空的可迭代对象, 这个方法将会同步返回一个已经完成的 promise。
> 如果传入的任何一个 promise 已成功, 或者传入的参数不包括任何 promise, 那么 Promise.any 返回一个异步成功的 promise。
>
> 失败/拒绝（Rejection）：
> 如果所有传入的 promises 都失败, Promise.any 将返回异步失败，和一个 AggregateError 对象，它继承自 Error，有一个 error 属性，属性值是由所有失败值填充的数组。

全部成功：

![image-20220127111014582](https://s2.loli.net/2022/01/27/zVQKeWL3TEOmw6D.png)

有一个失败：

![image-20220127105421409](https://s2.loli.net/2022/01/27/JQrIui21f7aOtHn.png)

Promise.race()

> `race` 函数返回一个 `Promise`，它将与第一个传递的 promise 相同的完成方式被完成。它可以是完成（ resolves），也可以是失败（rejects），这要取决于第一个完成的方式是两个中的哪个。
>
> 如果传的迭代是空的，则返回的 promise 将永远等待。
>
> 如果迭代包含一个或多个非承诺值和/或已解决/拒绝的承诺，则` Promise.race` 将解析为迭代中找到的第一个值。

```js
var p1 = new Promise(function(resolve, reject) {
    setTimeout(resolve, 500, "one");
});
var p2 = new Promise(function(resolve, reject) {
    setTimeout(resolve, 100, "two");
});

Promise.race([p1, p2]).then(function(value) {
  console.log(value); // "two"
  // 两个都完成，但 p2 更快
});

var p3 = new Promise(function(resolve, reject) {
    setTimeout(resolve, 100, "three");
});
var p4 = new Promise(function(resolve, reject) {
    setTimeout(reject, 500, "four");
});

Promise.race([p3, p4]).then(function(value) {
  console.log(value); // "three"
  // p3 更快，所以它完成了
}, function(reason) {
  // 未被调用
});

var p5 = new Promise(function(resolve, reject) {
    setTimeout(resolve, 500, "five");
});
var p6 = new Promise(function(resolve, reject) {
    setTimeout(reject, 100, "six");
});

Promise.race([p5, p6]).then(function(value) {
  // 未被调用
}, function(reason) {
  console.log(reason); // "six"
  // p6 更快，所以它失败了
});
```

关于setTimeout参数的说明

![image-20220127132441503](https://s2.loli.net/2022/01/27/WVwqBeaTXHgk1j9.png)



完结：

试题来源[lydiahallie/javascript-questions: A long list of (advanced) JavaScript questions, and their explanations (github.com)](https://github.com/lydiahallie/javascript-questions)





