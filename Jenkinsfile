pipeline {
    agent any
    
    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/AdolfBharath/nginx-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-nginx-app:latest .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                if [ $(docker ps -q -f name=mynginx) ]; then
                    docker stop mynginx
                    docker rm mynginx
                fi
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d --name mynginx -p 80:80 my-nginx-app:latest'
            }
        }
    }
}
