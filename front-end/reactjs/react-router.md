# REACT-ROUTER

### SETUP

#### Install 

```
npm install react-router-dom @types/react-router-dom
```

#### Create react application with create-react-app command

#### Set up routers in your application

* In App.tsx

```
import { BrowserRouter, Link, Route } from 'react-router-dom';
```

* Menu links

```
<ul>
  <li><Link to="/">Home Page</Link></li>
  <li><Link to="/about">About</Link></li>
  <li><Link to="/blog">Blog</Link></li>
</ul>
```

* Set Routes for applications

```
<Route path="/" component={Home} exact={true} />
<Route path="/About" component={About} />
<Route path="/Blog" component={Blog} />
```

* > **IMPORTANT: ALL BODY CONTENT WILL BE WRAPPED WITH &lt;BrowserRouter&gt; tag**

---

### PARAMETERS IN A ROUTE

#### Define parameter in a route

    <Route path={`${this.props.match.path}/:id`} component={BlogDetail} />

or

```
<Route path="/Blog/:id" component={BlogDetail} />
```

* > You have to define paramter **id **if you want to get its data in component **BlogDetail **

#### Get data from parameters

* All data of a page will be stored under **this.props.match** object

```
console.log(this.props.match.params.id);
```

#### Limit param data 

* Use regular expressions, for example below, only 2 values can be acepted: asc and desc

```
{/*
         It's possible to use regular expressions to control what param values should be matched.
            * "/order/asc"  - matched
            * "/order/desc" - matched
            * "/order/foo"  - not matched
      */}
      <Route
        path="/order/:direction(asc|desc)"
        component={ComponentWithRegex}
      />
```

---

### REDIRECT PAGE:

#### Import library

```
import { Redirect } from 'react-router-dom';
```

Redirect by return in render

```
constructor(props: any) {
        super(props);
        this.state = {
            redirect: false
        };
    }

    handleLogin = () => {
        this.setState({redirect: true});
    }
    render() {
        // tslint:disable-next-line:triple-equals
        if (this.state.redirect == true) { return <Redirect to="/Home" />; }
        return (
            <section>
                <h2>REDIRECT IN REACT-ROUTER</h2>
                <button className="btn btn-primary" onClick={this.handleLogin}>Login</button>
            </section>
        );
    }
```

* Page will be redirected to Home when clicking Login button



---

#### SHOW PROMP WITH REACT-ROUTER

* Import components:

```
import { Prompt } from "react-router-dom";

```

* In render\(\)

     <Prompt
              when={isBlocking}
              message={location =>
                `Are you sure you want to go to ${location.pathname}`
              }
            />

* **isBlocking**: a variable in your component
* **location**: is URL when user click on a link
* =&gt; For example: **isBlocking** = true when use is typing something 

> FULL SAMPLE CODE

    import * as React from 'react';
    import { Redirect } from 'react-router-dom';
    import { Prompt } from 'react-router';

    class RedirectSection extends React.Component<any, any> {

        constructor(props: any) {
            super(props);
            this.state = {
                redirect: false,
                email: '',
                isBlocking: false
            };
        }

        handleLogin = () => {
            this.setState({ redirect: true });
        }
        handleChange = (event: any) => {
            let email = event.target.value;
            this.setState({ email: email, isBlocking: email.length > 0 });
        }
        handleSave = () => {
            this.setState({ email: '', isBlocking: false });
        }
        render() {
            // tslint:disable-next-line:triple-equals
            if (this.state.redirect == true) { return <Redirect to="/Home" />; }
            return (
                <section>
                    <Prompt when={this.state.isBlocking} message={(location) =>  `All data will be lost if you redirect to ${location.pathname}`} />
                    <h2>REDIRECT IN REACT-ROUTER</h2>
                    <button className="btn btn-primary" onClick={this.handleLogin}>Login</button>

                    <input type="text" name="content" placeholder="type your email" value={this.state.email} className="form-control" onChange={(e) => this.handleChange(e)} />
                    <p><i>Block: {this.state.isBlocking.toString()}</i></p>
                    <button className="btn btn-danger" onClick={this.handleChange}>Save</button>
                </section>
            );
        }
    }
    export default RedirectSection;



