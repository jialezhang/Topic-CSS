## font相关 ##

1. line-height has a special case where it allows a unitless number:

```CSS
line-height: 1.4;
```
它的单位是依据本身的**font-size**来确定大小的，而不是父元素，如果本身采用的是`em`为单位，则此时`line-height:1.4em`

## 基本属性 ##

1. diaplay:inline-block
这个属性自带`white-space`,所以元素之间会有一定的**间隔**，如果用`float`会消除**间隔**这个问题，但是之后有多加的元素会有`clear`的问题;

## 布局相关 ##

## 垂直居中文字 ##
1. 单行文字：
```CSS
#box {
  height: 90px;
  line-height: 90px;
  }
```
2. 多行文字
```html
<div>
  <span>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</span>
  </div>
```
```CSS
div {
  width: 250px;
  height: 100px;
  line-height: 100px;
  text-align: center;
}

span {
  display: inline-block;
  vertical-align: middle;
  line-height: normal;
  }
```
3. 模拟table布局
```html
<div>
  <span>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</span>
</div>
```
```CSS
div {
  display: table;
  width: 250px;
  height: 100px;
  text-align: center;
}

span {
  display: table-cell;
  vertical-align: middle;
  }
```
4. 使用绝对定位
```CSS
.Absolute-Center {
  margin: auto;
  position: absolute;
  top: 0; left: 0; bottom: 0; right: 0;
  }
```
**优势**:
>
    1. Cross-browser (including IE8-10)
2. No special markup, minimal styles
3. Responsive with percentages and min-/max-
4. Use one class to center any content
5. Centered regardless of padding (without box-sizing!)
6. Blocks can easily be resized
6. Works great on images
**CAVEATS（警告）**:
1. Height must be declared (see Variable Height)
2. Recommend setting overflow: auto to prevent content spillover (see Overflow)
3. Doesn’t work on Windows Phone
**BROWSER COMPATIBILITY:**
`Chrome, Firefox, Safari, Mobile Safari, IE8-10.`

something to read
http://www.smashingmagazine.com/2013/08/09/absolute-horizontal-vertical-centering-css/2/
http://www.smashingmagazine.com/2013/08/09/absolute-horizontal-vertical-centering-css/3/

http://designshack.net/articles/css/how-to-center-anything-with-css

http://taligarsiel.com/Projects/howbrowserswork1.htm#Layout
