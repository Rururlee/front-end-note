#Iterators疊代器
####loop的概念

:star:常用方法
```
.forEach() --- 每個元素執行相同代碼
.map()
.filter()
.findIndex()
.some()
```
:star:.forEach() 
```js
const fruits = ['mango', 'papaya', 'pineapple', 'apple'];
fruits.forEach(fruitItem=>console.log('I want to eat a '+fruitItem));
//log 
//I want to eat a mango
//I want to eat a papaya
//I want to eat a pineapple
//I want to eat a apple
```
:star:.forEach() 
```js
const animals = ['Hen', 'elephant', 'llama', 'leopard', 'ostrich', 'Whale', 'octopus', 'rabbit', 'lion', 'dog'];

const secretMessage = animals.map(animal=>{return animal[0]})
// Create the secretMessage array below


console.log(secretMessage.join(''));
```
找出animals陣列裡每個字串第一個字為's'的字串<br>
:small_orange_diamond:str function將每個代入的animals又視為個別的陣列<br>
:small_orange_diamond:所以可使用str[i]陣列的方法<br>
:small_orange_diamond:或使用charAt(0)方法指定字串
```js
const animals = ['hippo', 'tiger', 'lion', 'seal', 'cheetah', 'elephant'];
const startsWithS = animals.findIndex(str=>{return str[0]=='s'});
//const startsWithS = animals.findIndex(str=>{return str.charAt(0)==='s'});
console.log(animals[startsWithS])
//print seal
```
