# Getting started

#### Install

* NodeJS
* Angular CLI

```
npm install -g @angular/cli
```

#### Create new application and Run

```
ng new projectName
```

* Navigate to project folder

```
cd projectName
```

* Install packages

```
npm install
```

* Run project

```
npm serve
```

#### Basis knowledge

> DATA BINDING
>
> * **Array**
>   * Use \*ngFor="let user of users"
> * **Class name**
>   * \[class.nameOfClass\] = "trueOrOperation"
> * **Function**
>   * \(click\)="selectedUser\(user\)"
> * **Data model**
>   * \[\(ngModel\)\] = "modelABC.name"
> * Binding data from parent to children
>   * &lt;user-detail \[seletedUser\] = "selectedUser" /&gt;

* _Set data models for a component:_

```
export class AppComponent {
  title = 'app';
  user: User = {
    id: 1, name: 'Tam le'
  };
}
```

* Define functions:

```
onSelectUser(selectedUser: User): void {
    this.selectedUser = selectedUser;
}
```

* Call function on presentation

```
<li *ngFor="let user of users">
    (click)="onSelectUser(user)"
  >
```

* Binding data from parent to children

```
<user-detail [selectedUser] ="selectedUser" />
```

---

## Service

* Create new service

```
ng g service service-name
```

* Create new function called: getUsers\(\) returns list of user
* Inject above Service to Component via constructor method:

```
constructor(private userService: UserService) {
  }
```

* Add Provider into app.module.ts \[IMPORTANT\]

```
providers: [UserService],
```

* Call service in component

```
ngOnInit(): void {
    this.userService.getUser();
  }
```

---

# Call parent's function from child components

* Parent 
  * Component 

  ```
  onSelectUser(user: GithubUser) {
      this.selectedUser = user;
    }
  ```

  * View

  ```
  <app-user-list  (onSelectUser)="onSelectUser($event)" ></app-user-list>
  ```

* Children
  * Component

  ```
  @Output() onSelectUser = new EventEmitter<GithubUser>();

  handleSelectUser(user: GithubUser): void {
      this.onSelectUser.emit(user);
    }
  ```

  * View

```
<a ...(click)="handleSelectUser(user)">
          ....
</a>
```



