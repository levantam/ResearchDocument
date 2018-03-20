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



