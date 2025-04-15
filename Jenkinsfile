pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                bat 'dir' 
            }
        }

        stage('Restore dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }

    post {
        always {
            echo 'Cleaning workspace...'
            deleteDir()
        }
        success {
            echo 'Tests ran successfully!'
        }
        failure {
            echo 'Something went wrong. Check the console output.'
        }
    }
}
