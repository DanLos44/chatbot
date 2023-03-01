
pipeline {
    agent {
        label 'docker'
    }
 
    stages {
       stage('Build') {
          steps {
             echo 'is this even working'    
             sh 'sudo docker build --tag nltk-chatbot .'  	
          }
       }
       
       stage('Upload') {
          steps { 
             sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 342375422541.dkr.ecr.us-east-1.amazonaws.com'  	
          }
       }

 }
 }



