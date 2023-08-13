pipeline {
    agent any

    environment {
        Project_Name = "Dobus"
        BuildPath = "C:\\jenkins-agent\\Build"
        DeployPath = "C:\\jenkins-agent\\Deploy"
    }

    tools {
        jdk 'Corretto 11.0.20'
        gradle 'Gradle-6.5'
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
                checkout scm
                bat 'java -version'
                bat 'gradle -version'
            }
        }

        stage('Build Module tabletPrivDebug') {
            steps {
                echo 'Step: Build Module tabletPrivRelease'
                bat 'gradle clean assemble -PbuildVariant=tabletPrivRelease'
            }
        }

        stage('Move to BuildPath') {
            steps {
                echo 'Step: Moving build artifacts...'
                // bat "xcopy /Y /E /I /Q \"%WORKSPACE%\\app\\build\\outputs\\apk\\*\" \"%BuildPath%\\\""
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
