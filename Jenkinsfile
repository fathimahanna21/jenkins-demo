
pipeline {
    agent any

    environment {
        APP_NAME = 'demo-app'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Getting the source code...'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Building $APP_NAME"'
                sh 'mkdir -p build && date > build/version.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'test -f build/version.txt && echo "Tests passed"'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying ${env.APP_NAME} build #${env.BUILD_NUMBER}"
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'build/*.txt'
            echo 'Pipeline succeeded'
        }
    }
}
