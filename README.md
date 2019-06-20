#js note



:fire:String Interpolation 字串插值(模板值)用法
```js
console.log(`My name is ${myName}. My favorite city is ${myCity}.`)
```
:fire:箭頭函式arrow function<br>
(1) 沒用花括號({})時，代表會自動加return，也只能在一行的語句的時候使用<br>
(2) 使用花括號({})則是可以加入多行的語句，不過return不會自動加

```js
//ex.1
function funA(){
  console.log('hello world!');
}
funA();
//es6後▼▼▼
const funA = () => {
  console.log('hello world!'); 
}
funA();

//ex.2
const funA = function (x) { return x + 1 }
//相當於
const funA = (x) => x + 1

//ex.3
const funA = x => x + 1
const funB = x => { x + 1 }

funcA(1) //2
funcB(1) //undefined
```
:fire:各種方法
```js
pop() //刪掉陣列末端元素
push() //在陣列末端增加元素
shift() //刪掉陣列首端元素
unshift() //在陣列首端增加元素
indexOf() //取出元素在陣列的索引值，若沒放元素，return -1
every() //每個元素都為真才回傳
some() //只要有一個元素為真就回傳

reduce() //最後只會傳回一個元素
//ex
var numbers = [65, 44, 12, 4];
function getSum(total, num) {
  return total + num;
}
//total-->累加器，num-->目前所迭代處理中的元素

```
:fire:運算子<br>
(1) && = 邏輯比較<br>
(2) & = 2進制位元運算(乘法概念)<br>
(3) || = 邏輯比較<br>
(4) | = 2進制位元運算(加法概念)
```js
console.log(1 && -2) //-2
console.log(1 && 0) //0
console.log(3 & 2) //2 11*10=10=2(上下乘)
console.log(1 | 2) //3 01+10=11=3
console.log(0 || 2) //2
```
<br>
<br>
<br>
```javascript
const satellite = 'The Moon';
const galaxy = 'The Milky Way';
let stars = 'North Star';

const callMyNightSky = () => {
  stars = 'Sirius';
	return 'Night Sky: ' + satellite + ', ' + stars + ', ' + galaxy;
};

console.log(stars);
console.log(callMyNightSky());
console.log(stars);
```

```javascript
const logVisibleLightWaves = () => {
  let lightWaves = 'Moonlight';
	let region = 'The Arctic';
  // Add if statement here:
  if (region==='The Arctic'){
    let lightWaves='Northern Lights';
    console.log(lightWaves);
  }
  console.log(lightWaves);
};

logVisibleLightWaves();
```

```javascript
const vacationSpots = ['Bali', 'Paris', 'Tulum'];

// Write your code below
for(let i =0;i<vacationSpots.length;i++){
  console.log('I would love to visit '+ vacationSpots[i]);
}
```

``` javascript
// Write your code below
let bobsFollowers=['ruru','lynn','dean','lisa'];
let tinasFollowers=['ruru','lynn','mary'];
let mutualFollowers =[];
for(let i=0;i<bobsFollowers.length;i++){
  for(let j=0;j<tinasFollowers.length;j++){
    if (bobsFollowers[i]===tinasFollowers[j]){
      mutualFollowers.push(bobsFollowers[i]);
    }    
  }
};
```

```javascript
let countString = '';
let i = 0;

do {
  countString = countString + i;
  i++;
} while (i < 5);

console.log(countString);
```

```javascript
const rapperArray = ["Lil' Kim", "Jay-Z", "Notorious B.I.G.", "Tupac"];

// Write your code below

for(let i=0;i<rapperArray.length;i++){
  console.log(rapperArray[i]);
  if(rapperArray[i]==='Notorious B.I.G.')
  break;
}
console.log("And if you don't know, now you know.")
```
```javascript
const checkThatTwoPlusTwoEqualsFourAMillionTimes = () => {
  for(let i = 1; i <= 1000000; i++) {
    if ( (2 + 2) != 4) {
      console.log('Something has gone very wrong :( ');
    }
  }
}

// Write your code below
let is2p2=checkThatTwoPlusTwoEqualsFourAMillionTimes;
is2p2();
console.log(is2p2.name)
```

```
gitbook serve跳掉解決方法

1.gitbook serve
2.delete _book folder once
3.now each time you change the md file, the server will stop and start over again and again
```