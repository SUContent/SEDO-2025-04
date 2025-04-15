pipeline {
    agent any

    environment {
        DOTNET_ROOT = '/usr/share/dotnet'
        PATH = "${env.DOTNET_ROOT}:${env.PATH}"
    }

    triggers {
        pollSCM('H/5 * * * *') 
    }

    stages {
    

        stage('Install .NET SDKs') {
            steps {
                bat '''
                    wget https://dotnet.microsoft.com/en-us/download/dotnet/scripts/v1/dotnet-install.sh -O dotnet-install.sh
                    chmod +x dotnet-install.sh
                    ./dotnet-install.sh --version 6.0.417
                    ./dotnet-install.sh --version 8.0.204
                    export PATH="$HOME/.dotnet:$PATH"
                '''
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

}
