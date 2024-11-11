HOW TO PULL ELASTICSEARCH DOCKER IMAGE
*********************************************

Requirements -> Anaconda with Python 3.11 and elasticsearch 8.11.3

Step1: You must download docker desktop and create a docker account.

Step2: 
- Go inside the Pull project directory provided to you.

- Open docker-compose.yml and update the docker image name with
	YOUR-DOCKERHUB-USERNAME/[REPOSITORY[:TAG]] (This will be the image that you pushed to docker hub).
	
	For example : jakkagunith/elasticsearch_vector:multi

Step3: Navigate to this directory and open the terminal/cmd and run following command:

	docker-compose up -d

	This will pull the image jakkagunith/elasticsearch_vector:multi from Docker hub and will run the container for it.

"docker-compose up" uses docker-compose.yml file that contains all the information about the image, such as services, port, volumes, etc.

Alternatively, you can also do :

1. docker pull YOUR-DOCKERHUB-USERNAME/[REPOSITORY[:TAG]]

For example: 

docker pull jakkagunith/elasticsearch_vector:multi

2. docker run -d \
  -e "discovery.type=single-node" \
  -e "xpack.security.enabled=false" \
  -e "node.name=localhost" \
  -e "network.host=0.0.0.0" \
  -p 9200:9200 \
  --name elasticsearch \
  YOUR-DOCKERHUB-USERNAME/[REPOSITORY[:TAG]] 

  For example: docker run -d \
  -e "discovery.type=single-node" \
  -e "xpack.security.enabled=false" \
  -e "node.name=localhost" \
  -e "network.host=0.0.0.0" \
  -p 9200:9200 \
  --name elasticsearch \
  jakkagunith/elasticsearch_vector:multi

Verify that elasticsearch is running and the data can be fetched

1. Go to your browser and type localhost:9200 and press Enter.

If you see a JSON response, this means it is running fine.

2. Update the "Pull_GitHub_Issues" python script with your OpenAI API key and run the script to fetch the data, if data is visible, then all steps were a success.

Docker image and the running container can also been checked on Docker desktop.