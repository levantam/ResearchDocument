#### Xử lý bất đồng bộ với Promise

#### Call back function:

    let myFunction = (a, b, cbFunc) => {
        let result, error;
        if (typeof (a) != 'number' || typeof (b) != 'number') {
            error = 'All arguments must be number';
        } else {
            result = a + b;
        }
        cbFunc(error, result);
    }
    myFunction(2, '3', (error, result) => {
        if (error) {
            console.log(error);
        } else {
            console.log(`Result: ${result}`);
        }
    });

* cbFunction is a callback function, defined by user

#### PROMISE IN ES 6:

* Example 1:

  var aPromise = new Promise\(\(resolve, reject\) =&gt; {  
        reject\('this is data from resolve function'\);  
        resolve\('this is data from resolve function'\);  
    }\);  
    aPromise.then\(msg =&gt; console.log\(msg\), err =&gt; console.log\(`Error: ${err}`\)\);

* Create promise function:

      const myFunction = (a, b) => {
          return new Promise((resolve, reject) => {
              setTimeout(() => {
                  let err, result;
                  if (typeof (a) != 'number' || typeof (b) != 'number') {
                      reject('All argurement must be number');
                  } else {
                      result = a + b;
                      resolve(result);
                  }
              }, 3000);

          })

      }
      myFunction(10, '2').then(data => console.log(`RESULT: ${data}`), error => console.log(error));

* > A promise have 2 properties: PromiseStatus, PromiseValue
  >
  > * Status: Pending, resolved, rejected
  > * undefine, .....

### ALL AND RACE IN PROMISE METHOD

* #### All

```
const func1 = (a, b) => {
    return new Promise((resolve, reject) => {
        resolve('Success 1');
    })
}
const func2 = (a, b) => {
    return new Promise((resolve, reject) => {
        reject('Error 2');
    })
}
Promise.all([func1(2,2), func2(1, 10)]).then(res => console.log(res), error=> console.log(error));
```

* All promises are success =&gt; success, else, return Error

  * **Error of above example will be raised in function func2**

* #### RACE: 1 of promise list success =&gt; return success, else error

```
const func1 = (a, b) => {
    return new Promise((resolve, reject) => {
        resolve('Success 1');
    })
}
const func2 = (a, b) => {
    return new Promise((resolve, reject) => {
        reject('Error 2');
    })
}
Promise.all([func1(2,2), func2(1, 10)]).then(res => console.log(res), error=> console.log(error));
```

* Success function will be called in function func1

### Await / Async

* Phiên bản javascript mà node hỗ trợ chưa có async await =&gt; sử dụng babel cli

* Install babel cli

  ```
  npm install babel-cli --save-dev
  ```

* Install babel-preset-2015 to compile from babel code to javascript

```
npm install babel-preset-2015 --save-dev
```

* Then, we can use await /sync to implement asynchronous function

```
const addItem = (result) =>{
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(result);
        }, 5000);
    })
}
var addListItem = async () => {
    var result = await addItem(true);
    if(result == true){
        result = await addItem(false);
    }
    console.log(result);
}

addListItem();
//result = false
```

* Using try, catch and callback function to handle error:

      const addItem = (result) => {
          return new Promise((resolve, reject) => {
              setTimeout(() => {
                  reject(result);
              }, 5000);
          })
      }
      var addListItem = async (cbFunction) => {
          try {
              var result = await addItem(true);
              if (result == true) {
                  result = await addItem(false);
              }
              cbFunction(undefined, "tamle");
          } catch (error) {
              cbFunction(error + '');
          }
      }
      const cbFunction = (err, msg) => {
          if (err) {
              console.log(`ERROR: ${err}`);
          } else {
              console.log(`Result: ${msg}`);
          }
      }
      addListItem(cbFunction);

* 


