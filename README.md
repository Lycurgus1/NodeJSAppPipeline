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

### Other Options
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

**webhook**
- create webhook on github
```http://jenkins.spartaglobal.academy:8080/github-webhook/```

**test ci job**
- set up branch
- do a test commit to test

## Continuous deployment set-up
**enables auto tested code to go to another server and be deployed**
- in this case the website being displayed

**follow readme linked on trello**
- in downlaods folder

**buttons**
- discard old builds
- github project
- sourcecode
	- git
	- use clone github link
	- watch master branch
- build triggers
	- build after other projects arebuilt
	- use name of ci job in projects to watch
	- trigger only if build is stable
- ssh agent
	- specifict credentials
	- add devops student
- build
	- execute shell
 ```
scp -o "StrictHostKeyChecking=no" app ubuntu@3.250.17.181:/home/ubuntu
scp -o "StrictHostKeyChecking=no" environment ubuntu@3.250.17.181:/home/ubuntu
ssh -o "StrictHostKeyChecking=no" ubuntu@3.250.17.181 <<EOF
    sudo bash ./environment/app/provision.sh
    cd app
    pm2 kill
    pm2 start app.js
EOF
```

**problems**
- make sure no apps are running else you may get "port 3000 is already in use" error
