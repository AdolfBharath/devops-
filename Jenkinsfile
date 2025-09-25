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
                // Stop old container if it exists
                bat 'docker stop mynginx || exit 0'
                bat 'docker rm mynginx || exit 0'
            }
        }

        stage('Run New Container') {
            steps {
                // Run container on port 9090 (since Jenkins uses 8080)
                bat 'docker run -d --name mynginx -p 9090:80 my-nginx-app'
            }
        }
    }
}
