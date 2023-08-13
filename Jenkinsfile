pipeline {
    agent any

    environment {
        Project_Name = "Dobus"
        BuildPath = "C:\\jenkins-agent\\Build"
        DeployPath = "C:\\jenkins-agent\\Deploy"
    }

    tools {
        jdk 'Corretto 11.0.20'

    }


    stages {
        
        stage('Checkout') {
            steps {
                echo 'Step: Git Checkout'
                checkout scm
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

        stage('Move to BuildPath') {
            steps {
                echo 'Step: Moving build artifacts...'
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

// Apply MultiDex configuration
android {
    defaultConfig {
       multiDexEnabled true
    }
}
