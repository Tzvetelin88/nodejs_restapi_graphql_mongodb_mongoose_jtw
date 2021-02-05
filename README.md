# nodejs_restapi_graphql_mongodb_mongoose_jtw
Nodejs RestAPI Application with GraphQL, JWT Authentication and Mongo DB.
- Backend achieved by Nodejs
- Frontend achieved by Reactjs. (p.s. [React Application](https://github.com/Tzvetelin88/reactjs_hooks_saga_redux) will be used to access backend.)

## Inside:

 - Crеate free account with MongoDB Atlas (https://account.mongodb.com/)
 - dotenv to set environment variables (dev/prod/test/stage) (In real env use DevOps stack - PipeLines, Releases etc.)
 - Use Mongoose as syntax sugar.
 - Use GraphQL
 - Create Models, Resolvers and Schema
 - Add authentication and validate with JWT.

## Using: 

 -  express           - https://expressjs.com/en/api.html
 -  dotenv			         - https://www.npmjs.com/package/dotenv
 -  mongoose          - https://mongoosejs.com/docs/documents.html
 -  MongoDB Cloud     - https://account.mongodb.com/
 -  validator         - https://github.com/validatorjs/validator.js
 -  express-graphql   - https://github.com/graphql/express-graphql 
 -  jsonwebtoken      - https://github.com/auth0/node-jsonwebtoken#readme
 -  bcryptjs		        - https://github.com/kelektiv/node.bcrypt.js#readme

## Only one Route: 
``` 
   - http://localhost:8080/graphql
```

## API Schema:
```
type RootQuery {
    login(email: String!, password: String!): AuthData!
    posts(page: Int): PostData!
    post(id: ID!): Post!
    user: User!
}

type RootMutation {
    createUser(userInput: UserInputData): User!
    createPost(postInput: PostInputData): Post!
    updatePost(id: ID!, postInput: PostInputData): Post!
    deletePost(id: ID!): Boolean
    updateStatus(status: String!): User!
}
```

## How to use:
 - Go to https://account.mongodb.com/ and crеate free account with MongoDB Atlas
 - Clone the repo
 - run "npm install" to install all packages from package.json
 - Set your environment variables in .env file - PORT and MONGODB_URL
 - Visit Application URL: https://localhost:<PORT>/  
 - Write API request with Postman (example: [GraphQL.postman_collection](https://github.com/Tzvetelin88/nodejs_restapi_graphql_mongodb_mongoose_jtw/blob/main/GraphQL.postman_collection.json)) or [React Application](https://github.com/Tzvetelin88/reactjs_hooks_saga_redux).
   Import "GraphQL.postman_collection" to your Postman for testing.


## P.S.
#### In next release we will re-write all .then() promises with async/await for more readable and structured code!
#### Still you can use the new ECMA syntax to import/export, but be aware that many are still Experimental, depends of the version of Nodejs:
 - v.15 https://nodejs.org/api/esm.html
 - v.14 https://nodejs.org/docs/latest-v14.x/api/esm.html

#### Will rewrite to TypeScript
