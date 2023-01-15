# UZH IOTA

The project was tested on computers running macOs (intel chip) and Linux operating system. 
To get the project started, you need to have Docker installed. 

## Start the network

cd ~/goshimmer/tools/docker-network

docker-compose -f docker-compose.local.yml -f docker-compose.yml up


## Open dashboards

localhost:8081
localhost:8071
localhost:18081

shows an interface used to see which nodes are active but not using the faucet api



localhost:9000

shows an interface used to see which nodes are active


### faucet node

localhost:8091

shows the interface of the node running the faucet api 


## Start and stop the spammer 

curl --location 'http://localhost:8090/spammer?cmd=start&rate=100'

curl --location 'http://localhost:8090/spammer?cmd=stop'

it possible to change on witch node to start the spammer by changing the port from 8090 to the desidered one


## Get the mana perception of the node in the network. 

curl http://localhost:8090/mana/all -X GET -H 'Content-Type: application/json'

It retrieve the full/short node ID, consensus mana, access mana of each node, and the mana updated time.

## Get information about a specific block 

curl --location --request GET 'http://localhost:8090/blocks/:blockID'

curl --location --request GET 'http://localhost:8090/blocks/:blockID/metadata'

where :blockID is the base58 encoded block ID, e.g. 4MSkwAPzGwnjCJmTfbpW4z4GRC7HZHZNS33c2JikKXJc. It is possible to find an ID of a block also in the dashboard. 
