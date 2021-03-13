# How to Install Node.js

**NODE.js Website** https://nodejs.org/en/

## Check Node JS Version to confirm installation
  node -v

## Create and run a simple project 

      npm init -y
  
   
# Understanding Node Package Manager(NPM)

NPM Website where you can search for packages :  https://www.npmjs.com/
Example : react 
 
## Installing a package using NPM

    npm install express
 
 This will add below 2 changes in your project 
 
 + New directory created in project **node_modules** contains the intsalled modules
 + Dependencies added to **package.json**
      
        "dependencies": {
            "express": "^4.17.1"
          }
	
# Create and Run a Simple Project with a Sample Script

      node my-script.js  

# Creating a startup script in package.json
     
Saves typing commonly used commands.
    
+ Add the **script name** : *hello* and the **command** to execute : *node ./my-script.js*
       
       "scripts": {
          "hello": "node ./my-script.js"

        },

+ You can now run the script using npm using npm run <script_name>
        
        npm run hello



Create Modules in Node.js
Node treats each file as module
We can share code between files, that is reuse code

2 ways of creating modules

Old Way
	function greet(){
	    console.log("Good Day");
	}
	module.exports=greet;
	
	const greet = require('./greet.js');
	console.log("Hello World");
	greet();
	
	
	npm run hello
	

Create and Run Modern JS Code
 
export default greet;

import greet from './greet.js';




npm install --save-dev @babel/core @babel/node @babel/preset-env



"scripts": {
    "hello": "npx babel-node my-script.js"
  },


    npm run hello


Setup a basic server
	 src/server.js

        npx babel-node src/server.js

Auto start server
npm install --save-dev nodemon

Instead of running npx command everytime, we tell the nodemon to watch our files and restart if any changes.

npx nodemon --exec npx babel-node src/server.js


"scripts": {
    "hello": "npx babel-node my-script.js",
    "start": "npx nodemon --exec npx babel-node src/server.js"
  },


For POST requests
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


/users/:username/repos
Copy
Any colons (:) on a path denotes a variable. You should replace these values with actual values of when you send your request. In this case, you should replace :username with the actual username of the user you’re searching for. If I’m searching for my Github account, I’ll replace :username with zellwk.

![image](https://user-images.githubusercontent.com/34193287/111023520-8703bb80-83ff-11eb-871a-4d9f79250523.png)
