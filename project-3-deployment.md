# Deploy on Heroku

## The project structure should be exactly like outlined in the project-3-structure guide example.

## Follow the steps from the guide for project 2 - you also need to connect the GitHub Repo, create the MongoAtlas Cluster and add all the environment variables on Heroku, including the MongoDB connection string.

## To create a new Cluster on MongoAtlas you have to create a new project. 
- https://docs.atlas.mongodb.com/tutorial/manage-projects/#create-a-project

## React deploy

As for the first time, you should initialize your git repo so that your server code is at the root level.

This should be the structure you have at the root level: 

![root-level structure](https://i.imgur.com/Xihs4uP.png)

Start by running `npm run build` inside your `client` folder, this will create the static files that we'll need to serve.

![npm run build](https://i.imgur.com/VWsclun.png)

This is what the `client` folder structure should look like: 

![client structure](https://i.imgur.com/3J9U4gQ.png)

Notice that the build folder is ignored by create-react-app:

![create-react-app .gitignore](https://i.imgur.com/RA3UmIT.png)


To add it to our commit, we will need to run `git add -f ` (force):

![git add -f](https://i.imgur.com/34seZ0K.png)

(and commit 😉)

🚨 We will need to run `npm run build` and to add and commit the changes (also to the `/build` folder) every time we write new code on the client side 

### Changes to server/app.js

Don't forget to link to `process.env.MONGODB_URI` for the mongoose connection.

We need to add this line to app.js so that express servers the build folder which contains the React app: 

```js
// app.js
const path = require('path');
app.use(express.static(path.join(__dirname, "/client/build")));
```

And finally, add this at the very bottom of your app.js, after any other route:

```js
app.use((req, res) => {
  // If no routes match, send them the React HTML.
  res.sendFile(__dirname + "/client/build/index.html");
});
```

The end of the app.js file will now look like this:
```js
const path = require('path');
app.use(express.static(path.join(__dirname, "/client/build")));

app.use((req, res) => {
  // If no routes match, send them the React HTML.
  res.sendFile(__dirname + "/client/build/index.html");
});


// ❗ To handle errors. Routes that don't exist or errors that you handle in specific routes
require("./error-handling")(app);

module.exports = app;
```

## Alternative to building the app before commiting it to GitHub

#### Install concurrently to be able to start client and server at the same time

```bash
$ npm install concurrently
```

#### Update 'scripts' in your root level package.json to this

```json
//
  "scripts": {
    "start": "node server.js",
    "install": "cd client && npm install",
    "build": "cd client && npm run build",
    "server": "nodemon server.js",
    "client": "npm start --prefix client",
    "dev": "concurrently --kill-others \"npm run server\" \"npm run client\""
  },
```

#### Locally you can now use this command to start server and client at once

```bash
$ npm run dev
```

And... that's it! Happy deployment 🐕 🚀