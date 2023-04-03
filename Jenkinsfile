pipeline {
    agent {
        docker {
            image 'microsoft/dotnet:latest'
            args '-u root'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'dotnet restore'
                sh 'dotnet build'
            }
        }
        stage('Test') {
            steps {
                sh 'dotnet test'
            }
        }
        stage('Publish') {
            steps {
                sh 'dotnet publish'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker build -t my-app .'
                sh 'docker run -d --name my-app-container my-app'
            }
        }
    }
}
