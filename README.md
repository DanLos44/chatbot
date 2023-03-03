This project is based on the following git repository:
https://github.com/cherdt/docker-nltk-chatbot

-- General --
It implements a pipeline in Jenkins using 2 agents that on each run:
First agent compiles the source code and packages it to a docker image using docker engine.
Uploads the image to an AWS ECR.
Second agent downloads and runs the Docker image in a pod in AWS EKS.

-- How to build --
First of all make sure you have the folowing:
- A git repo integrated with jenkins(webhook)
- ECR private repository, you can make it public if you want to
- Fully operational AWS EKS
- Both agents integrated with your aws credentials
- Second agent integrated with your EKS

After that just create a trigger to run the pipeline


-- How to interact --
The service type is a load balancer
you can access it using this format:
<your load balancer url>:443/chat

