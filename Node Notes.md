# How to Install Node.js
&nbsp;
&nbsp;
 **NODE.js Website** https://nodejs.org/en/
&nbsp;

### Check Node JS Version to confirm installation
  	node -v

### Create a simple project 
      mkdir react-backend
      npm init -y

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
   
This creates a script with the command provided and saves effort to type the entire command everytime.
    
+ Add the **script name** : *hello* and the **command** to execute : *node ./my-script.js*
       
       "scripts": {
          "hello": "node ./my-script.js"

        },

+ You can now run the script using npm using npm run <script_name>
        
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

+ **my-scrip.js** - Import and call the function **greet()** from **greet.js**

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

	Server.js
  
		import bodyParser from 'body-parser';

		app.use(bodyParser.json());




		app.post('/hello', (req, res) => { 
		    res.send(`Hello  ${req.body.name}!`)
		});
		app.get('/hello/:name', (req, res) => { 
		    res.send(`Hello ${req.params.name}!`)
		});


&nbsp;
# Connecting to Database - MongoDB


&nbsp;
&nbsp;

### Testing endpoints with curl

	curl http://localhost:8000/api/articles/School
	{"_id":"604bb7da7671bc7ca6e866a9","name":"School","upvotes":0,"comments":"Temp"}

	curl -X POST  http://localhost:8000/api/articles/School/upvote
	{"_id":"604bb7da7671bc7ca6e866a9","name":"School","upvotes":1,"comments":"Temp"}


	curl http://localhost:8000/api/articles/School
	{"_id":"604bb7da7671bc7ca6e866a9","name":"School","upvotes":1,"comments":"Temp"}![image](https://user-images.githubusercontent.com/34193287/111024386-8d486680-8404-11eb-952f-ce83cedd7c81.png)

