pipeline {
    agent any
    
    stages {
        stage('Pull and Tag Docker Image') {
            steps {
                script {
                    // Pull Nginx image from Docker Hub
                    docker.image('nginx').pull()

                    // Tag the Nginx image with the specified tag
                    docker.image('nginx').tag("mbargabella/myapps:v5")
                }
            }
        }

        stage('Push Docker Image to Docker Hub') {
            steps {
                script {
                    // Push the tagged image to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
                        docker.image("mbargabella/myapps:v5").push()
                    }
                }
            }
        }
    }
}
