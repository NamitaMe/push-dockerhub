def dockerRun ='docker run -p 8080:8080 -d --name java-test namiducker/java-test:2.0.0 .'
pipeline {
    
    agent any //{
        //dockerfile true
    //}
    stages {
        stage ('Build Docker Image'){
            steps {
                sh 'docker build -t namiducker/java-test:2.0.0 .'
            }
            
        }
        stage ('Push Docker Image'){
            
            steps {
                withCredentials([string(credentialsId: 'duckerhub-pwd', variable: 'dockerhubP')]) {
                    sh "docker login -u namiducker -p ${dockerhubP}"
                }
                sh 'docker push namiducker/java-test:2.0.0'
            }
        }
    }
