# Build and Push Intent Classifier Model Container

This document provides the commands to build the Docker image for the Intent Classifier model and push it to Docker Hub.

### Login to Docker Hub

`docker login`

### Build the Docker Image

'=> docker build -t mlops-demo:latest .'

'=> docker images | head -5'

'=> docker images | grep mlops-demo'

'=> docker run -p 6000:6000 -d mlops-demo:latest'

=> curl >> curl -X POST http://localhost:6000/predict -H "Content_Type: application/json" -d '{"text":"Hi, what's up ?"}'

Replace <dockerhub-username> with your Docker Hub username.

`docker build -t <dockerhub-username>/intent-classifier:latest .`

### Tag the Image (Optional Version Tag)

`docker tag <dockerhub-username>/intent-classifier:latest <dockerhub-username>/intent-classifier:v1`

### Push the Image to Docker Hub

Push the latest tag:

`docker push <dockerhub-username>/intent-classifier:latest`

Push the versioned tag:

`docker push <dockerhub-username>/intent-classifier:v1`

5. Verify the Image
docker pull <dockerhub-username>/intent-classifier:latest
