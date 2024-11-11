ELASTICSEARCH - VECTOR DB
***************************

Requirements -> Anaconda with Python 3.11 and elasticsearch 8.11.3

Step1: You must download docker desktop and create a docker account.

Step2: Open the terminal and navigate to Push directory and using the command below pull the original elasticsearch 8.11.3 image from docker hub and run a container out of it:
	
	docker-compose up -d

Step3: Make/run the "Push_GitHub_Issues" python script for creating changes.
	-> Before executing the script add your GitHub Username and Token in the script in the headers object and also add your OpenAI API key to the script.
	-> The data/changes can be seen inside this path of elasticsearch container-> /usr/share/elasticsearch/data

Before pushing the image, you need to commit the changes

Step4: Open the terminal and run docker ps, get the container ID from it.

Step5: Follow this to create commit command :

	 docker commit containerID YOUR-DOCKER-USERNAME/[REPOSITORY[:TAG]]

	 For example : docker commit 6c31284597e6 jakkagunith/elasticsearch_vector:latest

	 Note: If you will not mention a tag it will automatically give the tag as latest.

This commits all the new changes and will create a new image.

Step6: Stop the container using the command :
	
	docker stop containerID

	For example: docker stop 6c31284597e6

Step7: Push the Image to the Docker hub using the below command.

docker push YOUR-DOCKER-USERNAME/[REPOSITORY[:TAG]]

For example: docker push jakkagunith/elasticsearch_vector:latest

Step8: We need to build the image to support multiple - platforms. 
	
	Note: The build command requires a Dockerfile otherwise it will produce an error. This docker file contains the information about the image we need to build.
            
        You will have to modify the content of Dockerfile based on the image name you pushed in the previous step. 

	    Open the given Dockerfile in text editor and make changes accordingly as shown below and save it. 

	    FROM YOUR-DOCKER-USERNAME/[REPOSITORY[:TAG]]
	
	    For example : FROM jakkagunith/elasticsearch_vector:latest
	    

Step8: Now we can build and push the image to docker hub, using the following command:

      Note: Please make sure you are in the directory where the Dockerfile is present.

      Multi-platform build is not supported for the docker driver.Therefore, we need to switch to a different driver.

	  Use the below command to create a new driver 
	
	  docker buildx create --use  
	
	and then execute the below command to build a multi-platform image.

      docker buildx build --platform linux/amd64,linux/arm64 -t <username>/<image>:multi --push .
      
      For example: docker buildx build --platform linux/amd64,linux/arm64 -t jakkagunith/elasticsearch_vector:multi --push .

	  This will also push the Multi-platform docker image to the docker hub with the tag "multi".
