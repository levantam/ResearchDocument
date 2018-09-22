GITHUBER

Description: get data from github and show all users, detail users

Steps:

* Create react application with typescript

  **create-react-app githuber --scripts-version=react-scripts-ts**

* Install

  * **npm install --save-dev react-router-dom @types/react-router-dom** =&gt; create all routers for project, such as: Home, About, Contact,...

  * **npm install --save redux @types/redux**

  * **npm install --save react-redux @types/react-redux**

* Create template for website, menu

* Create reducers:

  * Create **users-reducer.tsx**, export array users

  * create index.tsx,

    * Import all reducers into index file

    * import combineReducers from redux

      const allReducers = combineReducers\({

      users: UserReducer

      }\);

      export default allReducers;

    =&gt; In file index.tsx, import reducers/index file: import {allReducers} from './reducers';

    const store = createStore\(allReducers\);

* Create Provider

  * In file index.tsx \(root directory\)

    * Import Provider

    * render:

      &lt;Provider store={store}&gt;

      ```
        &lt;App /&gt;
      ```

      &lt;/Provider&gt;

* Create Container

  * Like a component

  * Create file user-list.tsx

    * Class UserList

    * Create function

      function mapStateToProps\(state: any\) {

      ```
        return {

            users: state.users

        }
      ```

      }

    * import {connect} from 'react-redux'

      let UserContainer = connect\(mapStateToProps\)\(UserList\);

      export default UserContainer;

  * Import this container \(UserContainer\) in to page you want to mount

* Actions

  * create file action-types.tsx

    export const SELECT\_USER = "SELECT\_USER";

  * create index.tsx

    * import action-types

    * define a action

      export const selectUser = \(user: any\) =&gt; {

      ```
        console.log\("User click action"\);

        return {

            type: SELECT\_USER,

            payload: user

        }
      ```

      };

  * In container \(user-list\)

    * import

      import { bindActionCreators } from "redux";

      import { selectUser } from "../actions";

    * Create function

      function mapDispatchToProps\(dispatch: any\){

      ```
        return bindActionCreators\({selectUser: selectUser}, dispatch\);
      ```

      }

    * Add more code

      let UserContainer = connect\(mapStateToProps, mapDispatchToProps\)\(UserList\);

      =&gt; For now, you can call action via props: this.props.selectUser\(user\);



