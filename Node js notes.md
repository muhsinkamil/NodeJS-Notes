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
</table><h2 id="asynchronous-programming">Asynchronous programming:</h2>
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
<h1 id="module-system">Module system</h1>
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

