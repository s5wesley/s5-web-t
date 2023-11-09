pipeline {
    agent {
        label 'prod'
    }

    environment {
        DOCKER_HUB_USERNAME = 'mbargabella'
        DOCKER_HUB_PASSWORD = 'Dicaprio78'
        DOCKER_IMAGE_NAME = 'nginx'
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
                    // Configure Docker Tool
                    def docker = tool name: 'Docker', type: 'org.jenkinsci.plugins.docker.commons.tools.DockerTool'
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
