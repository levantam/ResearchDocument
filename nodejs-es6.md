# Research - NodeJS ES6

* Create new application

```
npm init
```

* Create new file **index.js**

```
console.log('this is command');
=> run:
node index.js
```

#### Module in NodeJS:

* VD: tính chu vi và diện tích của hình chữ nhật
* Tạo file **retangle.js** trong thư mục **Shape**
* ```
  // arrow function
  exports.area = (width, height) => {
      return width * height;
  }
  exports.circumference = (width, height) => 2 * (width + height);
  ```
* Import vào index.js để sử dụng

  const rectangleFunction = require\('./Shape/Retangle'\);

  let width = 10;  
    let height = 15;  
    console.log\(`Chu vi hinh chu nhat (width: ${width}, height: ${height}) = ${rectangleFunction.circumference(width, height)}`\);  
    console.log\(`Dien tich hinh chu nhat (width: ${width}, height: ${height}) = ${rectangleFunction.area(width, height)}`\);

---

#### Module Http

* Import 

```
let http = require('http');
```

* Create simple server

```
let http = require('http');
const port = 3001;
// Create server
const server = http.createServer((request, response) => {
    response.write('This is response from server');
    response.end();
}).listen(port);
```

* Server will return text: _**This is response from server**'_ when navigating to **localhost:3001**

---

#### Nodejs with Babel

* Is a compiler of nodejs, for compiling node js application
* Install:

  * ```
    npm install babel-cli --save-dev
    ```

* Install plugin for babel

  * ```
    npm install --save-dev babel-preset-es2015 babel-preset-stage-2
    ```

```
Add to package.js scripts:
"start": "babel-node http\\index.js --presets es2015,stage-2"
```

* Install nodemon = Node Monitor
  * ```
    npm install --save-dev nodemon
    ```

=&gt; Monit updated file and refresh application

```
Add to package.json scripts:
"start": "nodemon index.js --exec babel-node --presets es2015,stage-2"
```

* Create build script with babel

```
"build": "babel http -d dist --preset es2005,stage-2"
```

* _Description:_
  * _babel: babel command \[required\]_
  * _http: directory name of source code will be built_
  * _-d: directory_
  * _dist: directory name_

Beside, you can create a file to define all settings for babel:

* Create file **.babelrc**
* Settings:
  ```
  {
      "preset": ["es2015", "stage-2"],
      "plugin": []
  }
  ```
* Edit scripts: delete all text in scripts: --preset es2015,stage-2

```
"start": "nodemon index.js --exec babel-node"
```

---

#### Working with file in NodeJS

* Require\('fs'\); //fs = file system

* Create new file example: index.js

```
//import library
const fs = require('fs');
//create new file with name= myFile.txt
exports.createNewFile = (fileName) => {
    const file = fs.openSync(fileName, 'w');
}
```

* Write file
* Open file

---

#### Event trong nodejs

* Require: events 
* Import

```
const EventEmitter = require('events');
```

```

```

---

..... backup again



---

MongoDB

* Install mongoDB via .msi file
* Create directory: C:/data/db
* Add MongoDB to environment variables \(C:\Program Files\MongoDB\Server\3.6\bin\)
* Run **mongod **to run server
* Open MongoDB compass to check Is mongo running?

* Or run **mongo** on command line to check
  * 



