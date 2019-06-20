#Objects

:penguin:const變數，值也會改變(因為不是重新宣告)<br>
:penguin:底線命名的變數不要改變值
```js
const spaceship = {
  homePlanet : 'Earth',
  color : 'silver'
};

let paintIt = obj => {
  obj.color = 'glorious gold'
};//這是做個動作，不是重新宣告const值

paintIt(spaceship);

spaceship.color // Returns 'glorious gold'
```

```js
let spaceship = {
  'Fuel Type' : 'Turbo Fuel',
  homePlanet : 'Earth',
};

// Write your code below
let greenEnergy = obj => {
   obj['Fuel Type']='avocado oil';
} //只是個動作

let remotelyDisable = obj =>{
    obj.disabled=true;
}

greenEnergy(spaceship); //執行動作
remotelyDisable(spaceship); //執行動作
console.log(spaceship);
```

:blossom:Arrow Functions and this 箭頭函式與this
```js
const goat = {
  dietType: 'herbivore',
  makeSound() {
    console.log('baaa'); 
  },//此方法函式若有this是指向最外層的goat
  diet: () => { 
    console.log(this.dietType);
  }
};//箭頭函式裡的this指向本身function diet

goat.diet(); // Prints undefined
//diet裡沒有dietType，所以print沒有值
```

:blossom:Getters<br>
-- typeof輸出顯示方式是字串，所以條件設字串'number'<br>
```js
const robot = {
  _model: '1E78V2',
  _energyLevel: 100,
  get energyLevel(){
    if(typeof this._energyLevel === 'number')
    {
      return `My current energy level is ${this._energyLevel}`;
    }else
    {
      return `System malfunction: cannot retrieve energy level`;
    } 
  }
};
console.log(robot.energyLevel)
//pring My current energy level is 100
```
:blossom:getters<br>
:blossom:get和沒get function的區別
```js
let dogs = {
  _bark : 'Woo',
  get bark(){//取值
    return this._bark;
  },
  bark() {//執行
    return this._bark;
  }
}

console.log(dogs.bark);//取得值，知道狗的叫聲
dogs.bark();//執行，汪汪叫
```
```js
//getters範例
const person = {
  _firstName: 'John',
  _lastName: 'Doe',
  get fullName() {
   console.log(`${this._firstName} ${this._lastName}`);
  }
};
person.fullName; //Log:John Doe
```
:blossom:setters<br>
:blossom:Java的概念:有些值會設定外部不能取值(方便debug或防止覆蓋變數等...比較好維護原因)，就必須用get和set方式去取值兼修改
```js
const person = {
  _age: 37,
  set age(newAge){
    if (typeof newAge === 'number'){
      this._age = newAge;
    } else {
      console.log('You must assign a number to age');
    }
  }
};
person.age = 40;
console.log(person._age); // Logs: 40

person.age = '40'; 
console.log(person._age);// Logs: You must assign a number to age
```
```js
function Field(val){
this.value = val;
}
Field.prototype = {
get value(){
return this._value;
},
set value(val){
this._value = val;
}
};
```
:blossom:Factory Functions
```js
const robotFactory = (model,mobile) => {
  return {
    model: model,
    mobile: mobile,
    beep(){
      console.log('Beep Boop');
    }
  }
};

const tinCan = robotFactory('P-500',true);

tinCan.beep();
// Logs: Beep Boop
```
:blossom:Property Value Shorthand
```js
const monsterFactory = (name, age) => {
  return { 
    name: name,
    age: age
  }
};

//key和value一樣的話可只寫一個
const monsterFactory = (name, age) => {
  return { 
    name,
    age 
  }
};
```
:blossom:Destructured Assignment結構賦值
```js
const robot = {
  model: '1E78V2',
  energyLevel: 100,
  functionality: {
    beep() {
      console.log('Beep Boop');
    },
    fireLaser() {
      console.log('Pew Pew');
    },
  }
};

//原本寫法const functionality=robot.functionality
const {functionality}=robot; 
console.log(functionality);
functionality.beep();
//Log:{ beep: [Function: beep], fireLaser: [Function: fireLaser] }
//Beep Boop
```
:blossom:Built-in Object Methods
<br>
(1)Object.keys():取得物件的鍵值(key)，組成陣列後回傳
```js
const robot = {
  model: 'SAL-1000',
  mobile: true,
  sentient: false,
  armor: 'Steel-plated',
  energyLevel: 75
};
// What is missing in the following method call?
const robotKeys = Object.keys(robot);
console.log(robotKeys);
//Log:['model','mobile','sentient', 'armor','energyLevel']
```
(2)Object.entries():返回物件的key與value值
```js
// Declare robotEntries below this line:
const robotEntries = Object.entries(robot);
console.log(robotEntries);
/*Log:[[ 'model', 'SAL-1000'],
  ['mobile',true],
  ['sentient',false],
  ['armor','Steel-plated'],
  ['energyLevel',75]]
*/
```
(3)Object.assign():新增屬性返回原本的物件
```js
// Declare newRobot below this line:
const newRobot = Object.assign({laserBlaster: true, voiceRecognition: true},robot);
console.log(newRobot);
/*Log:{laserBlaster:true,
  voiceRecognition:true,
  model:'SAL-1000',
  mobile:true,
  sentient:false,
  armor:'Steel-plated',
  energyLevel: 75 }*/
```