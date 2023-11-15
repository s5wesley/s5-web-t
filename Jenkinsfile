pipeline {
    agent any
    
    stages {
        stage('Pull, Tag, and Push Docker Images') {
            steps {
                script {
                    // Pull the original Docker image
                    docker.image("mbargabella/myapps:v4").pull()

                    // Tag the pulled image with the new tag
                    docker.image("mbargabella/myapps:v4").tag("mbargabella/myapps:v6")

                    // Push the tagged image to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
                        docker.image("mbargabella/myapps:v6").push()
                    }

                    // Tag the image as mbargabella/game:v2
                    docker.image("mbargabella/myapps:v6").tag("mbargabella/game:v2")

                    // Push the tagged image to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
                        docker.image("mbargabella/game:v2").push()
                    }
                }
            }
        }
    }
}
