# CREATE SIMPLE DOCUMENT WITH GITBOOK

_**GITBOOK **is the best tool to create your documentation as I use it for write document here. I will let you know how to create document from scratch._

#### INIT PROJECT

* **Install gitbook**

```
npm install gitbook-cli -g
```

* **Init project**

```
gitbook init
```

* **Run project**

```
gitbook serve
```

* **Build project**

```
gitbook build
```

#### Add settings for gitbook

* Add file: _**book.json**_
* Below is simple settings for gitbook

```
{
  "plugins": [
    "header"
  ],
  "pluginsConfig": {
    "layout": {
      "headerPath" : "layouts/header.html"
    }
  }
}
```

#### Add plugins and custom layout

* You can add  plugin via npm 
* First, you have to install NodeJs to manage node packages
* Add plugin to gitbook, such as gitbook-plugin-header
* Run command:

```
npm install gitbook-plugin-header
```

* Add new file header.html under layouts folder
* Add simple html code for header section

```
<div class='header'>
   <div class="container">
       <button class="btn btn-primary">Click me</button>
        <img src="http://www.developerdrive.com/wp-content/themes/dd_v/css-images/logon.png" alt="Avatar" /> 
        <h2>Research document - @tamle</h2>
   </div>
</div>
```

* Add setting for gitbook:

```
{
  "plugins": [
    "header"
  ],
  "pluginsConfig": {
    "layout": {
      "headerPath" : "layouts/header.html"
    }
  }
}
```

* Finally,  run gibook serve to see changes, header will be shown in your document

#### Custom CSS, font face, add bootstrap into gitbook

* We will use sass language to write code, you can you css instead
* Create file website.scss under sass css, and config Prepos to build sass file into styles/website.css file
* Write some scss code to design your document page
* **Custom font face:**

  * Import font:

  ```
  @import url(http://fonts.googleapis.com/css?family=Open+Sans:300italic,400italic,700italic,400,300,700);
  ```

  * Set font for body tag: 

  ```
  $open-sans: 'Open Sans', sans-serif;
  body{
      font-family: $open-sans !important;
  }
  ```

* **Add bootstrap styles:**

```
@import url(https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css);
```

* Finally, custom page will be shown like image below:

![](https://i.imgur.com/afiSSiX.png)

