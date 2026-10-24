
pipeline {
    agent any

    triggers {
        githubPush()
    }

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Application') {
            steps {
                bat 'dotnet --info'
                bat 'dotnet restore Homies.sln'
                bat 'dotnet build Homies.sln --configuration Release --no-restore'
            }
        }

        stage('Run All Tests') {
            steps {
                bat 'dotnet test Homies.sln --configuration Release --no-build'
            }
        }
    }

    post {
        success {
            echo 'Build successful. All tests passed.'
        }
        failure {
            echo 'Build or tests failed. Check the console output.'
        }
        always {
            echo 'Jenkins pipeline finished.'
        }
    }
}
