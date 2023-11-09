pipeline {
    agent {
        label 'prod'
    }

    environment {
        DOCKER_HUB_USERNAME = 'devopseasylearning/s5wesley'
        DOCKER_HUB_PASSWORD = 'dckr_pat_44pgHmLgP-cPbekojpQdqsyB2B0'
        DOCKER_IMAGE_NAME = 'alpine'
        DOCKER_IMAGE_TAG = 'latest'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${env.DOCKER_IMAGE_NAME}:${env.DOCKER_IMAGE_TAG}", '.')
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry([credentialsId: 'your-docker-hub-credentials-id', url: 'https://index.docker.io/v1/']) {
                        docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials') {
                            dockerImage.push()
                        }
                    }
                }
            }
        }
    }
}
