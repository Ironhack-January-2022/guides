### One team member creates the repo on GitHub either in their personal account or as an organization. Then you add the others as collaborators. -> Settings -> Manage access


### Start the project with Ironlauncher

```bash
$ npx ironlauncher <ProjectName>
```
or if you have ironlauncher installed globally
```bash
$ ironlauncher <ProjectName>
```

### Then you push the the project to GitHub - you have to also copy paste the line to add the remote repository

```bash
$ git init
$ git add .
$ git commit -m 'initial commit'
$ git push origin master
```

### Then the other team menbers clone the project to their computers

In the repository on GitHub got to Settings -> Manage Access and add the other team members as collaborators.