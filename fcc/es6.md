## 探索 var 和 let 关键字之间的差异

使用`var`关键字来声明变量，会出现重复声明导致变量被覆盖却不会报错的问题：

> var camper = 'James';
> var camper = 'David';
> console.log(camper);
> // 打印出 'David'

在上面的代码中，`camper`的初始值为`'James'`，然后又被覆盖成了`'David'`。

在小型的应用中，你可能不会遇到这样的问题，但是当你的代码规模变得更加庞大的时候，就可能会在不经意间覆盖了之前定义的变量。

这样的行为不会报错，导致了 debug 非常困难。

在 ES6 中引入了新的关键字`let`来解决`var`关键字带来的潜在问题。

如果你在上面的代码中，使用了`let`关键字来代替`var`关键字，结果会是一个报错。

> let camper = 'James';
> let camper = 'David'; // 报错

你可以在浏览器的控制台里看见这个错误。

与`var`不同的是，当使用`let`的时候，同一名字的变量只能被声明一次。

请注意`"use strict"`。这代表着开启了严格模式，用于检测常见的代码错误以及"不安全"的行为，例如：

> "use strict";
> x = 3.14; // x 没有声明导致了报错



## 比较 var 和 let 关键字的作用域

当你使用`var`关键字来声明一个变量的时候，这个变量会被声明成全局变量，或是函数内的局部变量。

`let`关键字的作用类似，但会有一些额外的特性。如果你在代码块、语句或表达式中使用关键字`let`声明变量，这个变量的作用域就被限制在当前的代码块，语句或表达式之中。

举个例子：

> var numArray = [];
> for (var i = 0; i < 3; i++) {
>   numArray.push(i);
> }
> console.log(numArray);
> // 返回 [0, 1, 2]
> console.log(i);
> // 返回 3

当使用`var`关键字的时候，`i`会被声明成全局变量。当`i++`执行的时候，它会改变全局变量的值。这段代码可以看做下面这样:

> var numArray = [];
> var i;
> for (i = 0; i < 3; i++) {
>   numArray.push(i);
> }
> console.log(numArray);
> // returns [0, 1, 2]
> console.log(i);
> // returns 3

如果你在`for`循环中创建了使用`i`变量的函数，那么在后续调用函数的时候，上面提到的这种行为就会导致问题。这是因为函数存储的值会因为全局变量`i`的变化而不断的改变。

> var printNumTwo;
> for (var i = 0; i < 3; i++) {
>   if(i === 2){
>     printNumTwo = function() {
>       return i;
>     };
>   }
> }
> console.log(printNumTwo());
> // 返回 3

可以看到，`printNumTwo()`打印了 3 而不是 2。这是因为`i`发生了改变，并且函数`printNumTwo()`返回的是全局变量`i`的值，而不是`for`循环中创建函数时`i`的值。`let`关键字就不会有这种现象：

> 'use strict';
> let printNumTwo;
> for (let i = 0; i < 3; i++) {
>   if (i === 2) {
>     printNumTwo = function() {
>       return i;
>     };
>   }
> }
> console.log(printNumTwo());
> // 返回 2
> console.log(i);
> // 返回 "没有定义 i 变量"

`i`在全局作用域中没有声明，所以它没有被定义，它的声明只会发生在`for`循环内。在循环执行的时候，`let`关键字创建了三个不同的`i`变量，他们的值分别为 0、1 和 2，所以`printNumTwo()`返回了正确的值。



------



修改这段代码，使得在`if`语句中声明的`i`变量与在函数的第一行声明的`i`变量是彼此独立的。请注意不要在你的代码的任何地方使用`var`关键字。

这个练习说明了使用`var`与`let`关键字声明变量时，作用域之间的不同。当编写类似这个练习中的函数的时候，通常来说最好还是使用不同的变量名来避免误会。







## 用 const 关键字声明只读变量



`let`并不是唯一的新的声明变量的方式。在 ES6里面，你还可以使用`const`关键字来声明变量。

`const`拥有`let`的所有优点，所不同的是，通过`const`声明的变量是只读的。这意味着通过`const`声明的变量只能被赋值一次，而不能被再次赋值。

> "use strict"
> const FAV_PET = "Cats";
> FAV_PET = "Dogs"; // 报错

可以看见，尝试给通过`const`声明的变量再次赋值会报错。你应该使用`const`关键字来对所有不打算再次赋值的变量进行声明。这有助于你避免给一个常量进行额外的再次赋值。一个最佳实践是对所有常量的命名采用全大写字母，并在单词之间使用下划线进行分隔。



------



改变以下代码，使得所有的变量都使用`let`或`const`关键词来声明。当变量将会改变的时候使用`let`关键字，当变量要保持常量的时候使用`const`关键字。同时，对使用`const`声明的变量进行最佳实践的重命名，变量名中的字母应该都是大写的。





## 改变一个用 const 声明的数组

在现代的 JavaScript 里，`const`声明有很多用法。

一些开发者倾向默认使用`const`来声明所有变量，但如果它们打算在后续的代码中修改某个值，那在声明的时候就会用`let`。

然而，你要注意，对象（包括数组和函数）在使用`const`声明的时候依然是可变的。使用`const`来声明只会保证它的标识不会被重新赋值。

> "use strict";
> const s = [5, 6, 7];
> s = [1, 2, 3]; // 试图给 const 变量赋值，报错
> s[2] = 45; // 与用 var 或 let 声明的数组一样，这个操作也会成功
> console.log(s); // 返回 [5, 6, 45]

从以上代码看出，你可以改变`[5, 6, 7]`自身，所以`s`变量指向了改变后的数组`[5, 6, 45]`。和所有数组一样，数组`s`中的数组元素是可以被改变的，但是因为使用了`const`关键字，你不能使用赋值操作符将变量标识`s`指向另外一个数组。



------



这里有一个使用`const s = [5, 7, 2]`声明的数组。使用对各元素赋值的方法将数组改成`[2, 5, 7]`。







## 防止对象改变Object.freeze



通过之前的挑战可以看出,`const`声明并不会真的保护你的数据不被改变。为了确保数据不被改变，JavaScript 提供了一个函数`Object.freeze`来防止数据改变。

当一个对象被冻结的时候，你不能再对它的属性再进行增、删、改的操作。任何试图改变对象的操作都会被阻止，却不会报错。

> let obj = {
>   name:"FreeCodeCamp",
>   review:"Awesome"
> };
> Object.freeze(obj);
> obj.review = "bad"; // obj 对象被冻结了，这个操作会被忽略
> obj.newProp = "Test"; // 也会被忽略，不允许数据改变
> console.log(obj); 
> // { name: "FreeCodeCamp", review:"Awesome"}



------



在这个挑战中，你将使用`Object.freeze`来防止数学常量被改变。你需要冻结`MATH_CONSTANTS`对象，使得没有人可以改变`PI`的值，抑或增加或删除属性。



```javascript
function freezeObj() {
  "use strict";
  const MATH_CONSTANTS = {
    PI: 3.14
  };
  // 在这行以下修改代码
  Object.freeze(MATH_CONSTANTS);


  // 在这行以上修改代码
  try {
    MATH_CONSTANTS.PI = 99;
  } catch( ex ) {
    console.log(ex);
  }
  return MATH_CONSTANTS.PI;
}
const PI = freezeObj();
```





## 使用箭头函数编写简洁的匿名函数

在 JavaScript 里，我们会经常遇到不需要给函数命名的情况，尤其是在需要将一个函数作为参数传给另外一个函数的时候。这时，我们会创建匿名函数。因为这些函数不会在其他地方复用，所以我们不需要给它们命名。

这种情况下，我们通常会使用以下语法：

> const myFunc = function() {
>   const myVar = "value";
>   return myVar;
> }

ES6 提供了其他写匿名函数的方式的语法糖。你可以使用箭头函数：

> const myFunc = () => {
>   const myVar = "value";
>   return myVar;
> }

当不需要函数体，只返回一个值的时候，箭头函数允许你省略`return`关键字和外面的大括号。这样就可以将一个简单的函数简化成一个单行语句。

> const myFunc= () => "value"

这段代码仍然会返回`value`。



## 编写带参数的箭头函数

和一般的函数一样，你也可以给箭头函数传递参数。

> // 给传入的数值乘以 2 并返回结果
> const doubler = (item) => item * 2;

你同样可以给箭头函数传递多个参数。





## 编写高阶箭头函数

我们已经见识到了箭头函数在处理数据时候的强大之处。

箭头函数在类似`map()`，`filter()`，`reduce()`等需要其他函数作为参数来处理数据的高阶函数里会很好用。

阅读以下代码：

> FBPosts.filter(function(post) {
>   return post.thumbnail !== null && post.shares > 100 && post.likes > 500;
> })

我们写下了`filter`函数，并尽量保证可读性。现在让我们用箭头函数来写同样的代码看看：

> FBPosts.filter((post) => post.thumbnail !== null && post.shares > 100 && post.likes > 500)

这段代码完成了同样的任务，却变得更加简短易懂了。





## 设置函数的默认参数

ES6 里允许给函数传入默认参数，来构建更加灵活的函数。

请看以下代码：

> function greeting(name = "Anonymous") {
>   return "Hello " + name;
> }
> console.log(greeting("John")); // Hello John
> console.log(greeting()); // Hello Anonymous

默认参数会在参数没有被指定（值为 undefined ）的时候起作用。在上面的例子中，参数`name`会在没有得到新的值的时候，默认使用值 "Anonymous"。你还可以给多个参数赋予默认值。





## 将 rest 操作符与函数参数一起使用

ES6 推出了用于函数参数的 rest 操作符帮助我们创建更加灵活的函数。在`rest`操作符的帮助下，你可以创建有一个变量来接受多个参数的函数。这些参数被储存在一个可以在函数内部读取的数组中。

请看以下代码：

> function howMany(...args) {
>   return "You have passed " + args.length + " arguments.";
> }
> console.log(howMany(0, 1, 2)); // 输出：You have passed 3 arguments.
> console.log(howMany("string", null, [1, 2, 3], { })); // 输出：You have passed 4 arguments.

`rest`操作符可以避免查看`args`数组的需求，并且允许我们在参数数组上使用`map()`,`fiter()`，和`reduce()`。







## 使用 spread 运算符展开数组项 ...arr ps:apply()

ES6 允许我们使用 展开操作符 来展开数组，以及需要多个参数或元素的表达式。

下面的 ES5 代码使用了`apply()`来计算数组的最大值：

> var arr = [6, 89, 3, 45];
> var maximus = Math.max.apply(null, arr); // 返回 89

我们必须使用`Math.max.apply(null,arr)`，是因为直接调用`Math.max(arr)`会返回`NaN`。`Math.max()`函数需要传入的是一系列由逗号分隔的参数，而不是一个数组。

展开操作符可以提升代码的可读性，这对后续的代码维护是有积极作用的。

> const arr = [6, 89, 3, 45];
> const maximus = Math.max(...arr); // 返回 89

`...arr`返回了一个“打开”的数组。或者说它 *展开* 了数组。

然而，展开操作符只能够在函数的参数中，或者数组之中使用。下面的代码将会报错：

> const spreaded = ...arr; // 将会发生语法错误
>
> ```javascript
> const arr1 = ['JAN', 'FEB', 'MAR', 'APR', 'MAY'];
> let arr2;
> (function() {
>   "use strict";
>   arr2 = []; // 改变这一行
> })();
> console.log(arr2);
> ```



## 使用解构赋值从对象中分配变量

我们之前看到了展开操作符是如何展开数组的内容的。

对于对象，我们也可以做同样的操作。解构赋值 就是可以从对象中直接获取对应值的语法。

看看以下 ES5 的代码：

> var voxel = {x: 3.6, y: 7.4, z: 6.54 };
> var x = voxel.x; // x = 3.6
> var y = voxel.y; // y = 7.4
> var z = voxel.z; // z = 6.54

使用 ES6 的解构语法可以完成同样的赋值语句：

> const { x, y, z } = voxel; // x = 3.6, y = 7.4, z = 6.54

如果你想将`voxel.x`,`voxel.y`,`voxel.z`的值分别赋给`a`,`b`,`c`，可以用以下这种很棒的方式：

> const { x : a, y : b, z : c } = voxel // a = 3.6, b = 7.4, c = 6.54

你可以这样理解：“将`x`地址中的值拷贝到`a`当中去。”，等等。



```javascript
function getLength(str) {
  "use strict";

  // 在这行以下修改代码
  const {length:len}=str; // change this
  // 在这行以上修改代码

  return len; // 你必须在这行将<code>length</code>赋值给<code>len</code>

}

console.log(getLength('FreeCodeCamp'));


```

## 使用解构赋值从嵌套对象中分配变量

同样，我们可以将 *嵌套的对象*解构到变量中。

请看以下代码：

> const a = {
>   start: { x: 5, y: 6},
>   end: { x: 6, y: -9 }
> };
> const { start : { x: startX, y: startY }} = a;
> console.log(startX, startY); // 5, 6

在上面的例子里，`a.start`将值赋给了变量`start`，`start`同样也是个对象。

```javascript

```

```javascript
const LOCAL_FORECAST = {
  today: { min: 72, max: 83 },
  tomorrow: { min: 73.3, max: 84.6 }
};

function getMaxOfTmrw(forecast) {
  "use strict";
  // 在这行以下修改代码
  const maxOfTomorrow = undefined; // 改变这一行
  // 在这行以上修改代码
  return maxOfTomorrow;
}

console.log(getMaxOfTmrw(LOCAL_FORECAST)); // 应该为 84.6
```



## 使用解构赋值从数组中分配变量

在 ES6 里面，解构数组可以如同解构对象一样简单。

与数组解构不同，数组的扩展运算会将数组里的所有内容分解成一个由逗号分隔的列表。所以，你不能选择哪个元素来给变量赋值。

而对数组进行解构却可以让我们做到这一点：

> const [a, b] = [1, 2, 3, 4, 5, 6];
> console.log(a, b); // 1, 2

变量`a`以及`b`分别被数组的第一、第二个元素赋值。

我们甚至能在数组解构中使用逗号分隔符，来获取任意一个想要的值：

> const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
> console.log(a, b, c); // 1, 2, 5



## 使用解构赋值配合 rest 操作符来重新分配数组元素

在解构数组的某些情况下，我们可能希望将剩下的元素放进另一个数组里面。

以下代码的结果与使用`Array.prototype.slice()`相同：

> const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
> console.log(a, b); // 1, 2
> console.log(arr); // [3, 4, 5, 7]

变量`a`与`b`分别获取了数组的前两个元素的值。之后，因为`rest`操作符的存在，`arr`获取了原数组剩余的元素的值，并构成了一个新的数组。

`rest`操作只能对数组列表最后的元素起作用。这意味着你不能使用`rest`操作符来截取原数组中间元素的子数组。





## 使用解构赋值将对象作为函数的参数传递

在某些情况下，你可以在函数的参数里直接解构对象。

请看以下代码：

> const profileUpdate = (profileData) => {
>   const { name, age, nationality, location } = profileData;
>   // 对这些变量执行某些操作
> }

上面的操作解构了传给函数的对象。这样的操作也可以直接在参数里完成：

> const profileUpdate = ({ name, age, nationality, location }) => {
>   /* 对这些参数执行某些操作 */
> }

这样的操作去除了多余的代码，使代码更加整洁。

这样做还有个额外的好处：函数不需要再去操作整个对象，而仅仅是操作复制到函数作用域内部的参数。





## 使用模板字面量创建字符串：${variable}；反引号（```）

模板字符串是 ES6 的另外一项新的功能。这是一种可以轻松构建复杂字符串的方法。

请看以下代码：

> const person = {
>   name: "Zodiac Hasbro",
>   age: 56
> };
>
> // string interpolation
> const greeting = `Hello, my name is ${person.name}!
> I am ${person.age} years old.`;
>
> console.log(greeting); // 打印出
> // Hello, my name is Zodiac Hasbro!
> // I am 56 years old.

这段代码有许多的不同：

首先，上面使用的`${variable}`语法是一个占位符。这样一来，你将不再需要使用`+`运算符来连接字符串。当需要在字符串里增加变量的时候，你只需要在变量的外面括上`${`和`}`，并将其放在字符串里就可以了。

其次，在例子使用了反引号（```），而不是引号（`'`或者`"`）将字符串括了起来，并且这个字符串可以换行。

这个新的方式使你可以更灵活的创建复杂的字符串。



## 使用简单字段编写简洁的对象字面量声明

ES6 添加了一些很棒的功能，以便于更方便地定义对象。

请看以下代码：

> const getMousePosition = (x, y) => ({
>   x: x,
>   y: y
> });

`getMousePosition`是一个返回了拥有2个属性的对象的简单函数。

ES6 提供了一个语法糖，消除了类似`x: x`这种冗余的写法.你可以仅仅只写一次`x，解释器会自动将其转换成x: x。`

下面是使用这种语法重写的同样的函数：

> const getMousePosition = (x, y) => ({ x, y });



## 用 ES6 编写简洁的函数声明

在 ES5 中，当我们需要在对象中定义一个函数的时候，我们必须如下面这般使用`function`关键字：

> const person = {
>   name: "Taylor",
>   sayHello: function() {
>     return `Hello! My name is ${this.name}.`;
>   }
> };

在 ES6 语法的对象中定义函数的时候，你可以完全删除`function`关键字和冒号。请看以下例子：

> const person = {
>   name: "Taylor",
>   sayHello() {
>     return `Hello! My name is ${this.name}.`;
>   }









## 使用 class 语法定义构造函数

ES6 提供了一个新的创建对象的语法，使用关键字`class`。

值得注意的是，`class`只是一个语法糖，它并不像 Java、Python 或者 Ruby 这一类的语言一样，严格履行了面向对象的开发规范。

在 ES5 里面，我们通常会定义一个构造函数，然后使用 `new`关键字来实例化一个对象：

> var SpaceShuttle = function(targetPlanet){
>   this.targetPlanet = targetPlanet;
> }
> var zeus = new SpaceShuttle('Jupiter');

`class`的语法只是简单地替换了构造函数的写法：

> class SpaceShuttle {
>   constructor(targetPlanet){
>     this.targetPlanet = targetPlanet;
>   }
> }
> const zeus = new SpaceShuttle('Jupiter');

注意`class`关键字声明了一个新的函数，并在其中添加了一个会在使用`new`关键字创建新对象时调用的构造函数。





## 使用 getter 和 setter 来控制对象的访问

你可以从对象中获得一个值，也可以给对象的属性赋值。

这些通常行为被称为 getters 以及 setters。

Getter 函数的作用是可以让返回一个对象私有变量的值给用户，而不需要直接去访问私有变量。

Setter 函数的作用是可以基于传进的参数来修改对象中私有变量的值。这些修改可以是计算，或者是直接替换之前的值。

> class Book {
>   constructor(author) {
>     this._author = author;
>   }
>   // getter
>   get writer(){
>     return this._author;
>   }
>   // setter
>   set writer(updatedAuthor){
>     this._author = updatedAuthor;
>   }
> }
> const lol = new Book('anonymous');
> console.log(lol.writer);  // anonymous
> lol.writer = 'wut';
> console.log(lol.writer);  // wut

注意我们调用 getter 和 setter 的语法，它们看起来并不像一个函数调用。

Getter 和 Setter 非常重要，因为它们隐藏了内部的实现细节。





## 了解 import 和 require 之间的差异

在过去，我们会使用`require()`函数来从外部文件或模块中引入函数或者代码。这时候会遇到一个问题：有些文件或者模块会特别大，但你却往往只需要引入其中的一些核心代码。

ES6 给我们提供了`import`这个便利的工具。通过它，我们能够从外部的文件或者模块中选择我们需要的部分进行引入，从而节约载入的时间和内存空间。

请看下面的例子：想象`math_array_functions`拥有大概20个函数，但是我只需要`countItems`这一个函数在我当前的文件里。使用老的`require()`方式会强制我引入所有20个函数。而使用新的`import`语法，我可以只引入需要的那个函数：

> import { countItems } from "math_array_functions"

下面是对于上面代码的语义描述：

> import { function } from "file_path_goes_here"
> // 我们还可以用同样的方式来引入变量！

对`import`的使用，有许多的写法，但是上面的例子是最常用的写法。

**注意**
在大括号里的函数名的两侧加上空格是一个最佳实践——这可以帮助我们轻松的阅读`import`语句。

**注意**
本节课中进行的是一个非浏览器操作。`import`以及与其相关的在后面课程中的语句，是无法直接在浏览器上运行的。但是，我们可以通过一些工具来使它可以在浏览器中运行。

**注意**
在许多的例子中，在文件的路径前会加上`./`；否则， node.js 会先尝试去`node_modules`目录中寻找依赖项。





## 用 export 来重用代码块

在上一个挑战中，你学习了关于`import`语句是如何从大文件中引入其中的部分代码的。但是，为了让其正常的工作，我们还必须了解一个与之相关的语句，叫做`export`。当我们想要一些代码——函数或者变量——在其他文件中使用，我们必须将它们导出来供其他文件导入。和`import`一样，`export`也是一个非浏览器的功能。

下面的例子阐述了如何进行一个命名导出。通过这样，我们可以使用上节课学习的`import`语法，将导出的代码导入到其他的文件中去。请看下面的例子：

> const capitalizeString = (string) => {
>   return string.charAt(0).toUpperCase() + string.slice(1);
> }
> export { capitalizeString } //如何导出函数。
> export const foo = "bar"; //如何导出变量。

另外，如果你想要将你所有的`export`语句打包成一行，你可以像下面这个例子一样实现：

> const capitalizeString = (string) => {
>   return string.charAt(0).toUpperCase() + string.slice(1);
> }
> const foo = "bar";
> export { capitalizeString, foo }



## 用 * 从文件中导入所有内容

我们还可以用`import`语法从文件中导入所有的内容。

下面是一个从同目录下的`"math_functions"`文件中导入所有内容的例子：

> **import * as myMathModule from "math_functions";**
> myMathModule.add(2,3);
> myMathModule.subtract(5,3);

让我们来分析一下这段代码：

> import * as object_with_name_of_your_choice from "file_path_goes_here"
> object_with_name_of_your_choice.imported_function

你可以在`import * as`之后添加任意的名称。这个方法接收到的值是一个对象，你可以使用点表示法来获取对象里具体的值。





## 用 export default 创建一个默认导出

在`export`的课程中，你学习了命名导出的语法。这让你可以在其他文件中引用一些函数或者变量。

你还需要知道另外一种被称为默认导出的`export`的语法。在文件中只有一个值需要导出的时候，你通常会使用这种语法。它也常常用于给文件或者模块创建返回值。

下面是一个简单的`export default`例子：

> export default function add(x,y) {
>   return x + y;
> }

注意：当使用`export default`去声明一个文件或者模块的返回值，你在每个文件或者模块中应当只默认导出一个值。特别地，你能将`export deafult`与`var`，`let`与`const`一起使用。



## 导入一个默认的导出

在上一个挑战里，你学会了`export default`的用法。还有一个重要的点，你可能需要另外一种`import`的语法来导入默认导出。

在下面的例子里有一个`add`函数, 它在`"math_functions"`文件里默认被导出。让我们看看来如何导入它：

> import add from "math_functions";
> add(5,4); //将会返回 9

这个语法只有一处不同的地方 —— 被导入的`add`值，并没有被花括号`{}`所包围。与导出值的方法不同，导入默认导出的写法仅仅只是简单的讲变量名写在`import`之后。