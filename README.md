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

**buttons**
- discard old builds
- github project 
	- github url
- saving space for webhooks
	- to do later
- restrict where project can
	- sparta-ubuntu-node
- source code managment
	- git, use git@github from your github and credentials
	- branches to build = */dev*
- provide node and npm folder
	- leave defaults
- build
	- execute shell:cd app/
	npm install
	npm test 
- post build actions, gitpublisher
	- push if build succeds
	- merge results
	- branches - master, origin (branch to push, target remote name)
