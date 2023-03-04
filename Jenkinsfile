
pipeline {

    agent none

    stages {

       stage('Build') {
       
         agent {
           label 'docker'  	  
    	  }
    	  
          steps { 
            dir('/home/ubuntu/workspace/newchatbot/src')
             { 
             sh 'sudo docker build --tag nltk-chatbot .'  	
          }
       }
       }
       
       stage('Upload') {
       
          agent {
           label 'docker'  	  
    	  }
    	  
          steps { 
             sh 'aws ecr get-login-password --region us-east-1 | sudo docker login --username AWS --password-stdin 342375422541.dkr.ecr.us-east-1.amazonaws.com'  
             sh 'sudo docker tag nltk-chatbot 342375422541.dkr.ecr.us-east-1.amazonaws.com/daniel_chatbot:latest'	
             sh 'sudo docker push 342375422541.dkr.ecr.us-east-1.amazonaws.com/daniel_chatbot:latest'
          }
       }
       
       stage('Deploy') {
       
          agent {
           label 'chatbot2'  
    	  }
    	  
          steps { 
		sh 'kubectl apply -f eks-files/deployment.yml'
		sh 'kubectl apply -f eks-files/service.yml'
		sh 'kubectl rollout restart deployment/chatbot'				
          }
       }

 }
 }



