pipeline {
    agent any

    stages {
        
        stage('Checkout') {
            steps {
                echo 'Step: Git Checkout'
                checkout scm
                bat 'java -version'
                bat 'gradle -version'
            }
        }

        stage('Build') {
            steps {
                bat 'gradle clean build'
            }
        }
        stage('Finish') {
            steps {
                echo 'Step: Build finished...'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed'
        }
    }
}
