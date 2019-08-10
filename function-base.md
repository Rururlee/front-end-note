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
    console.log(result_two); //print 210
```

:penguin:範例二:設定一個範圍的加總
```js
function getSum(range){
      var sum=0;
      var n=1;
      while(n<=range){ 
        sum+=n; 
        n++ 
      }
      return sum;//回傳值
    };

    var result_three = getSum(50)*getSum(100);//需有回傳值，結果sum透過回傳到這程式
    console.log(result_three); //print 6438750
```