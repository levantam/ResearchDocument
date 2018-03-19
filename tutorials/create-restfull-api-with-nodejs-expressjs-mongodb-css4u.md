* Create new NodeJS project with ExpressJS

  * Install  express-generator first
  * Create new application:

  ```
  express --view=ejs myCSS
  ```

  * cd to myCSS directory and install all packages

  ```
  cd myCSS
  npm install
  ```

* Install extra packages:

  * nodemon

    * Change start script to use node monitor

    ```
    "scripts": {
        "start": "nodemon ./bin/www"
      },
    ```

* Run

```
npm run start
```

Navigate to [http://localhost:3000/](http://localhost:3000/) to view website

### Create schema for all entities:

* We will create 4 schemas:

  * Category
  * Framework
  * Item
  * Platform

  ![](/assets/css-schemas.png)

* Example code for Item schema:

```
var mongoose = require('mongoose');

var itemSchema = mongoose.Schema({
    name: {
        type: string, 
        require: true
    },
    image_url:{
        type: string,
        require: true
    },
    description: {
        type: string
    },
    category: {
        type: mongoose.Types.ObjectId
    },
    install: {
        type: string
    }/*,
    properties: {
        type: string[]
    },
    events: {
        type: string[]
    }
    */
});
module.exports = mongoose.model('Item', itemSchema);
```

* Create new database

  * Using cmd, type: mongod to start dbserver
  * Open MongoDB compass community to create new data, named css4u
  * Create user for login:

    * Open another cmd
    * Type: mongo
    * Type: use css4u
    * Type:

    ```
    db.createUser( { user: "admin",pwd: "tamle",roles: [ "readWrite", "dbOwner", "dbAdmin"]} )
    ```

* Edit App.js to connect to mongo db

```
var mongoose = require('mongoose');

var app = express();
let options = {
  db: {
    native_parser: true
  },
  server: {
    poolSize: 5
  },
  user: "tamle",
  pass: "tamle"
};
mongoose.Promise = global.Promise;
mongoose.connect('mongodb://localhost:27017/css4u', options).then(
  () => {
    console.log('Connect MongoDB successfully')
  },
  err => {
    console.log('Connect MongoDB failed: ' + err)
  }
);
```



