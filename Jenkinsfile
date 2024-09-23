pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from your Git repository
                git 'https://github.com/Deeppatel1331/TestJenkins.git'
            }
        }

        stage('Restore Dependencies') {
            steps {
                // Restore NuGet packages
                script {
                    bat 'dotnet restore'
                }
            }
        }

        stage('Build') {
            steps {
                // Build the project
                script {
                    bat 'dotnet build --configuration Release'
                }
            }
        }

        stage('Test') {
            steps {
                // Run unit tests
                script {
                    bat 'dotnet test --no-build --configuration Release'
                }
            }
        }

        stage('Publish') {
            steps {
                // Publish the application
                script {
                    bat 'dotnet publish --configuration Release --output ./publish'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded!'
            // Add any post-success actions here (e.g., notifications)
        }
        failure {
            echo 'Pipeline failed.'
            // Add any post-failure actions here (e.g., notifications)
        }
    }
}
 
