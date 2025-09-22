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
                bat '''
                docker stop mynginx || exit 0
                docker rm mynginx || exit 0
                '''
            }
        }

        stage('Run New Container') {
            steps {
                bat 'docker run -d --name mynginx -p 80:80 my-nginx-app'
            }
        }
    }
}
