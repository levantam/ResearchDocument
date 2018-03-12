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





