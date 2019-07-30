#function函式基本使用



:penguin:範例一
```js
function test(message /*參數的名稱，自己決定*/){
      console.log(message);//此message只是個代號，真正的資料在呼叫的時候決定
    }
    test('hello' /*傳入函式的參數資料*/);//真正的資料->hello

    function add(n1,n2){
      // console.log(n1+n2);
      return n1+n2;
    }
    var result = add(3,4);
    console.log(result);

    var result_two = add(3,4)*add(10,20);
    console.log(result_two);
```
