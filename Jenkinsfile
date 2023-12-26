pipeline {
    agent {
        docker {
            image 'ubuntu:tag'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('dockerhub')
        IMAGE_NAME = 'cmenezesaus/teste'
        TAG = 'latest'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', DOCKER_HUB_CREDENTIALS) {
                        def customImage = docker.build("${IMAGE_NAME}:${TAG}", '.')
                        customImage.push()
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Docker build and push succeeded!'
        }
    }
}