# NGRX - STATE MANAGE WITH REDUX PATTERN IN ANGULAR JS APPLICATION

* Create new angular application with angular CLI
* Install dependency packages:
  * npm install **@ngrx/store @ngrx/effects** **@ngrx/store/devtools** --save
* ## Model:

  * Create folder **models **and file: **user.model.ts**
  * ```
    export interface User {
        login: string;
        id: string;
    }
    ```
* ## ACTIONS:

  * Create **actions **folder, and file **users.action.ts**
  * Actions: **LoadUser, LoadUserSuccess** \(callback function\), **DeleteUser, EditUser, AddUser**

  * ```
    import { User } from '../models/user.model';

    export const LOAD_USER = 'LOAD_USER';
    export const LOAD_USER_SUCCESS = '';
    export const ADD_USER = 'ADD_USER';
    export const EDIT_USER = 'EDIT_USER';
    export const DELETE_USER = 'DELETE_USER';

    export class LoadUser {
        readonly type = LOAD_USER;
        constructor() { }
    }
    export class LoadUserSuccess {
        readonly type = LOAD_USER_SUCCESS;
        constructor(public payload: User[]) { }
    }
    export class AddUser {
        readonly type = ADD_USER;
        constructor(public payload: User) { }
    }
    export class DeleteUser {
        readonly type = DELETE_USER;
        constructor(public payload: number) { }
    }
    export class EditUser {
        readonly type = EDIT_USER;
        constructor(public index: number, public payload: User) { }
    }
    export type Action = LoadUser | LoadUserSuccess | AddUser | DeleteUser | EditUser;
    ```
* ## Reducer:

  * Create **reducers **folder and file: **users.reducer.ts**
  * ```
    import * as UserActions from '../actions/users.actions';
    import { User } from '../models/user.model';

    export function UserReducer(state: User[] = [], action: UserActions.Action) {
        switch (action.type) {
            case UserActions.LOAD_USER_SUCCESS:
                return action.payload;
            case UserActions.ADD_USER:
                return [...state, action.payload];
            case UserActions.DELETE_USER:
                state.splice(action.payload);
                return state;
            case UserActions.EDIT_USER:
                state[action.index] = action.payload;
                return state;
            default:
                return state;
        }
    }
    ```
* ## Effects:

  * To dispatch action with other actions such as: services,...

  * Create folder **effects **and file: **users.effect.ts**

  * \`\`\`  
    import { Injectable } from '@angular/core';  
    import {Actions, Effect} from '@ngrx/effects';  
    import 'rxjs/add/operator/switchMap';  
    import 'rxjs/add/operator/map';

    import \* as UserActions from '../actions/users.actions';  
    import { UserService } from '../services/user.service';  
    import { User } from '../models/user.model';  
    import { Observable } from 'rxjs/Observable';

    @Injectable\(\)  
    export class UserEffects {  
        constructor\(  
            private actions$: Actions,  
            private userService: UserService  
        \) {}

    ```
    @Effect() LoadUser$ = this.actions$.ofType(UserActions.LOAD_USER)
        .switchMap((action) => this.userService.getUser().map((users: User[]) => new UserActions.LoadUserSuccess(users)));
    ```

    }

    \`\`\`
* Service will return **Observable&lt;User\[\]&gt; object**

  * ```
    getUser() {
        const url = 'https://api.github.com/users?since=1&access_token=a87b8ff614b96bd43edb26f9ba056abf89e6decc';
        return this.http.get(url).map(res => res.json());
      }
    ```

* ## App State

  * Contains all state of application:

  * Create a file: **app.state.ts**

    * ```
      import { User } from './models/user.model';

      export interface AppState {
          readonly users: User[];
      }
      ```
* Define **StoreModule **and **EffectModule **in **app.module.ts**

  * ```
    const store = {
      users: UserReducer
    };

    @NgModule({
      ........
      imports: [
        ....
        StoreModule.forRoot(store),
        EffectsModule.forRoot([UserEffects])
      ],
      ......
    })
    ```

* ## Use in component

  * ```
    export class UserComponent implements OnInit {
      users: Observable<User[]>;

    //Inject  store
      constructor(private store: Store<AppState>) {
        this.users = this.store.select('users');
        this.store.dispatch(new userActions.LoadUser()); // dispatch load user
      }

      ngOnInit() {
      }

    }

    ```





