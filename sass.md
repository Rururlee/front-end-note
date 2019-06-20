#sass note


:penguin:若子元素有共同屬性可使用>*{屬性} 
```css
.main {
      width: 85%;
      min-height: 750px;
      min-width: 600px;
      background-color: $color-main;
        > * {
          padding-left:30;
        } 
        ul {
        padding-left: 30px;
          li {
          font-size: 0.85rem;
          }
        }
        h1 {
        font-size: 62px;
        -webkit-margin-before: 0;
        padding-top: 40px;
        }
        p {
        width: 55%;
        min-width: 550px;
        }
        a {
        color: inherit;
        text-decoration: none;
        }
        a:hover {
        text-decoration: underline;
        }
     }
```
:penguin:What is a Mixin?<br>
(1)Mixin將一段css包住，這段css可以插入在任一css內
```css
/*Mixin定義backface-visibility*/
@mixin backface-visibility {
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
  -moz-backface-visibility: hidden;
  -ms-backface-visibility: hidden;
  -o-backface-visibility: hidden;
}

/*include backface-visibility*/
.notecard {
.front, .back {
    width: 100%;
    height: 100%;
    position: absolute;

    @include backface-visibility;
  }
}  

/*編譯後的css*/
.notecard .front, .notecard .back {
  width: 100%;
  height: 100%;
  position: absolute;

   backface-visibility: hidden;
  -webkit-backface-visibility: hidden; 
  -moz-backface-visibility: hidden;
  -ms-backface-visibility: hidden;
  -o-backface-visibility: hidden;
}
```
(2)Mixin可帶參數
```css
@mixin backface-visibility($visibility) { //Add an argument
  backface-visibility: $visibility;
  -webkit-backface-visibility: $visibility;
  -moz-backface-visibility: $visibility;
  -ms-backface-visibility: $visibility;
  -o-backface-visibility: $visibility;
}

.front, .back {
    @include backface-visibility(hidden);
}
```
(3)可帶多個參數
```css
@mixin dashed-border($width, $color: #FFF) {
  border: {
     color: $color;
     width: $width;
     style: dashed;
  }
}

span { //only passes non-default argument
    @include dashed-border(3px);
}

p { //passes both arguments
    @include dashed-border(3px, green);
}

div { //passes out of order but explicitly defined
   @include dashed-border(color: purple, width: 5px); 
}
```
(4)一些參數使用
```css
@mixin transition($time){
  transition: $time;
  -webkit-transition: $time;
  -moz-transition: $time;
  -o-transition: $time;
}  

@mixin transform-style($style){
   transform-style: $style;
  -moz-transform-style: $style;
  -o-transform-style: $style;
  -ms-transform-style: $style;
  -webkit-transform-style: $style;
}
.notecard {
  @include transform-style(preserve-3d);
  @include transition(0.4s);
}
```
:penguin:(1)Sass List Arguments<br>
// 提升程式碼可讀性、變數群組化<br>
```css
@mixin stripes($direction, $width-percent, $stripe-color, $stripe-background: #FFF) {
  background: repeating-linear-gradient( /*css一個方法*/
    $direction,
    $stripe-background,
    $stripe-background ($width-percent - 1),
    $stripe-color 1%,
    $stripe-background $width-percent
  );
}
```
:penguin:(2)使用Maps資料格式存欲傳入變數<br>
// 最後一個key/value後面的逗號可以省略<br>
// key的名稱不能重複，否則會編譯錯誤<br>
// key/value的名稱可以是許多資料類型(數字、字串、布林等等)
```js
$college-ruled-style: ( /*與上方stripes屬性相對應*/
    direction: to bottom,
    width-percent: 15%,
    stripe-color: blue,
    stripe-background: white
);
```
:penguin:(3)變數使用 ... 進行傳遞：
```css
.definition {
      width: 100%;
      height: 100%;
      @include stripes($college-ruled-style...);
 }
```
:penguin:The & Selector in Mixins<br>
mixin中選擇器的使用
```css
@mixin text-hover($color){
  &:hover {
      color: $color; 
  }
}

.word { //SCSS: 
    display: block; 
    text-align: center;
    position: relative;
    top: 40%;
    @include text-hover(red);
  }

/*css*/
.word{ 
    display: block;
    text-align: center;
    position: relative;
    top: 40%;
  }
  .word:hover{
    color: red;
  }
```
