cd ~/goshimmer/tools/docker-network

docker-compose -f docker-compose.local.yml -f docker-compose.yml up



# Start and stop the spammer 

curl --location 'http://localhost:8080/spammer?cmd=start&rate=100'
curl --location 'http://localhost:8080/spammer?cmd=stop'

