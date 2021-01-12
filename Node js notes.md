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
</ul>
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

