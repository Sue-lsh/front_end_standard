## 前端代码规范

### 一、HTML

#### DOCTYPE 声明

HTML 文件必须加上 DOCTYPE 声明，并统一使用 HTML5 的文档声明：

```
<!DOCTYPE html>
```

#### 页面语言 LANG

```
<html lang="zh-CN">
```

#### CHARSET

一般情况下统一使用<font color="red">“UTF-8”</font>编码

```
<meta charset="UTF-8">
```

#### 元素及标签闭合

---

HTML 元素共有一下 5 种：

- 空元素：area、base、br、col、command、embed、hr、img、input、keygen、link、meta、param、source、track、wbr
- 原始文本元素：script、style
- RCDATA 元素：textarea、title
- 外来元素：来自 MathML 命名空间和 SVG 命名空间的元素
- 常规元素：其他 HTML 允许的元素都称为常规元素

为了能让李璐蓝旗更好的解析代码以及能让代码具有更好的可读性，有如下约定：

- 所有具有开始标签和结束标签的元素都要写上起止标签，某些允许省略开始标签或结束标签的元素亦都要写上。
- 空元素标签都不加“/”字符

```
<div>
    <h1>我是h1标题</h1>
    <p>我是一段文字，我有始有终，浏览器能正确解析</p>
</div>

<br>
```

#### 书写风格

##### HTML 代码大小写

HTML 标签名、类名、标签属性和大部分属性值统一用小写

_推荐_

```
<div class="demo"></div>
```

_不推荐_

```
<div class="DEMO"></div>
<DIV CLASS="DEMO"></DIV>
```

HTML 文本、CDATA、JavaScript、meta 标签某些属性等内容可大小写混合

```
<!-- 优先用IE最新版本和Chrome Frame -->
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>

<!-- HTMl文本内容 -->
<h1>I AM WHAT I AM </h1>

<!-- JavaScript 内容 -->
<script type="text/javascript">
  var demoName = 'demoName'
  ...
</script>
<!-- CDATA内容 -->
<script type="text/javascript">
  <![CDATA[...]]>
</script>
```

##### 类型属性

不需要为 CSS、JS 指定类型属性，HTML5 中默认已包含

_推荐_

```
<link rel="stylesheet" href="">
<script src=""></script>
```

_不推荐_

```
<link rel="stylesheet" type="text/css" href="">
<script type="text/javascript" src=""></script>
```

##### 元素属性

- 元素属性值使用双引号语法
- 元素属性值可以写上的都写上

_推荐_

```
<input type="text">
<input type="radio" name="name" checked="checked">
```

_不推荐_

```
<input type=text>
<input type='text'>
<input type="radio" name="name" checked>
```

##### 特殊字符引用

文本可以和字符引用混合出现。这种方法可以用来转义在文本中不能合法出现的字符。
在 HTML 中不能使用小于号“<”和大于号“>”特殊字符，浏览器会将它们作为标签解析，若要正确显示，在 HTML 源代码中使用字符实体

_推荐_

```
<a href="#">more&gt;&gt;</a>
```

_不推荐_

```
<a href="#">more>></a>
```

##### 代码缩进

统一使用两个空格进行代码缩进，使得各编辑器变现一致（各编辑器有相关配置）

```
<div class="jdc">
  <a href="#"></a>
</div>
```

##### 纯数字（整数）输入框

_推荐_

```
<input type="tel">
```

_不推荐_

```
<input type="number">
```

##### 代码嵌套

元素嵌套规范，每个块状元素独立一行，内联元素可选

_推荐_

```
<div>
  <h1></h1>
  <p></p>
</div>
<p><span></span><span></span></p>
<p>
  <span></span>
  <span></span>
</p>
```

_不推荐_

```
<div>
  <h1></h1><p></p>
</div>
```

段落元素与标题元素只能嵌套内联元素

_推荐_

```
<h1><span></span></h1>
<p><span></span><span></span></p>
```

_不推荐_

```
<h1><div></div></h1>
<p><div></div><div></div></p>
```

#### 注释规范

##### 遵循标准

- 必须以 4 个有序字符开始："<!--"
- 在此之后是注释内容，注释的内容有以下限制：
  - 不能以单个“>”字符开始
  - 不能以由“-”和“>”组合的字符开始：“->”
  - 不能包含两个连续的“-”：“--”
  - 不能以一个“-”字符结束
- 必须以 3 个有序字符结束：“-->”

标准写法

```
<!-- Comment Text -->
```

错误写法：

```
<!-->The Wrong Comment Text-->

<!--->The Wrong Comment Text-->

<!--The--Wrong--Comment Text-->

<!--The Wrong Comment Text--->
```

##### 单行注释

一般用于简单的描述，如某些状态描述、属性描述等

注释内容前后各一个空格字符，注释要位于要注释代码的上面，单独一行

_推荐_

```
<!-- Comment Text -->
<div>...</div>
```

_不推荐_

```
<div>...</div><!-- Comment Text -->

<div><!-- Comment Text -->
  ...
</div>
```

##### 模块注释

一般用于描述模块的名称以及模块开始与结束的位置

注释内容前后各一个空格字符，模块与模块之间相隔一行

_推荐_

```
<!-- S Comment Text A -->
<div class="mod_a">
  ...
</div>
<!-- E Comment Text A -->

<!-- S Comment Text B -->
<div class="mod_b">
  ...
</div>
<!-- E Comment Text B -->
```

_不推荐_

```
<!-- S Comment Text A -->
<div class="mod_a">
  ...
</div>
<!-- E Comment Text A -->
<!-- S Comment Text B -->
<div class="mod_b">
  ...
</div>
<!-- E Comment Text B -->
```

##### 嵌套模块注释

当模块注释内再出现模块注释的时候，为了突出主要模块，嵌套模块不再使用

```
<!-- S Comment Text -->
<!-- E Comment Text -->
```

而改用

```
<!-- /Comment Text -->
```

注释写在模块结尾标签底部，单独一行

```
<!-- S Comment Text A -->
<div lcass="mod_a">
  <div class="mod_b">
    ...
  </div>
  <!-- /mod_b -->
  <div class="mod_c">
    ...
  </div>
  <!-- /mod_c -->
</div>
<!-- E Comment Text A -->
```

### 二、图片规范

#### 图片格式

##### 内容图

- 优先考虑 JPEG 格式
- 尽量不使用 PNG 格式，PNG8 色位太低，PNG24 压缩率低，文件体积大

##### 背景图

- PNG 与 GIF 格式，优先考虑使用 PNG 格式，PNG 格式允许更多的颜色并提供更好的压缩率
- 图像颜色比较简单的，如纯色块线条图标，优先考虑使用 PNG8 格式，避免使用 JPEG 格式
- 图像颜色丰富而且图片文件不太大的（40KB 以下）或有半透明效果的优先考虑 PNG24 格式
- 图像颜色丰富而且文件比较大的（40KB-200KB）优先考虑 JPEG 格式
- 条件允许的，优先考虑 WebP 代替 PNG 和 JPEG 格式

#### 图片大小

- PC 平台单张的图片的大小不应大于 200KB
- 移动平台单张的图片大小不应大于 100KB

#### 图片质量

- 上线的图片都应该经过压缩处理，压缩后的图片不应该出现肉眼可感知的失真区域
- 60 质量的 JPEG 格式图片与质量大于 60 的相比，肉眼已看不出明显的区别，因此保存 JPEG 图的时候，质量一般控制在 60，若保真度要求高的图片可适量提高到 80，图片大小控制在 200KB 以内

#### 图片引入

测试内容图应该写上表明图片尺寸的占位图，可以用线上占位图生成服务

```
http://placeholder.qiniudn.com/300x200
```

HTML 中图片引入不需添加 width、height 属性，alt 属性应该写上

_推荐_

```
<img src="" alt="">
```

_不推荐_

```
<img src="" width="" height="">
```

CSS 中图片引入不需要引号

```
.jdc {
  background-image: url(icon.png)
}
```

#### CSS Sprites

- 减少请求数
- 加速图片的显示
- 维护更新成本大
- 更多的内存消耗，特别是大体积或有过多空白的 Sprites 图
- 图片渗漏，相邻的不需展示的图片有可能出现在展示元素中，特别是在高清设备移动设备上

#### Data URIs（base64 编码）

- 减少请求数
- 转换文件体积大，大约比原始的二进制大 33%
- IE6/IE7 不支持
- 图片显示相对较慢，需要更多的 CPU 消耗

#### CSS Sprites 使用建议

- 适合使用频率高更新频率低的小图标
- 尽量不留太多的空白
- 体积较大的图片不合并
- 确保要合并的小图坐标数值和合并后的 Sprites 图尺寸均为偶数

#### Data URIs（base64 编码）使用建议

- 适合更新频率高的小图片，如某些 icon 等
- 转换成 Base64 的图片应小于 2KB
- 移动端不使用 Base64 编码
- 要兼容 IE6/IE7

### 三、CSS 规范

#### 代码规范（基于 stylus）

##### 代码风格-展开式

不同预编译器，格式化不同

```
.jdc
  display block
  width 50px

.jdc {
  display: block;
  width: 50px;
}
```

##### 代码大小写

样式选择器、属性名、属性值关键字全部使用小写字母书写，属性字符串允许使用大小写

_推荐_

```
.jdc
  display block
```

_不推荐_

```
.JDC
  DISPLAY BLOCK
```

##### 选择器

- 尽量少用通用选择器 \*
- 不使用 ID 选择器
- 不使用无具体语义定义的标签选择器

_推荐_

```
.jdc {}
.jdc li {}
.jdc li p {}
```

_不推荐_

```
*{}
#jdc {}
.jdc div {}
```

##### 代码缩进

统一使用两个空格进行代码缩进，使得各编辑器变现一致（各编辑器有相关配置）

```
.jdc
  width 100%
  height 100%
```

##### 代码易读性

左括号与选择器之间一个空格，属性名与属性值之间一个空格

_推荐_

```
.jdc
  width 100%

.jdc {
  width:100%;
}
```

_不推荐_

```
.jdc{
  widht:100%;
}
```

逗号分隔的取值，逗号之后一个空格

_推荐_

```
.jdc
  box-shadow 1px 1px 1px #333, 2px 2px 2px #ccc
```

_不推荐_

```
.jdc
  box-shadow: 1px 1px 1px #333,2px 2px 2px #ccc
```

为单个 css 选择器或新申明开启新行

_推荐_

```
.jdc,
.jdc_logo,
.jdc_hd
  color #ccc
```

_不推荐_

```
.jdc, .jdc_logo, .jdc_hd {
  color #ccc
}.nav{
  color #fff
}
```

颜色值 rgb()、rgba()、hsl()、hsla()、rect()中取值不要带有不必要的 0

_推荐_

```
.jdc
  color rgba(255, 255, 255, .5)
```

_不推荐_

```
.jdc
  color rgba(255, 255, 255, 0.5)
```

属性值十六进制数值能用简写的尽量用简写

_推荐_

```
.jdc
  color #fff
```

_不推荐_

```
.jdc
  color #ffffff
```

css 属性值需要用到引号时，统一使用单引号

_推荐_

```
.jdc
  font-family 'Hiragino Sans GB'
```

_不推荐_

```
.jdc
  font-family "Hiragino Sans GB"
```

##### 属性书写顺序

1. 布局定位属性：display / position / float / clear / visibility / overflow
2. 自身属性：margin / padding / width / height / border / border-radius / background
3. 文本属性：color / font / text-decoration / text-align / vertical-align / white-space / break-word
4. 其他属性（CSS3）：content / cursor / box-shadow / text-shadow / background: linear-gradient...

```
.jdc
  position relative
  display block
  float left
  margin 0 10px
  padding 20px 0
  width 100px
  height 100px
  border-radius 10px
  background rgba(0, 0, 0, 0.5)
  color #333
  font-family Arial, 'Helvetica Neue', Helvetica, sans-serif
```

##### CSS3 浏览器私有前缀写法

CSS3 浏览器私有前缀在前，标准前缀在后

```
.jdc
  -webkit-border-radius 10px
  -moz-border-radius 10px
  -o-border-radius 10px
  -ms-border-radius 10px
  border-radius 10px

```

#### 注释规范

##### 单行注释

注释字符与注释内容添加空格，单独占一行,
<font color="red">使用统一的单行注释</font>

_推荐_

```
/* CSS Comment Text */
.jdc {
  font-family: 'Hiragino Sans GB';
}
// stylus Comment Text
.jdc
  font-family 'Hiragino Sans GB'
```

_不推荐_

```
.jdc {
  font-family: 'Hiragino Sans GB'; /* CSS Comment Text */
}
.jdc
  font-family "Hiragino Sans GB" // stylus Comment Text
```

##### 模块注释

注释内容第一个字符和最后一个字符都是一个空格字符，/_ 与 模块信息描述占一行，多个横线分隔符-与_/占一行

_推荐_

```
/* Module A
---------------------------------------------------------------- */
.mod_a {}

/* Module B
---------------------------------------------------------------- */
.mod_b {}
```

_不推荐_

```
/* Module A ---------------------------------------------------- */
.mod_a {}
/* Module B ---------------------------------------------------- */
.mod_b {}
```

##### 文件信息注释

在样式文件编码声明 @charset 语句下面注明页面名称、作者、创建日期等信息

```
@charset "UTF-8";
/**
 * @desc File Info
 * @author Author Name
 * @date 2015-10-10
 */
```

#### 预编译器

约定：<font color="red">选择一款统一的预编译器</font>

##### 变量

可复用属性尽量抽离为变量，易于统一维护

##### 混合（mixin）

根据功能定义模块，然后在需要使用的地方通过名称调用 调用，避免编码时重复输入代码

```
positionA()
  position absolute
  top 0
  left 0

.page
  positionA()
```

#### 重置样式（参考）

##### 移动端

```
* { -webkit-tap-highlight-color: transparent; outline: 0; margin: 0; padding: 0; vertical-align: baseline; }
body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin: 0; padding: 0; vertical-align: baseline; }
img { border: 0 none; vertical-align: top; }
i, em { font-style: normal; }
ol, ul { list-style: none; }
input, select, button, h1, h2, h3, h4, h5, h6 { font-size: 100%; font-family: inherit; }
table { border-collapse: collapse; border-spacing: 0; }
a { text-decoration: none; color: #666; }
body { margin: 0 auto; min-width: 320px; max-width: 640px; height: 100%; font-size: 14px; font-family: -apple-system,Helvetica,sans-serif; line-height: 1.5; color: #666; -webkit-text-size-adjust: 100% !important; text-size-adjust: 100% !important; }
input[type="text"], textarea { -webkit-appearance: none; -moz-appearance: none; appearance: none; }
```

##### PC 端

```
html, body, div, h1, h2, h3, h4, h5, h6, p, dl, dt, dd, ol, ul, li, fieldset, form, label, input, legend, table, caption, tbody, tfoot, thead, tr, th, td, textarea, article, aside, audio, canvas, figure, footer, header, mark, menu, nav, section, time, video { margin: 0; padding: 0; }
h1, h2, h3, h4, h5, h6 { font-size: 100%; font-weight: normal }
article, aside, dialog, figure, footer, header, hgroup, nav, section, blockquote { display: block; }
ul, ol { list-style: none; }
img { border: 0 none; vertical-align: top; }
blockquote, q { quotes: none; }
blockquote:before, blockquote:after, q:before, q:after { content: none; }
table { border-collapse: collapse; border-spacing: 0; }
strong, em, i { font-style: normal; font-weight: normal; }
ins { text-decoration: underline; }
del { text-decoration: line-through; }
mark { background: none; }
input::-ms-clear { display: none !important; }
body { font: 12px/1.5 \5FAE\8F6F\96C5\9ED1, \5B8B\4F53, "Hiragino Sans GB", STHeiti, "WenQuanYi Micro Hei", "Droid Sans Fallback", SimSun, sans-serif; background: #fff; }
a { text-decoration: none; color: #333; }
a:hover { text-decoration: underline; }
```

### 四、命名规范

- 采用小写方式
- 使用下划线分割
- 文件命名总是以字母开头而不是数字，且字母一律小写，以下划线连接且不带其他标点符号

#### 项目命名

- <font color="red">公司缩写\_项目名[\_功能模块\_客户端]</font>
- h5 项目：以<font color="red">\_h5</font> 结尾
- 小程序 项目：以<font color="red">\_mp</font> 结尾

#### 图片命名

<font color="red">模块名\_功能名[序号][图片精度].后缀</font>

##### 模块

- mod：公共模块
- login：登录模块
- user：个人中心模块
- ...

##### 功能

- \_icon：图标
- \_logo：Logo
- \_spr：精灵图
- \_btn：按钮
- \_bg：平铺背景
- \_banner：banner
- ...

##### 图片精度

- 普清：无
- Retina：@2x | @3x
- ...

#### ClassName 命名

ClassName 的命应该尽量精短、明确，必须以字符开头命名，且全部字母为小写，单词之间统一使用下划线“\_”连接

##### 命名原则

- 基于姓氏命名法（继承+外来）
- 祖先模块不能出现下划线，除了全站公用模块，如<font color="red">mod\_</font>系列的命名

_推荐_

```
<div class="modulename">
  <div class="modulename_info>
    <div class="modulename_info_son"></div>
    <div class="modulename_info_son"></div>
    ...
  </div>
</div>

<!-- 这个是全站公用模块，祖先模块允许直接出现下划线 -->
<div class="mod_info">
	<div class="mod_info_son"></div>
	<div class="mod_info_son"></div>
	...
</div>
```

_不推荐_

```
<div class="modulename_info">
	<div class="modulename_info_son"></div>
	<div class="modulename_info_son"></div>
	...
</div>
```

在子孙模块数量可预测的情况下，严格继承祖先模块的命名前缀

```
<div class="modulename">
	<div class="modulename_cover"></div>
	<div class="modulename_info"></div>
</div>
```

当子孙模块超过 4 级及以上的时候，可以考虑在祖先模块内具有识辨性的独立缩写作为新的子孙模块

_推荐_

```
<div class="modulename">
  <div class="modulename_info>
    <div class="modulename_info_user">
      <div class="modulename_info_user_img">
        <img src="" alt="">
       <!-- 这个时候 miui 为 modulename_info_user_img 首字母缩写-->
       <div class="miui_txt></div>
       <div class="miui_txt></div>
       ...
      </div>
    </div>
  </div>
</div>

```

_不推荐_

```
<div class="modulename">
	<div class="modulename_cover"></div>
  <div class="modulename_info">
    <div class="modulename_info_user">
      <div class="modulename_info_user_img">
        <img src="" alt="">
        <div class="modulename_info_user_img_txt"></div>
        <div class="modulename_info_user_img_txt"></div>
        ...
      </div>
    </div>
    <div class="modulename_info_list"></div>
	</div>
</div>
```

##### 模块命名

全站公共模块，以<font color="red">mod\_</font>开头

```
<div class="mod_modulename"></div>
```

功能公共模块：以<font color="red">功能\_mod\_</font>开头

```
<div class="user_mod_modulename"></div>
```

##### 常用命名推荐

![image](http://pro.yuemia.com/static/class_name.png)

## 五、JS

#### 语言规范

##### 引用

<font color="red">const</font>和<font color="red">let</font>都是块级作用域，<font color="red">var</font>是函数级作用域

- 对所有引用都使用<font color="red">const</font>，不要使用
  <font color="red">var</font>

```
// bad
var a = 1
var b = 2

// good
const a = 1
const b = 2
```

- 如果引用是可变的，则使用<font color="red">let</font>

```
// bad
var count = 1
if (count < 10) {
  count += 1
}

// good
let count = 1
if (count < 10) {
  count += 1
}
```

##### 对象

- 使用字面量值创建对象

```
// bad
const a = new Object()

// good
const a = {}
```

- 别使用保留字作为对象的键值，这样在 IE8 下不会运行

```
// bad
const a = {
  default: {},  // default 是保留字
  common: {}
}

// good
const a = {
  defaults: {},
  common: {}
}
```

- 请使用对象方法的简写方式

```
// bad
const item = {
  value: 1,

  addValue: function (val) {
    return item.value + val
  }
}

// good
const item = {
  value: 1,

  addValue(val) {
    return item.value + val
  }
}
```

- 请使用对象属性的简写方式

```
const job = 'FrontEnd'

// bad
const item = {
  job: job
}

// good
const item = {
  job
}
```

- 对象属性值的简写方式要和声明式的方式分组

```
const job  = 'FrontEnd'
const department = 'JDC'

// bad
const item = {
  sex: 'male',
  job,
  age:25,
  department
}

// good
const item = {
  job,
  department,
  sex: 'male',
  age: 25
}
```

##### 数组

- 使用字面量值创建数组

```
// bad
const items = new Array()

// good
const item = []
```

- 向数组末尾添加元素时，请使用<font color="red">push</font>方法

```
const items = []
// bad
items[items.length] = 'test'

// good
items.push('test')
```

- 使用拓展运算符<font color="red">...</font>复制数组

```
const items = []
const itemsCopy = []
const len = items.length
let i

// bad
for(i = 0; i < len; i++) {
  itemsCopy[i] = items[i]
}

// good
itemsCopy = [...items]

```

- 使用数组的<font color="red">map</font>等方法时，请使用<font color="red">return</font>声明，如果是单一声明语句的情况下，可省略<font color="red">return</font>

```
// good
[1, 2, 3].map(x => {
  const y = x + 1
  return x * y
})

// good
[1, 2, 3].map(x => x + 1)

// bad
const flat = {}
[[0, 1], [2, 3], [4, 5]].reduce((memo, item, index) => {
  const flatten = memo.concat(item)
  flat[index] = flatten
})

// good
const flat = {}
[[0, 1], [2, 3], [4, 5]].reduce((memo, item, index) => {
  const flatten = memo.concat(item)
  flat[index] = flatten
  return flatten
})

// bad
inbox.filter((msg) => {
  const { subject, author } = msg
  if (subject === 'Mockingbird') {
    return author === 'Harper Lee'
  } else {
    return false
  }
})

// good
inbox.filter((msg) => {
  const { subject, author } = msg
  if (subject === 'Mockingbird') {
    return author === 'Harper Lee'
  }

  return false
})
```

##### 解构赋值

- 当需要使用对象的多个属性时，请使用解构赋值

```
// bad
function getFullName (user) {
  const firstName = user.firstName
  const lastName = user.lastName

  return `${firstName} ${lastName}`
}

// good
function getFullName (user) {
  const { firstName, lastName } = user

  return `${firstName} ${lastName}`
}

// better
function getFullName ({ firstName, lastName }) {
    return `${firstName} ${lastName}`
}
```

- 当需要使用数组的多个值时，请同样使用解构赋值

```
const arr = [1, 2, 3, 4]

// bad
const first = arr[0]
const second = arr[1]

// good
const [first, second] = arr
```

- 函数需要回传多个值时，请使用对象的解构，而不是数组的解构

```
// bad
function doSomething () {
  return [top, right, bottom, left]
}

// 如果是数组解构，那么在调用时就需要考虑数据的顺序
const [top, xx, xxx, left] = doSomething()

// good
function doSomething () {
  return { top, right, bottom, left}
}

// 此时不需要考虑数据的顺序
const {top, left} = doSomething()

```

##### 字符串

- 统一使用单引号
- 程序化生成字符串时，使用模板字符串

```
const test = 'test'

// bad
const str = ['a', 'b', test].join()

// bad
const str = 'a' + 'b' + test

// good
const str = `ab${test}`
```

##### 函数

- 不要使用<font color="red">arguments</font>，可以选择使用<font color="red">...</font>
  > <font color="red">arguments</font> 只是一个类数组，而 <font color="red">...</font> 是一个真正的数组

```
// bad
function test () {
  const args = Array.prototype.slice.call(arguments)
  return args.join('')
}

// good
function test (...args) {
  return args.join('')
}
```

- 不要更改函数参数的值

```
// bad
function test (opts) {
  opts = opts || {}
}

// good
function test (opts = {}) {
  // ...
}
```

##### 模块

- 使用标准的 ES6 模块语法<font color="red">import</font>和<font color="red">export</font>

```
// bad
const util = require('./util')
module.exports = util

// good
import Util from './util'
export default Util

// better
import { Util } from './util'
export default Util
```

- 不要使用 import 的通配符<font color="red">\*</font>，这样可以确保你只有一个默认的 export

```
// bad
import * as Util from './util'

// good
import Util from './util'
```

##### 迭代器

- 不要使用<font color="red">iterators</font>

```
const numbers = [1, 2, 3, 4, 5]

// bad
let sum = 0
for (let num of numbers){
  sum += num
}

// good
let sum = 0
numbers.forEach(num => sum += num)

// better
const sum = numbers.c((total, num) => total + num, 0)
```

##### 变量声明

- 声明变量时，请使用 <font color="red">const</font>、<font color="red">let</font> 关键字，如果没有写关键字，变量就会暴露在全局上下文中，这样很可能会和现有变量冲突，另外，也很难明确该变量的作用域是什么。这里推荐使用 <font color="red">const</font> 来声明变量，我们需要避免全局命名空间的污染。

```
// bad
demo = new Demo()

// good
const demo = new Demo()
```

- 将所有的 <font color="red">const</font> 和 <font color="red">let</font> 分组

```
// bad
let a
const b
let c
const d
let e

// good
const b
const d
let a
let c
let e
```

##### 分号

- 我们遵循 <font color="red">Standard</font> 的规范，不使用分号

#### 代码规范

- 变量命名：当命名变量时，使用驼峰式命名（variableName）
- 操作符空格：操作符前后都需要添加空格
- 逗号空格，逗号后台使用空格

## 六、Vue 风格指南

#### 规则分类

- 优先级 A：必要的

  这些规则会帮你规避错误，所以学习并接受它们带来的全部代价吧。这里面可能存在例外，但应该非常少，且只有你同时精通 JavaScript 和 Vue 才可以这样做。

- 优先级 B：强烈推荐

  这些规则能够在绝大多数工程中改善可读性和开发体验。即使你违反了，代码还是能照常运行，但例外应该尽可能少且有合理的理由。

- 优先级 C：推荐

  当存在多个同样好的选项，选任意一个都可以确保一致性。在这些规则里，我们描述了每个选项并建议一个默认的选择。也就是说只要保持一致且理由充分，你可以随意在你的代码库中做出不同的选择。请务必给出一个好的理由！通过接受社区的标准，你将会：

  1. 训练你的大脑，以便更容易的处理你在社区遇到的代码；
  2. 不做修改就可以直接复制粘贴社区的代码示例；
  3. 能够经常招聘到和你编码习惯相同的新人，至少跟 Vue 相关的东西是这样的。

- 优先级 D：谨慎使用

  有些 Vue 特性的存在是为了照顾极端情况或帮助老代码的平稳迁移。当被过度使用时，这些特性会让你的代码难于维护甚至变成 bug 的来源。这些规则是为了给有潜在风险的特性敲个警钟，并说明它们什么时候不应该使用以及为什么。

#### 优先级 A 的规则：必要的

##### 组件名为多个单词

组件名应该始终是多个单词的，根组件 <font color="red">App</font> 除外

_不推荐_

```
Vue.component('todo'),{
  // ...
})
```

```
export default {
  name: 'Todo',
  // ...
}
```

_推荐_

```
Vue.component('todo-item', {
  // ...
})
```

```
export default {
  name: 'TodoItem'
}
```

##### 组件数据

组件的 <font color="red">data</font> 必须是一个函数

_不推荐_

```
Vue.component('some-comp'),{
  data: {
    foo: 'bar'
  }
})
```

```
export default {
  data: {
    foo: 'bar'
  }
}
```

_推荐_

```
Vue.component('some-comp', {
  data () {
    return {
      foo: 'bar'
    }
  }
})
```

```
export default {
  data () {
    return {
      foo: 'bar'
    }
  }
}
```

```
// 在一个Vue的根实例上直接使用对象是可以的，
// 因为只存在一个这样的实例
new Vue({
  data: {
    foo: 'bar'
  }
})
```

##### Prop 定义

Prop 定义应该尽量详细

_不推荐_

```
props: ['status']
```

_推荐_

```
props: {
  status: String
}
```

```
// 更好的做法
props: {
  status: {
    type: String,
    required: true,
    validator(value){
      return [
        'syncing',
        'synced',
        'version-conflict',
        'error'
      ].indexOf(value) !== -1
    }
  }
}
```

##### 为 <font color="red">v-for</font> 设置键值

总是用 <font color="red">key</font> 配合 <font color="red">v-for</font>

_不推荐_

```
<ul>
  <li v-for="todo in todos">
    {{ todo.text }}
  </li>
</ul>
```

_推荐_

```
<ul>
  <li
    v-for="todo in todos"
    :key="todo.id">
    {{ todo.text }}
  </li>
</ul>
```

##### 避免 <font color="red">v-if</font> 和 <font color="red">v-for</font> 用在一起

- 为了过滤一个列表中的项目，请将列表替换为一个计算属性，让其返回过滤后的列表，例如：

```
v-for="user in users" v-if="user.isActive"
```

- 为了避免渲染本应该被隐藏的列表，请将 <font color="red">v-if</font> 移至父级容器元素上

```
v-for="user in users" v-if="showUsers"
```

##### 为组件样式设置作用域

对于应用来说，顶级组件 <font color="red">App</font> 和布局组件中的样式可以是全局的，但是其它所有组件都应该是有作用域的。

##### 私有属性名

在插件、混入等扩展中始终为自定义的私有属性使用 <font color="red">\$\_</font> 前缀，并附带一个命名空间以回避和其它作者的冲突（比如： <font color="red">\$\_yourPluginName\_</font> ）

_不推荐_

```
let myGreatMixin = {
  // ...
  methods: {
    update () {
      // ...
    }
  }
}
```

```
let myGreatMixin = {
  // ...
  methods: {
    _update () {
      // ...
    }
  }
}
```

```
let myGreatMixin = {
  // ...
  methods: {
    $update () {
      // ...
    }
  }
}
```

```
let myGreatMixin = {
  // ...
  methods: {
    $_update () {
      // ...
    }
  }
}
```

_推荐_

```
let myGreatMixin = {
  // ...
  methods: {
    $_myGreatMixin_update () {
      // ...
    }
  }
}
```

#### 优先级 B 的规则：强烈推荐（增强可读性）

##### 组件文件

只要是能够拼接文件的构建系统，就把每个组件单独分成文件

_不推荐_

```
Vue.component('TodoList', {
  // ...
})

Vue.component('TodoItem', {
  // ...
})
```

_推荐_

```
components/
|- TodoList.vue
|- TodoItem.vue
```

##### 单文件组件的大小写

单文件组件的文件名应该要么始终是单词大写开头，要么始终是横线连接

约定：大写开头驼峰式 Or 横线连接

_不推荐_

```
components/
|- mycomponent.vue
```

```
components/
|- myComponent.vue
```

_推荐_

```
components/
|- MyComponent.vue
```

```
components/
|- my-component.vue
```

##### 基础组件名

应用特定样式和约定的基础组件（展示类、无逻辑或无状态的组件）应该全部以一个特定的前缀开头，比如 <font color="red">Base</font> 、 <font color="red">App</font> 或 <font color="red">V</font>

约定：基础组件前缀 <font color="red">C</font>

_不推荐_

```
components/
|- MyButton.vue
|- VueTable.vue
|- Icon.vue
```

_推荐_

```
components/
|- BaseButton.vue
|- BaseTable.vue
|- BaseIcon.vue
```

```
components/
|- VButton.vue
|- VTable.vue
|- VIcon.vue
```

##### 单例组件名

单个活跃实例的组件应该以 <font color="red">The</font> 前缀命名，以示其唯一性

这不意味着组件只可用于一个单页面，而是每个页面只使用一次。这些组件永远不接受任何 <font color="red">prop</font> ，
因为它们是为你的应用定制的，而不是它们在你的应用正的上下文。如果你发现有必要添加 <font color="red">prop</font> ,
那就表明这实际上是一个可复用的组件，只是目前在每个页面里只使用一次

_不推荐_

```
components/
|- Heading.vue
|- MySidebar.vue
```

_推荐_

```
components/
|- BaseButton.vue
|- BaseTable.vue
|- BaseIcon.vue
```

```
components/
|- TheHeading.vue
|- TheSidebar.vue
```

##### 紧密耦合的组件名

和父组件紧密耦合的子组件应该以父组件名

如果一个组件只在某个父组件的场景下有意义，这层关系应该体现在其名字上。因为编辑器通常会按字符顺序组织文件，所以这样做可以把相关联的文件排在一起

_不推荐_

```
components/
|- TodoList.vue
|- TodoItem.vue
|- TodoButton.vue
```

```
components/
|- SearchSidebar.vue
|- NavigationForSearchSidebar.vue
```

_推荐_

```
components/
|- TodoList.vue
|- TodoListItem.vue
|- TodoListItemButton.vue
```

```
components/
|- SearchSidebar.vue
|- SearchSidebarNavigation.vue
```

##### 组件名中的单词顺序

组件名应该以高级别（一般化描述的）的单词开头，以描述性的修饰词结尾

_不推荐_

```
components/
|- ClearSearchButton.vue
|- ExcludeFromSearchInput.vue
|- LaunchOnStartupCheckbox.vue
|- RunSearchButton.vue
|- SearchInput.vue
|- TermsCheckbox.vue
```

_推荐_

```
components/
|- SearchButtonClear.vue
|- SearchButtonRun.vue
|- SearchInputQuery.vue
|- SearchInputExcludeGlob.vue
|- SettingsCheckboxTerms.vue
|- SettingsCheckboxLaunchOnStartup.vue
```

##### 自闭合组件

在单文件组件、字符串模板和 JSX 中没有内容的组件应该是自闭合的——但在 DOM 模板里永远不要这样做。

自闭合组件表示它们不仅没有内容，而且刻意没有内容。其不同之处就好像书上的一页白纸对比贴有“本页有意留白”标签的白纸。而且没有了额外的闭合标签，你的代码也更简洁。

不幸的是，HTML 并不支持自闭合的自定义元素——只有官方的“空”元素。所以上述策略仅适用于进入 DOM 之前 Vue 的模板编译器能够触达的地方，然后再产出符合 DOM 规范的 HTML。

_不推荐_

```
<!-- 在单文件组件、字符串模板和 JSX 中 -->
<MyComponent></MyComponent>

<!-- 在 DOM 模板中 -->
<my-component/>
```

_推荐_

```
<!-- 在单文件组件、字符串模板和 JSX 中 -->
<MyComponent/>

<!-- 在 DOM 模板中 -->
<my-component></my-component>
```

##### 模板中的组件名大小写

对于绝大多数项目来说，在单文件组件和字符串模板中组件名应该总是 PascalCase 的——但是在 DOM 模板中总是 kebab-case 的。

PascalCase 相比 kebab-case 有一些优势：

- 编辑器可以在模板里自动补全组件名，因为 PascalCase 同样适用于 JavaScript。
- <font color="red">\<MyComponent\></font> 视觉上比 <font color="red">\<my-component\></font> 更能够和单个单词的 HTML 元素区别开来，因为前者的不同之处有两个大写字母，后者只有一个横线。
- 如果你在模板中使用任何非 Vue 的自定义元素，比如一个 Web Component，PascalCase 确保了你的 Vue 组件在视觉上仍然是易识别的。

不幸的是，由于 HTML 是大小写不敏感的，在 DOM 模板中必须仍使用 kebab-case。

还请注意，如果你已经是 kebab-case 的重度用户，那么与 HTML 保持一致的命名约定且在多个项目中保持相同的大小写规则就可能比上述优势更为重要了。在这些情况下，在所有的地方都使用 kebab-case 同样是可以接受的。

约定： <font color="red">PascalCase</font> Or <font color="red">kebab-case</font>

_不推荐_

```
<!-- 在单文件组件和字符串模板中 -->
<mycomponent/>

<!-- 在单文件组件和字符串模板中 -->
<myComponent/>

<!-- 在 DOM 模板中 -->
<MyComponent></MyComponent>
```

_推荐_

```
<!-- 在单文件组件和字符串模板中 -->
<MyComponent/>

<!-- 在 DOM 模板中 -->
<my-component></my-component>

<!-- 在所有地方 -->
<my-component></my-component>
```

##### JS/JSX 中的组件名大小写

JS/JSX 中的组件名应该始终是 PascalCase 的，尽管在较为简单的应用中只使用 Vue.component 进行全局组件注册时，可以使用 kebab-case 字符串。

_不推荐_

```
Vue.component('myComponent', {
  // ...
})

import myComponent from './MyComponent.vue'

export default {
  name: 'myComponent',
  // ...
}

export default {
  name: 'my-component',
  // ...
}
```

_推荐_

```
Vue.component('MyComponent', {
  // ...
})

Vue.component('my-component', {
  // ...
})

import MyComponent from './MyComponent.vue'

export default {
  name: 'MyComponent',
  // ...
}
```

##### 完整单词的组件名

组件名应该倾向于完整单词（或明确性高的缩写）而不是缩写

_不推荐_

```
components/
|- SdSettings.vue
|- UProfOpts.vue
```

_推荐_

```
components/
|- StudentDashboardSettings.vue
|- UserProfileOptions.vue
```

##### Prop 名大小

在声明 prop 的时候，其命名应该始终使用 camelCase，而在模板和 JSX 中应该始终使用 kebab-case。

我们单纯的遵循每个语言的约定。在 JavaScript 中更自然的是 camelCase。而在 HTML 中则是 kebab-case。

_不推荐_

```
props: {
  'greeting-text': String
}

<WelcomeMessage greetingText="hi"/>
```

_推荐_

```
props: {
  greetingText: String
}

<WelcomeMessage greeting-text="hi"/>
```

##### 多个特性的元素

多个特性的元素应该分多行撰写，每个特性一行。

_不推荐_

```
<img src="https://vuejs.org/images/logo.png" alt="Vue Logo">

<MyComponent foo="a" bar="b" baz="c"/>
```

_推荐_

```
<img
  src="https://vuejs.org/images/logo.png"
  alt="Vue Logo"
>

<MyComponent
  foo="a"
  bar="b"
  baz="c"
/>
```

##### 模板中简单的表达式

组件模板应该只包含简单的表达式，复杂的表达式则应该重构为计算属性或方法

_不推荐_

```
{{
  fullName.split(' ').map(function (word) {
    return word[0].toUpperCase() + word.slice(1)
  }).join(' ')
}}
```

_推荐_

```
<!-- 在模板中 -->
{{ normalizedFullName }}

// 复杂表达式已经移入一个计算属性
computed: {
  normalizedFullName: function () {
    return this.fullName.split(' ').map(function (word) {
      return word[0].toUpperCase() + word.slice(1)
    }).join(' ')
  }
}
```

##### 简单的计算属性

##### 应该把复杂计算属性分割为尽可能多的更简单的属性

_不推荐_

```
computed: {
  price: function () {
    var basePrice = this.manufactureCost / (1 - this.profitMargin)
    return (
      basePrice -
      basePrice * (this.discountPercent || 0)
    )
  }
}
```

_推荐_

```
computed: {
  basePrice: function () {
    return this.manufactureCost / (1 - this.profitMargin)
  },
  discount: function () {
    return this.basePrice * (this.discountPercent || 0)
  },
  finalPrice: function () {
    return this.basePrice - this.discount
  }
}

```

##### 带引号的特性值

非空 HTML 特性值应该始终带引号 (单引号或双引号，选你 JS 里不用的那个)。

约定：双引号

_不推荐_

```
<input type=text>

<AppSidebar :style={width:sidebarWidth+'px'}>
```

_推荐_

```
<input type="text">

<AppSidebar :style="{ width: sidebarWidth + 'px' }">
```

##### 指令缩写

指令缩写，（用 <font color="red">:</font> 表示 <font color="red">v-bind</font> 和用 <font color="red">@</font> 表示 <font color="red">v-on</font>

#### 优先级 C 的规则：推荐（将选择和认知成本最小化）

####组件/实例的选项顺序

1. 副作用（触发组件外的影响）
   - <font color="red">el</font>
2. 全局感知（要求组件以外的知识）

   - <font color="red">name</font>
   - <font color="red">parent</font>

3. 组件类型（更改组件的类型）

   - <font color="red">functional</font>

4. 模板修改器（改变模板的编译方式）

   - <font color="red">delimiters</font>
   - <font color="red">comments</font>

5. 模板依赖（模板内使用的资源）

   - <font color="red">components</font>
   - <font color="red">directives</font>
   - <font color="red">filters</font>

6. 组合（向选项里合并属性）

   - <font color="red">extends</font>
   - <font color="red">mixins</font>

7. 接口（组件的接口）

   - <font color="red">inheritAttrs</font>
   - <font color="red">model</font>
   - <font color="red">props / propsData</font>

8. 本地状态（本地的响应式属性）

   - <font color="red">data</font>
   - <font color="red">computed</font>

9. 事件（通过响应式事件触发的回调）

   - <font color="red">watch</font>
   - 生命周期钩子（按照它们被调用的顺序）
     - <font color="red">beforeCreate</font>
     - <font color="red">created</font>
     - <font color="red">beforeMount</font>
     - <font color="red">mounted</font>
     - <font color="red">beforeUpdate</font>
     - <font color="red">updated</font>
     - <font color="red">activated</font>
     - <font color="red">deactivated</font>
     - <font color="red">beforeDestroy</font>
     - <font color="red">destroyed</font>

10. 非响应式的属性（不依赖响应系统的实例属性）

    - <font color="red">methods</font>

11. 渲染（组件输出的声明式描

    - <font color="red">template / render</font>
    - <font color="red">renderError</font>

##### 元素特性的顺序

1. 定义

   - <font color="red">is</font>

2. 列表渲染

   - <font color="red">is</font>

3. 条件渲染

   - <font color="red">v-if</font>
   - <font color="red">v-else-if</font>
   - <font color="red">v-else</font>
   - <font color="red">v-show</font>
   - <font color="red">v-cloak</font>

4. 渲染方式（改变元素的渲染方式）

   - <font color="red">v-pre</font>
   - <font color="red">v-once</font>

5. 全局感知

   - <font color="red">id</font>

6. 唯一的特性

   - <font color="red">ref</font>
   - <font color="red">key</font>
   - <font color="red">slot</font>

7. 双向绑定

   - <font color="red">v-model</font>

8. 其他特性（所有普通的绑定或未绑定的特性）

9. 事件

   - <font color="red">v-on</font>

10. 内容

    - <font color="red">v-html</font>
    - <font color="red">v-text</font>

#### 优先级 D 的规则：谨慎使用（有潜在危险的模式）

##### 没有在 <font color="red">v-if</font> / <font color="red">v-else-if</font> / <font color="red">v-else</font> 中使用 <font color="red">key</font>

如果一组 <font color="red">v-if</font> + <font color="red">v-else</font> 的元素类型相同，最好使用 <font color="red">key</font> (比如两个 <font color="red">div</font> 元素)

##### <font color="red">scoped</font> 中的元素选择器

在 <font color="red">scoped</font> 样式中，类选择器比元素选择器更好，因为大量使用元素选择器是很慢的

_不推荐_

```
<template>
  <button>X</button>
</template>

<style scoped>
button {
  background-color: red;
}
</style>
```

_推荐_

```
<template>
  <button class="btn btn-close">X</button>
</template>

<style scoped>
.btn-close {
  background-color: red;
}
</style>
```

##### 隐性的父子组件通信

应该优先通过 prop 和事件进行父子组件之间的通信，而不是 <font color="red">this.\$parent</font> 或改变 prop

一个理想的 Vue 应用是 prop 向下传递，事件向上传递的。遵循这一约定会让你的组件更易于理解。然而，在一些边界情况下 prop 的变更或 this.\$parent 能够简化两个深度耦合的组件。

问题在于，这种做法在很多简单的场景下可能会更方便。但请当心，不要为了一时方便 (少写代码) 而牺牲数据流向的简洁性 (易于理解)。

_不推荐_

```
Vue.component('TodoItem', {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  template: '<input v-model="todo.text">'
})
```

```
Vue.component('TodoItem', {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  methods: {
    removeTodo () {
      var vm = this
      vm.$parent.todos = vm.$parent.todos.filter(function (todo) {
        return todo.id !== vm.todo.id
      })
    }
  },
  template: `
    <span>
      {{ todo.text }}
      <button @click="removeTodo">
        X
      </button>
    </span>
  `
})
```

_推荐_

```
Vue.component('TodoItem', {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  template: `
    <input
      :value="todo.text"
      @input="$emit('input', $event.target.value)"
    >
  `
})
```

```
Vue.component('TodoItem', {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  template: `
    <span>
      {{ todo.text }}
      <button @click="$emit('delete')">
        X
      </button>
    </span>
  `
})
```

## 七、Vue 目录结构

```
├── index.html                      入口页面
├── build                           构建脚本目录
│   ├── build-server.js                 运行本地构建服务器，可以访问构建后的页面
│   ├── build.js                        生产环境构建脚本
│   ├── dev-client.js                   开发服务器热重载脚本，主要用来实现开发阶段的页面自动刷新
│   ├── dev-server.js                   运行本地开发服务器
│   ├── utils.js                        构建相关工具方法
│   ├── webpack.base.conf.js            wabpack基础配置
│   ├── webpack.dev.conf.js             wabpack开发环境配置
│   └── webpack.prod.conf.js            wabpack生产环境配置
├── config                          项目配置
│   ├── dev.env.js                      开发环境变量
│   ├── index.js                        项目配置文件
│   ├── prod.env.js                     生产环境变量
│   └── test.env.js                     测试环境变量
├── mock                            mock数据目录
│   └── index.js
├── package.json                    npm包配置文件，里面定义了项目的npm脚本，依赖包等信息
├── src                             项目源码目录
│   ├── main.js                         入口js文件
│   ├── app.vue                         根组件
│   ├── components                      公共组件目录
│   │   └── Title.vue
│   ├── assets                          资源目录，这里的资源会被wabpack构建
│   │   ├── img
│   │   │   └── logo.png
│   │   ├── js
│   │   │   └── utils.js
│   │   ├── styles
│   │   │   └── base.styl
│   │   ├── service
│   │   │   └── axios.js
│   │   └── icons
│   │       └── iconfont.css
│   ├── routes                          前端路由
│   │   └── index.js
│   ├── store                           应用级数据（state）
│   │   └── index.js
│   └── views                           页面目录
│       ├── User
│       │   └── Center.vue
│       ├── Mall
│       │   ├── components
│       │   │   └── Component.vue
│       │   └── Center.vue
│       ├── Hello.vue
│       └── NotFound.vue
├── static                          纯静态资源，不会被wabpack构建。
└── test                            测试文件目录（unit&e2e）
    └── unit                            单元测试
        ├── index.js                        入口脚本
        ├── karma.conf.js                   karma配置文件
        └── specs                           单测case目录
            └── Hello.spec.js
```
