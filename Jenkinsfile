pipeline {
    agent any

    environment {
        DOCKER_CRED=credentials('dockerhub')
  
        IMAGE_NAME="vishwasvishu123/develops"
    }

    stages {

        stage('checkout') {
            steps {
                git url: "https://github.com/Darshan262003/appmy.git",
                    branch: "main"
            }
        }

        stage('build') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE_NAME}:latest")
                }
            }
        }

        stage('push') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
                        dockerImage.push()
                    }
                }
            }
            
        }
         
    }
}
