pipeline {
    agent any

    

    stages {
       
        stage('Restore Dependencies') {
         
            steps {
                bat 'dotnet restore'
            }
        }
        stage('Build Application') {
           
            steps {
                bat 'dotnet build --configuration Release'
            }
        }
        stage('Run Tests') {
           
            steps {
                bat 'dotnet test'
            }
        }
    }

   
}
