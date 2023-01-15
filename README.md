# UZH IOTA

The project was tested on computers running macOs (intel chip) and Linux operating system. 
To get the project started, you need to have Docker installed. 

## Initial install

This removes old docker versions and sets up the new one including the keys:

sudo apt-get remove docker docker-engine docker.io containerd runc

sudo apt-get update

sudo apt-get install \    ca-certificates \    curl \    gnupg \    lsb-release

sudo mkdir -p /etc/apt/keyringscurl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin

sudo docker run hello-world

(last line to check if everything works)

Also if you haven't git clone this repo.


## Start the network

cd ~/goshimmer/tools/docker-network

docker-compose -f docker-compose.local.yml -f docker-compose.yml up


## Open dashboards

http://localhost:8081

http://localhost:8071

http://localhost:18081

opens an interface in which you can get information about the node such as Blocks Per Second and  Memory Usage


http://localhost:9000

shows an interface used to see which nodes are active


### faucet node

http://localhost:8091

shows the interface of the node running the faucet api 


## Start and stop the spammer 

curl --location 'http://localhost:8090/spammer?cmd=start&rate=100'

curl --location 'http://localhost:8090/spammer?cmd=stop'

it possible to change on which node to start the spammer by changing the port from 8090 to the desidered one ( e.g. 
curl --location 'http://localhost:8080/spammer?cmd=start&rate=100')

its also possible to increase ore decrese the rate of the spammer by changing the rate value ( e.g. 
curl --location 'http://localhost:8090/spammer?cmd=start&rate=10')


## Get the mana perception of the node in the network. 

curl http://localhost:8090/mana/all -X GET -H 'Content-Type: application/json'

It retrieve the full/short node ID, consensus mana, access mana of each node, and the mana updated time.

## Get information about a specific block 

curl --location --request GET 'http://localhost:8090/blocks/:blockID'

curl --location --request GET 'http://localhost:8090/blocks/:blockID/metadata'

where :blockID is the base58 encoded block ID, e.g. 4MSkwAPzGwnjCJmTfbpW4z4GRC7HZHZNS33c2JikKXJc. It is possible to find an ID of a block also in the dashboard. 
