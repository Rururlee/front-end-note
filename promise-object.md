#Constructing a Promise Object

:sunny:Promise物件<br>
(1)物件需new出來
```js
const inventory = {
  sunglasses: 1900,
  pants: 1088,
  bags: 1344
};

// Write your code below:

const myExecutor = (resolve,reject) => {
  if (inventory.sunglasses>0) {
      resolve('Sunglasses order processed.');
  } else {
      reject('That item is sold out.'); 
  }
}

const orderSunglasses = ()  =>{
  return new Promise(myExecutor);
} //物件需new出來

const orderPromise = orderSunglasses();

console.log(orderPromise);

//Log:Promise{'Sunglasses order processed.'}

```
:sunny:Jquery回傳資料<br>
(1)then()是其中一種callback方法，收到資料接下來做什麼動作<br>
(2)promise很多callback方法,ex:then()、fail()等
```js
$.get("https://api.wakool.net").then(function(response){
  data = response; //我們不用處理資料，只是要從遠端判斷回傳資料是否符合。所以不用宣告data
  console.log(data);//這可設定回傳成功的model
})

//Log:{errno: 0, error: null, data: "1.0.0"}

$.get("https://api.wakool.net").then(function(response){
  data = response;
  console.log(data);
  return '1';
}).then(function(response){
  console.log(response);
});
//Log:{errno: 0, error: null, data: "1.0.0"}
///1  (return 1的部分)
```
:sunny:then函數<br>
then的函數是選用的
```js
doSomething().then(function(result) {
  return doSomethingElse(result);
})
.then(function(newResult) {
  return doThirdThing(newResult);
})
.then(function(finalResult) {
  console.log('Got the final result: ' + finalResult);
})
.catch(failureCallback);
//catch(failureCallback)是then(null, failureCallback)

```
以上用箭頭函數寫法為
```js
doSomething()
.then(result => doSomethingElse(result))
.then(newResult => doThirdThing(newResult))
.then(finalResult => {
  console.log(`Got the final result: ${finalResult}`);
})
.catch(failureCallback);
```
:sunny:使用catch()函數
```js
const {checkInventory} = require('./library.js');

const order = [['sunglasses', 1], ['bags', 2]];

const handleSuccess = (resolvedValue) => {
  console.log(resolvedValue);
};

const handleFailure = (rejectReason) => {
  console.log(rejectReason);
};

//---------------------------------//

checkInventory(order)
.then((resolvedValue) => {
    console.log(resolvedValue);                       
})
.catch((rejectReason) => {
    console.log(rejectReason);                       
});

//將上方code簡化
checkInventory(order)
.then(handleSuccess)
.catch(handleFailure);
```