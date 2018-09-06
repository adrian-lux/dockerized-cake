pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out repository...'
                checkout scm
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'echo "port=80" > .env'
                sh 'docker-compose -p master build'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker-compose -p master up -d'
            }
        }
    }
}
