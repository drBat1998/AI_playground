Title: Introduction to Docker
Author: [[Google Cloud Skills Boost]]
Tags: #docker


# Notes
In order to see all containers, including ones that have finished executing, run docker ` docker ps -a`


```bash
# Use an official Node runtime as the parent image
FROM node:lts

# Set the working directory in the container to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
ADD . /app

# Make the container's port 80 available to the outside world
EXPOSE 80

# Run app.js using node when the container launches
CMD ["node", "app.js"]
EOF
```

```bash
cat > app.js << EOF;
const http = require("http");

const hostname = "0.0.0.0";
const port = 80;

const server = http.createServer((req, res) => {
	res.statusCode = 200;
	res.setHeader("Content-Type", "text/plain");
	res.end("Hello World\n");
});

server.listen(port, hostname, () => {
	console.log("Server running at http://%s:%s/", hostname, port);
});

process.on("SIGINT", function () {
	console.log("Caught interrupt signal and will exit");
	process.exit();
});
EOF
```

`docker build -t node-app:0.1 ` -  to build and image

`docker images` - display images

`docker run -p 4000:80 --name my-app node-app:0.1` - run the image

curl http://localhost:4000

`docker stop my-app && docker rm my-app` - to stop and remove a container

> Note: You don't have to write the entire container ID, as long as the initial characters uniquely identify the container. For example, you can execute docker logs 17b if the container ID is 17bcaca6f....

`docker logs [container_id]`

# Publish
Create the target Docker repository (Using Cloud Console)
1. From the Navigation Menu, under CI/CD navigate to Artifact Registry > Repositories.
2. Click the +CREATE REPOSITORY icon next to repositories.
3. Specify my-repository as the repository name.
4. Choose Docker as the format.
5. Under Location Type, select Region and then choose the location : REGION.
6. Click Create.

Before you can push or pull images, configure Docker to use the Google Cloud CLI to authenticate requests to Artifact Registry.
1. To set up authentication to Docker repositories in the region REGION, run the following command in Cloud Shell:
`gcloud auth configure-docker "REGION"-docker.pkg.dev`

2. Enter Y when prompted.
The command updates your Docker configuration. You can now connect with Artifact Registry in your Google Cloud project to push and pull images.

Create an Artifact Registry repository (Using CLI)
1. Run the following commands to create an Artifact Repository.
	1. `gcloud artifacts repositories create my-repository --repository-format=docker --location="REGION" --description="Docker repository"`

Push the container to Artifact Registry
1. Change into the directory with your Dockerfile.
	1. `cd ~/test`
2. Run the command to tag node-app:0.2.
	1. `docker build -t "REGION"-docker.pkg.dev/"PROJECT_ID"/my-repository/node-app:0.2 .`
3. Run the following command to check your built Docker images. `docker images`
4. Push this image to Artifact Registry.
	1. `docker push "REGION"-docker.pkg.dev/"PROJECT_ID"/my-repository/node-app:0.2`
5. After the push finishes, from the Navigation Menu, under CI/CD navigate to Artifact Registry > Repositories.
6. Click on my-repository. You should see your node-app Docker container created:



# Links
https://www.cloudskillsboost.google/focuses/1029?catalog_rank=%7B%22rank%22%3A1%2C%22num_filters%22%3A0%2C%22has_search%22%3Atrue%7D&parent=catalog&search_id=35668148