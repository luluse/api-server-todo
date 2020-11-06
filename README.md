# api-server-todo

An Express/Node.js based server designed to be a “model agnostic” REST API server, which can perform CRUD operations on any data model

## Author: Lulu Sevignon

## Users stories
- As a developer, I want to CREATE a new record in a database, using the POST method on a custom API
- As a developer, I want the API to return the record I create in JSON format
- As a developer, I want to GET list of all records in a database, using the GET method on a custom API
- As a developer, I want the API to return an object containing count, and a results[] array
- As a developer, I want to GET an existing in a database, using the GET method with an ID parameter on a custom API
- As a developer, I want the API to return an object containing the record from the database
- As a developer, I want to UPDATE an existing record in a database, using the PUT and PATCH methods with an ID parameter on a custom API
- As a developer, I want the API to return the record I updated in JSON format
- As a developer, I want to DELETE an existing record in a database, using the DELETE method with an ID parameter on a custom API
- As a developer, I want the API to return the record I updated in JSON format
- As a developer, I want Swagger documentation for this API so that I can make it easier for other developers to use and understand

## Links and Resources

[Dynamic API Server - Business Requirements](https://codefellows.github.io/code-401-javascript-guide/curriculum/apps-and-libraries/api-server/)
 
## Setup

1. Clone down this repo locally
2. Run `npm i` in root directory
3. Add `.env` file with following setup: `PORT=` and `MONGODB_URI=`
4. In one terminal turn on server using `node .` or `node index.js`
5. Use Postman or HTTPie in another terminal to perform CRUD operations on data models

### Products Schema:

- name: { type: String, required: true },
- display_name: { type: String, required: true },
- category: { type: String, required: true },
- description: { type: String },

### categories Schema:
- name: { type: String, required: true },
- description: { type: String, required: true },


#### Support all REST/HTTP methods
- GET: Retrieve record(s) from a data source
    - All
    - One (by id)
    - Some (by filtering)
- POST: Create a new record in a data source
- PUT: Update a single full record in a data source
- PATCH: Update part of a single record in a data source
- DELETE: Delete a record in a data source

#### Standard routing structure

i.e. http://localhost:3000/api/v1/products/12345

- `/api/v#` where # is the version number of our API
  - `/model` where ‘model’ is the name of the data model to operate on
    - `/id` where ‘id’ is the id number of a specific entity in the data model


- Allow for Query String parameters for filtering
  - i.e. http://localhost:3000/api/v1/products?category=electronics
  - This would GET every entry in our products data model where the category is ‘electronics’


## Technical Requirements

- Node.js
- ES6 Classes
- ExpressJS Web Server, built modularly
    - Middleware for handling 404 and 500 conditions
    - Middleware for handling the dynamic loading of the correct data model as specified in the route
    - Use a single router (v1.js) to handle the ReST methods for CRUD for any model
      
- Persistence using a Mongo Database
- Mongoose Schemas to define and model data
- Mongoose Model “wrapper” class to serve as the API between the express server and the data models themselves
- Test Driven Development, using Jest
