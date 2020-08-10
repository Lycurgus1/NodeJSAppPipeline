# Creating CICD pipeline

## Continuous integration set-up
**removing git remote**
```git remote --v``` gets current remote
```git remote rm origin``` removes remote

**create new repo**
create repo

**add remote origin**
```git remote add origin git@github.com:Lycurgus1/NodeJSAppPipeline.git```

**push to intialise**
```git push -u origin master```
-sets up remote to track master

**set up jenkins job**
- create, name appropriate name
- job function.name
