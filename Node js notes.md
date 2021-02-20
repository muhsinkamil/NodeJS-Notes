---


---

<h2 id="check-the-version-of-node">Check the version of node:</h2>
<blockquote>
<p>node -v     ⇒  v12.18.0</p>
</blockquote>
<h2 id="what-is-node-js-">What is node js ?</h2>
<ul>
<li>Node js is javascript <strong>runtime</strong> built in chrome v8 JS engine.</li>
<li>Node js <strong>uses an event driven, non blocking I/O model</strong> that makes it lightweight and efficient.</li>
<li><strong>Features</strong>: Reduced resources, fast, highly scalable</li>
<li><strong>✔️ Used for</strong> : Real time chat apps iwth large I/O operations, data streaming apps</li>
<li><strong>❌ Not used for</strong>: CPU intensive operations</li>
</ul>
<p>JS code runs on node environment. Node js has a collection of dependencies. Most important of the dependency is <strong>V8 and Libuv</strong></p>
<h2 id="v8">V8:</h2>
<ul>
<li>compile and execute js code</li>
<li>Provide memory heap to allocate and store variables</li>
<li>Provide a call stack</li>
<li>Garbage collector - to garbage collect the object and memory references that are not in use</li>
<li>Provide an event loop to run async code</li>
</ul>
<h2 id="libuv-open-source-c-project">Libuv: Open source C++ project</h2>
<ul>
<li>Gives access to os file systems and networking</li>
<li>async loops and thread pools</li>
<li>Threading and sync primitives</li>
</ul>
<p>Node js provides a set of wrappers  and a consistent API such as http, fs, crypto, path to use. These modules are related to Libuv which is C++ code.<br>
Node js helps us use these functionalities without js code.</p>
<h2 id="js-on-browser-and-node">JS on browser and Node</h2>

<table>
<thead>
<tr>
<th>Command</th>
<th>Browser</th>
<th>Node</th>
</tr>
</thead>
<tbody>
<tr>
<td>window</td>
<td>Gives the window object</td>
<td>Reference error</td>
</tr>
<tr>
<td>global</td>
<td>Reference error</td>
<td>Gives the global object</td>
</tr>
<tr>
<td>document</td>
<td>Available : Used for DOM manipulation</td>
<td>Reference error</td>
</tr>
<tr>
<td>process</td>
<td>Reference error</td>
<td>Available : Gives the various process</td>
</tr>
</tbody>
</table><h1 id="module-system">Module system</h1>
<p>One of the most popular, most used module is “File system”</p>
<p><a href="https://nodejs.org/api/fs.html">File system Node Documentation: </a></p>
<h2 id="importing-the-file-system">Importing the file system:</h2>
<pre><code>const fs = require('fs')
</code></pre>
<h2 id="writing-the-file">Writing the file:</h2>
<pre><code>fs.writeFileSync('myFile.txt', "Hello world!!!")
</code></pre>
<h2 id="some-useful">Some useful:</h2>
<pre><code>fs.writeFileSync()    	=&gt; write file
fs.appendFileSync()		=&gt; append to the existing file or create, if none
fs.unlink() 			=&gt; remove the file
fs.rmdir()				=&gt; remove the directory
</code></pre>
<h1 id="exporting-and-importing-own-file">Exporting and Importing own file:</h1>
<h2 id="create-greeting.js">Create greeting.js</h2>
<pre><code>const greeting = (name) =&gt; { return `Hello ${name}` }
module.exports = greeting
</code></pre>
<h2 id="importing-greeting.js-and-utilising-the-defined-function">Importing greeting.js and utilising the defined function:</h2>
<p>Import with relative path for own files.</p>
<pre><code>const  fs  =  require('fs')
const  greeting  =  require('./greeting')
fs.writeFileSync('notes.txt',  greeting("Kamil"))
</code></pre>
<p>This creates names.txt file and writes with the name passed on to it.</p>
<h2 id="importing-npm-package">Importing npm package:</h2>
<p>Importing npm package is same as importing the core node modules( like ‘fs’)</p>
<pre><code>const validator = require('validator')
</code></pre>
<p><strong>Installing as dev dependency: npm install nodemon --save-dev</strong></p>
<h2 id="streams--buffer">Streams &amp; Buffer</h2>
<p>Start using data before it has finished loading.<br>
Small buffer of data can be used during every interval of load.<br>
Eg., Youtube loading video</p>
<h2 id="getting-input-from-command-line">Getting input from command line</h2>
<p>The arguments are accessed by “process.argv” -&gt; argument vector</p>
<pre><code>node app Muhsin

console.log(process.argv)  --&gt; [[
  'C:\\Program Files\\nodejs\\node.exe',
  'F:\\NodeProjects\\notes-app\\app',
  'Muhsin'
]
</code></pre>
<h2 id="parsing-command-line-arguments">Parsing command line arguments:</h2>
<p>NPM module used: yargs</p>
<pre><code>yargs.command({
    command:  "add",
    describe:  "adding note",
    builder:  {
	    title:  {
			describe:  "Note title",
			demandOption:  true,
			type:  "string",
		},
    }

    handler:  function  ()  {
	    console.log("adding new note")
    }
})
yargs.parse()
</code></pre>
<p><strong>Exploring JSON</strong>:</p>
<pre><code>const  series  =  {
	title:  "The office",
	starred:  "Steve Carell",
}

const  seriesJSON  =  JSON.stringify(series)
const  seriesObject = JSON.parse(seriesJSON)

console.log("JSON: ",  seriesJSON) // {"title":"The office","starred":"Steve Carell"}
console.log("Object: ",  seriesObject) // { title: 'The office', starred: 'Steve Carell' }

console.log("JSON title: ",  seriesJSON.title) // JSON title: undefined
console.log("Object title: ",  seriesObject.title) // Object title: The office
</code></pre>
<p><strong>Writing to file and getting buffer</strong>:</p>
<pre><code>fs.writeFileSync("series.json",  seriesJSON)

const  dataBuffer  =  fs.readFileSync("series.json")

console.log("Still in json format ",  dataBuffer.toString()) //{"title":"The office","starred":"Steve Carell"}
</code></pre>
<h2 id="debugging-with-chrome">Debugging with chrome:</h2>
<ul>
<li>Add “debugger” statement where necessary.</li>
<li>Run with “node inspect app”</li>
<li>Open “chrome://inspect” to inspect</li>
<li>Select the app and inspect</li>
<li>To restart the debug session, on terminal, “restart”</li>
<li>To exit from the debug session, “ctrl + c” twice</li>
</ul>
<h2 id="asynchronous-programming">Asynchronous programming:</h2>
<p><strong>Without Async:</strong></p>
<ul>
<li>Server sends a request to file system</li>
<li>The server waits till the file opens and data is being read</li>
<li>It returns the data to client</li>
<li>The server is now ready to take the next request</li>
</ul>
<p><strong>With Async</strong>:</p>
<ul>
<li>Server sends a request to file system</li>
<li>Now the server is ready to handle the next request</li>
<li>Meanwhile when the file is opened and data is read from file, server sends the content to client</li>
</ul>
<h2 id="architecture">Architecture:</h2>
<p><strong>Multi Threading request response architecture</strong>: uses HTTP protocol, also called “Stateless model”</p>
<ul>
<li>There are limited number of threads waiting.</li>
<li>Request sent by the client.</li>
<li>Single thread gets assigned from thread pool.</li>
<li>The assigned thread is responsible to read the request, process and perform blocking I/O</li>
</ul>
<p><strong>Cons of Multithreading:</strong></p>
<ul>
<li>If the requests are more than the number of threads, the requests have to wait.</li>
<li>Difficult to manage concurrent requests</li>
<li>wastage of time in processing I/O operations.</li>
</ul>
<p><strong>Node uses Single thread event loop model</strong>:</p>
<ul>
<li>Multiple requests are placed in “Event queue”. Node internally maintains the limited thread pool and infinite loop known as “Event loop”</li>
<li>Event loop receives and process the requests using single thread. Event loop executes always and checks if the event queue has any requests.</li>
<li>Event loop picks the request if any. If the request has no blocking I/O operations, it responds immediately.</li>
<li>If it is blocking I/O, thread is assigned, which is responsible for request’s processing and response.</li>
</ul>
<h2 id="express">Express</h2>
<pre><code>const  express  =  require("express")
const  app  =  express()

// For root page
app.get("/", (req, res) =&gt; {
res.send("Need to render index.html")
})

//Help page
app.get("/help", (req, res) =&gt; {
res.send("Help page")
})

//We can return HTML as response
app.get("/about" ,(req, res) =&gt; {
res.send("&lt;h1&gt;This is about page&lt;/h1&gt;")
})

app.listen(3090, () =&gt; {
console.log("server listening at port 3090")
})
</code></pre>
<h2 id="path-in-node-core-module">Path in node core module:</h2>
<pre><code>const path = require('path')
const  publicFolder  =  path.join(__dirname, '../public')

// goes to the public folder and serves the files
app.use(express.static(publicFolder))
</code></pre>
<ul>
<li>Configure public folder and link with app with app.use(express.static(PUBLIC_FOLDER_NAME))</li>
<li>Public folder is used to render the static files.</li>
</ul>
<h2 id="handlebars-for-dynamic-templating">Handlebars for Dynamic templating:</h2>
<ul>
<li>Create Views folder</li>
<li>`// set handlebar using</li>
<li>app.set(‘view engine’, ‘hbs’)  // in app.js</li>
</ul>
<p>Create routes for hbs:<br>
Node automatically checks for views folder:</p>
<pre><code> app.get('', (req, res) =&gt; {
		res.render('index', {
			title:  "Weather App",
			name:  "Mohamed Muhsin"
			})
	})
</code></pre>
<h2 id="setting-partials-with-hbs">Setting partials with hbs:</h2>
<p>Register the partials in app.js</p>
<pre><code>const  partialFolder  =  path.join(__dirname, "../templates/partials")
hbs.registerPartial(partialFolder)
</code></pre>
<p>Customise Nodemon: Tell nodemon to notice for extensions of js and hbs</p>
<pre><code>"start":  "nodemon src/app.js -e js, hbs"
</code></pre>
<h2 id="query-strings">Query Strings:</h2>
<ul>
<li>
<p>Obtained from request ( request.query )</p>
</li>
<li>
<p>name=“location” in html acts as key and value will be searchInput.value</p>
</li>
<li>
<p>add action to form:</p>
<pre><code>  &lt;form&gt;
  
  &lt;input  type="text"  placeholder="Location"  name="location"  class="search-input"&gt;
  &lt;button  class="submit-btn"&gt;
  		Submit
  &lt;/button&gt;

  	&lt;/form&gt;
</code></pre>
</li>
</ul>
<h2 id="mongo-db">Mongo DB:</h2>
<p><strong>Start Mongo</strong>:</p>
<p>“C:\Program Files\MongoDB\Server\4.4\bin\mongod.exe” --dbpath=“c:\data\taskdb”</p>
<p><strong>Mongo GUI:</strong></p>
<ul>
<li>Install Robo Mongo 3T</li>
<li>Connect the Local Mongo which is running at port 27017 to Robo 3T and test by running command <strong>db.version()</strong>.</li>
<li>To run the command, ctrl + Enter or F5</li>
</ul>
<p><strong>Mongo Db Npm module</strong>:</p>
<ul>
<li>Objective: CRUD</li>
<li>MongoClient</li>
</ul>
<h2 id="connecting-to-database">Connecting to database:</h2>
<pre><code>const mongodb =  require("mongodb")

const  MongoClient  = mongodb.MongoClient
const  connectionURL  =  "mongodb://127.0.0.1:27017"
MongoClient.connect(
	connectionURL,
	{ useUnifiedTopology:  true },
	(error, client) =&gt; {
	if (error) {
		return  console.log("Error connecting to db")
	}
		const  db  =  client.db(databaseName)
		db.collection("users").insertMany([{
			name: "ashiq"
		}])
		console.log("Connected to server")
	}
)
</code></pre>
<p>**Most used in InsertOne callback: ** are</p>
<ul>
<li>insertedCount,</li>
<li>ops,</li>
<li>insertedId</li>
<li><a href="http://mongodb.github.io/node-mongodb-native/3.6/api/Collection.html#~insertOneWriteOpResult">http://mongodb.github.io/node-mongodb-native/3.6/api/Collection.html#~insertOneWriteOpResult</a></li>
</ul>
<p><strong>Object ID:</strong><br>
Create Object ID,</p>
<ul>
<li>require ObjectID from  ‘mongodb’</li>
</ul>
<p><strong>Update with set operator</strong>:</p>
<pre><code>db.collection("tasks")
	.updateOne(
	{ _id:  new  ObjectID("60210e27bd70a430a45db269")},
	{
	$set: {
		description:  "Buy sugar",
		},
	}
	)
	.then((res) =&gt;  console.log(res))
	.catch((error) =&gt;  console.log(error))
</code></pre>
<p><strong>Structuring a REST API:</strong></p>
<p>REST - Representational state transfer - Application programming interface</p>
<p><strong>Create</strong> :</p>
<ul>
<li>POST /products</li>
</ul>
<p><strong>Read</strong>:</p>
<ul>
<li>GET /products</li>
<li>GET /products/:id</li>
</ul>
<p><strong>Update:</strong><br>
-PATCH /products/:id</p>
<p><strong>Delete:</strong><br>
-DELETE /products/:id</p>
<p><strong>Status code:</strong> <a href="httpstatuses.com">httpstatuses.com</a></p>
<ul>
<li>200 -&gt; Success</li>
<li>400 -&gt; Error</li>
<li>500 -&gt; server error</li>
</ul>
<p><strong>Structure of Request:</strong><br>
Eg.,</p>
<pre><code>POST  /products HTTP/1.1
Accept: application/json
Connection: Keep-alive
Authorisation: Bearer dfjalkjdfal;kjdfa;lkjd;lakj1039i409..
</code></pre>
<p>{ “description” : “Order shirt” }</p>
<p><strong>Structure of Response:</strong><br>
Eg.,</p>
<pre><code>    HTTP/1.1 201 Created
	Date: Sun, 02/09/2020 19:59:12
	Server: Express
	Content-type: application/json
</code></pre>
<p>{ “_id”: “djsa;lkjsadshdsflkajshlsa”, “description” : “Order shirt” }</p>
<p><strong>Creating EndPoints in REST</strong>:</p>
<pre><code>app.use(express.json()) // parse incoming json to object

app.post("/products", (req, res) =&gt; {
    res.send("Posted")
})
</code></pre>
<ul>
<li>Extract model to separate js file</li>
<li>keep mongoose.js file only as means to connect to db</li>
</ul>
<p><strong>Read EndPoint:</strong></p>
<pre><code>app.get('/products', (req, res) =&gt; {
	 User.find({})
		 .then(users =&gt; res.send(users))
		 .catch(error =&gt; res.status(500).send())
})
</code></pre>
<p><strong>Read Individual Product: Read based on dynamic value</strong></p>
<pre><code> app.get('/users/:id', (req, res) =&gt; {
        const _id = req.params.id
        User.findById(_id)
	        .then(user =&gt; res.send(user))
	        .catch(error =&gt; res.status(500).send("No match found"))
    })
</code></pre>
<p><strong>Data Validation and sanitization:</strong></p>
<ul>
<li>use validate(value) { condition here }</li>
<li><a href="https://mongoosejs.com/docs/schematypes.html">https://mongoosejs.com/docs/schematypes.html</a></li>
<li>use <strong>validator npm module</strong></li>
</ul>
<h2 id="authentication">Authentication:</h2>
<ol>
<li>
<p>Hash the password</p>
</li>
<li>
<p>Use <strong>bcryptjs npm module</strong> to securely store password</p>
<pre><code> const bcrypt = require('bcryptjs')
 const hashPassword = async () =&gt; {
     const password = "Mypassword"
     
 	// bcrypt.hash(password, no of rounds to hash)
     const hashedPassword = bcrypt.hash(password, 8)
 	console.log(password)       // "Mypassword"
 	console.log(hashPassword)    // "dkkjdsfdhfjkdfhkjhfjkld" 
 }
</code></pre>
</li>
</ol>
<ul>
<li>To compare the passwords, use <strong>bcrypt.compare(inputPassword, password)</strong> -&gt; is a async function and returns true or false</li>
</ul>
<h2 id="hash-the-password-before-saving-to-db">Hash the password before saving to db:</h2>
<ul>
<li>
<p>To do so, use middleware on mongoose</p>
</li>
<li>
<p>use method on schema called ‘pre’ to hash the password before saving.</p>
</li>
<li>
<p>Need to use standard function() not a arrow function as binding needs to done on ‘pre’ hook.</p>
</li>
<li>
<p>function is async and takes next to pass the control after the hook is done.</p>
</li>
<li>
<p>create normally uses the ‘pre’ hook before saving, but update("<strong>findByIdAndUpdate"</strong>) <strong>bypasses</strong> the middleware and changes db directly. So special care needs to be taken.</p>
</li>
<li>
<p>so to tackle this, use <strong>findById</strong> and update by looping over req.body.<br>
1. Find the user by <strong>findById</strong><br>
2. Alter the fields provided by bracket notation.<br>
3. await and save the user.</p>
</li>
<li>
<p>Needs to hash the password only if the password is not modified or not hashed.</p>
</li>
<li>
<p>Mongoose has <strong>isModified</strong> method to check if the password is hashed or not.</p>
</li>
</ul>
<h2 id="logging-in-users">Logging in users:</h2>
<ol>
<li>Make findByCredentials(req.body.email, req.body.password)</li>
<li>To setup, use <strong>userSchema.statics.findByCredentials</strong></li>
<li>use <strong>bcrypt.compare(inputPassword, originalPassword)</strong></li>
</ol>
<h2 id="jwt">JWT:</h2>
<ol>
<li><strong>npm install jsonwebtoken</strong></li>
<li>To create jwt token, use  <strong>jwt.sign()</strong></li>
<li>JWT is separated by 2 periods,</li>
<li>1st part -&gt; Base 64 encoded Header</li>
<li>2nd Part -&gt; payload or body</li>
<li>3rd Part -&gt; signature</li>
<li>use <a href="http://base64decode.org">base64decode.org</a></li>
<li>To verify, <strong>jwt.sign(token, secret)</strong></li>
</ol>
<h2 id="checklist">Checklist:</h2>
<ol>
<li>
<p>Make a pre save middleware on userSchema.</p>
</li>
<li>
<p>Hash the password if the <strong>user.isModified(“password”)</strong> // serving for both creating new user and changing password on update profile.</p>
</li>
<li>
<p>Alter the password , " this.password = await bcrypt.hash(this.password, Rounds) "</p>
</li>
<li>
<p>next()</p>
<p><strong>Login:</strong></p>
<ol>
<li>Create login route</li>
<li>create <strong>userSchema.statics.(function) on model</strong></li>
<li>Find user by email.</li>
<li>Handle errors if user is not found.</li>
<li>if found, make sure the password is correct by <strong>await bcrypt.compare(inputPassword, user.password)</strong></li>
<li>Handle error for incorrect password.</li>
<li>If the password is correct, return user.</li>
<li>Next step is create jwt token.</li>
<li>Define the <strong>userSchema.methods.generateJWT()</strong> function that signs and attaches the token to user.</li>
</ol>
<p><strong>JWT</strong>:</p>
<ol start="10">
<li>To issue jwt, <strong>jwt.sign({ _id:  user._id },  SECRET)</strong></li>
<li>Make use of node’s &gt; <strong>require(‘crypto’).randomBytes(64).toString(‘hex’)</strong>  to get the access token</li>
<li>sign the token and attach the token</li>
<li>save the user.</li>
<li>return token.</li>
</ol>
</li>
</ol>
<h2 id="authenticate-tokens-with-middleware">Authenticate tokens with Middleware:</h2>
<ul>
<li>
<p>without middleware: new req -&gt; run route handler</p>
</li>
<li>
<p>with middleware: new req -&gt; do something in middleware -&gt; run route handler</p>
</li>
<li>
<p>Get the <strong>header(‘Authorization’)</strong> and verify with <strong>jwt.verfiy</strong></p>
</li>
<li>
<p>The <strong>jwt.verify</strong> returns the object that has been set on <strong>jwt.sign({ _id:  user._id },  SECRET)</strong></p>
</li>
<li>
<p>Find the user by the object returned from jwt.verify.</p>
</li>
<li>
<p>If no user found, throw error</p>
</li>
<li>
<p>If the user is found,</p>
<ul>
<li>Attach user to req</li>
<li>next()</li>
</ul>
</li>
</ul>
<h2 id="postman-features">PostMan features:</h2>
<ul>
<li>
<p>Create environment for both dev and prod</p>
</li>
<li>
<p>have url as variable</p>
</li>
<li>
<p>Make a bearer token set to variable eg., {{authToken}}</p>
</li>
<li>
<p>Now on routes, signup and login where the token is issued and are public, set the Tests(on postman)</p>
<pre><code>  if(pm.response.code  ===  200){
  		pm.environment.set('authToken', pm.response.json().token)
  }
</code></pre>
</li>
</ul>
<p><strong>On signup the response code would be 201. change accordingly.</strong></p>
<h2 id="logging-out">Logging out:</h2>
<ul>
<li>Include auth middleware as user has to be logged in before logging out.</li>
<li>Clear the token by filter.</li>
<li>save the <strong>await req.user.save()</strong></li>
<li>send status</li>
</ul>
<p><strong>Logout all</strong>:</p>
<ul>
<li>clear all the tokens by emptying <strong>req.user.tokens = []</strong></li>
<li>save the user to db</li>
<li>res.send()</li>
</ul>
<h2 id="hiding-private-info-on-sending-response-back">Hiding private info on sending response back:</h2>
<ul>
<li>when the response is sent by res.send(user), the user object is calling JSON.stringify(user) and sends the JSON object of user</li>
<li>Making use of this, when we attach the method <strong>toJSON</strong>, the method <strong>toJSON</strong> first gets called and the return value of this method is stringified and sent back.</li>
<li>So on method, toJSON, remove all the unnecessary properties to send.</li>
</ul>
<h2 id="setting-relationship-between-two-models">Setting relationship between two models:</h2>
<ul>
<li>
<p>create a separate field with type of <strong>mongoose.Schema.Types.ObjectId</strong> and make it required</p>
<pre><code>  owner: {		   
  	    type: mongoose.Schema.Types.ObjectId,
  	    required: true,
  	    ref: 'MODELNAME'
  }
</code></pre>
</li>
</ul>
<p>on other model, setup a virtual connection,</p>
<pre><code>userSchema.virtual({
	  ref: "Task',
	  localField: '_id',
	  foreignField: 'owner'
})
</code></pre>
<ul>
<li>
<p>To populate the field,</p>
<pre><code> const task = await Task.findById('6734918432adsjh23498')
 await task.populate('owner').execPopulate()
 console.log(task)
</code></pre>
</li>
</ul>
<p><strong>Cascade delete:</strong></p>
<ul>
<li>when the user deletes his profile, his tasks should also get deleted.</li>
<li>To do this, create a middleware on userSchema to delete all his tasks.</li>
<li>There is ‘pre’ remove hook.</li>
</ul>

