# Deploy on Heroku

Start by signing up on [Heroku](https://www.heroku.com)

Select _Create a new app_ and in the next screen, choose the name of your app.

It will be the name used in the URL to access your app, so choose wisely!

Also, select _Europe_ as a region.




##  MongoDB Atlas configuration 


<br>



### 1. [Signup for a Free MongoDB Atlas account](https://www.mongodb.com/cloud/atlas/lp/try2)

![](https://i.imgur.com/vKJgkEB.png)



<br>



![](https://i.imgur.com/jLhyP7k.png)



<br>



### 2. [Sign Up & Create a Free Cluster](https://docs.atlas.mongodb.com/tutorial/deploy-free-tier-cluster/)

1. Sign Up for Mongo Atlas - enter the email, password, first name, last name

2. Select  >>>  **Starter Clusters (or Shared Clusters)** 

3. In the drop-down **Cloud Provider & Region** select: 

   -  Europe Region 

4. in the **Cluster Tier** select:

   

5. In the drop-down "**Cluster Tier**" make sure to select:

   -  **M0 Sandbox** - with the flag **Free forever**.

6. Click the button **Create Cluster**



<br>



![](https://i.imgur.com/uxoAE6C.png)



<br>







![](https://i.imgur.com/auYMuhb.png)



<br>





![](https://i.imgur.com/sOOp0vs.png)



<br>



![](https://i.imgur.com/j8kcopJ.png)



<br>





## 3. Setup MongoDB Atlas Cluster:



1. In the sidebar in the **SECURITY** part:

   - select **->  Database Access**

   

   <br>

   

2. Click on **<u>+ ADD NEW USER</u>** to create a new user

   - Select **Read and write to any database** - User Privileges
   - Set the **Username** and **Password**
   - Set **Database User Privileges** to : ***Atlas admin***
   - Create New User

   

   <br>

   

   ![](https://i.imgur.com/L9Pie5j.png)

   

   <br>

   

3. In the sidebar select **SECURITY  ->  Network Access**

   

   <br>



![](https://i.imgur.com/88GeH9u.png)



<br>



4. Click on **<u>+ ADD IP ADDRESS</u>**

- Click on **ALLOW ACCESS FROM ANYWHERE**
- Confirm



<br>



![](https://i.imgur.com/f3tGfbn.png)



<br>



5. Connect To Your Cluster: Click on the gray button **CONNECT**

- Select **Connect Your Application** option
- Choose Your driver version:  **DRIVER**: Node.js
- **Copy** the **Connection String Only**



<br>



![](https://i.imgur.com/btWKcLp.png)



<br>



![](https://i.imgur.com/7pYGh0P.png)





<br>





6. Update the connection string and add the ***username*** and ***password***.



<br>


## Add the Environment variables to heroku and update the monogoose connection in app.js  

You need to make sure that you have all the variables that are in your .env are also saved in Heroku, in the _Config Vars_ section of the _Settings_ tab.

So click on the _Settings_ tab and then on the _RevealConfigVars_ tab. There you enter the configuration variables.

Add the connection string from Atlas that you copied above - MONGODB_URI should be the key and the value is the connection string

The connection string should look something like this 

You will have to replace the database name and the password, the brackets just indicate that this is a variable, (the database name you can choose freely - the password you copied from atlas)
```
mongodb+srv://fullstacksteve:<password>@ironhack.5tfbhz.mongodb.net/<dbname>?retryWrites=true&w=majority
```

If you want to connect your local application to the mongodb Atlas database you have to add a connection string to your .env file:
```
MONGODB_URI=<your connection string to atlas>
``` 

Because we have the following line in in the index.js in the db folder this will now connect to mongodb Atlas if there is an entry in the .env file - otherwise the local connection string will be used.
```js
// db/index.js
const MONGO_URI = process.env.MONGODB_URI || "mongodb://localhost/library";
```

Now if the env variable is set we use it otherwise we just use the local database

Commit the changes and push to the master branch

<br>


### Deploy from GitHub
- Now, click on the _Deploy_ tab and _Connect to GitHub_.

- Select your repo from Github (make sure that your package.json is at the root of your repository) and enable _Automatic Deploys_.

- For the first time, select the manual deploy to deploy your master branch.

- If there is an error, select _More_ > _View Logs_.



## Connect to a GUI with Compass 

Start by copying the MONGODB_URI config variable from the *Settings* tab and then open Compass. You should get a prompt asking if you want to use the URI in your clipboard. Accept and then change the following field: *authentication database* which is set as `admin` and use the value in the *username* field instead.




### Optional: The Heroku Command Line Interface (CLI)

#### If you want to deploy directly to heroku via git or run a script on the server you can also use the Heroku CLI


## Install Heroku CLI


#### [LINK: Docs - Install the Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli#npm)


### If unable to install the CLI via the Standalone installation (using a file) :

```bash
$ npm install -g heroku


$ heroku --version

# heroku/7.0.0 (darwin-x64) node-v8.0.0

$ heroku login
```


<br>



### Deploying with the CLI



While in the server root directory, in the terminal run :



```bash
# Commit the most recent work and merge it to the master branch
$ git add .
$ git commit -m 'Update xyz.js with new middleware'
$ git push origin <branch-name>
```

# Checkout to the master branch
```bash
$ git checkout master
```

# Add heroku remote
```bash
$ heroku git:remote -a <name-of-the-newly-created-app>
```


# Check the remotes available
```bash
$ git remote -v
```

# Make some changes to the code and deploy them to Heroku using Git.
```bash
$ git add .

$ git commit -m 'Make it better'

$ git push heroku master
```

<br>

## Heroku commands


#### To fetch your app’s most recent logs, use the `heroku logs` command:

```bash
$ heroku logs
```

The `logs` command retrieves 100 log lines by default. 

#### You can specify the number of log lines to retrieve (up to a maximum of 1,500 lines) by using the `--num` (or `-n`) option.

```bash
$ heroku logs -n 200
```


### [Real-time tail](https://devcenter.heroku.com/articles/logging#real-time-tail)

#### Real-time tail displays recent logs and leaves the session open for real-time logs to stream in. 

The name of your app can be found on heroku under settings

```bash
$ heroku logs --tail --app <name of your app>

```

## Executing scripts on the server - e.g. running a seed file - after logging in with the Heroku CLI as showed above

```bash
# This opens the terminal connection to our application
$ heroku run bash --app <name of your app>

# We may then run the seed file
$ node bin/seed.js
```

<br>