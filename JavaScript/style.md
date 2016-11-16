# 1. 编码风格

这部分主要描述代码风格规范。

# 1.1 空白

#### 使用 4 个空格进行缩进，统一缩进格式，禁止使用 Tab 缩进。
[indent](http://eslint.cn/docs/rules/indent), [no-tabs](http://eslint.cn/docs/rules/no-tabs), [no-mixed-spaces-and-tabs](http://eslint.cn/docs/rules/no-mixed-spaces-and-tabs)

``` javascript
// ✗ bad
function () {
  console.log('Hello');
}
function () {
——console.log('Hello');
}
    function () {
        console.log('Hello');
    }

// ✓ good
function () {
    console.log('Hello');
}
```

---

#### 使用空行来划分一组逻辑上相关联的代码片段。

#### 禁止连续出现多个空行。
[no-multiple-empty-lines](http://eslint.cn/docs/rules/no-multiple-empty-lines)

``` javascript
// ✗ bad
var value = 'Hello';


console.log(value);
```

``` javascript
// ✓ good
var value = 'Hello';

console.log(value);
```

#### 禁止块的内边缘出现空行。
[padded-blocks](http://eslint.cn/docs/rules/padded-blocks)

``` javascript
// ✗ bad
function bar() {

    console.log(foo);

}

// ✓ good
function bar() {
    console.log(foo);
}
```

#### 要求运行指令之后必须有一个空行。
[lines-around-directive](http://eslint.cn/docs/rules/lines-around-directive)

``` javascript
// ✗ bad
'use strict';
var foo;
```

``` javascript
// ✓ good
'use strict';

var foo;
```

#### 要求文件末尾有且只有一个空行。
[eol-last](http://eslint.cn/docs/rules/eol-last)

``` javascript
// ✗ bad
(function (global) {
    // ...stuff...
})(this);
```

``` javascript
// ✗ bad
(function (global) {
    // ...stuff...
})(this);↵
↵
```

``` javascript
// ✓ good
(function (global) {
    // ...stuff...
})(this);↵
```

---

#### 禁止行尾出现空格。
[no-trailing-spaces](http://eslint.cn/docs/rules/no-trailing-spaces)

#### 禁止连续出现多个空格。
[no-multi-spaces](http://eslint.cn/docs/rules/no-multi-spaces)

``` javascript
// ✗ bad
var a =  1;
if(foo   === 'bar') {}
a <<  b
var arr = [1,  2];
a ?  b: c;
WRONG_Object.prototype = {
    a          : 0,
    b          : 1,
    lengthName : 2
};

// ✓ good
var a = 1;
if(foo === 'bar') {}
a << b
var arr = [1, 2];
a ? b: c;
CORRECT_Object.prototype = {
    a: 0,
    b: 1,
    lengthName: 2
};
```

#### 要求分号、逗号、冒号之后必须有一个空格。
[semi-spacing](http://eslint.cn/docs/rules/semi-spacing), [comma-spacing](http://eslint.cn/docs/rules/comma-spacing), [key-spacing](http://eslint.cn/docs/rules/key-spacing)

``` javascript
// ✗ bad
var arr = [1,2,3,4];
var obj = { id:1,name:'Alice' };
foo(a,b,c);
for (var i = 0;i < 10;i++)

// ✓ good
var arr = [1, 2];
var obj = { id: 1, name: 'Alice' };
foo(a, b, c);
for (var i = 0; i < 10; i++)
```

#### 禁止点号（属性、rest 参数、扩展运算符）和单词之间有空格。
[no-whitespace-before-property](http://eslint.cn/docs/rules/no-whitespace-before-property), [rest-spread-spacing](http://eslint.cn/docs/rules/rest-spread-spacing)

``` javascript
// ✗ bad
foo. bar. baz();

// ✓ good
foo.bar.baz();
```

#### 要求一元运算符周围没有空格，等号、二元运算符、箭头符号周围有一个空格。
[space-unary-ops](http://eslint.cn/docs/rules/space-unary-ops), [space-infix-ops](http://eslint.cn/docs/rules/space-infix-ops), [arrow-spacing](http://eslint.cn/docs/rules/arrow-spacing)

``` javascript
// ✗ bad
i ++;
var x=-y*5;
var message='Hello, '+name+'!';

// ✓ good
i++;
var x = -y * 5;
var message = 'Hello, ' + name + '!';
```

#### 禁止在小括号（表达式、函数）和中括号（数组、属性）内边缘加空格，要求在大括号（对象、单行代码块）内边缘加一个空格。
[space-in-parens](http://eslint.cn/docs/rules/space-in-parens), [array-bracket-spacing](http://eslint.cn/docs/rules/array-bracket-spacing), [computed-property-spacing](http://eslint.cn/docs/rules/computed-property-spacing), [object-curly-spacing](http://eslint.cn/docs/rules/object-curly-spacing), [block-spacing](http://eslint.cn/docs/rules/block-spacing)

``` javascript
// ✗ bad
var num = 3 * ( 2 + 5 );
function hello( name ) {
    console.log( 'Hi,', name );
}
if ( test ) {
    thing();
}

// ✓ good
var num = 3 * (2 + 5);
function hello(name) {
    console.log('Hi,', name);
}
if (test) {
    thing();
}
```

``` javascript
// ✗ bad
var arr = [ 1, 2, 3 ];
obj[ key ] = 'test';
user[ 'name' ] = 'John';

// ✓ good
var arr = [1, 2, 3];
obj[key] = 'test';
user['name'] = 'John';
```

``` javascript
// ✗ bad
var obj = {id: 1, name: 'Alice'};
function foo() {return true;}
if (foo) { bar = 0;}

// ✓ good
var obj = { id: 1, name: 'Alice' };
function foo() { return true; }
if (foo) { bar = 0; }
```

``` javascript
// ✗ bad
product.attr({price: 10.6, tags: ['food', 'sweet']});
product.attr( { price: 10.6, tags: [ 'food', 'sweet' ] } );

// ✓ good
product.attr({ price: 10.6, tags: ['food', 'sweet'] });
```

#### 要求在大括号前放一个空格。
[space-before-blocks](http://eslint.cn/docs/rules/space-before-blocks)

``` javascript
// ✗ bad
function test(){
    console.log('test');
}

// ✓ good
function test() {
    console.log('test');
}
```

``` javascript
// ✗ bad
dog.set('attr',{
    age: '1 year',
    breed: 'Bernese Mountain Dog',
});

// ✓ good
dog.set('attr', {
  age: '1 year',
  breed: 'Bernese Mountain Dog',
});
```

#### 要求在关键字和小括号之间加一个空格，禁止在函数名和参数列表之间加空格。
[keyword-spacing](http://eslint.cn/docs/rules/keyword-spacing), [func-call-spacing](http://eslint.cn/docs/rules/func-call-spacing), [space-before-function-paren](http://eslint.cn/docs/rules/space-before-function-paren)

``` javascript
// ✗ bad
if(isJedi) {
    fight ();
} else {
    chat ();
}

// ✓ good
if (isJedi) {
    fight();
} else {
    chat();
}
```

``` javascript
// ✗ bad
function fight () {
    console.log ('Swooosh!');
}
run(function() {
    console.log ('Swooosh!');
});

// ✓ good
function fight() {
    console.log('Swooosh!');
}
run(function () {
    console.log('Swooosh!');
});
```

#### 禁止出现空块语句或空函数，除非添加一个注释。
[no-empty](http://eslint.cn/docs/rules/no-empty), [no-empty-function](http://eslint.cn/docs/rules/no-empty-function)

``` javascript
// ✗ bad
if (cond) {
}
while (cond) { }

// ✓ good
if (cond) {
    // @TODO
}
while (cond) { /* @TODO */ }
```

``` javascript
// ✗ bad
function foo() {}
var foo = function () {};

// ✓ good
function foo() { /* noop */ }
var foo = function () { /* noop */ };
```

# 1.2 块

#### 要求大括号风格使用：`1tbs` (one true brace style) 格式，允许单行模式。
[brace-style](http://eslint.cn/docs/rules/brace-style)

``` javascript
// ✗ bad
function foo()
{
    return true;
}

if (foo) {
    bar();
}
else {
    baz();
}

try
{
    somethingRisky();
} catch(e)
{
    handleError();
}

// ✓ good
function foo() {
    return true;
}

if (foo) {
    bar();
} else {
    baz();
}

try {
    somethingRisky();
} catch(e) {
    handleError();
}

function func() { return true; }
if (foo) { bar(); }
```

#### 在块或者语句中，无论多行或单行，时刻保留大括号。
[curly](http://eslint.cn/docs/rules/curly)

``` javascript
// ✗ bad
if (!obj)
    obj = {
        id: 1,
        name: 'alice',
    };

while (cond)
    if (cond2)
        doSomething();
    else
        doSomethingElse();

if (foo)
    foo++;

while (cond)
    doSomething();

for (let i = 0; i < count; i++)
    doSomething();

// ✓ good
if (!obj) {
    obj = {
        id: 1,
        name: 'alice',
    };
}

while (cond) {
    if (cond2)
        doSomething();
    else
        doSomethingElse();
}

if (foo) {
    foo++;
}

while (cond) {
    doSomething();
}

for (var i = 0; i < count; i++) {
    doSomething();
}
```

# 1.3 符号

#### 强制使用 `===` 和 `!==` ，禁止使用 `==` 和 `!=`。
[eqeqeq](http://eslint.cn/docs/rules/eqeqeq)

``` javascript
// ✗ bad
if (a == b)
if (foo == true)
if (bananas != 1)
if (value == undefined)
if (typeof foo == 'undefined')
if ('hello' != 'world')
if (0 == 0)
if (true == true)
if (foo == null)

// ✓ good
if (a === b)
if (foo === true)
if (bananas !== 1)
if (value === undefined)
if (typeof foo === 'undefined')
if ('hello' !== 'world')
if (0 === 0)
if (true === true)
if (foo === null)
```

#### 要求把换行符放在运算符的前面。
[operator-linebreak](http://eslint.cn/docs/rules/operator-linebreak)

``` javascript
// ✗ bad
var fullHeight = borderTop +
                 innerHeight +
                 borderBottom;
if (someCodition ||
    otherCondition) {
        // ...
}

// ✓ good
var fullHeight = borderTop
               + innerHeight
               + borderBottom;
if (someCodition
    || otherCondition) {
       // ...
}
```

#### 语句结尾强制使用分号，禁止多余的分号。
[semi](http://eslint.cn/docs/rules/semi), [no-extra-semi](http://eslint.cn/docs/rules/no-extra-semi), [no-unexpected-multiline](http://eslint.cn/docs/rules/no-unexpected-multiline)

``` javascript
// ✗ bad
(function () {
    var name = 'Skywalker'
    return name;;
})()

// ✓ good
(function () {
    var name = 'Skywalker';
    return name;
})();
```

#### 禁止使用行首逗号方式。
[comma-style](http://eslint.cn/docs/rules/comma-style)

``` javascript
// ✗ bad
var story = [
    once
  , upon
  , aTime
];

// ✓ good
var story = [
    once,
    upon,
    aTime
];
```

#### 禁止使用拖尾逗号（如：数组的最后一项后、对象的最后一个属性后）。
[comma-dangle](http://eslint.cn/docs/rules/comma-dangle)

``` javascript
// ✗ bad
var arr = [1, 2, 3,];
var obj = {a: 1, b: 2, c: 3,};
var hero = {
    firstName: 'Dana',
    lastName: 'Scully',
};
var heroes = [
    'Batman',
    'Superman',
];

// ✓ good
var arr = [1, 2, 3];
var obj = {a: 1, b: 2, c: 3};
var hero = {
    firstName: 'Dana',
    lastName: 'Scully'
};
var heroes = [
    'Batman',
    'Superman'
];
```

# 1.4 命名

采用一致的方法对变量和函数进行**语义化**命名，有助于提高代码可预测性和可维护性。

#### 基础命名规则

**解释清楚命名所代表的意义，优先于命名的书写长度。**

| 名称 | 释义 |
| :--- | :--- |
| 文件名 | 纯小写字母，以 `.` 号分隔单词（Unix 系统区分大小写），以 `.js` 结尾（如：`goods.detail.js`） |
| 普通属性、变量 | 小驼峰命名。通用全大写缩写（如：`ID`、`URL` ）全部仅取首字母大写（如：`goodsId`、`goodsUrl`） |
| &nbsp; | boolean 类型变量用 `is`、`can`、`has` 开头，如 `isEdit` **（特别注意：值为 true 时表示条件成立！！）** |
| &nbsp; | 循环的变量用 i、j、k、l、m、n 等表示 |
| 普通函数 | 小驼峰命名。统一使用动词或者动词 + 名词形式 |
| &nbsp; | 命名举例如 `getTime`（其实这里的 `getTime` 例子不好，命名要具象化，如 `getActivityStartTime`） |
| &nbsp; | 涉及返回逻辑值的函数可以使用 `is`、`has` 等表示逻辑的词语代替动词，如：`isObject()`、`hasClass()` |
| 类名或构造函数 | 大驼峰命名。统一使用名词形式（如：`TemplateModule，EditModal`）|

**注意**：

 - 任何情况下都**不能**以**拼音**命名；
 - 避免单字母命名（如：`q`），命名应具备描述性（如：`query`）；
 - 不能使用 JavaScript 的关键字、保留字（使用同义词进行替换）；
 - Promise 对象用动宾短语的进行时表示，如 `loadingData`。

---

#### 命名前缀规范

 - 基本函数前缀

| 符号 | 释义 |
| --- | --- |
| cb + 名词 + 动词 | 回调函数，比如 `cbGetList` |

 - NEJ 前缀

| 符号 | 释义 |
| ---|--- |
| __ | 受保护的属性、方法，控件范围及所有子类可使用 |
| _$ | 对外属性、方法，控件外可直接调用 |
| _$$ | 类名前缀，控件外可直接使用 |
| on + 名词 + 动词 | 事件触发函数命名，比如 `onEditBtnClick` |

 - Regular 前缀

| 符号 | 释义 |
| ---|--- |
| 动词 + 名词 | 事件触发函数，同普通的方法函数 |
| 私有属性、变量 | 不加前缀 |
| 私有方法 | 前缀加`_`（如：`_getList`） |
| 公有方法 | 前缀加`$` |

> 对外属性、变量：建议需要外部拿到的属性，使用 `$getXXX` 方法封装。

---

#### 单词缩写规则

 - 较短的单词可通过去掉「元音」形成缩写；

 - 较长的单词可取单词的头几个字母形成缩写，比如 animation => anim，previous => prev，default => def，attribute => attr 。

**常用功能命名举例：**

 1. 与后台数据交互

列表：`getList`，`getParam`，`validateDate`

 2. 与用户逻辑交互（一般由事件触发）

动画：`updateAnimFrame`，`nextAnimFrame`，`prevAnimFrame`

---

#### 附录

 - 函数方法常用动词

| 名称 | 释义 |
| :-- | :-- |
| get | 获取 - 数据 |
| set | 设置 - 数据，内容 |
| update | 更新 - 模块，数据 |
| validate | 验证 - 数据格式 |
| check | 核实 - 内容 |
| change | 改变 - 状态 |
| load | 加载 - 数据 |
| add | 增加 - 模块，数据 |
| remove | 删除 - 模块，数据 |
| upload | 上传 - 图片，Excel |
| import | 导入 - 模块，数据 |
| save | 保存 - 模块，数据 |
| reset | 重置 - 数据 |
| is | 是否 |

 - 常用缩写单词

 **注意：没有必要写看起来像错别字一样的缩写，如 edit 不应该写成 edt。**

| 完整单词 | 缩写 |
| :--- | :--- |
| to | 2 |
| for | 4 |
| A | &nbsp; |
| average | avg |
| B | &nbsp; |
| background | bg |
| buffer | buf |
| D | &nbsp; |
| delete | del |
| document | doc |
| E | &nbsp; |
| error | err |
| I | &nbsp; |
| information | info |
| initial | init |
| image | img |
| L | &nbsp; |
| length | len |
| library | lib |
| M | &nbsp; |
| manager | mgr |
| message | msg |
| P | &nbsp; |
| password | pwd |
| picture | pic |
| position | pos |
| S | &nbsp; |
| source | src |
| string | str |
| T | &nbsp; |
| template | tpl |
| text | txt |
| W | &nbsp; |
| window | win |

 - 关键字

 break，case，catch，continue，default，delete，do，else，finally，for，function，if，in，instanceof，new，return，switch，this，throw，try，typeof，var，void，while，with

 - 保留字

abstract，boolean，byte，char，class，const，debugger，double，enum，export，extends，final，float，goto，implements，import，int，interface，long，native，package，private，protected，public，short，static，super，synchronized，throws，transient，volatile

# 1.5 声明

#### 变量使用前必须使用 `var` 关键字进行声明。

 - 一个 `var` 只能声明一个包含赋值操作的变量；
 - 一个 `var` 可以声明多个未赋值变量，但这些变量必须写在一行上，不能换行。

``` javascript
// ✗ bad
var items = getItems(),
    goSportsTeam = true,
    dragonball,
    superMan;

// ✓ good
var items = getItems();
var goSportsTeam = true;
var dragonball, superMan;
```

#### 常量使用全大写字符，并用下划线分隔。

例如：`NAMES_LIKE_THIS`。

#### 禁止初始化变量值为 `undefined`。
[no-undef-init](http://eslint.cn/docs/rules/no-undef-init)

``` javascript
// ✗ bad
var bar = undefined;

// ✓ good
var bar;
```

#### 不要在非函数代码块内声明一个函数。

在严格模式下，块内声明函数会报语法错误。

``` javascript
// × bad
if (x) {
    function foo() {};
}

// √ good
var foo;
if (x) {
    foo = function() {};
}
```

#### 不要在循环体内包含函数表达式。

``` javascript
// × bad
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    addListener(element, 'click', function () {});
}

// √ good
function clicker() {
    // some code
}
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    addListener(element, 'click', clicker);
}
```

# 1.6 注释

使用 JSDoc 的注释风格，良好的注释可以增加代码的可读性和可维护性。

#### 总原则

 1. **如无必要，勿增注释**：尽量提高代码本身的清晰性、可读性。
 2. **如有必要，尽量详尽**：合理的注释、空行排版等，使代码更易阅读、更具美感。

#### 要求注释的符号和内容之间有一个空格。
[spaced-comment](http://eslint.cn/docs/rules/spaced-comment)

``` javascript
// ✗ bad
//is current tab
const active = true;

// ✓ good
// is current tab
const active = true;

// ✗ bad
/**
*make() returns a new element
*based on the passed-in tag name
*/
function make(tag) {

    // ...

    return element;
}

// ✓ good
/**
 * make() returns a new element
 * based on the passed-in tag name
 */
function make(tag) {

    // ...

    return element;
}
```

#### 文件注释

需要有文件注释用来说明当前文件所实现内容，主要包括说明部分和作者部分。

> 建议：在文件注释下方增加「全局变量」声明

``` javascript
/**
  *  描述文件实现的功能、模块或接口等，如有需要增加使用说明或者范例
  *  author 作者姓名（邮箱）
  *  创建日期
  */
```

#### 单行注释要求使用 `//` 并将注释放在代码上方，且要求在注释前放一个空行，除非它是块中的首行。

``` javascript
// ✗ bad
const active = true;  // is current tab

// ✓ good
// is current tab
const active = true;

// ✗ bad
function getType() {
    console.log('fetching type...');
    // set the default type to 'no type'
    const type = this.type || 'no type';

    return type;
}

// ✓ good
function getType() {
    console.log('fetching type...');

    // set the default type to 'no type'
    const type = this.type || 'no type';

    return type;
}

// ✓ good
function getType() {
    // set the default type to 'no type'
    const type = this.type || 'no type';

    return type;
}
```

#### 要求多行注释使用`/** ... */`。

``` javascript
// ✗ bad
// make() returns a new element
// based on the passed in tag name
//
// @param {String} tag
// @return {Element} element
function make(tag) {
    // ...
    return element;
}

// ✓ good
/**
 * make() returns a new element
 * based on the passed-in tag name
 * @param {String} tag
 * @return {Element} element
 */
function make(tag) {
    // ...
    return element;
}
```

#### 函数注释

使用 `/** ... */` 作为函数注释，需包含描述、指定所有参数和返回值的类型和值。

``` javascript
/**
  * 说明当前函数的功能，如有需要可增加使用说明或者范例
  *
  * @param  {Function} func        入参，函数类型
  * @param  {number}   wait        入参，数字类型
  * @param  {boolean}  immediate   入参，布尔类型
  * @return {Function}             返回一个函数
  * @description（非必要）           描述本函数可能存在的缺陷，需要优化的部分，可能出现的错误
  */
```

| 类型定义 | 语法示例 |
| ------- | ------ |
| Boolean | {boolean} |
| Number | {number} |
| String | {string} |
| Object | {Object} |
| Json | {Json} |
| Array | {Array} |
| Function | {Function} |
| Date | {Date} |
| RegExp | {RegExp} |

> 基础类型使用纯小写语法，引用类型使用首字母大写写法

#### 细节注释

在某些时候我们会需要使用一些特殊标记进行说明，特殊标记使用「单行注释」的方式。

``` javascript
// TODO
var name = 'Tracy McGrady';
```

解释：

 - TODO: 功能未完成，待实现。此时需要对将要实现的功能做简单说明。
 - FIXME: 此处代码运行正常，但由于写法不够优雅需要修正。此时需要对如何修正进行简单说明。
 - HACK: 为修正某些问题而写了晦涩难懂的代码。此时需要对思路或手段进行描述。
 - TRAP: 该处存在陷阱。此时需要对陷阱进行描述。

 # 1.7 字符串

 #### 要求使用单引号包裹字符串，在需要插值或换行时才使用反引号，在内部单引号需要转义时才使用双引号。
 [quotes](http://eslint.cn/docs/rules/quotes)

 ``` javascript
 // ✗ bad
 var name = 'Bob Parr';
 var element = `<div class="box"></div>`;
 var message = 'I don\'t like quotes.';

 // ✓ good
 var name = "Bob Parr";
 var element = `<div class="${className}"></div>`;
 var message = "I don't like quotes.";
 ```
