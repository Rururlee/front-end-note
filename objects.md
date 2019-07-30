#Objects

<!-- - [ ] checklist
- [x] checklist -->

:penguin:**初階物件**<br>
* 範例一
```js
    //建立空白物件
    var point = new Object();
    //建立物件的成員
    point.x = 3;
    point.y = 4;
    point.getPosition = function(){ //將一個函式代入getPosition
      console.log(this.x + ',' + this.y); //this指向point   
    };
    point.getPosition(); //print 3,4
```

* 範例二
```js
    //設計一個遊戲角色物件
    var player2= new Object();
    player2.name = 'sasuke';
    player2.hp = 100;
    player2.fight = function(){ 
      this.hp=this.hp-2;
    };
    player2.rest = function(){
      this.hp++;
    };
    player2.report = function(){
      console.log(this.name + ':' + this.hp);
    };
    player2.fight(); //打一架扣兩滴
    player2.rest(); //休息回一滴
    player2.report(); //回報角色血量
    //print sasuke:99
```

* 範例三
```js
    //建構物件的函式
    function Player(name,hp){ //參數對到this.name(hp)後的name、hp
      //this代表新建的空白物件
      this.name = name;
      this.hp = hp;
      this.fight = function(){
        this.hp-=2;
      };
      this.rest = function(){
        this.hp++;
      };
      this.report = function(){
        console.log(this.name + ':' + this.hp);
      }
    }//自動回傳，不用寫return

    //呼叫建構式(建構式會建立物件並回傳，存放在變數player_1)
    var player_1 = new Player('john',100);
    player_1.fight();
    player_1.report(); //print john:98
    var player_2 = new Player('mary',80);
    player_2.rest();    
    player_2.report(); //print mary:81 
```

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