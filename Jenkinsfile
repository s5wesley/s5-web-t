pipeline {
    agent any
    
    stages {
        stage('Pull Docker Image') {
            steps {
                script {
                    // Pull the specified Docker image
                    docker.image("mbargabella/myapps:v4").pull()
                }
            }
        }
    }
}
