pipeline {
    agent any

    environment {
        APP_NAME = "my-app"
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
                echo "Running on branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Static Code Analysis') {
            steps {
                echo "Running code analysis"
            }
        }

        stage('Unit Tests') {
            when {
                anyOf {
                    branch 'main'
                    branch 'dev'
                }
            }
            steps {
                echo "Running unit tests"
            }
        }

        stage('Build') {
            when {
                branch 'main'
            }
            steps {
                echo "Building application (main only)"
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying to production (main only)"
            }
        }
    }

    post {
        always {
            echo "Finished pipeline for: ${env.BRANCH_NAME}"
        }
    }
}
