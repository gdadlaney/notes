Mosh node tutorial - https://www.youtube.com/watch?v=TlB_eWDSMt4&t=1441s
Full Course - RESTful api using Node, Express, MongoDB for a real application		// Describes it well at around 30 mins in the video


window & document are objects in the browser runtime environment, not in node, so
console.log(window)			// won't work

Why node -
Paypal switched to Node - see advantages gained - e.g - dev. time, maintainablity, etc.

Useful for async applications, i.e. - that involve a lot of network or fs access.
Node is async by default(unlike django & asp.net)
Conversely node is single threaded(why?), hence not good for cpu intensive applications, but they can be called using a micro-service

Inbuilt(Global) objects & functions in Node
os, fs, events, http

others -
console							// console.log
setTimeout(); clearTimeout()	// call a function after a certain time
setInterval(); clearInterval()	// repeatedly call a function after a given delay

these functions and objects are part of the "global" object i.e
console & golbal.console mean the same thing
similarly we can add objects to global, to share them between different modules(files) whne running as the same process, as -
global.my_var = 1
But don't add all variables to global, you need to create modularity so that objects and functions that fit into one module more than the other, should be in the former. We can always import them inn the later module. This is done to make the code more easy to understand, debug and solves the hassles of global variables(unexpected override by some function in other module).

In the browser, there's a similar object "window", which by default includes the varibles defined in the console. i.e
var a = "";
window.a 		// works
But in node
global.a		// undefined, you need to explicitly add it to global

Why modules? 
modules as namespaces
For code maintianability & easier debugging

module object(not in global)
console.log(module)				console.log(global)

## Modules
Creating a module to log messages. Something like a service with URL to log messages in the cloud.

We have a variable and a function in the logger.js module.

.But to make the log function accessible to the other file, we need to make it Public // unlike in Python, where everything is public. To do that -
module.exports.log = log			// where log is a function in logger.js
Think of exports as an interface
.You can also use a different public name i.e exports.logToFile = log
.You can also export just one function from a module by -
module.exports = log // this is possible because exports is a normal js var, the case above it is a object(dict) here it is a reference to a function
In this case, require() would return the function, not the object. 

To import a module -
	const logger = require('logger')			// looks for inbuilt modules & js files in the same dir with the name logger
	// path of the module also works	// require() is not present in browsers
	logger.log()
	
* VSC - F2 when a function name is selected to rename the defination and all calls of that function

### How Modules work under the hood			// not imp?
.Module Wrapper Function(iife)
Parameters - exports, require, module, __filename, __dirname

### Node Documentation at nodejs.org, click docs, then the LTS API
Names some useful modules
1) Path module - makes it easier to work with file paths, rather than dealing with strings
2) OS - .totalmem(), .freemem()

Template strings in ES 6 -
	To build strings without using concat(+), like in console.log
	e.g - console.log(`Total Memory: ${os.totalmem()}`);			// instead of console.log('Total Memory: '+os.totalmem());

3) File System
There exists synchronous methods along with the usual async methods, always prefer to use async methods
	const fs = require('fs');
	fs.readdir('./', function(err, files) {
		if (err) console.log("Error", err);
		else console.log("Result", files);				//	array with files names in current directory
	});
	
## Events
A lot of functionalities depend on events
4) Events Module
const EventEmitter = require('events');	// EventEmitter is a class in Events
const emitter = new EventEmitter();

// Register a listener, should be before raising an event 		// ?Does it make sense to add multiple listeners to the same event?
emitter.on('messageLogged', function(arg) {						// .on() and .addListener() are the same
	console.log('Listener called ', arg);
});

// Raise an event				// ?Are events the same as exceptions?
emitter.event('messageLogged', {id:1, url: "http://"});			// the object is called the "event argument", used to pass data about the event

* Arrow function in ES6
emitter.on('messageLogged', (arg) => {				// using the => after the () instead of the function keyword

### Accomodating Events in the logger module - 1:02:50 // video needed
1) Make a class in logger.js and make it extend the EventEmitter class. why? - Because we want the functionalities of .emit() and .on() in the object of our class.
2) change emitter.emit() to this.emit() as the object used to create the event listener( outside the class ) and the object calling .emit() must be the same.
* .on() and .emit() must be called on the same object *

final code - app.js
const Logger = require('logger');
const logger = new Logger();

logger.on('messageLogged', (arg) => { 
	console.log('Listener called', arg);
})

logger.log('message');

// logger.js
class Logger extends EventEmitter {
	log(message) {						// function
		// some code to send http request
		console.log(message);
		
		// raise event 
		this.emit('messageLogged', { id: 1, url: 'http://' });
	}
}
module.exports = Logger;

* Functions inside a class don't need to be prefixed by the function keyword *

Extra - why not composition instead of inhertiance - Because we don't need to extend the functionality of .emit() and .on(), we just want them to be accessible to the user using it outside the class - logger.emitter.emit() is extra work and it doesn't enhace readability. The case where composition would be suitable is - when we need to add a wrapper to .emit() and .on() in our class, we would out own functions like .myemit() and .myon() which would call the emitter.emit() and .on() functions inside(emitter is global inside class). We can also use inheritance instead of composition, but composition will enhance readability & debugging in that the user won't get confused about where these functions are coming from.

5) HTTP module -
const http = require('http');

const server = http.createServer((req, res) => {
	if (req.url === '/') {							// sequence of ifs
		res.write('Hello World');
		res.end();
	}
	
	if (req.url === '/api/courses') {
		// some code to fetch from DB
		res.write(JSON.stringify(["course1", "course2", "course3"]);		// JSON is inbuilt?
		res.end();
	}
});

// He removed this code - why?
server.on('connection', (socket) => {
	console.log('New connection...');
});

server.listen(3000);	// listens for requests on port 3000 and raises events like connection & request	// wrapper around this.emit() like .log()
console.log('listening on port 3000...');

Extra - ?why the ===? just == will work here as a number cannot equal '/'

### Need of the framework Express
A sequence of ifs in one function becomes huge and difficult to read & maintain.
It uses the same http module internally.

# Summary + Things to remember -
### Syntax - 
1) functions are the ones with shortcuts in syntax -
	1. No need to type the function keyword in callbacks - ES6 arrow function
	2. No need to type the function keyword in classes
	3. No need to type the semicolon after function defination
	
# Npm basics
- `npm list -g full_module_name` - lists the version installed too.
- To install a specific version of a package use @ - `npm i express@9.0.1` // == in pip
