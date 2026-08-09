pipeline {
    agent any

    environment {
        IMAGE_NAME = 'justinaugust123/docker-cicd-demo'
        IMAGE_TAG = 'latest'
    }

    stages {

        stage('Check Variables') {
            steps {
                echo "IMAGE_NAME = ${env.IMAGE_NAME}"
                echo "IMAGE_TAG = ${env.IMAGE_TAG}"
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh '''
                    docker stop demo-container || true
                    docker rm demo-container || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name demo-container ${IMAGE_NAME}:${IMAGE_TAG}'
            }
        }
    }
}
