pipeline {
    agent any

    stages {
      stage('Restore dependencies') {
        steps {
          bat "dotnet restore"
        }
      }

      stage('Build') {
        steps {
          bat "dotnet build --no-restore"
        }
      }

      stage('Run Unit Tests') {
        steps {
          bat "dotnet test HouseRentingSystem.UnitTests/HouseRentingSystem.UnitTests.csproj --no-build --verbosity normal"
        }
      }

    
      stage('Run Integration Tests') {
        steps {
          bat "dotnet test HouseRentingSystem.Tests/HouseRentingSystem.Tests.csproj --no-build --verbosity normal"
        }
      }
    }
}
