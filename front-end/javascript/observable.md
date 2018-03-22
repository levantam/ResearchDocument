OBSERVABLE IN JAVASCRIPT

* Import:
  * Import **{Observable} from 'rxjs'**
  * Import **'rxjs/add/operator/map'**
* Example 1:

  * Html:

  ```
  <div class="images">
    <div *ngFor="let item of images" class="image">
        {{item.description}}
    </div>
  </div>
  ```

  * Component:

  ```
  import { Component, OnInit } from '@angular/core';
  import { Observable } from 'rxjs';
  import 'rxjs/add/operator/map';
  import { Http } from '@angular/http';

  @Component({
    selector: 'app-home',
    templateUrl: './home.component.html',
    styleUrls: ['./home.component.css']
  })
  export class HomeComponent implements OnInit {

    // tslint:disable-next-line:max-line-length
    apiUrl = 'https://api.unsplash.com/search/photos?page=1&query=office&client_id=b2d9e8f9f339e7ae6bbc820ca558c54a5765279103fa4518ba1139ecf2741828';
    images = [];
    constructor(private http: Http) { }

    ngOnInit() {
      this.getData().subscribe(data => { this.images = data; console.log(data); });
    }

    getData = (): Observable<User[]> => {
      return this.http.get(this.apiUrl).map(res => {
        const result = res.json().results.map(item => {
          const user = new User();
          user.id = item.id;
          user.created_at = item.created_at;
          user.updated_at = item.updated_at;
          user.width = item.width;
          user.height = item.height;
          user.color = item.color;
          user.description = item.description;
          return user;
        });
        return result;
      });
    }
  }
  class User {
    id: string;
    created_at: Date;
    updated_at: Date;
    width: number;
    height: number;
    color: string;
    description: string;
  }
  ```

* Example 2:
  * Return Observable&lt;Object&gt; and use async to wait all api success
  * Html:

  ```
  <div class="images">
    <div *ngFor="let item of images2| async" class="image">
        {{item.description}}
    </div>
  </div>
  ```

  * Component:

  ```
  import { Component, OnInit } from '@angular/core';
  import { Observable } from 'rxjs';
  import 'rxjs/add/operator/map';
  import { Http } from '@angular/http';

  @Component({
    selector: 'app-home',
    templateUrl: './home.component.html',
    styleUrls: ['./home.component.css']
  })
  export class HomeComponent implements OnInit {

    // tslint:disable-next-line:max-line-length
    apiUrl = 'https://api.unsplash.com/search/photos?page=1&query=office&client_id=b2d9e8f9f339e7ae6bbc820ca558c54a5765279103fa4518ba1139ecf2741828';
    images = [];
    images2: Observable<User[]>;
    constructor(private http: Http) { }

    ngOnInit() {
      this.images2 =  this.getData(); // .subscribe(data => { this.images = data; console.log(data); });
    }

    getData = (): Observable<User[]> => {
      return this.http.get(this.apiUrl).map(res => {
        const result = res.json().results.map(item => {
          const user = new User();
          user.id = item.id;
          user.created_at = item.created_at;
          user.updated_at = item.updated_at;
          user.width = item.width;
          user.height = item.height;
          user.color = item.color;
          user.description = item.description;
          return user;
        });
        return result;
      });
    }
  }
  class User {
    id: string;
    created_at: Date;
    updated_at: Date;
    width: number;
    height: number;
    color: string;
    description: string;
  }

  ```



