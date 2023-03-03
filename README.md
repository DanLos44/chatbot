This project is based on the following git repository:
https://github.com/cherdt/docker-nltk-chatbot

-- General --
It implements a pipeline in Jenkins using 2 agents that on each run:
First agent compiles the source code and packages it to a docker image using docker engine.
Uploads the image to an AWS ECR.
Second agent downloads and runs the Docker image in a pod in AWS EKS.

-- How to build --
First of all make sure you have the folowing:
1) A git repo integrated with jenkins(webhook)
you can visit this site for more info:
https://www.blazemeter.com/blog/how-to-integrate-your-github-repository-to-your-jenkins-project

2)Install docker on both agents
visit this site for more info:
https://docs.docker.com/engine/install/ubuntu/

3)ECR private repository, you can make it public if you want to
visit this site for more info:
https://docs.aws.amazon.com/AmazonECR/latest/userguide/repository-create.html

4)Fully operational AWS EKS
visit this site for more info:
https://docs.aws.amazon.com/eks/latest/userguide/create-cluster.html

5)Install AWS cli on both agents
visit this site for more info:
https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

-- How to run --
-If you want to run this project without a pipeline you can use the following commands:

1)docker build --tag <image name> .

2)aws ecr get-login-password --region <region> |docker login --username AWS --password-stdin <your ecr>

3)docker tag <image name> <ecr repo>:<tag>

4)docker push <ecr repo>

-If not, create a trigger like a push event to start the pipeline automatic


-- How to interact --
The service type is a load balancer
you can access it using this format:
<your load balancer url>:443/chat

