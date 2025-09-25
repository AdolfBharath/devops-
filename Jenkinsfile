pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-nginx-app .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker stop mynginx || true'
                sh 'docker rm mynginx || true'
                sh 'docker run -d --name mynginx -p 80:80 my-nginx-app'
            }
        }
    }
}
