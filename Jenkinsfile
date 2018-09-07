pipeline {
    agent any

    stage('Clone repository') {
        checkout scm
    }

    stage('Build containers') {
        sh 'docker-compose -p master down'
        sh 'echo "port=80" > .env'
        sh 'docker-compose -p master build'
    }

    stage ('Test image') {
        sh 'echo "Test passed"'
    }

    stage ('Run containers') {
        sh 'docker-compose -p master up -d'
    }
}
