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
            when {
                anyOf {
                    branch 'feature'
                    branch 'main'
                }
            }
            steps {
                sh 'dotnet build --no-restore'
            }
        }

        stage('Test') {
            when {
                anyOf {
                    branch 'feature'
                    branch 'main'
                }
            }
            steps {
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
