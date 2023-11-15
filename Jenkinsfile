pipeline {
    agent any
    
    stages {
        stage('Pull, Tag, and Push Docker Image') {
            steps {
                script {
                    // Pull the original Docker image
                    docker.image("mbargabella/myapps:v4").pull()

                    // Tag the pulled image with the new tag
                    docker.image("mbargabella/myapps:v4").tag("game:v3")

                    // Push the tagged image to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
                        docker.image("game:v3").push()
                    }
                }
            }
        }
    }
}
