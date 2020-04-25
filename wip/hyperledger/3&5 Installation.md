# 011

# 012 & 013 & 024 - Complete Installation
See composer docs installation tab alongside

## Actions taken
1. From prereqs-ubuntu.sh
- Added git-core ppa & updated git to 2.19.1
- Composer requires Py2.7, changed the name of the annaconda link to python
- Installed docker-compose.
2. npm installs
- yo - yeoman
- composer-cli
- composer-rest-server
- generator-hyperledger-composer - yeoman generator, skeleton business n/w applications.
3. Others
- VSC extention hyperledger composer
4. Fabric 
- Copy pasting commands from docs. 5 images are seen after lengthy download. +1 composer-playground image.
- Creating peer admin card using script.        // Cards will be useful for connecting to fabric dev environment.

**node-gyp**


### Scripts to start/stop hyperledger -
1. composer-playground -p 5001				// stop by killing container?
2. ./startFabric.sh & ./stopFabric.sh		// inside ~/fabric-tools

# 027 Using the dev toos
Installed docker extention for VSC
Fabric tools(dev) is available in containers

- composer-cli - most comonly used tool, manages business n.w applications on fabric

# 024 (Extra) Shows setup of ubuntu VM on AWS
- We will need to open up ports for each type of container, ca, client, etc.
- putty in win 10 for connecting to server
- do not install HL using root, create a user, and add it to sudoers list

# Extra
- nvm - to allow running of different node versions(subset of pip)
- hyperledger on ubuntu 18?
- full vs para virt - virtual box does one & Hyper-V does the other
- docker toolbox on windows home(boot 2 docker) - full virt?
