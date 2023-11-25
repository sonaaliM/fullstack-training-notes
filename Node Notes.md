# Creating App with React

	npx create-react-app my-app

**Sample Project Structure**

    public/
    src/
      setupTests.js
      reportWebVitals.js
      logo.svg
      index.js
      index.css
      App.test.js
      App.js
      App.css

    README.md
    package.json
    node_modules/
    yarn.lock

&nbsp;

# How to Install Node.js
&nbsp;

 **NODE.js Website** https://nodejs.org/en/
&nbsp;

### Check Node JS Version to confirm installation
  	node -v

### Create a simple project 
      mkdir react-backend
      cd react-backend
      npm init -y
#### This will create the package.json file for you. Next we will install the required packages with npm install command.

&nbsp;
# Understanding Node Package Manager(NPM)
&nbsp;
NPM Website where you can search for packages :  https://www.npmjs.com/
Example : react 
&nbsp;
### Installing a package using NPM

    npm install express
 
 This will add below 2 changes in your project 
 
 + New directory created in project **node_modules** contains the intsalled modules
 + Dependencies added to **package.json**
      
        "dependencies": {
            "express": "^4.17.1"
          }
&nbsp;

# Create and Run a Project with a Simple Script

            node my-script.js  


### Creating a startup script in package.json
   
This creates a command for the script provided and saves effort to type the entire command everytime. To add your own command for npm start, you add it to the scripts property of your project’s package.json file.
    
+ Add the mapping for **script execution command** : *node ./my-script.js* and the **command name** : "hello" in **package.json** 
       
       "scripts": {
          "hello": "node ./my-script.js"

        },

+ You can now run the script using npm using npm run <Command name>
        
        npm run hello

&nbsp;
### Adding more Scripts to the Project - Creating Modules in Node.js

Node treats each file as module. We can share code between files, that is reuse code

2 ways of creating modules : The first is older version syntax of javascript
&nbsp;
+ **greet.js** - Create a function **greet()** to reuse in another script

		function greet(){
		    console.log("Good Day");
		}
		module.exports=greet;

+ **my-script.js** - Import and call the function **greet()** from **greet.js**

		const greet = require('./greet.js');
		console.log("Hello World");
		greet();


		npm run hello
	
&nbsp;


### How to Run Modern JS Code
 
		export default greet;

		import greet from './greet.js';



*To run the code we need **Babel** which is a javascript compiler*

Website : https://babeljs.io/

+ Install Babel


		npm install --save-dev @babel/core @babel/node @babel/preset-env


+ Change the startup script to use **npx babel-node** 


		"scripts": {
		    "hello": "npx babel-node my-script.js"
		  },

+ Run the sscript with npm


    		npm run hello

&nbsp;

# Setup a basic server with express

	 src/server.js
	 	import express from 'express';
		const app = express();
		app.listen(8000, () =>  {
		    console.log('Server is listening on port 8000')
		});

        npx babel-node src/server.js



&nbsp;
### Auto start server on code changes
		npm install --save-dev nodemon

Instead of running npx command everytime, we tell the nodemon to watch our files and restart if any changes.

		npx nodemon --exec npx babel-node src/server.js


		"scripts": {
		    "hello": "npx babel-node my-script.js",
		    "start": "npx nodemon --exec npx babel-node src/server.js"
		  },


&nbsp;
### Handling  POST requests
   		  
         npm install body-parser

**Server.js**
  
		import bodyParser from 'body-parser';

		app.use(bodyParser.json());




		app.post('/hello', (req, res) => { 
		    res.send(`Hello  ${req.body.name}!`)
		});
		app.get('/hello/:name', (req, res) => { 
		    res.send(`Hello ${req.params.name}!`)
		});


&nbsp;

### Testing endpoints with curl

	curl http://localhost:8010/api/articles/React
	{"_id":"6054fc5a6b7e9891e0de8d1e","name":"React","upvotes":4,"comments":[{"postedBy":"ME","text":"Nice"},{"postedBy":"test","text":"test"}]}

&nbsp;

# Connecting to Database - MongoDB


**Starting the MongoDB Server**

      mongod --port 27017 --dbpath C:\Users\xyz\mdb

**Importing Data using json**

      mongoimport --db="react-blog-db" --collection="articles" --file="articles.json" --jsonArray

      mongo --port 27017 
      use react-blog-db
      db.articles.find()
      db.articles.drop()


**Sample JSON File : articles.json**

    [{
      "name": "React",
      "upvotes" : 1,
      "comments": [{
        "postedBy" : "ME",
      "text" : "Nice"
      }]
      
          
    }]


&nbsp;




# Configuring Proxy for Backend Server 


&nbsp;
### Add below entry to package.json of the react project

    "proxy": "http://localhost:8010/",

