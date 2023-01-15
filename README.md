# Start the network

cd ~/goshimmer/tools/docker-network

docker-compose -f docker-compose.local.yml -f docker-compose.yml up



# Start and stop the spammer 

curl --location 'http://localhost:8080/spammer?cmd=start&rate=100'
curl --location 'http://localhost:8080/spammer?cmd=stop'


# Get the mana perception of the node in the network. You can retrieve the full/short node ID, consensus mana, access mana of each node, and the mana updated time.

curl http://localhost:8080/mana/all -X GET -H 'Content-Type: application/json'


# POST request asking for funds from the faucet to be transferred to address in the request.

curl --location --request POST 'http://localhost:8080/faucet' \
--header 'Content-Type: application/json' \
--data-raw '{
    "address": "target address",
    "accessManaPledgeID": "nodeID",
    "consensusManaPledgeID": "nodeID",
  "nonce": 50
}'

https://wiki.iota.org/shimmer/goshimmer/apis/faucet/






curl --location --request GET 'http://localhost:8080/blocks/:blockID'

curl --location --request GET 'http://localhost:8080/blocks/:blockID/metadata'

# where :blockID is the base58 encoded block ID, e.g. 4MSkwAPzGwnjCJmTfbpW4z4GRC7HZHZNS33c2JikKXJc.
