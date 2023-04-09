# [CSS全解] CSS基础

## CSS历史

### 目录

* CSS 的历史
* CSS是艺术
* 体系化学习
* 文档流

1.  Normal Flow

#### CSS的牛x之处在哪？

* 层叠样式表

### 层叠指什么？

* 样式层叠

1. 可以多次对同一选择器进行样式声明

* 选择器层叠

1. 可以用不同选择器对同一元素进行样式声明

* 文件层叠

1. 可以用多个文件进行层叠

* 这些特性使得CSS 极度灵活

1. 这也为CSS后来被吐槽留下隐患

#### 我怎么知道那些浏览器支持哪些特性呢

1. 方法一： 几十种浏览器全部跑一遍
2. 方法二： [使用caniuse.com](https://caniuse.com/)

## 体系化学习 CSS


### 体系化学习

* 学一门语言必须学会什么

1. 语法(怎么写代码)
2. 如何调试(怎么知道自己代码写错了)
3. 在哪查资料(其实就是为了抄代码)
4. 标准制定者是谁

* 如何学

1. Copy-抄文档、抄老师
2. Run-放在自己的机器上运行成功
3. Modify-加入一点自己的想法，然后重新运行

### 语法超级简单

* 语法一： 样式语法

```
选择器{
    属性名: 属性值;
    /*注释*/
}
```
* 注意事项

1. 所以符号都是英文符号，如果写错了，浏览器会警告
2. 区分大小写，a和A是不同的东西
3. 没有//注释
4. 最后一个分号可以省略，但建议不要省略
5. 任何地方写错了，都不会报错，浏览器会直接忽略
6. 那我们怎么知道自己写没写错呢

* 语法二： at 语法

```
 @charset "UTF-8";
 @import url(2.css);
 @media(min-width: 100px)and(max-width: 200px){
    语法一
 }
 ```

 * 注意事项

1. @charset 必须放在第一行
2. 前两个at 语法必须以分号;结尾
3. @media 语法会单独教学
4. charset 是字符集的意思,但 UTF-8 是字符编码encoding,这是历史遗留问题

<h2 style="color:red">border调试法</h2>

* 步骤

1. 怀疑某个元素有问题
2. 就给这个元素加border
3. border没出现？说明选择器错了或者语法错了
4. border出现了？看看边界是否符合预期
5. bug解决了才可以把border删掉

* 记住

1. CSS的border调试法
2.  就相当于JS的log调试发
3.  之后每节课重复这个调试法

### 在哪里查资料

* 网站推荐

1. google搜索关键词时加MDN
2. CSS tricks(英文)
3. 张鑫旭的博客

* 书籍推荐

1. 不推荐买任何书
2. CSS 和 HTML 一样，以练为主

### 在哪搜练习素材

* PSD

1. Freepik 搜索 [PSD web](https://www.freepik.com/search?format=search&query=web&type=psd)

* 效果图(不提供下载)

1. [dribbble.com](https://dribbble.com/search/web) 顶级设计师社区
2. 可以用肉眼去模仿它

* 商业网站

1. 直接模仿你常去的网站

## 文档流

### 基本概念

* 要理解几个重要的概念

1. 文档流 Normal Flow
2. 块、内联、内联块
3. margin合并
4. 两种盒模型(botder-box 更符合人类的思维)

* span 元素从左到右依次排列
* div 元素从上到下依次排列

### 文档流

* 流动方向

1. inline 元素从左到右， 到达最右边才会换行
2. block 元素从上到下，每一个都会另起一行
3. inline-block 也是从左到右，但是到达最后是不会把自己分成两块

* 宽度

1. inline 宽度为内部inline元素的和，不能用width指定
2. block 默认自动计算宽度，可用width指定
3. inline-block 结合前两者特点，可用width

* 高度

1. inline 高度由line-height 间接确定，跟height无关
2. block高度由内部文档流元素决定，可以设height
3. inline-block 跟block 类似，可以设置height

* display: inline-block; 不会分成两行，只会一块一块的

### overflow 溢出

* 当内容大于容器

1. 等内容的宽度或高度大于容器的，会溢出
2. 可用overflow 来设置是否显示滚动条
3. auto 是灵活设置
4. scroll 是永远显示
5. hidden 是直接隐藏溢出部分
6. visible 是直接显示溢出部分
7. overflow 可以分为 overflow-x 和 overflow-y

### 脱离文档流
```css
1. pos:a
position: absolute/fixed;
2.float:left;
```

## 盒模型

### 两种盒模型

* content box 与 border box

1. border 边框 里面是有一个padding，内边距
2. padding 再里面就是我们写内容的区域 content 内容区
3. border 边框 外面有一个margin， 外边距
4. 你的width宽度只包含内容，就是内容区域，那么就叫做content box，叫做:内容盒模型；
5. 那么你的width宽度只包含border; padding; content ，那么叫做border-box。

<p>margin----外边距</p>
<p>padding----内边距</p>
<p>border-----边框</p>
<p>box-sizing----盒子的类型，尺寸</p>

* 公式

1. content-box width=内容宽度
2. border-box 内容宽度+padding+border

### margin 合并

* 哪些情况会合并

1. 父子 margin 合并
2. 兄弟 margin 合并

* 如何组织合并

1. 父子合并用 padding/border 挡住
2. 父子合并用 overflow:hidden 挡住
3. 父子合并用 display:flex,不知道为什么
4. 兄弟合并是符合预期的
5. 兄弟合并可以用inline-block 消除
6. 总之要一条一条死记
7. 而且 CSS 的属性逐年曾多，每年都可能有新的

### 基本单位

* 长度单位

1. px 像素
2. em 相对于自身 font-size 的倍数
3. 百分数
4. 整数
5. rem: 等你把 em 滚瓜烂熟了再问 rem
6. vw 和 vh
7. 其他长度单位都用得少，不用了解

* 颜色

1. 十六进制 #FF6600 或者 #F60
2. RGBA 颜色 rgb(0,0,0) 或者(0,0,0,1)
3. hsl 颜色 hsl(360,100%,100%)
