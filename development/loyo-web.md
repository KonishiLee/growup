# 快启Web前端项目规范说明

> 要想做一名合格的前端工程师，必须要有一套自己的代码风格与规范!

[TOC]

## 目录
* *代码结构说明*

* *框架整体规范*

* *JavaScript编码规范*

* *CSS编码规范*

###代码结构说明

*  loyo-web-rails *`——根目录`*
   *   gulp *`——构建目录`*
    *  assets *`——文件目录`*
      * icons *`——图标`*
      * images *`——图片`*
      * lib   *`——基础插件`*
      * src *`——模块开发目录`*
        * products
        * ...
      * styl *`——样式开发目录`*
        * main.styl
        * ...
      * stylesheets *`——基础样式`*



### 框架整体规范

##### 1. 如何引用包？
&nbsp;&nbsp;&nbsp;&nbsp;为什么要引用那么的包呢？对于大多数开发人员来说，在一个项目中不一定所有的功能控件都需要自己手动编写，这是一个开源的时代，资源共享成了开发人员的一个可以相互学习，相互进步的先进思想，作为一名合格的前端工程师来说，我们也需要学会怎样去引用别人的包到自己的项目中，因为我们是用[Node.js](https://nodejs.org/en/)作为平台来开发的，所以我们的可以使用到[NPM](https://www.npmjs.com/)或者[GITHUB](https://github.com/)上面的各种第三方库来支持我们的项目，当然你也可以开发一些第三方库供大家使用！

```
//这里是第三方库引用区
var $ = require('jquery');
var lodash = require('lodash');

//这里是自己的基础包
var Model = require('src/common/model');

//这里是模块下的包
var View = require('./view');
```

##### 2. 怎样组成一个模块单元？
&nbsp;&nbsp;&nbsp;&nbsp;在快启这个项目中，我们是运用了分模块开发的方式，所以模块与模块之间是各自独立却相互依赖的，所以每一个模块对于我们来说就是一个单体，那怎样的单体才能组成一个模块呢。

* module_name `模块`
  * module.js `定义模块`
  * router.js `路由`
  * layout-template.hbs `模板元素`
  * layout-view.js  `定义模板方法，函数`
  * model.js  `模型`
  * collection.js `集合`

  以上就是一个简单的模块所具备的基础的文件

* model.js    ——定义了模块所使用的基础模型
* collection.js ——定义以基础model为单位的集合
* module.js   ——定义了这个模块的一些基础方法
* router.js   ——定义了这个模块下所使用到的所有路由
* layout-template.hbs   ——定义了模块主容器的节点元素
* layout-view.js    ——定义了模块主容器的一些方法与函数
* ...

  当然初次之外还会根据模块的功能多少来自己定义模块内部的结构，因为js没有package概念，所以所有的功能模块都以文件夹来区分定义。

#####3. 如何引用CSS？
在目录 `【styl】` 下面有一个 *`main.styl`* 文件

```
@import "rome"
@import "rating"
@import "global"
@import "search-box"
@import "../src/app"
...

```
这里包含了引用的第三方CSS包，其中 `../src/app` 这个文件表示整个App的style，那我们再来看看这个 `app.styl`。

```
@import "member-drop/style"
@import "member-drop-module/style"
@import "select-drop/style"
@import "search-dropdown/style"
@import "subordinate-menu/style"
@import "usermenu/style"
@import "sideslide/style"
...
```

之所以会创建一个`app.styl`文件是因为我们的CSS文件必须分模块管理，其中引用到比如_**【 project 】**_，_**【 products 】**_，_**【 customers 】**_模块当中的**【 styl 】**文件，每一个模块有一个特定的CSS样式表，_这样会避免样式污染，减少CSS性能和可维护性的问题。_

##### 4. 怎样写模块下面的CSS？
因为现在我们的CSS是分模块管理，所以我就以`products`这个模块来讲解_style_文件应该怎样去编写。

* products
  * layout-template.hbs
  * layout-view.js
  * style.styl
  * ...

1.首先讲一下我们怎么去管理我们的CSS分模块编写。原理其实很简单，在每一个模块下我们都会有一个 `layout-template.hbs` 文件，这个文件的功能作用是作为当前这个模块的容器，简单的说就是这个模块最外层的view。
以下就是`layout-template.hbs`文件的内容：

```
  <div class="products__container"></div>

```
我们定义了该模块最外层的容器是名为 `products__container` 的 _div_ 元素。这里命名一般为 `模块名` + `__container`，既然我们找到了该模块的最外层view，那么我们的styl书写方式就应该是：

```
  .products__container
    .create_button
      color: red
```
如上所述，我们的_styl_文件就应该是以`.products__container`为父节点来编写。

因为在这里我们使用到的是[stylus](http://stylus-lang.com/)，所以我们可以按照stylus的语法来编写CSS

```
  .products__container
    width: 400px
    height: 400px
```


### JavaScript编码规范
##### 1. 基本语法与变量
####### 1.1  语句
_JavaScript的执行单位是行（line），也就是说代码是一行一行的执行，一般情况下每一行就是一个语句。_

  var i = 1 + 1;

每一个语句都以`;`结束，一个`;`代表一个语句，一行内也可以有多个语句。
###### 1.2 运算符
* 两元逻辑运算符： && (And)，|| (Or)
* 前置逻辑运算符： ! (Not)
* 相等运算符：===，!==，==，!=
* 比较运算符：>，>=，<，<=

##### 2. 编程风格
###### 1.  缩进
  空格和Tab键都可以产生缩进效果，但是有时候Tab产生的是2个空格或者是4个空格，但是在我们的项目中编辑器我一般设置的是2个空格，所以需要统一。

###### 2.  全局变量
  JavaScript最大的缺陷就是全局变量对于任何一个代码块都是可读可写，这对代码的模块化和重复使用特别不利，所以我们要尽量少使用全局变量，如果需要使用，都用大写字母表示变量名。

  var UPPER_CASE = '这是全部变量';

###### 3.  相等与严格相等

```
0 == ''// true
1 == true // true
2 == true // false
0 == '0' // true
false == 'false' // false
false == '0' // true
’ \t\r\n ' == 0 // true
```
因此，不要使用“相等”（==）运算符，只使用“严格相等”（===）运算符。

###### 4.  命名规范
  首先应该注意的是，在编写JavaScript的时候，我们应该尽量采用驼峰式命名，对于不同的类型，我们的命名方法也是不一样。

```
//变量
var i = 0;
var iValue = 0;
var sValue = '';
var aValue = [];
var bValue = true;
var fValue = 0.01;
var oType = new Object();

//对象
var Backbone = require('backbone');
var LayoutView = require('./layout-view');

//方法
handleClick: function(){
  //Todo
}

handleChange: function(){
  //Todo
}

handleSearch: function(){
  //Todo
}

searchProductsByName: function(){
  //Todo
}

```

 在代码中我不赞成使用注释，因为所有的代码应该是自我解读的，所以在命名的时候应该更加语义化，更加易读。

###### 5.  类的规范

   如何正确的创建一个类，才能让别人看着更加清晰，舒服。在我们定义类的时候，我们应该按照以下基本顺序来编写类，这样既可以很清晰的知道这个类是做什么用的，还可以提高我们代码可读可维护性效率。

 *  属性
 *  初始化事件，重写事件
 *  自定义事件


 ```
 module.exports = View.extend({
  template: template,

  behaviors: {
    form: {
      behaviorClass: FormBehavior
    },
    flextext: {
      behaviorClass: FlexTextBehavior,
      el: '#content',
      multipleRows: true
    }
  },

  ui: {
    cancelButton: '.close-btn',
    submitButton: '.submit-btn'
  },

  events: {
    'click @ui.cancelButton' : 'cancel',
    'submit form': 'handleSubmit'
  },

  initialize: function () {
    Radio.request('modal', 'open', this);
  },

  onRender: function(){
    //Todo
  },

  onShow: function(){
    //Todo
  }

  cancel: function () {
    Radio.request('modal', 'close');
  },

  handleSubmit: function() {
    var errors = this.model.validate(this.form);

    if (!_.isEmpty(errors)) {
      Radio.command('flashes', 'add', {
        timeout: 5000,
        type: 'danger',
        body: errors[0]
      });
    } else {
      this.ui.submitButton.button('loading');
      this.model.saveWithItems(this.form)
        .done(_.bind(this.handleSaveSuccess, this));
    }
  },

  handleSaveSuccess: function() {
    this.collection.add(this.model);

    Radio.command('flashes', 'add', {
      timeout: 5000,
      type: 'success',
      body: '标签创建成功'
    });

    Radio.request('modal', 'close');
  }
});
 ```

### CSS编码规范
