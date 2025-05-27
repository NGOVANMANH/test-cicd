pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/dotnet/sdk:9.0'
        }
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'dotnet build --configuration Release'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh 'dotnet publish --configuration Release -o ./publish'
            }
        }
        stage('Run') {
            steps {
                echo 'Running application...'
                sh 'dotnet ./publish/test-cicd-project.dll'
            }
        }
    }
}