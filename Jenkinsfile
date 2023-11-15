pipeline {
    agent any
    
    stages {
        stage('Pull and Tag Docker Image') {
            steps {
                script {
                    // Pull Nginx image from Docker Hub
                    docker.image('nginx').pull()

                    // Tag the Nginx image with the specified tag
                    docker.image('nginx').tag('mbargabella/myapps:v5')
                }
            }
        }
    }
}
