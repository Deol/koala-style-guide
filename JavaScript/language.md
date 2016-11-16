# 2. 语言规范

这部分主要介绍语言规范。

# 2.1 条件

#### 禁止在条件中使用常量表达式。
[no-varant-condition](http://eslint.cn/docs/rules/no-varant-condition)

``` javascript
// ✗ bad
if (true) { /* ... */ }
while (x = -1) { /* ... */ }
var result = 0 ? a : b;

// ✓ good
if (x === 0) { /* ... */ }
while (x) { /* ... */ }
var result = x !== 0 ? a : b;
```

#### 禁止在条件中出现赋值操作符，除非它们被括号包裹起来。
[no-cond-assign](http://eslint.cn/docs/rules/no-cond-assign)

``` javascript
// ✗ bad
if (count = 0) { /* code */ }
while (node = node.parentNode) { /* code */ }

// ✓ good
if (count === 0) { /* code */ }
while ((node = node.parentNode)) { /* code */ }
```

#### 禁止不必要的布尔类型转换。
[no-extra-boolean-cast](http://eslint.cn/docs/rules/no-extra-boolean-cast)

``` javascript
// ✗ bad
var result = !!x ? a : b;
if (!!obj) {
    // ...
}
while (Boolean(obj)) {
    // ...
}

// ✓ good
var result = x ? a : b;
if (obj) {
    // ...
}
while (obj) {
    // ...
}
```

#### 禁止不必要的三元表达式。
[no-unneeded-ternary](http://eslint.cn/docs/rules/no-unneeded-ternary)

``` javascript
// ✗ bad
var foo = a ? a : b;
var bar = c ? true : false;
var baz = c ? false : true;
var bazz = num > 1 ? true : false;

// ✓ good
var foo = a || b;
var bar = !!c;
var baz = !c;
var bazz = num > 1;
```

#### 禁止多行和嵌套的三元表达式。
[no-nested-ternary](http://eslint.cn/docs/rules/no-nested-ternary), [multiline-ternary](http://eslint.cn/docs/rules/multiline-ternary)

> 会使代码难以理解，请使用 `if` 语句。

``` javascript
// ✗ bad
var location = env.development
    ? 'localhost'
    : 'www.api.com';

// ✓ good
var location = env.development ? 'localhost' : 'www.api.com';

// ✗ bad
var thing = foo ? bar : baz === qux ? quxx : foobar;

// ✓ good
var thing;
if (foo) {
    thing = bar;
} else {
    thing = baz === qux ? quxx : foobar;
}
```

#### 尽量不使用否定表达式。
[no-negated-condition](http://eslint.cn/docs/rules/no-negated-condition)

``` javascript
// ✗ bad
if (!condition) {
    doSomething();
} else {
    doSomethingElse();
}
if (a !== b) {
    doSomething();
} else {
    doSomethingElse();
}

// ✓ good
if (condition) {
    doSomething();
} else {
    doSomethingElse();
}
if (a === b) {
    doSomething();
} else {
    doSomethingElse();
}
```

#### 禁止不安全的否定表达式。
[no-unsafe-negation](http://eslint.cn/docs/rules/no-unsafe-negation)

``` javascript
// ✗ bad
if (!key in obj) { /* code */ }
if (!obj instanceof Person) { /* code */ }

// ✓ good
if (!(key in obj)) { /* code */ }
if (!(obj instanceof Person)) { /* code */ }
if (('' + !key) in object) { /* code */ }
```

# 2.2 类型

#### 禁止对 `String`、`Number`、`Boolean`、`Symbol`、`Array`、`Object`、`Function` 使用 new 操作符
[no-new-wrappers](http://eslint.cn/docs/rules/no-new-wrappers), [no-new-symbol](http://eslint.cn/docs/rules/no-new-symbol), [no-array-varructor](http://eslint.cn/docs/rules/no-array-varructor), [no-new-object](http://eslint.cn/docs/rules/no-new-object), [no-new-func](http://eslint.cn/docs/rules/no-new-func)

``` javascript
// ✗ bad
var str = new String('Hello world');
var num = new Number(33);
var bool = new Boolean(false);
var sym = new Symbol('sym');
var arr = new Array();
var obj = new Object();
var func = new Function('a', 'b', 'return a + b');

// ✓ good
var str = String(value);
var num = Number(value);
var bool = Boolean(value);
var sym = Symbol('sym');
var arr = [];
var obj = {};
var func = function (a, b) { return a + b; }
```

#### 要求调用无参构造函数时有小括号。
[new-parens](http://eslint.cn/docs/rules/new-parens)

``` javascript
// ✗ bad
var date = new Date
var dog = new Animal;

// ✓ good
var date = new Date();
var dog = new Animal();
```

#### 尽量使用较短的符号实现类型转换。
[no-implicit-coercion](http://eslint.cn/docs/rules/no-implicit-coercion)

``` javascript
// ✗ bad
var b = Boolean(foo);
var b = foo.indexOf('.') !== -1;
var n = Number(foo);
var s = String(foo);
foo = String(foo);

// ✓ good
var b = !!foo;
var b = ~foo.indexOf('.');
var n = +foo;
var s = '' + foo;
foo += '';
```

# 2.3 数组

#### 使用直接量创建数组

``` javascript
// bad
var items = new Array();

// good
var items = [];
```

#### 禁止使用关联数组

禁止用 Array 去做 `map/hash/associative` 要做的事情。

需要键值对映射时，直接使用 Object 来表示。

#### 向数组增加元素时使用 Array.push 来替代直接赋值

``` javascript
var someStack = [];

// bad
someStack[someStack.length] = 'newItem';

// good
someStack.push('newItem');
```

#### 需要拷贝数组时，使用 Array.slice

``` javascript
var len = items.length;
var itemsCopy = [];
var i;

// bad
for (i = 0; i < len; i++) {
  itemsCopy[i] = items[i];
}

// good
itemsCopy = items.slice();
```

#### 使用 Array.slice 将类数组对象转换成数组

``` javascript
function trigger() {
    var args = Array.prototype.slice.call(arguments);
    ...
}
```

# 2.4 对象

#### 使用直接量创建对象。

``` javascript
// bad
var item = new Object();

// good
var item = {};
```

#### 要求尽可能使用 `.` 来访问对象的属性。
[dot-notation](http://eslint.cn/docs/rules/dot-notation)

``` javascript
var config = {
  isEdit: true
};

// bad
var isEdit = config['isEdit'];

// good
var isEdit = config.isEdit;
```

#### 当且仅当属性名是变量时，使用中括号 `[]` 访问属性。

``` javascript
var config = {
  isEdit: true
};

function getProp(prop) {
  return obj[prop];
}

var isEdit = getProp('isEdit');
```

#### 要求点操作符和属性放在同一行。
[dot-location](http://eslint.cn/docs/rules/dot-location)

``` javascript
// ✗ bad
var p = promise.
    then(function() {
        // code
    }).
    catch(function() {
        // code
    });

// ✓ good
var p = promise.then(function() {
    // code
}).catch(function() {
    // code
});
```

#### 要求给且仅给对象中需要的属性名加引号（如数字）。
[quote-props](http://eslint.cn/docs/rules/quote-props)

``` javascript
// ✗ bad
var bad = {
  'foo': 3,
  'bar': 4,
  'data-blah': 5,
  100: 6
};

// ✓ good
var good = {
  foo: 3,
  bar: 4,
  'data-blah': 5,
  '100': 6
};
```

#### 禁止修改内置对象的原型。

如 `Object.prototype`、`Array.prototype`、`Function.prototype` 等。

# 2.5 函数

#### 要求使用函数表达式，而不是函数声明。
[func-style](http://eslint.cn/docs/rules/func-style), [no-inner-declarations](http://eslint.cn/docs/rules/no-inner-declarations), [no-func-assign](http://eslint.cn/docs/rules/no-func-assign)

> 函数声明很容易被提升到当前作用域的顶部，这意味着可以把调用它的语句放在函数声明之前。

``` javascript
// ✗ bad
function foo() {
    // ...
}

// ✓ good
var foo = function () {
    // ...
}
```

#### 永远不要把参数命名为 arguments

把参数命名为 arguments 将取代函数作用域内的 arguments 对象。

``` javascript
// bad
function nope(name, options, arguments) {
  // ...some code
}

// good
function yup(name, options, args) {
  // ...some code
}
```

同理，不要直接操作 arguments 对象，可以用数组方法 `slice` 处理后使用。

#### `IIFE` 必须在函数表达式外添加 `()`
[wrap-iife](http://eslint.cn/docs/rules/wrap-iife)

> 解释：IIFE = Immediately-Invoked Function Expression（立即调用的函数表达式）
> 额外的 `(` 能够让看的人在阅读的一开始就知道函数是否立即被调用，且在无返回值时默认在开头添加 `;` 确保执行正确

``` javascript
// ✗ bad
function () {
    console.log('Hello');
}();
(function () {
    console.log('Hello');
}());

// ✓ good
;(function () {
    console.log('Hello');
})();
```

#### 禁止不必要的`return`。
[no-useless-return](http://eslint.cn/docs/rules/no-useless-return)

``` javascript
// ✗ bad
function foo() { return; }
function foo() {
    doSomething();
    return;
}

// ✓ good
function foo() { return 5; }
function foo() {
    return doSomething();
}
```

#### 禁用不必要的`.call()`和`.apply()`。
[no-useless-call](http://eslint.cn/docs/rules/no-useless-call)

``` javascript
// ✗ bad
// These are same as `foo(1, 2, 3);`
foo.call(undefined, 1, 2, 3);
foo.apply(undefined, [1, 2, 3]);
foo.call(null, 1, 2, 3);
foo.apply(null, [1, 2, 3]);
// These are same as `obj.foo(1, 2, 3);`
obj.foo.call(obj, 1, 2, 3);
obj.foo.apply(obj, [1, 2, 3]);

// ✓ good
foo(1, 2, 3);
obj.foo(1, 2, 3):
```

#### 禁止使用 `caller` 或 `callee`。
[no-caller](http://eslint.cn/docs/rules/no-caller)

> `arguments.caller` 和 `arguments.callee`，在JavaScript的新版本中它们已被弃用，同时在 ECMAScript 5 的严格模式下，它们也是被禁用的。

``` javascript
// ✗ bad
function factorial(n) {
    return !(n > 1) ? 1 : arguments.callee(n - 1) * n;
}

// ✓ good
function factorial(n) {
    return !(n > 1) ? 1 : factorial(n - 1) * n;
}
```

#### 如果要获取 `this`，要求统一使用 `self` 单词作为别名。
[consistent-this](http://eslint.cn/docs/rules/consistent-this)

``` javascript
// ✗ bad
function foo() {
    var that = this;
    return function () {
        console.log(that);
    };
}

// ✓ good
function foo() {
    var self = this;
    return function () {
        console.log(self);
    };
}
```

# 2.6 循环

#### for-in

 - 不要在 Array 上使用 `for-in` 循环（[原因][for-in]）；

``` javascript
// for
var a = [];
a[5] = 5;

for (var i = 0, len = a.length; i < len; i++) {
    console.log(a[i]);
}

/* 全部显示，包含 undefined：
   undefined
   undefined
   undefined
   undefined
   5
 */

// for-in
var a = [];
a[5] = 5;
for (var x in a) {
    //
    console.log(x);
}

/* 仅显示 5，忽略 0 - 4 的 undefined：
   5
 */

```

 - 循环时用 `hasOwnProperty` 方法检查成员是否为自身成员，避免来自原型链上的污染：

``` javascript
for(var target in object) {
    if(object.hasOwnProperty(target)) {
        // Some code
    }
}
```

#### 使用 for 循环时缓存变量

使用 for 循环时，缓存遍历次数的变量。

```js
for (var i = 0, len = array.length; i < len; i++) {
    // some code
}
```

缓存的遍历次数不一定是数组长度，也可能是其他层级结构较深的数据（如 `goodsObj.format.maxLimit` ），提升查找效率。

#### 使用更具语义的迭代函数代替 for 循环

在需要 continue 或者 break 操作来提前终止循环的情况下，仍然推荐使用传统的循环。否则使用迭代方法替换 for 循环更准确表明意图、增强代码可读性，并避免重复循环控制逻辑。

常用迭代函数：

 - every()：对数组中的每一项运行给定函数，如果该函数对每一项都返回 true，则返回 true。
 - filter()：对数组中的每一项运行给定函数，返回该函数会返回 true 的项组成的数组。
 - forEach()：对数组中的每一项运行给定函数。这个方法没有返回值。
 - map()：对数组中的每一项运行给定函数，返回每次函数调用的结果组成的数组。
 - some()：对数组中的每一项运行给定函数，如果该函数对任一项返回 true，则返回 true。

``` javascript
// 传统的循环需要我们手动控制循环的条件，易出错
var arr = [1, 2, 3, 5];
for(var i = 0, n = arr.length; i < n; i++) {
    console.log(arr[i]);
}

// 我们可以使用数组的 forEach 替代，更方便一些
arr.forEach(function(item, index) {
    console.log(item, index);
});

// 我们可以产生一个新的数组
var arr1 = arr.map(function(item, index) {
    return ++item;
});
// [ 2, 3, 4, 6 ]
console.log(arr1);

// 我们可以过滤数组中的一些值
var arr2 = arr.filter(function(item) {
    return item > 2;
});
// [ 3, 5 ]
console.log(arr2);

// 使用 some every 方法提前终止循环
console.log(arr.some(function(item, index) {
    console.log(index);
    return item > 2;
}));
console.log(arr.every(function(item, index) {
    console.log(index);
    return item > 2;
}));
```

[for-in]: http://stackoverflow.com/questions/500504/why-is-using-for-in-with-array-iteration-a-bad-idea

# 2.7 异常处理

#### 要求抛出异常必须用 `Error`。
[no-throw-literal](http://eslint.cn/docs/rules/no-throw-literal)

``` javascript
// ✗ bad
throw 'error';
throw 0;
throw undefined;
throw null;

// ✓ good
var e = new Error('error');
throw e;

throw new Error();
throw new Error('error');
```

#### 自定义异常

返回适量的自定义错误定义提升代码的可维护性。

``` javascript
// base
throw new Error('Something wrong.');

// expand
throw new SyntaxError('I don’t like your syntax.');
throw new TypeError('What type of variable do you take me for?');
throw new RangeError('Sorry, you just don’t have the range.');
throw new EvalError('That doesn’t evaluate.');
throw new URIError('Uri, is that you?');
throw new ReferenceError('You didn’t cite your references properly.');
```

# 2.8 生产环境

#### 不推荐使用 `alert`、`confirm`、`prompt`。
[no-alert](http://eslint.cn/docs/rules/no-alert)

``` javascript
// ✗ bad
alert('message');
confirm('Are you sure?');
```

#### 在生产环境禁止出现 `console.log` 和 `debugger`，允许出现 `console.warn` 和 `console.error`。
[no-console](http://eslint.cn/docs/rules/no-console), [no-debugger](http://eslint.cn/docs/rules/no-debugger)

``` javascript
// ✗ bad
console.log('code info.');
debugger;

// ✓ good
console.warn('This method is deprecated.');
console.error('Circular dependencies!')
```

# 2.9 其他

#### 禁止使用`eval`以及类似`eval`的方法。
[eval](http://eslint.cn/docs/rules/eval), [no-implied-eval](http://eslint.cn/docs/rules/no-implied-eval), [no-script-url](http://eslint.cn/docs/rules/no-script-url)

``` javascript
// ✗ bad
var value = eval('obj.' + key);
setTimeout('alert("Hi!");', 100);
setInterval('alert("Hi!");', 100);
execScript('alert("Hi!")');
location.href = 'javascript:void(0)';

// ✓ good
var value = obj[key];
setTimeout(function() {
    alert('Hi!');
}, 100);
setInterval(function() {
    alert('Hi!');
}, 100);
alert('Hi!');
```

#### 禁止使用 `void`, `with`, `label`, `__iterator__`, `__proto__`。
[no-void](http://eslint.cn/docs/rules/no-void), [no-with](http://eslint.cn/docs/rules/no-with), [no-labels](http://eslint.cn/docs/rules/no-labels), [no-unused-labels](http://eslint.cn/docs/rules/no-unused-labels), [no-extra-label](http://eslint.cn/docs/rules/no-extra-label), [no-label-var](http://eslint.cn/docs/rules/no-label-var), [no-iterator](http://eslint.cn/docs/rules/no-iterator), [no-proto]

#### 不要给 `setInterval` / `setTimeout` 传递字符串

#### 要求调用 `isNaN()` 检查 `NaN`。
[use-isnan](http://eslint.cn/docs/rules/use-isnan)

``` javascript
// ✗ bad
if (num === NaN) { /* ... */ }

// ✓ good
if (isNaN(num)) { /* ... */ }
```

#### 不建议使用位运算
