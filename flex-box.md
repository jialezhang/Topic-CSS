# Flexbox 的全面探索 #

# 背景 #

# 基础知识和相关术语 #
 由于flexbox是一个完整的模块而不单单是一个属性,它涉及了许多东西,包括它的一整套属性.其中一些属性是设置在容器元素(父级元素,被认为是"flex container")上面,其余的设置在子元素(被认为是"flex items")上面.
如果说普通的样式是基于"块(block)"元素和"行内(inline)"元素流方向的话,flex样式就是基于"flex流方向".来瞅瞅下面的图以便有一个更具体的认识,解释了flex样式的中心思想.
![flexbox](https://cdn.css-tricks.com/wp-content/uploads/2011/08/flexbox.png);

一般来说,items不是以`main axis`(从`main-start`到`main-end`)就是以`cross axis`(从`cross-start`到`cross-end`的方式布置.
    * **main axis** flex容器的`main axis`是flex items排布的基本方式,请注意,并非必须是水平排布,一切都取决于属性`flex-direction`如何设置;
    * **main-start|main-end** flex items 从`main-start`到`mian-end`放置在容器中;
    * **main-size** flex items 的宽或者高,取决于item的`main`大小.
    * cross相关同main

## 父元素属性(flex container) ##
1. `display:flex|inline-flex`
> 定义了一个flex容器;为其直系子元素创造了一个flex的上下文;

2. `flex-direction: row | row-reverse | column | column-reverse`
    > 这个建立了 `main-axis`,因此将`flex items`放置在了`flex container`里面.`Flexbox`(除去可选择的包裹)是一个单方向布局的概念.`flex items`基本上要么是以水平行(horizontal row)要么是以垂直列(vertical columns)的形式排布的.
![flex-direction](https://cdn.css-tricks.com/wp-content/uploads/2014/05/flex-direction1.svg)
>
- row(default):从左到右(ltr);从右到左(rtl);
- row-reverse:ltr;rtl;
- column:同row,但是是从上到下;
- column-reverse:同row-reverse,但是是从上到下;

3. `flex-wrap: nowrap | wrap | wrap-reverse; `
> 在默认情况下,所有的`flex items`将会尽量塞成一行.你可以通过这个属性让这些`items`在需要的情况.方向在这里也会起作用,这取决于新一行的方向是如何设置;
![flex-wrap](https://cdn.css-tricks.com/wp-content/uploads/2014/05/flex-wrap.svg)
>
- nowrap(default):单行(ltr|rtl);
- wrap:多行|(ltr|rtl);
- wrap-reverse:多行|(从右到左-ltr|从左到右rtl);

4. `flex-flow: <‘flex-direction’> || <‘flex-wrap’> `
> `flex-direction`和`flex-wrap`的合成简写,同时定义了`flex-container`的`main-axis`和`cross-axis`;默认是row-nowrap

5. `justify-content: flex-start | flex-end | center | space-between | space-around;`
> `main-axis`的对齐方式;当一行之内的所有`flex items`都是不能转变的时候,这个属性可以用来分布左侧多余的空白;或者`flex items`是可以改变但是已经达到最大尺寸;当这些items溢出单行的时候,这个属性能够对这些需要对齐的元素施加一些控制;
![jsutify-content](https://cdn.css-tricks.com/wp-content/uploads/2013/04/justify-content.svg)
>
    - flex-start (default): 以行开始处排布

    - flex-end: 以行结束处排布

    - center: 以行中间排布

    - space-between: 均匀的分布在一行,第一个在开头,最后一个在结束处.

    - space-around: 均匀的分布,但是items周围的间隙是相等的;注意,这里的相等的并不是所有的间隙相同,相邻item的间隙不会覆盖;

6. `align-items: flex-start | flex-end | center | space-between | space-around;`
> flex-items 在`cross axis`的当前行如何排布;把这个想象成`cross axis`的`justify-content`,
![align-items](https://cdn.css-tricks.com/wp-content/uploads/2014/05/align-items.svg)
>
    - flex-start: items顶部对齐

    - flex-end: items底部对齐

    - center: items居中对齐

    - baseline: 基线对齐

    - stretch (default): 拉伸同容器等大(min-width/max-width依然有效)
7. `align-content: flex-start | flex-end | center | space-between | space-around | stretch;`
> 当flex-container的`cross-axis`方向还有多余空间的时候用来对齐;好比在`main-axis`的`jusitfy-content`用来对齐单个item;注意:这个属性在单行的时候可能没有什么效果;
![align-content](https://cdn.css-tricks.com/wp-content/uploads/2013/04/align-content.svg)
>
    - flex-start: 容器内元素顺容器顶部对齐;

    - flex-end: 容器内元素顺容器底部对齐;

    - center: 容器内元素沿容器中部对齐;

    - space-between: 容器内元素均匀分布在容器内,第一行元素在最顶部,最后一行元素在最底部;

    - space-around: 每行元素上下均匀分布空间;(注意不是所有空隙相同);

    - stretch (default): 每行元素拉伸以充分占满容器;

## 子元素属性(flex items) ##
1. `order: <integer>;`

> 默认情况下,`flex-teims`是以代码顺序来排布的.然后,这个属性可以用来改变item在容器中出现次序的属性;

2. `flex-grow: <number>; /* default 0 */`

> 这个属性可以让item在必要的时候拉伸;接受一个无量纲的值作为占比;规定items可以使用container中多少可用空间;
如果,flex-grow设置为1,每一个item等大的占据container;如果你给某个item的flex-item设置成2,那么此元素的大小将是其余的两倍;

3. `flex-shrink: <number>; /* default 1 */`

> 赋予item在必要时候收缩的能力;

4. `flex-basis: <length> | auto; /* default auto */`

    > 定义每个元素在剩余空间被分配之前的默认大小;`main-size`值使之与`width`和`height`匹配.(这句话自己也不知道他在说什么),取决于相关联的基于`flex-direction`的元素;

> 如果设置位0,那么内容周围多余的空间将不会分解;如果设置位`auto`,多余的空间将被分配,这取决于`flex-grow`的值.

5. `flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]`

    > `flex-grow`,`flex-shrink`,`flex-basis`的组合简写.第二,三个是可选的,默认是`0 1 auto`;
6. `align-self: auto | flex-start | flex-end | center | baseline | stretch;`

    > 用来复写单个item的对齐方法(align-item设定的).注意:`float`,`clear`,`vertical-align`对`flex-item`无效;
