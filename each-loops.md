#Each Loops/For Loops
(一)Each Loops<br>
:sunny:scss<br>
```scss
$list: (orange, purple, teal);

//Add your each-loop here
@each $item in $list {
  .#{$item} {
    background: $item;
  }
}
```
:sunny:編譯後-css
```css
.orange {
  background: orange;
}

.purple {
  background: purple;
}

.teal {
  background: teal;
}

```
(二)For Loops<br>
:sunny:顏色函數:adjust-hue()<br>
:sunny:i只是索引的變量，或列表中元素的位置
```css
$total: 10; //Number of .ray divs in our html
$step: 360deg / $total; //Used to compute the hue based on color-wheel


.ray {
  height: 30px;
}

//Add your for-loop here:
@for $i from 1 through $total {
  .ray:nth-child(#{$i}) {
   background: adjust-hue(blue, $i * $step);

   /*條件式*/
   width: if($i % 2 == 0, 300px, 350px);
   margin-left: if($i % 2 == 0, 0px, 50px);
   }
}
```
:sunny:編譯後-css
```css
.ray {
  height: 30px;
}

.ray:nth-child(1) {
  background: #9900ff;
  width: 350px;
  margin-left: 50px;
}

.ray:nth-child(2) {
  background: #ff00cc;
  width: 300px;
  margin-left: 0px;
}

.ray:nth-child(3) {
  background: #ff0033;
  width: 350px;
  margin-left: 50px;
}

.ray:nth-child(4) {
  background: #ff6600;
  width: 300px;
  margin-left: 0px;
}

.ray:nth-child(5) {
  background: yellow;
  width: 350px;
  margin-left: 50px;
}

.ray:nth-child(6) {
  background: #66ff00;
  width: 300px;
  margin-left: 0px;
}

.ray:nth-child(7) {
  background: #00ff33;
  width: 350px;
  margin-left: 50px;
}

.ray:nth-child(8) {
  background: #00ffcc;
  width: 300px;
  margin-left: 0px;
}

.ray:nth-child(9) {
  background: #0099ff;
  width: 350px;
  margin-left: 50px;
}

.ray:nth-child(10) {
  background: blue;
  width: 300px;
  margin-left: 0px;
}


/*html*/
<div class='ray'></div>
<div class='ray'></div>
<div class='ray'></div>
<div class='ray'></div>
<div class='ray'></div>
<div class='ray'></div>
<div class='ray'></div>
<div class='ray'></div>
<div class='ray'></div>
<div class='ray'></div>
```