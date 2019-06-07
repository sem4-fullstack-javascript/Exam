# Exam

## Babel/WebPack

### Explain (some) of the purposes with the tools Babel and WebPack, using  examples from the exercises

#### Babel
Babel is a JavaScript transpiler that converts edge JavaScript into plain old ES5 JavaScript that can run in any browser (even the old ones).

It makes available all the syntactical sugar that was added to JavaScript with the new ES6 specification, including classes, fat arrows and template literals.

#### WebPack
ES6 modules allow the JavaScript developer to break their code up into manageable chunks, but the consequence of this is that those chunks have to be served up to the requesting browser, potentially adding dozens of additional HTTP requests back to the server — something we really ought to be looking to avoid. This is where webpack comes in.

Webpack is a module bundler. Its primary purpose is to process your application by tracking down all its dependencies, then package them all up into one or more bundles that can be run in the browser.

## Callbacks, Promises and async/await

### Explain about promises in ES-6 including, the problems they solve, a quick explanation of the Promise API and:

The `Promise` object represents the eventual completion (or failure) of an asynchronous operation, and its resulting value.  
A `Promise` is a proxy for a value not necessarily known when the promise is created. It allows you to associate handlers with an asynchronous action's eventual success value or failure reason. This lets asynchronous methods return values like synchronous methods: instead of immediately returning the final value, the asynchronous method returns a promise to supply the value at some point in the future.  
A `Promise` is in one of these states:

- pending: initial state, neither fulfilled nor rejected.
- fulfilled: meaning that the operation completed successfully.
- rejected: meaning that the operation failed.

A pending promise can either be *fulfilled* with a value, or *rejected* with a reason (error). When either of these options happens, the associated handlers queued up by a promise's `then` method are called.  
If the promise has already been fulfilled or rejected when a corresponding handler is attached, the handler will be called, so there is no race condition between an asynchronous operation completing and its handlers being attached.

As the `Promise.prototype.then()` and `Promise.prototype.catch()` methods return promises, they can be chained.

#### Example(s) that demonstrate how to avoid the callback hell  (“Pyramid of Doom")

**Pyramid of Doom**
```js
doSomething(function(responseOne) {
    doSomethingElse(responseOne, function(responseTwo, err) {
        if (err) { handleError(err); }
        doMoreStuff(responseTwo, function(responseThree, err) {
            if (err) { handleAnotherError(err); }
            doFinalThing(responseThree, function(err) {
                if (err) { handleAnotherError(err); }
                // Complete
            }); // end doFinalThing
        }); // end doMoreStuff
    }); // end doSomethingElse
}); // end doSomething
```
**Solution**
```js
doSomething()
.then(doSomethingElse)
.catch(handleError)
.then(doMoreStuff)
.then(doFinalThing)
.catch(handleAnotherError)
```

#### Example(s) that demonstrate how to execute asynchronous (promise-based) code in serial or parallel

```js
var arrayOfPromises = [] // array containing promises

Promise.all(arrayOfPromises)
.then(function(arrayOfResults) {
    /* Do something when all Promises are resolved */
})
.catch(function(err) {
    /* Handle error is any of Promises fails */
})
```

#### Example(s) that demonstrate how to implement our own promise-solutions.

```js
function get(url) {
  return new Promise(function(resolve, reject) {
    var req = new XMLHttpRequest();
    req.open('GET', url);
    req.onload = function() {
      if (req.status == 200) { 
          resolve(req.response); /* PROMISE RESOLVED */
      } else { 
          reject(Error(req.statusText)); /* PROMISE REJECTED */
      }
    };
    req.onerror = function() { reject(Error("Network Error")); };
    req.send();
  });
}
```

#### Example(s) that demonstrate error handling with promises

Since both the success and error functions are optional, we can split them into two `.then()`s for better readability.

```js
get(url)
.then(function(response) {
    /* successFunction */
}, undefined)
.then(undefined, function(err) {
    /* errorFunction */
})
```
To make things even more readable, we make use of the `.catch()` method, which is a shorthand for a `.then(undefined, errorFunction)`.
```js
get(url)
.then(function(response) {
    /* successFunction */
})
.catch(function(err) {
    /* errorFunction */
})
```

### Explain about JavaScripts async/await
*How it relates to promises and reasons to use it compared to the plain promise API.*

Async Await is syntactic sugar that changes the .then notation to more readable syntax. Instead of making a . connection between the promises the keyword awaitcan be used instead.

### Provide examples to demonstrate:

#### Why this often is the preferred way of handling promises

```js
function async myFunc() {
    const res = await fetch(...)
    const json = res.json()
    // ...
}
```

#### Error handling with async/await

```js
function async myFunc() {
    try {
        const res = await fetch(...)
        const json = res.json()
        // ...
    } catch (err) {
        new Error(err)
    } 
}
```

#### Serial or parallel execution with async/await.

Async/await makes asynchronous code look and behave like synchronous code

```js
async function SerialFlow(){
    let result1 = await doJob(1,1);
    let result2 = await doJob(2,2);
    let result3 = await doJob(3,3);
    let finalResult = result1+result2+result3;
    console.log(finalResult);
    return finalResult; 
}
```

## ES6,7,8... and TypeScript

-	Explain the two strategies for improving JavaScript: ES6 (es2015) + ES7, versus Typescript. What does it require to use these technologies: In our backend with Node and in (many different) Browsers
-	Provide examples and explain the es2015 features: let, arrow functions, this, rest parameters, de-structuring assignments, maps/sets etc.
-	Explain and demonstrate how es2015 supports modules (import and export) similar to what is offered by NodeJS.
-	Provide an example of ES6 inheritance and reflect over the differences between Inheritance in Java and in ES6.
-	Provide examples with es-next, running in a browser, using Babel and Webpack
-	Provide a number of examples to demonstrate the benefits of using TypeScript, including, types, interfaces, classes and generics
-	Explain the ECMAScript Proposal Process for how new features are added to the language (the TC39 Process) 

## Geo-data, GeoJSON, Geospatial Queries with MongoDB, React Native/Expo’s Location and MapView Components

-	Explain and demonstrate basic Geo-JSON, involving as a minimum, Points and Polygons
-	Explain and demonstrate ways to create Geo-JSON test data
-	Explain the typical order of longitude and latitude used by Server Side API’s and Client Side API’s
-	Explain and demonstrate a REST API that implements geo-features, using a relevant geo-library and plain JavaScript
-	Explain and demonstrate a REST API that implements geo-features, using Mongodb’s geospatial queries and indexes.
-	Explain and demonstrate a React Native Client that uses geo-components (Location, MapView, etc.)
-	Demonstrate both server and client-side, of the geo-related parts of your implementation of the mini project

## GraphQL

-	Explain shortly about GraphQL, its purpose and some of its use cases
-	Explain some of the Server Architectures that can be implemented with a GraphQL backend
-	What is meant by the terms over- and under-fetching in relation to REST
-	Explain shortly about GraphQL’s type system and some of the benefits we get from this
-	Explain shortly about GraphQL Schema Definition Language, and provide a number of examples of schemas you have defined.
-	Provide a number of examples demonstrating data fetching with GraphQL. You should provide examples both running in a Sandbox/playground and examples executed in an Apollo Client
-	Provide a number of examples demonstrating creating, updating and deleting with Mutations. You should provide examples both running in a Sandbox/playground and examples executed in an Apollo Client.
-	Explain the Concept of a Resolver function, and provide a number of simple examples of resolvers you have implemented in a GraphQL Server.
-	Explain the benefits we get from using a library like Apollo-client, compared to using the plain fetch-API
-	In an Apollo-based React Component, demonstrate how to perform GraphQL Queries, including:
    -	Explain the structure of the Query Component
    -	Explain the purpose of ApolloClient and the ApolloProvider component
    -	Explain the purpose of the gql-function (imported from graphql-tag)
-	In an Apollo-based React Component, demonstrate how to perform GraphQL Mutations?
-	Demonstrate and highlight important parts of a “complete” GraphQL-app using Express and MongoDB on the server side, and Apollo-Client on the client.

## Mocha/Chai – testing

-	Explain, using relevant examples, concepts related to testing a REST-API using Node/JavaScript + relevant packages
-	Explain, using relevant examples, about testing JavaScript code, relevant packages (Mocha etc.) and how to test asynchronous code.
-	Explain, using relevant examples, different ways to mock out databases, HTTP-request etc.

## Node.js + Express

-	Explain generally about node.js, when it “makes sense” and npm, and how it “fits” into the node echo system
-	Explain about the Event Loop in Node.js
-	Explain using sufficient code examples the following features in JavaScript. 
    -	Provide examples of user-defined reusable modules implemented in Node.js
-	Why would you consider a Scripting Language as JavaScript as your Backend Platform?
-	Explain the difference between “Debug outputs” and application logging. What’s wrong with console.log(..) statements in our backend-code.
-	Demonstrate a system using application logging and “colored” debug statements.
-	Explain Pros & Cons in using Node.js + Express to implement your Backend compared to a strategy using, for example, Java/JAX-RS/Tomcat
-   Node.js uses a Single Threaded Non-blocking strategy to handle asynchronous task. Explain strategies to implement a Node.js based server architecture that still could take advantage of a multi-core Server.
-	Explain briefly how to deploy a Node/Express application including how to solve the following deployment problems:
    -	Ensure that you Node-process restarts after a (potential) exception that closed the application
    -	Ensure that you Node-process restarts after a server (Ubuntu) restart
    -   Ensure that you can take advantage of a multi-core system
    -	Ensure that you can run “many” node-applications on a single droplet on the same port (80)
-	Explain, using relevant examples, the Express concept: middleware.
-	Explain, using relevant examples, how to implement sessions and the legal implications of doing this
-	Compare the express strategy toward (server side) templating with the one you used with Java on second semester.
-	Demonstrate a simple Server Side Rendering example using a technology of your own choice (pug, EJS, ..).
-	Explain, using relevant examples, your strategy for implementing a REST-API with Node/Express and show how you can "test" all the four CRUD operations programmatically using, for example, the Request package.
-	Explain, preferably using an example, how you have deployed your node/Express applications, and which of the Express Production best practices you have followed.

## NoSQL, MongoDB and Mongoose

-	Explain, generally, what is meant by a NoSQL database.
-	Explain Pros & Cons in using a NoSQL database like MongoDB as your data store, compared to a traditional Relational SQL Database like MySQL.
-	Explain reasons to add a layer like Mongoose, on top on of a schema-less database like MongoDB
-	Explain about indexes in MongoDB, how to create them, and demonstrate how you have used them.
-	Explain, using your own code examples, how you have used some of MongoDB's "special" indexes like TTL and 2dsphere
-	Demonstrate, using a REST-API you have designed, how to perform all CRUD operations on a MongoDB
-	Explain the benefits of using Mongoose, and demonstrate, using your own code, an example involving all CRUD operations
-	Explain the “6 Rules of Thumb: Your Guide Through the Rainbow” as to how and when you would use normalization vs. denormalization.
-	Demonstrate, using your own code-samples, decisions you have made regarding → normalization vs denormalization 
-	Explain, using a relevant example, a full JavaScript backend including relevant test cases to test the REST-API (not on the production database)

## PWA

-	Explain at a conceptual level about Progressive Web Apps and how they promise to change the way we think about WEB and APP development
-	Explain the rationale behind the course materials suggestion “Mobile First”
-	What is a Service Worker and why is it necessary for a PWA.
-	What can Service Workers do?
-	Explain, using an example, about the Service Worker Lifecycle AND a some of the Service Worker Events.
-	Demonstrate, using an example, how to use the caching API to implement, among other things, off-line capabilities
-	Explain, and demonstrate what it takes to provide “add to home screen” capabilities to a PWA
-	Depending on what you have chosen during this period pick ONE of the following.
    -	Explain, and if possible, demonstrate what it takes to add Push Notifications to a PWA
    -	Explain and demonstrate a simple PWA made with React

## Vanilla JavaScript

### Explain the differences between Java and JavaScript. You should include both topics related to the fact that Java is a compiled language and JavaScript a scripted language, and general differences in language features
*You should include both topics related to the fact that Java is a compiled language and JavaScript a scripted language, and general differences in language features.*

||Java|JavaScript|
|-|-|-|
|Compiled vs Interpreted|Java is a compiled programming language.<br>Java is compiled into bytecode and run on a virtual machine|JavaScript is an interpreted scripting language.<br>JavaScript can be interpreted directly by a browser in the syntax it is written.|
|Static vs Dynamic Type Checking|Java uses static type checking, where the type of a variable is checked at compile-time. The programmer must specify the type (integer, double, string, etc.) of any variable they create.|JavaScript, like most scripting languages, uses dynamic typing, where type safety is verified at runtime. It is not required for a programmer to specify the type of any variable they create.|
|Concurrency|Java makes use of multiple threads to perform tasks in parallel.|JavaScript, particularly as it exists as Node.js in server-side applications, handles concurrency on one main thread of execution via a queue system called the event loop, and a forking system called Node Clustering.|
|Class Based vs Prototype Based|Java follows class based inheritance—a top down, hierarchical, class-based relationship whereby properties are defined in a class and inherited by an instance of that class.|In JavaScript, inheritance is prototypal—all objects can inherit directly from other objects. Hierarchy is accomplished in JavaScript by assigning an object as a prototype with a constructor function.|

### Explain the purpose of “use strict” and Linters, exemplified with ESLint
The "use strict" directive was new in ECMAScript version 5. It is not a statement, but a literal expression, ignored by earlier versions of JavaScript. The purpose of "use strict" is to indicate that the code should be executed in "strict mode". With strict mode, you can not, for example, use undeclared variables.

"Use strict" and linters are tools to protect us form ourselves. They warn us when our code contains a syntax error, and tells us if the variable we defined or assigned a value isn't being used. This improves the quality of our code, and may save time we would have use on debuging.

### Explain using sufficient code examples the following features in JavaScript. 
#### Variable/function-Hoisting
Hoisting means lifting up. A `var` declaration is lifted to the top of its scope.
```js
console.log(x)
var x = 10
```
is equivalent with
```js
var x
console.log(x)
x = 10
```
the declaration of x is hoisted not the assignment.
Like `var` declaration, a function is also hoisted

#### this in JavaScript and how it differs from what we know from Java/.net.
`this` in JavaScript typically refers to the function it is called in, while in Java it refers to the class.

```js
function Car(make,model) {
    this.make = make;
    this.model = model;
    this.show = function(){setTimeout(function(){ //This function gets it's own "this"
        console.log(this.make + ", " + this.model);
    },0)};
}
var car = new Car("Volvo","V70");
car.show();
```
output
```
undefined, undefined
```
if a function is defined as a arrow function it does not get its own `this`
```js
function Car(make,model) {
    this.make = make;
    this.model = model;
    this.show = function(){setTimeout(()=>{ //This function doesn't gets it's own "this"
        console.log(this.make + ", " + this.model);
    },0)};
}
var car = new Car("Volvo","V70");
car.show();
```
output
```
Volvo, V70
```

#### Function Closures and the JavaScript Module Pattern
##### Closures

A closure is an inner function that has access to the outer (enclosing) function's variables—scope chain. The closure has three scope chains: it has access to its own scope (variables defined between its curly brackets), it has access to the outer function's variables, and it has access to the global variables.  
The inner function has access not only to the outer function’s variables, but also to the outer function’s parameters. Note that the inner function cannot call the outer function’s arguments object, however, even though it can call the outer function’s parameters directly.

```js
function showName (firstName, lastName) {
    var nameIntro = "Your name is ";
        // this inner function has access to the outer function's variables, including the parameter
    function makeFullName () {
        return nameIntro + firstName + " " + lastName; 
    }
    return makeFullName ();
}
showName ("Michael", "Jackson");
```
output
```
Your name is Michael Jackson
```

##### Module Pattern

The Module pattern was originally defined as a way to provide both private and public encapsulation for classes in conventional software engineering.  
In JavaScript, the Module pattern is used to further emulate the concept of classes in such a way that we're able to include both public/private methods and variables inside a single object, thus shielding particular parts from the global scope. What this results in is a reduction in the likelihood of our function names conflicting with other functions defined in additional scripts on the page.

```js
var modularpattern = (function() {
    // your module code goes here
    var sum = 0 ;

    return {
        add:function() {
            sum = sum + 1;
            return sum;
        },
        reset:function() {
            return sum = 0;    
        }  
    }   
}());
console.log(modularpattern.add())
console.log(modularpattern.add())
console.log(modularpattern.reset())
```
output
```
1
2
0
```

#### Immediately-Invoked Function Expressions (IIFE)
```js
(function(){/*do stuff*/})()
```

#### JavaScripts Prototype
```js
const names = ['Lars', 'Jan', 'Peter', 'Bo', 'Frederik']
names.prototype.myMap = function(callback){
    let arr = []
    for(let i = 0; i < this.length; i++){
        arr.push(callback(this[i]))
    }
    return arr
}
```

#### User-defined Callback Functions (writing your own functions that take a callback)
```js
function myFilter(callback){
    let arr = []
    for(let i = 0; i < this.length; i++){
        if(callback(this[i])){
            arr.push(this[i])
        }
    }
    return arr
}
```

#### Explain the methods map, filter and reduce
`Array.prototype.map()`: The `map()` method creates a new array with the results of calling a provided function on every element in the calling array.
```js
const numbers = [2, 3, 4, 5]
const mappedNumbers = numbers.map((e) => e * 2)
console.log(mappedNumbers);
```
output
```
[4, 6, 8, 10]
```

`Array.prototype.filter()`: The `filter()` method creates a new array with all elements that pass the test implemented by the provided function.
```js
const names = ['Lars', 'Jan', 'Peter', 'Bo', 'Frederik']
const filteredNames = names.filter(name => name.length <= 3)
console.log(filteredNames)
```
output
```
["Jan", "Bo"]
```

`Array.prototype.reduce()`: The `reduce()` method executes a reducer function (that you provide) on each member of the array resulting in a single output value.  

The reducer function takes four arguments:

1. Accumulator (acc)
2. Current Value (cur)
3. Current Index (idx)
4. Source Array (src)

Your reducer function's returned value is assigned to the accumulator, whose value is remembered across each iteration throughout the array and ultimately becomes the final, single resulting value.
```js
const numbers = [2, 3, 4, 5]
const reducer = (acc, cur, idx, src) => accumulator + currentValue)
console.log(numbers.reduce(reducer);
```
output
```
14
```