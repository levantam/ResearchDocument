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





