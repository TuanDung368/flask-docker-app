pipeline {
    agent any

    environment {
        IMAGE_NAME = "flask-jenkins-demo"
    }

    stages {
        stage('Clone') {
            steps {
             
                git branch: 'main', url: 'https://github.com/TuanDung368/flask-docker-app.git' // Thay đổi branch và URL
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker rm -f flask-ci || true'
                sh 'docker run -d -p 5000:5000 --name flask-ci $IMAGE_NAME'
            }
        }
    }
}

