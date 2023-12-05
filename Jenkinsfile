pipeline {
    agent any 
    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main' , url: 'https://github.com/Nish1102/docker-image-pipeline.git'
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    // Pull the Docker image and run the container on  desired port
                    sh 'docker pull nish1102/youthful_kapitsa' 
                    sh 'docker run -d -p 85:80 nish1102/youthful_kapitsa'
                }
            }
        }
        stage('Cleanup') {
            steps {
                script {
                    // Clean up , stop , and remove the running container
                    sh 'docker stop $(docker ps -q --filter ancestor=nish1102/youthful_kapitsa)'
                    sh 'docker rm $(docker ps -a --filter ancestor=nish1102/youthful_kapitsa)'
                }
            }
        }
        
    }
}