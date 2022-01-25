## Create the project

```bash
$ mkdir <name of the project>
```

Add some code 

```bash
$ git init
$ git add .
$ git commit -m 'initial commit'
```

Create a new respository on git and copy the line that adds this repo as a remote and execute it on the command line

```bash
$ git remote add origin <url to the repository>.git
$ git push origin master
```

### Follow the steps in this guide to deploy your app to GitHub Pages

https://docs.github.com/en/github/working-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

#### TLDR;

* Navigate to your GitHub Repository of the project that you want to deploy

* Click on Settings at the top

* Under "GitHub Pages", use the None or Branch drop-down menu and select master as a publishing source.

* Click the save button

* You should see the URL where the app can be accessed

* You only need to do this once - whenever you push now to master the app is automatically updated

#### 🚨 Update can take a few minutes 🚨