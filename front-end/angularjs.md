# HTTP REQUEST - SERVICE IN ANGULARJS



* Create new angular js application
* Create service by angular CLI

```
ng g service user 
```

* File **user-service.ts** will be created 
* Import module into **app.module.ts IMPORTANT**
  ```
  ....
  import { HttpModule } from '@angular/http';
  import { UserService } from './user.service';

  @NgModule({
    declarations: [
      .....
    ],
    imports: [
      ...
      HttpModule
    ],
    providers: [UserService],
    .....
  })
  ```

* Use Fake json-server in this [Fake API Server With Json Server](/front-end/fake-api-server-with-json-server.md "link") to create server

* In file **user-service.ts**
  * Import 

  ```
  import { Http, Response } from '@angular/http';
  ```

  * Inject http into constructor

  ```
  constructor(private http: Http) { }
  ```

  * Create sample function

  ```
  getAllUsers() {
      return this.http.get(this.url).map((response: Response) => response.json());
    }
  ```

* Call Service in component
  * Inject service

  ```
  constructor(private userService: UserService) {
    }
  ```

  * Call API

  ```
  ngOnInit(): void {
      // this.users = this.userService.getUser();
      this.userService.getAllUsers().subscribe(responseUsers => this.users = responseUsers);
    }
  ```





