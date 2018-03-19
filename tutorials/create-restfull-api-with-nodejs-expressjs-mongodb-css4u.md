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



