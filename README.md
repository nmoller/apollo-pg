# fullstack-apollo-express-postgresql-boilerplate

## BD postgres

```bash
docker run --name postgres --network host \
 -e POSTGRES_PASSWORD=root  \
  -e POSTGRES_USER=root   \
  -e POSTGRES_DB=apollo -d \
  postgres:10

  docker run -it --rm -v ${PWD}:/opt/react  -u 1000 \
  --network host --name njsserv -w /opt/react \
  node:11.15.0-stretch \
 npm install
```

Se familiariser avec posgres:

* <https://stackoverflow.com/questions/769683/show-tables-in-postgresql>
* <https://www.robinwieruch.de/postgres-express-setup-tutorial/>
* <http://docs.sequelizejs.com/manual/read-replication.html>
* <https://www.robinwieruch.de/graphql-apollo-server-tutorial/>

```bash
docker exec -it postgres  bash
psql apollo root
```

POur que l'ajout des utilisateurs fonctionne, ajouter:

```bash
DATABASE_URL=postgres://root:root@0.0.0.0:5432/apollo
```

dans le fichier `.env`.

Une fois cela fait, la requête:

```grapql
query {
  user (id:1){
    username
    email
  }
}
```

fonctionne.

### Mutations

* <https://blog.apollographql.com/designing-graphql-mutations-e09de826ed97>
* <https://github.com/apollographql/githunt-api>

### Extra middleware

* <https://stackoverflow.com/questions/25468786/what-does-morgan-module-have-to-do-with-express-apps>
* <https://medium.com/@tobydigz/logging-in-a-node-express-app-with-morgan-and-bunyan-30d9bf2c07a>
* <https://hackernoon.com/build-a-realtime-serverless-graphql-api-with-websockets-on-aws-d9e553a997>

[![Build Status](https://travis-ci.org/the-road-to-graphql/fullstack-apollo-express-postgresql-boilerplate.svg?branch=master)](https://travis-ci.org/the-road-to-graphql/fullstack-apollo-express-postgresql-boilerplate) [![Slack](https://slack-the-road-to-learn-react.wieruch.com/badge.svg)](https://slack-the-road-to-learn-react.wieruch.com/) [![Greenkeeper badge](https://badges.greenkeeper.io/the-road-to-graphql/fullstack-apollo-express-postgresql-boilerplate.svg)](https://greenkeeper.io/)

A full-fledged Apollo Server with Apollo Client starter project with React and Express. [Read more about it in this tutorial to build it yourself](https://www.robinwieruch.de/graphql-apollo-server-tutorial/).

**Family of universal fullstack repositories:**

Server Applications:

* [Node.js with Express + MongoDB](https://github.com/the-road-to-graphql/fullstack-apollo-express-mongodb-boilerplate)
* [Node.js with Express + PostgreSQL](https://github.com/the-road-to-graphql/fullstack-apollo-express-postgresql-boilerplate)

Client Applications:

* [React Client](https://github.com/the-road-to-graphql/fullstack-apollo-react-boilerplate)
* [React Native Client](https://github.com/morenoh149/fullstack-apollo-react-native-boilerplate)

## Features of Client + Server

* React (create-react-app) with Apollo Client
  * Queries, Mutations, Subscriptions
* Node.js with Express and Apollo Server
  * cursor-based Pagination
* PostgreSQL Database with Sequelize
  * entities: users, messages
* Authentication
  * powered by JWT and local storage
  * Sign Up, Sign In, Sign Out
* Authorization
  * protected endpoint (e.g. verify valid session)
  * protected resolvers (e.g. e.g. session-based, role-based)
  * protected routes (e.g. session-based, role-based)
* performance optimizations
  * example of using Facebook's dataloader
* E2E testing

## Installation

* `git clone git@github.com:the-road-to-graphql/fullstack-apollo-express-postgresql-boilerplate.git`
* `cd fullstack-apollo-express-postgresql-boilerplate`
* `touch .env`
* `npm install`
* fill out *.env file* (see below)
* start PostgreSQL database
* `npm start`
* visit `http://localhost:8000` for GraphQL playground

#### .env file

Since this boilerplate project is using PostgreSQL, you have to install it for your machine and get a database up and running. You find everything for the set up over here: [Setup PostgreSQL with Sequelize in Express Tutorial](https://www.robinwieruch.de/postgres-express-setup-tutorial). After you have created a database and a database user, you can fill out the environment variables in the *server/.env* file.

```
DATABASE=mydatabase

DATABASE_USER=postgres
DATABASE_PASSWORD=postgres

SECRET=asdlplplfwfwefwekwself.2342.dawasdq
```

The `SECRET` is just a random string for your authentication. Keep all these information secure by adding the *.env* file to your *.gitignore* file. No third-party should have access to this information.

#### Testing

* adjust `test:run-server` npm script with `TEST_DATABASE` environment variable in package.json to match your testing database name
  * to match it from package.json: `createdb mytestdatabase` with psql
* one terminal: npm run test:run-server
* second terminal: npm run test:execute-test

## Want to learn more about React + GraphQL + Apollo?

* Don't miss [upcoming Tutorials and Courses](https://www.getrevue.co/profile/rwieruch)
* Check out current [React Courses](https://roadtoreact.com)
