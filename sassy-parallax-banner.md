#Sassy Parallax Banner
視覺差背景效果<br>
:sunny:scss
```scss
@mixin background-size($size){
  background-size:$size;
  -webkit-background-size:$size;
  -moz-background-size:$size;
  -o-background-size:$size;
}

@mixin parallax-background($file) {
  background: url($file) no-repeat center center fixed;
  @include background-size(cover);
}

$parallax-height: 100vh;
$center-margin: 0px auto;

html,
body {
  margin: 0;
  padding: 0;
  font-family: Roboto;
  color: #2e3738;
}


#landscape {
  height:$parallax-height;
  margin:$center-margin;
  width: 100%;
  perspective: 1px;
  transform: translateZ(-1px);
  overflow-x: hidden;
  overflow-y: auto;
  @include parallax-background("https://s3.amazonaws.com/codecademy-content/projects/sass/landscape.jpg");
}

#monkeys {
  height:$parallax-height;
  margin:$center-margin;
  width: 100%;
  perspective: 1px;
  transform: translateZ(-1px);
  overflow-x: hidden;
  overflow-y: auto;
  @include parallax-background("https://s3.amazonaws.com/codecademy-content/projects/sass/monkeys.jpg");
}

#landscape,
#monkeys {

	h1{
		  text-transform: uppercase;
	  	font-family: 'Bitter', serif;
	  	letter-spacing: 0.06em;
	  	font-size: 120px;
	  	color: #FFF;
	  	opacity: 0.7;
	  	text-align: center;
      transform: translateZ(-2px);
	}
}

p {
	width: 70%;
	padding: 5%;
	margin: 0px auto;
	text-align: center;
	font-size: 20px;
	font-weight: 200;
	line-height: 1.4;
}
```

:sunny:編譯後-css
```css
html,
body {
  margin: 0;
  padding: 0;
  font-family: Roboto;
  color: #2e3738;
}

#landscape {
  height: 100vh;
  margin: 0px auto;
  width: 100%;
  perspective: 1px;
  transform: translateZ(-1px);
  overflow-x: hidden;
  overflow-y: auto;
  background: url("https://s3.amazonaws.com/codecademy-content/projects/sass/landscape.jpg") no-repeat center center fixed;
  background-size: cover;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
}

#monkeys {
  height: 100vh;
  margin: 0px auto;
  width: 100%;
  perspective: 1px;
  transform: translateZ(-1px);
  overflow-x: hidden;
  overflow-y: auto;
  background: url("https://s3.amazonaws.com/codecademy-content/projects/sass/monkeys.jpg") no-repeat center center fixed;
  background-size: cover;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
}

#landscape h1,
#monkeys h1 {
  text-transform: uppercase;
  font-family: 'Bitter', serif;
  letter-spacing: 0.06em;
  font-size: 120px;
  color: #FFF;
  opacity: 0.7;
  text-align: center;
  transform: translateZ(-2px);
}

p {
  width: 70%;
  padding: 5%;
  margin: 0px auto;
  text-align: center;
  font-size: 20px;
  font-weight: 200;
  line-height: 1.4;
}
```
:sunny:html
```
<head>
	<link rel="stylesheet" type="text/css" href="main.css">
</head>
<body>

<div id="landscape">
  <h1 class="title">Visit Myanmar</h1>
</div>

<p>
  Descriptions to come. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer consectetur, libero eget bibendum elementum, lorem orci rutrum justo, at fermentum neque felis ac ex. Phasellus suscipit dapibus ante, eu sodales risus sagittis ut. Phasellus eget augue purus. Sed eget auctor felis, egestas vestibulum augue. Aenean pharetra metus quis orci consequat dapibus. Integer aliquam aliquet ipsum ut pellentesque. Curabitur cursus, nibh ut vehicula maximus, eros libero pretium diam, eu luctus nisl mauris a augue. Nulla luctus in orci non vulputate. Suspendisse at tortor elit.
</p>

<div id="monkeys">
  <h1 class="title">Book my trip now</h1>
</div>

</body>

```
