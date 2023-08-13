pipeline {
    agent any

    environment {
        Project_Name = "Test"
   
    }

    tools {
        jdk 'Corretto 11.0.20'
        gradle 'Gradle-8.0.2'
    }


    stages {

        stage('Clean Gradle Cache') {
                steps {
                    echo 'Cleaning Gradle Cache...'
                    bat './gradlew cleanBuildCache'
                }
            }

        stage('Checkout') {
            steps {
                echo 'Step: Git Checkout'
                bat 'java -version'
                bat 'gradle -version'
            }
        }

        stage('Build Module tabletPrivDebug') {
            steps {
                echo 'Step: Build Module tabletPrivRelease'
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

