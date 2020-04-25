Mosh tutorial - https://www.youtube.com/watch?v=W6NZfCO5SIk
** Port to Hupyter notebook

JS can be used to build Real Time Application(RTAs) like chat, video streaming, online editors, games, etc.

ECMA script is a standard that JS conforms to.

Variables -
	types - var, let, const
	use let instead of var from ES6
	by default names(unless initialized) are undefined
	Camel case Convention for var. names
	Best practise to declare each variable on a new line - why? - (for git?)
	
	Data stored in variables - 
		"typeof var_name" tp get type of var
		1) Primitives - string, numbers(includes int & float), boolean(true, false), undefined, null(to explicitly clear the value of a variable)
		2) Reference types - objects, arrays, functions
		exceptional cases in "typeof" - null & arrays are of type "object"
	
	Static languages - once a datatype is assigned to a variable, it cannot be changed throughout the life of the program
	Dynamic languages - flexible, but need to have check conditions in plcae for robust code - especially for passing arguments to function, sometimes a string may be passed instead of an array, and it may be traversed & the error just cascades down.
	
	objects -
		creation e.g -
			let person = {
				name: "Gaurav",
				age: 30
			};
		access/modify e.g 1 - 
			person.name = 'abc';		console.log(person.name)
		access/modify e.g 2 - 
			let selection = 'name'; 		// value decided at runtime
			person[selection] = 'abc';
	
	arrays - 
		application - list of items in a shopping cart
		declaration e.g -
			let selectedColors = ['red', 'blue'];
		The objects in the array(including their type) and the size of the array is dynamic - flexibility in dynamic languages
		mutation e.g -
			selectedColors[2] = 1;		// no need for .append(), unlike python
		Properties - .length			// like Java
		Other methods -
		1) .push(data) - like .append() in Python
		extra - prototypes, because of which we have the extra attributes inherited to each array object
		
	functions - 
		e.g - 
			function greet(name) {
				console.log('Hello ' + name);		// like Java
			}		// a function declaration does not end with a semicolon, unlike var declarations or statements - why?
		passing arguments are optional in JS // unlike Python, which has the param_name=None syntax for dealing with this
		e.g -
			greet(); 		// "Hello undefined"
		extra - parameter is the one in the function declaration, argument is the one in the function call
		extra - template literals to clear up string addition
		
	# Json
	1) JSON.stringify(obj) - returns a JSON string		// like json.dumps(str) in Python
	2) JSON.parse(json_str) - returns a JS object		// like json.loads(str) in Python 
	
	# New js syntax
	- String ... with ``
	- Destructuring assignment
	
	# Other trics
	- || to sift out null or undefined, e.g - `port = process.env.PORT || 3000;`. ! too, e.g - `if(!error)`
