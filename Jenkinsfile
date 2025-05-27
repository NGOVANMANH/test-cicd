pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/dotnet/sdk:9.0'
        }
    }
    stages {
        stage('Restore') {
            steps {
                echo 'Restoring dependencies...'
                sh 'dotnet restore'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'dotnet build --configuration Release'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'dotnet test --no-build'
            }
        }
        stage('Publish') {
            steps {
                echo 'Publishing...'
                sh 'dotnet publish --configuration Release -o ./publish'
            }
        }
        stage('Run') {
            steps {
                echo 'Running application...'
                sh 'dotnet ./publish/TestCICDProject.dll'
            }
        }
    }
}
