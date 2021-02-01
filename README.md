# nodejs_restapi_graphql_mongodb_mongoose_jtw
Nodejs RestAPI Application with GraphQL, JWT Authentication and Mongo DB.
- Backend achieved by Nodejs
- Frontend achieved by Reactjs. (p.s. React Application will be used to access backend. https://github.com/Tzvetelin88/reactjs_hooks_saga_redux)

## Inside:

 - Crеate free account with MongoDB Atlas (https://account.mongodb.com/)
 - Use Mongoose as syntax sugar.
 - Use GraphQL
 - Create Models, Resolvers and Schema
 - Add authentication and validate with JWT.

## Using: 

 -  express           - https://expressjs.com/en/api.html
 -  mongoose          - https://mongoosejs.com/docs/documents.html
 -  MongoDB Cloud     - https://account.mongodb.com/
 -  validator         - https://github.com/validatorjs/validator.js
 -  express-graphql   - https://github.com/graphql/express-graphql 
 -  jsonwebtoken      - https://github.com/auth0/node-jsonwebtoken#readme
 -  bcryptjs		  - https://github.com/kelektiv/node.bcrypt.js#readme

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

## Simple GraphQL Queries:

### USER CREATE/LOGIN/LIST/UPDATE
#### Create a new user object in database with 'Mutation'
```
mutation {
  createUser(userInput: {email: "test@test.com", name: "Test User", password: "test123"}) {
    _id,
    name
  }
}
```
#### Get Created user data with 'Query'
```
{
  login(email: "test@test.com", password: "test123") {
    token
    userId
  }
}
```
#### List User data, e.g. "status"
```
{
  user {
    status
  }
}
```
#### Update User data, e.g. "status"
```
mutation {
  updateStatus(status: "Online") {
    name
    status
  }
}
```

### POST'S GET/CREATE/UPDATE/DELETE
#### Create a new Post object in database with 'Mutation'
```
mutation {
  createPost(postInput:{ title:"test1", content: "Body test 1", imageUrl:"img_url.png" }) {
    _id
    title
    content
    imageUrl
  }
}
```
#### Get Created Post's data with 'Query'
```
{
  posts(page: 1) {
    posts {
      _id
      title
      content
      creator {
        name
      }
    }
    totalPosts
  }
}
```
#### Get Created Post data with 'Query'
```
{
	post(id: "<item_id>") {
    _id
    title
    content
    createdAt
    updatedAt
  }
}
```
#### Update current POST data with Mutation
```
mutation {
  updatePost(id: "<item_id>", postInput:{ title:"test1111", content: "Body test 1111", imageUrl:"img_url.png" }) {
    _id
    title
    content
    imageUrl
  }
}
```
#### Delete current POST data with Mutation
```
mutation {
  deletePost(id: "<item_id>")
}
```
