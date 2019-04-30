# 🚀 LEAN REST API - NodeJS, MongoDB, Fastify & Swagger

The Fastify web framework is highly focused on providing the best developer experience with the least overhead and a powerful plugin architecture. It is inspired by Hapi and Express and currently the fastest web frameworks. The following technologies and toolsare used in this exercise.

## nodemon

nodemon is a tool that helps develop node.js based applications by automatically restarting the node application when file changes in the directory are detected.
nodemon does not require any additional changes to your code or method of development. nodemon is a replacement wrapper for node, to use nodemon replace the word node on the command line when executing your script.

To set up nodemon, we need to add the following line of code to our package.json file, in the scripts object:

“start”: “./node_modules/nodemon/bin/nodemon.js ./src/index.js”,


## mongoose

Mongoose provides a straight-forward, schema-based solution to model your application data. It includes built-in type casting, validation, query building, business logic hooks and more, out of the box.


## fastify

Fastify is a web framework highly focused on providing the best developer experience with the least overhead and a powerful plugin architecture. It is inspired by Hapi and Express and as far as we know, it is one of the fastest web frameworks in town.
fastify-swagger

## Swagger documentation generator for Fastify. It uses the schemas you declare in your routes to generate a swagger compliant doc.


## boom

boom provides a set of utilities for returning HTTP errors.