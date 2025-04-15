pipeline {
    agent any

    stages {
        stage('Check Files') {
            steps {
                bat 'echo Current folder: %cd%'
                bat 'dir'
                bat 'dir /s *.csproj'
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
                bat 'dotnet test HouseRentingSystem.Tests/HouseRentingSystem.Tests.csproj --no-build --verbosity normal'
            }
        }
    }
}
