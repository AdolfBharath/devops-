pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t my-nginx-app .'
            }
        }
        
        stage('Stop Old Container') {
            steps {
                // Stop container if it exists
                bat 'docker stop mynginx || exit 0'
            }
        }
        
        stage('Remove Old Container') {
            steps {
                // Remove container if it exists
                bat 'docker rm mynginx || exit 0'
            }
        }
        
        stage('Run Container') {
            steps {
                // Run new container on port 9090
                bat 'docker run -d --name mynginx -p 9090:80 my-nginx-app'
            }
        }
    }
}
