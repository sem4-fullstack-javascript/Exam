# Exam

## Babel/WebPack

-	Explain (some) of the purposes with the tools Babel and WebPack, using  examples from the exercises

## Callbacks, Promises and async/await

-	Explain about promises in ES-6 including, the problems they solve, a quick explanation of the Promise API and:
    -	Example(s) that demonstrate how to avoid the callback hell  (“Pyramid of Doom")
    -	Example(s) that demonstrate how to execute asynchronous (promise-based) code in serial or parallel
    -	Example(s) that demonstrate how to implement our own promise-solutions.
    -	Example(s) that demonstrate error handling with promises
-	Explain about JavaScripts async/await, how it relates to promises and reasons to use it compared to the plain promise API
-	Provide examples to demonstrate 
    -	Why this often is the preferred way of handling promises
    -	Error handling with async/await
    -	Serial or parallel execution with async/await

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

-	Explain the differences between Java and JavaScript. You should include both topics related to the fact that Java is a compiled language and JavaScript a scripted language, and general differences in language features
-	Explain the purpose of “use strict” and Linters, exemplified with ESLint
-	Explain using sufficient code examples the following features in JavaScript. 
    -	Variable/function-Hoisting
    -	this in JavaScript and how it differs from what we know from Java/.net.
    -	Function Closures and the JavaScript Module Pattern
    -	Immediately-Invoked Function Expressions (IIFE)
    -	JavaScripts Prototype
    -	User-defined Callback Functions (writing your own functions that take a callback)
    -	Explain the methods map, filter and reduce
