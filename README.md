# MERN Stack
### MERN Stack is a Javascript Stack that is used for easier and faster deployment of full-stack web applications. MERN Stack comprises of 4 technologies namely: MongoDB, Express, React and Node.js. It is designed to make the development process smoother and easier.
### <p> Each of these 4 powerful technologies provides an end-to-end framework for the developers to work in and each of these technologies play a big part in the development of web applications.</p>

## What Is a Stack?
### Stacks are groupings of multiple technologies used to create a single web application. Each web application is built with a variety of databases, libraries and frameworks. In the MERN stack, the technology group is based around JavaScript and is intended to simplify and streamline the process of web development. All the technologies in the MERN stack make up an end-to-end framework that developers can use from start to finish on single applications.

## What Is the MERN Stack?
### The MERN is similar MEAN stack but with a key distinction: the MEAN stack uses Angular to build front end web applications, while the MERN stack uses React to create them.

### The MERN stack is comprised of four powerful web development technologies that, when used together, have far more efficient and effective results. MERN is simply an acronym for these four technologies when used in tandem. They are:

* MongoDB: An open-source, document-based database.
* Express: A minimalist web framework for Node.js known for its speed.
* React: A front end JavaScript library for creating user interfaces.
* Node.js: A JavaScript runtime that operates on Chrome’s V8 JavaScript engine and brings JavaScript to the server.

## Understanding the Parts of the MERN Stack
### MongoDB
#### *MongoDB* is a cross-platform document-based database known as a nonrelational document-orientated database, or NoSQL. MongoDB stores data in flexible documents using a query language based on JavaScript Object Notation (JSON). The size, number and content of document fields vary, so the data structure can be altered later on. MongoDB is easy to scale and quite flexible, making it popular among many web developers.

### Express
#### *Express* is a back end framework for Node.js web applications. We can use Express to make writing server code much simpler, as opposed to the traditional alternative of manually writing full web server code on Node.js, since it lets us avoid having to repeat the same code like we would using the Node.js HTTP module.

#### Express’s framework was designed to enable simple, easy construction of APIs and efficient web applications. It is loaded with plugin features and is renowned for its speed. Its minimalistic structure makes it simple for developers to pick up and start using right away.

### React
#### In *React*, views are declarative, meaning developers do not have to manage the effects of changes in data or the view’s state. (A view’s state is the object that determines the behavior of individual components.) Instead, React lets developers use a full-featured programming language to design conditional or repetitive DOM elements rather than relying on templates that automatically create repetitive DOM (Document Object Model) or HTML elements. React lets the same code run on the browser and server simultaneously, which is what enables React to anchor the MERN stack and makes it essential to the operation.

### Node.js
#### *Node.js* is a cross-platform JavaScript runtime environment that is built on Chrome’s V8 JavaScript engine and is intended to allow developers to build scalable network applications and execute JavaScript code outside of browsers. Node.js works by using its own module system that is based on CommonJS, meaning it does not need an enclosing HTML page to put together more than one JavaScript file.

## How does the MERN stack work?
The MERN architecture allows us to easily construct a 3-tier architecture (frontend, backend, database) entirely using JavaScript and JSON.

![MERN STRUCTURE](struct.jpg)

### In this project, we are required to implement a web solution based on MERN stack on a Linux server.  We will be deploying an application that is used to create ‘Todo’ lists by implementing the steps below:


# Step 1 - Prepare the backend Linux server
* Update ubuntu
```
$ sudo apt update
```
* Upgrade ubuntu
```
sudo apt upgrade
```
# Step 2 - First, we will need to locate and install nodejs on the server.

* We need to get the location of nodejs software from ubuntu repositories over the internet.
```
$ curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
```
### We'll see something like this after the installation.

![CURL](curl.jpg)

* We need to Install Node.js with the command below
```
$ sudo apt install -y nodejs
```
*Note:* The command above will install both nodejs and npm. NPM is a package manager. Similar to what apt does on Ubuntu, NPM is used to install node modules or softwares, and manages dependency conflicts intelligently.

* We need to verify the node installation with both commands below
```
$ node -v
```
```
$ npm -v 
```
### We'll see something like this

![Node & Npm](NodeNpm.jpg)


# Step 3 - Application Code Setup

* We need to create a new file directory in any convienient location on your Ubuntu Desktop. Name it *Todo*. Run the command below to achieve this:
```
$ mkdir Todo
```
* Verify that the Todo directory is created
```
$ ls
```
* Now we enter into the file directory with the command below
```
$ cd ls
```
### We'll see something like this

![Todo](Todo.jpg)

* Next, we will use the command *npm init* to initialise our project, so that a new file named *package.json* will be created. This file will normally contain information about our app and the dependencies that it needs to run. Follow the prompts after running the command. We can hit enter to accept default values, then we accept to write out the package.json file by typing *yes*.
```
$ npm init
```
### We'll see something like this

![Mpm Init](npminit.jpg)

### Run the command *ls* to confirm that you have package.json file created.


# Step 4 - Install ExpressJS
### *Express* is a back end framework for Node.js web applications. it lets us avoid having to repeat the same code like we would using the Node.js HTTP module and It also  helps to define routes of our application based on HTTP methods and URLs.

* Inside the todo list folder,We will install Express using npm :
```
$ npm install express
```
* Now create a file index.js with the command below
```
$ touch index.js
```
* Run *ls* to confirm that your *index.js* file is successfully created
```
$ ls
```
* Inside the todo list folder, We will Install the dotenv module
```
$ npm install dotenv
```

### We'll see something like this

![ExpressJS](express.jpg)

* We need to open the *index.js* file with the command below
```
$ vi index.js
```
* Type the code below into it and save. Do not get overwhelmed by the code you see. For now, simply paste the code into the file.
```
const express = require('express');
require('dotenv').config();

const app = express();

const port = process.env.PORT || 5000;

app.use((req, res, next) => {
res.header("Access-Control-Allow-Origin", "\*");
res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
next();
});

app.use((req, res, next) => {
res.send('Welcome to Express');
});

app.listen(port, () => {
console.log(`Server running on port ${port}`)
});
```
### We'll see something like this

![INDEX.JS](indexjs.jpg)

### We use *:w* to save in vi and use *:q!* to exit vi.

### *NOTE* we have specified to use port 5000 in the code. This will be required later when we go on the browser.

### To test if our server works. We open our terminal in the same *Todo* directory as our *index.js* file and type

```
$ node index.js
```

### If every thing goes well, We should see our Server running on port 5000 in our terminal.

![Server Running](serverworks.jpg)


![Welcome Express](WelcomeEx.jpg)

### The above confirms that the server is running on *port 5000* in the terminal and on *localhost* by typing *localhost:5000* in the browser.

# Step 5 - Routes
### For each task, we need to create routes that will define various endpoints that the todo app will depend on. 

* So let’s create a folder routes
```
$ mkdir routes
```
* Change directory into the routes folder.
```
$ cd routes
```
* Now, create a file api.js with the command below
```
$ touch api.js
```
* Open the file with the command below
```
vi api.js
```

![Routes](routes.jpg)

* Input below code in it.
```
const express = require ('express');
const router = express.Router();

router.get('/todos', (req, res, next) => {

});

router.post('/todos', (req, res, next) => {

});

router.delete('/todos/:id', (req, res, next) => {

})

module.exports = router;
```


![API JS](apijs.jpg)

# Step 6 - Models
### Since the app is going to make use of Mongodb which is a NoSql database, we need to create a model which will be used to define the database schema. This is important so that we will be able to define the fields stored in each Mongodb document. 

### In essence the Schema is a blueprint of how the database will be constructed, including other data fields that may not be required to be stored in the database. These are known as virtual properties. To create a Schema and a model, *install mongoose* which is a node package that makes working with mongodb easier.

* Change directory back *Todo* folder with *cd ..* and install Mongoose
```
$ npm install mongoose
```

![Mongoose](mongoose.jpg)

### Now we will do 3 things at once by chaining 2 commands into one with the && directive.
* Create a new folder with *mkdir models*.
```
$ mkdir models
```
* And change directory into the newly created models folder with *cd models*.
```
$ cd models
```
* Inside the models folder, Create a file and name it *todo.js*
```
$ touch todo.js
```

![Models](models.jpg)


* Open the file created with vi *todo.js* then paste the code below in the file:
```
const mongoose = require('mongoose');
const Schema = mongoose.Schema;

//create schema for todo
const TodoSchema = new Schema({
action: {
type: String,
required: [true, 'The todo text field is required']
}
})

//create model for todo
const Todo = mongoose.model('todo', TodoSchema);

module.exports = Todo;
```

![Todojs](todojs.jpg)

### Now we need to update our routes from the file *api.js* in Routes directory to make use of the new model.
* In Routes directory, open *api.js* with *vi api.js*, delete the code inside with *:%d* and paste the code below into it then save and exit
```
const express = require ('express');
const router = express.Router();
const Todo = require('../models/todo');

router.get('/todos', (req, res, next) => {

//this will return all the data, exposing only the id and action field to the client
Todo.find({}, 'action')
.then(data => res.json(data))
.catch(next)
});

router.post('/todos', (req, res, next) => {
if(req.body.action){
Todo.create(req.body)
.then(data => res.json(data))
.catch(next)
}else {
res.json({
error: "The input field is empty"
})
}
});

router.delete('/todos/:id', (req, res, next) => {
Todo.findOneAndDelete({"_id": req.params.id})
.then(data => res.json(data))
.catch(next)
})

module.exports = router;
```

![Update API JS](updateapijs.jpg)


# Step 7- MongoDB Database

### We need a database where we will store our data. For this we will make use of mLab. mLab provides MongoDB database as a service solution, so to make life easy, we will need to sign up for the shared clusters free account which is ideal for our use case. ***https://www.mongodb.com/atlas-signup-from-mlab*** . Follow the sign up process, select AWS as the cloud provider, and choose a region near you.

### Create a mongodb database and connection inside mLab and then obtain the connection string through the connect TAB. Also, update the password and database name and removed the <>.

***DB=mongodb+srv://ysf:Password@cluster0.twofo.mongodb.net/yusuffDB?retryWrites=true&w=majority***

### Create a file in your TODO directory with and name it .env. Add the connection string to access the database in it, just as below

### In order to allow the node.js to connect to the database in Mongodb, the *index.js* was updated so as to reflect the use of dotenv.

* Now, paste the entire code below in the file.
```
const express = require('express');
const bodyParser = require('body-parser');
const mongoose = require('mongoose');
const routes = require('./routes/api');
const path = require('path');
require('dotenv').config();

const app = express();

const port = process.env.PORT || 5000;

//connect to the database
mongoose.connect(process.env.DB, { useNewUrlParser: true })
.then(() => console.log(`Database connected successfully`))
.catch(err => console.log(err));

//since mongoose promise is depreciated, we overide it with node's promise
mongoose.Promise = global.Promise;

app.use((req, res, next) => {
res.header("Access-Control-Allow-Origin", "\*");
res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
next();
});

app.use(bodyParser.json());

app.use('/api', routes);

app.use((err, req, res, next) => {
console.log(err);
next();
});

app.listen(port, () => {
console.log(`Server running on port ${port}`)
});
```

![Index Updated](updindexjs.jpg)


![Index Updated](updindexjs2.jpg)

* Start your server using the command:
```
node index.js
```

![Node Server](nodec.jpg)


![Local Host](working.jpg)


# Step 8 - Testing The Code Without A Frontend User Interface
### So far we have written our TODO application, and configured backend database, but we do not have a frontend UI yet. We need ReactJS code to achieve that. But during development, we will need a way to test our code using RESTFUL API. Therefore, we will need to make use of some api development clients to test our code.

### In this project, we will use Postman to test for our API.
* Install Postman in Ubuntu

```
$ sudo snap install postman
```

![Postman Installation](snap.jpg)


### Now we open our Postman, We will create a ‘POST’ and ‘GET’ request in postman to the API http://localhost:5000/api/todos

### POST Request

![POST](post.jpg)

### GET Request

![GET](get.jpg)

# Step 9 - Creating the Frontend
### we are done with the functionality we want from our api, it is time to create an interface for the client to interact with the api. To start out with the frontend of the todo app, we will use the *create-react-app* command to scaffold our app.

* In our Todo directory, We will run:
```
$ npx create-react-app client
```

### This will create a new folder in our Todo directory called *client*, where we will add all the react code.

![React Client](reactclient.jpg)

# Step 10 - Running the React App
### Before testing the react app, there are a number of dependencies that need to be installed.

* We need to Install *concurrently*: It is used to run more than one command simultaneously from the same terminal window.

```
$ npm install concurrently --save-dev
```

![Concurrently](conco.jpg)


* We need to Install *nodemon*: It is used to run and monitor the server. If there is any change in the server code, *nodemon* will restart it automatically and load the new changes.

```
$ npm install nodemon --save-dev
```

![Nondemon](nondemon.jpg)

* In the *Todo* folder, open the package.json file. Change the highlighted part of the below screenshot and replace with the code below.

```
"scripts": {
"start": "node index.js",
"start-watch": "nodemon index.js",
"dev": "concurrently \"npm run start-watch\" \"cd client && npm start\""
},
```
# Step 11 - Configure Proxy in *package.json*
* Enter into the *client* folder from Todo directory

```
$ cd client
```

* Open the *package.json* file

```
$ vi package.json
```

* Add the key value pair in the *package.json* file *"proxy"*: *"http://localhost:5000"*.

![Package JSON](pjson.jpg)

* Now, we will ensure that we are inside the *Todo* directory, and simply do:

```
$  npm run dev
```

### I got the error above but corrected it by removing the } in the JSON at position 260 in the */home/tsf/Todo/package.json*

![ERROR](error.jpg)


### Our app should open and running on localhost:3000

![REACT PORT 3000](react.jpg)

# Step 12 - Creating our React Components
### Components are independent and reusable bits of code. They serve the same purpose as JavaScript functions, but work in isolation and return HTML via a render() function. Components come in two types, Class components and Function components.

### For our todo app, there will be two state components and one stateless component.

* From our *Todo* directory run
```
$ cd client
```

* Move to the *src* directory
```
$ cd src
```

* Inside our *src* folder we will create another folder called *components*
```
$ mkdir components
```

* Move into the *components* directory with

```
$ cd components
```

* inside the components directory create three files *Input.js*, *ListTodo.js* and *Todo.js*.
```
$ touch Input.js ListTodo.js Todo.js

```
* Open *Input.js* file
```
$ nano Input.js
```
* Copy and paste the following


```
import React, { Component } from 'react';
import axios from 'axios';

class Input extends Component {

state = {
action: ""
}

addTodo = () => {
const task = {action: this.state.action}

    if(task.action && task.action.length > 0){
      axios.post('/api/todos', task)
        .then(res => {
          if(res.data){
            this.props.getTodos();
            this.setState({action: ""})
          }
        })
        .catch(err => console.log(err))
    }else {
      console.log('input field required')
    }

}

handleChange = (e) => {
this.setState({
action: e.target.value
})
}

render() {
let { action } = this.state;
return (
<div>
<input type="text" onChange={this.handleChange} value={action} />
<button onClick={this.addTodo}>add todo</button>
</div>
)
}
}

export default Input
```

![Components](compo.jpg)


### Axios is a promise based HTTP client for the browser and node.js, you need to cd into your client from your terminal and run yarn add axios or npm install axios.

* Move to the *src* folder
```
$ cd ..
```
* Move to *clients* folder
```
$ cd ..
```
* Install Axios in the *clients* folder
```
$ npm install axios
```

![Axios](axios.jpg)

* Go to *components* directory

```
$ cd src/components
```

* After that open yowe will open our ListTodo.js

```
$ nano ListTodo.js
```
* In the *ListTodo.js* copy and paste the following code

```
import React from 'react';

const ListTodo = ({ todos, deleteTodo }) => {

return (
<ul>
{
todos &&
todos.length > 0 ?
(
todos.map(todo => {
return (
<li key={todo._id} onClick={() => deleteTodo(todo._id)}>{todo.action}</li>
)
})
)
:
(
<li>No todo(s) left</li>
)
}
</ul>
)
}

export default ListTodo
```

* Then in our *Todo.js* file we will write the following code

```
$ nano Todo.js
```
* Then we input the follow codes
```
import React, {Component} from 'react';
import axios from 'axios';

import Input from './Input';
import ListTodo from './ListTodo';

class Todo extends Component {

state = {
todos: []
}

componentDidMount(){
this.getTodos();
}

getTodos = () => {
axios.get('/api/todos')
.then(res => {
if(res.data){
this.setState({
todos: res.data
})
}
})
.catch(err => console.log(err))
}

deleteTodo = (id) => {

    axios.delete(`/api/todos/${id}`)
      .then(res => {
        if(res.data){
          this.getTodos()
        }
      })
      .catch(err => console.log(err))

}

render() {
let { todos } = this.state;

    return(
      <div>
        <h1>My Todo(s)</h1>
        <Input getTodos={this.getTodos}/>
        <ListTodo todos={todos} deleteTodo={this.deleteTodo}/>
      </div>
    )

}
}

export default Todo;
```

![Todo](todonew.jpg)

### We need to make little adjustment to our react code. We will Delete the logo and adjust our App.js to look like this.

* Move to the *src* folder
```
$ cd ..
```
* In the *src* folder we will do

```
$ nano App.js
```
* Copy and paste the code below into it
```
import React from 'react';

import Todo from './components/Todo';
import './App.css';

const App = () => {
return (
<div className="App">
<Todo />
</div>
);
}

export default App;
```

* In the *src* directory open the App.css

```
$ nano App.css
```

* Then paste the following code into App.css
```
.App {
text-align: center;
font-size: calc(10px + 2vmin);
width: 60%;
margin-left: auto;
margin-right: auto;
}

input {
height: 40px;
width: 50%;
border: none;
border-bottom: 2px #101113 solid;
background: none;
font-size: 1.5rem;
color: #787a80;
}

input:focus {
outline: none;
}

button {
width: 25%;
height: 45px;
border: none;
margin-left: 10px;
font-size: 25px;
background: #101113;
border-radius: 5px;
color: #787a80;
cursor: pointer;
}

button:focus {
outline: none;
}

ul {
list-style: none;
text-align: left;
padding: 15px;
background: #171a1f;
border-radius: 5px;
}

li {
padding: 15px;
font-size: 1.5rem;
margin-bottom: 15px;
background: #282c34;
border-radius: 5px;
overflow-wrap: break-word;
cursor: pointer;
}

@media only screen and (min-width: 300px) {
.App {
width: 80%;
}

input {
width: 100%
}

button {
width: 100%;
margin-top: 15px;
margin-left: 0;
}
}

@media only screen and (min-width: 640px) {
.App {
width: 60%;
}

input {
width: 50%;
}

button {
width: 30%;
margin-left: 10px;
margin-top: 0;
}
}
```
* In the *src* directory open the *index.css*
```
$ nano index.css
```

* Copy and paste the code below:

```
body {
margin: 0;
padding: 0;
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen",
"Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue",
sans-serif;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
box-sizing: border-box;
background-color: #282c34;
color: #787a80;
}

code {
font-family: source-code-pro, Menlo, Monaco, Consolas, "Courier New",
monospace;
}
```
* Go to the Todo directory
```
$ cd ../..
```

* When you are in the Todo directory run:
```
$ npm run dev
```

![Settings](appindex.jpg)


![NMP RUN](1.jpg)


![NM22](2.jpg)


![MPRUN3](3.jpg)


### We just created a todo app using the MERN stack. We wrote a frontend application using React that communicates with a backend application written using expressjs. We also created a Mongodb backend for storing tasks in a database.


# Credits
* https://www.mongodb.com/mern-stack
* https://medium.com/@beaucarnes/learn-the-mern-stack-by-building-an-exercise-tracker-mern-tutorial-59c13c1237a1
* https://www.educative.io/edpresso/what-is-mern-stack
* https://bootcamp.berkeley.edu/resources/coding/learn-node-js/node-js-understanding-mern-stack/
* https://www.geeksforgeeks.org/mern-stack/
