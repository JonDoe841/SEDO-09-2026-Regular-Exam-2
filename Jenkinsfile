
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

        stage('Check Main Branch') {
            steps {
                script {
                    if (env.BRANCH_NAME != 'main' &&
                        env.GIT_BRANCH != 'origin/main' &&
                        env.GIT_BRANCH != 'main') {
                        error('This pipeline is configured for the main branch only.')
                    }
                }
            }
        }

        stage('Build Application') {
            steps {
                echo 'Building application...'
                // Add your application's build command here
            }
        }

        stage('Run All Tests') {
            steps {
                echo 'Executing all tests...'
                // Add your application's test command here
            }
        }
    }

    post {
        success {
            echo 'Build and tests completed successfully.'
        }
        failure {
            echo 'Build or tests failed.'
        }
        always {
            echo 'Pipeline finished.'
        }
    }
}
