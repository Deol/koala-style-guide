# 二. regular模板规范

规则前面加`*`为强制，不加为可选。

## \*HTML 引号
引用属性值的时候一律采用双引号("")

regular插值直接作为某一属性的属性值不用加引号，数字属性不加引号

(注：对于必须要加引号的，比如class中的插值另当别论)

``` html
<a class="maia-button maia-button-secondary">Sign in</a>
<input r-model={value}>
```

## \*注释
1. 注释格式要求：
    - HTML 基本注释用`<!-- ... -->`，此注释在 Sources 中可见
    - Regular注释用`{! .... !}`，此注释在 Sources 中不可见
    - ftl注释用`<#-- ...  -->`
2. 在注释中注明页面名称、作者，如 <!-- 购物车页 xxx(xxx@corp.netease.com) -->

## \*命名格式
包括HTML文件命名，自定义组件标签，自定义属性

- HTML文件：采用xxx.xxx.html格式
- 自定义组件标签：采用驼峰命名，这里的闭合有两种写法，推荐h5标签写法，见下例。
- 自定义属性：regular以内嵌组件方式定义的组件可以传入自定义属性，regular规定连缀写法会自动转驼峰，驼峰写法不会做转化。建议采用驼峰写法，和我们写js的时候习惯一致。(注：bool属性不加{true}或{false})

``` html
<!-- html 文件-->
castModal.html,recordList.html
<!-- 在标签右尖括号前加斜杠的自定义标签 -->
<datePicker date="2008-08-08" />
<!-- 带有结束标签的自定义组件 -->
<custom></custom>
<!-- 自定义属性 -->
<deliveryinfo config={config} baseInfo={baseInfo}></deliveryinfo>
```

## \*属性顺序
按照先原生再指令的形式，如果某指令"-"后面的属性和原生重合，则指令紧跟原生，事件放在最后

- id
- class（r-class）
- name
- data-xxx
- src, for, type, href
- title, alt
- on-[eventName]

属性和属性，属性和指令之间用**一个**空格隔开。

若属性过多，将属性断行来写

``` html
<button
    class="f-fl u-btn u-btn-range u-btn-range-r"
    r-class={{'z-dis':true==querying}}
    title="后七天"
    on-click={this.changeTimeRange($event, 2)}>
    后七天
</button>
```

## \*插值
采用`{}`写法，不要自己配置成`{{}}`

对于插入到页面中不再改变的值，我们用单向绑定

``` html
<!-- item不再改变 -->
<span>{@item}</span>
```

## \*列表优化
循环列表的时候，使用列表的 `track by`功能

(注：对于低版本regularjs，加了会报错)
``` html
{list list as item by item_index}
<span>hello, {item}</span>
{/list}
```
