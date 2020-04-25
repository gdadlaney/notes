# 029 

dev env is configured only for one org.
docker compose file

Docker containers per org. -
1. Certificate Authority(CA)
2. Orderer
3. Peer - depends on CouchDB for state Data
4. CouchDB

Folders
1. Crypto 
2. ConfigTx

will see the scripts for manging the dev env later

- He's using HLF v1 not HLF v12
- export var if needed

Containers need access to channel config. & genesis block - available in ConfigTx, composer folder

Crypto folder - manages certificates(crypt-config dir)

# More about Containers in setup
- CAs can be more than one, in multi-org network
- One orderer of type Solo Orderer is only suitable for development, **for production** use more than one.
- CouchDB - state mngt. for peer
- Single Peer

## Walked through the fabric-dev folder


# Extra 
- Tools used to crate the 2 folders - crytogen, configtxgen. Details not needed

# 030 - scripts

Maintaining the state of env between restarts

- Composer cli tool will be used to create busniess n/w archive files. Also will be used to deploy the files to HF runtime.

- ./startFabric.sh
    - if containers for dev env are up, they are killed & removed i.e any app deployed  or chaincode will be removed.

- ./stopFabric.sh
    - Kills containers and removes them

- fabricUtil.sh
    - added a file fabricUtil.sh - for suspending and restarting w/o loosing deployed apps or chaincode.
    - How to suspend 
        1. start
        2. deploy
        3. fabricUtil.sh stop
        4. fabricUtil.sh start






VLC
Shift + right/left, shift+v