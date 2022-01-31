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