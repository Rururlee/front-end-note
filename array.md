#Array


:star:使用const宣告的變數無法重新定義。但是，使用const宣告的數組中的元素仍然是可變的。 表示我們可以更改const數組的內容，但不能重新分配新數組或不同的值。
```js
//將陣列第一個元素改成Mayo
let condiments = ['Ketchup', 'Mustard', 'Soy Sauce', 'Sriracha'];
condiments[0]='Mayo';
console.log(condiments);
//Log:['Mayo','Mustard','Soy Sauce','Sriracha']

condiments= ['Mayo'];//不用再寫let,即是重新分配變數
console.log(condiments);
//Log:['Mayo']

const utensils = ['Fork', 'Knife', 'Chopsticks', 'Spork'];
//若陣列項目太多，可用長度-1選取最後一個陣列
condiments[3]='Spoon';
//或寫成
//utensils[utensils.length-1]='Spoon';
console.log(utensils);
//Log:['Fork','Knife','Chopsticks','Spoon']
```
:star:Arrays and Functions<br>
function一個方法，對array執行動作
```js
const concept = ['arrays', 'can', 'be', 'mutated'];
function removeElement(newArr){
    newArr.pop();
};
removeElement(concept);//將concept代入function removeElement的參數
console.log(concept);
//Log: ['arrays','can','be']
```
:star:陣列中的陣列
```js
const numberClusters =[[1,2],[3,4],[5,6]];
const target = numberClusters[2][1];
//Log:6
```