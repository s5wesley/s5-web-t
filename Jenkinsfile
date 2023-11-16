pipeline {
    agent any

    stages {
        stage('Stage 1') {
            steps {
                echo 'Hello, wesley! - Stage 1'
            }
        }

        stage('Stage 2') {
            steps {
                echo 'Hello, harold! - Stage 2'
            }
        }

        stage('Stage 3') {
            steps {
                echo 'Hello, World! - Stage 3'
            }
        }

        stage('Stage 4') {
            steps {
                echo 'Hello, World! - Stage 4'
            }
        }

        stage('Stage 5') {
            steps {
                echo 'Hello, World! - Stage 5'
            }
        }
    }

    post {
        success {
            echo 'All stages completed successfully!'
        }

        failure {
            echo 'One or more stages failed. Please check the logs.'
        }
    }
}
