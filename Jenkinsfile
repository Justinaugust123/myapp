pipeline {
    agent any

    environment {
        IMAGE_NAME = "justinaugust123/my-website"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:latest .'
            }
        }

        stage('Test') {
            steps {
                sh 'docker image inspect $IMAGE_NAME:latest'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                echo 'Push Docker image here'
            }
        }
    }
}
