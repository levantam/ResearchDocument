# Router

* Using Angular CLI to create routers for application
  > --flat: put file in src/app folder  
  > --module=app: tells the CLI to register it in the imports array of the AppModule

```
ng g module app-routing --flat --module=app
```

* In file app-routing.module.ts

```
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './home/home.component';
import { AboutComponent } from './about/about.component';

//All routers of application
const routes: Routes = [
  { path: 'home', component: HomeComponent },
  { path: 'about', component: AboutComponent },
  { path: '', redirectTo: '/home', pathMatch: 'full' }
];

@NgModule({
  imports: [
   .....
    RouterModule.forRoot(routes)
  ],
  exports: [RouterModule],
  .......
})
export class AppRoutingModule { }
```

* Template:
  ```
  <nav>
      <a routerLink="/home" routerLinkActive="active">Home</a>
      <a routerLink="/about" routerLinkActive="active">About</a>
    </nav>
    <router-outlet></router-outlet>
  ```
* In file app.module.ts

```
......
import { HomeComponent } from './home/home.component';
import { AboutComponent } from './about/about.component';
import { AppRoutingModule } from './app-routing.module';


@NgModule({
  declarations: [
    ......
    HomeComponent,
    AboutComponent
  ],
  imports: [
   ......
    AppRoutingModule
  ],
  ......
})
export class AppModule { }
```

## Navigate to other routes

* Inject **ActivatedRoute **in constructor
* this.route.navigate\(\[param1\], queryparam, fragment\);
  * param1: 'link', 'id','sdfdsf',.... For example: Link to server/1/edit =&gt; \['server', 1, ;'edit'\]
  * query params: ?name=abc =&gt; queryparams: {name: 'abc'}
  * fragment: \#loading =&gt; fragment:'loading'
  * 

### Nested Route





