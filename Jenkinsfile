pipeline {
    agent any
    // comment
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }


        stage('Restore dependencies') {
            when {
                anyOf {
                    branch 'feature'
                    branch 'main'
                }
            }
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build --no-restore'
            }
        }

        stage('Test') {
            steps {
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
