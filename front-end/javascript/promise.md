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

#### PROMISE IN ES6:

* Example 1:

    var aPromise = new Promise((resolve, reject) => {
        reject('this is data from resolve function');
        resolve('this is data from resolve function');
    });
    aPromise.then(msg => console.log(msg), err => console.log(`Error: ${err}`));

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

* 


