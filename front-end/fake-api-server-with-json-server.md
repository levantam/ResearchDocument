# JSON Server

> Get a full fake REST API with zero coding in less than 30 seconds \(seriously\)

* Install

```
npm install -g json-server
```

* Create file json contains all information of users in fake system \(in plural form\): **users.json**

```
{
    users: [
        {id: 1, name: 'tamle', age=20},
        .....
    ]
}
```

* Run JsonServer: command line is the same to json file

```
json-server --watch users.json --port 1111
```

* All method will be supported:
  * **POST**
  * **PUT**
  * **GET**
  * **DELETE**



