[![Build Status](https://travis-ci.org/sumaiabrinti/cloud-capstone.svg?branch=master)](https://travis-ci.org/sumaiabrinti/cloud-capstone)

# Github Repo Link
https://github.com/sumaiabrinti/cloud-capstone

# Serverless TODO

This repo implements a simple TODO application using AWS Lambda and Serverless framework.

There are two components of the Project
 - Backend 
 - Client 

 # Functionality of the application

This application will allow creating/removing/updating/fetching TODO items. Each TODO item can optionally have an attachment image. Each user only has access to TODO items that he/she has created.

# Backend
The `backend` folder contains the AWS lamda functions which provide the Serverless Todo API. 

It is built and deployed to AWS using TravisCI on each push to master/dev/test branches

`.travis.yml` is located at the root of the project

endpoints:
  GET - https://i35bnoe274.execute-api.us-east-1.amazonaws.com/dev/todos
  POST - https://i35bnoe274.execute-api.us-east-1.amazonaws.com/dev/todos
  PATCH - https://i35bnoe274.execute-api.us-east-1.amazonaws.com/dev/todos/{todoId}
  DELETE - https://i35bnoe274.execute-api.us-east-1.amazonaws.com/dev/todos/{todoId}
  POST - https://i35bnoe274.execute-api.us-east-1.amazonaws.com/dev/todos/{todoId}/attachment
functions:
  RS256Auth: serverless-todo-app-dev-RS256Auth
  GetTodos: serverless-todo-app-dev-GetTodos
  CreateTodo: serverless-todo-app-dev-CreateTodo
  UpdateTodo: serverless-todo-app-dev-UpdateTodo
  DeleteTodo: serverless-todo-app-dev-DeleteTodo
  GenerateUploadUrl: serverless-todo-app-dev-GenerateUploadUrl

# Frontend

The `client` folder contains a web application that can uses the API for Serverless Todo.

The frontend is deployed to and hosted at AWS S3 using Jenkins.
The `Jenkinsfile` is located at the project root. 
This can be configured to be built and deployed on each commit/ pull request using github hooks.


## Authentication

We used auth0 service for authentication



# How to run the application

## Backend

To deploy an application run the following commands:

```
cd backend
npm install
sls deploy -v
```

## Frontend

To run a client application first edit the `client/src/config.ts` file to set correct parameters. And then run the following commands:

```
cd client
npm install
npm run start
```

This should start a development server with the React application that will interact with the serverless TODO application.