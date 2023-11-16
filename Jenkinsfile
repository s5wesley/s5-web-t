pipeline {
    agent any

    stages {
        stage('Pull and Tag Images') {
            steps {
                script {
                    // Pull and tag thomisis-ui image
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        def uiImage = docker.image('devopseasylearning/thomisis-ui:v0.01')
                        uiImage.pull()
                        uiImage.tag('mbargabella/thomisis-ui:v0.01')
                    }

                    // Pull and tag thomisis-auth image
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        def authImage = docker.image('devopseasylearning/thomisis-auth:v0.0.1')
                        authImage.pull()
                        authImage.tag('mbargabella/thomisis-auth:v0.01')
                    }

                    // Pull and tag thomisis-weather image
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        def weatherImage = docker.image('devopseasylearning/thomisis-weather:v0.0.1')
                        weatherImage.pull()
                        weatherImage.tag('mbargabella/thomisis-weather:v0.0.1')
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Image pulling and tagging completed successfully!'
        }

        failure {
            echo 'Image pulling and tagging failed. Please check the logs.'
        }
    }
}
