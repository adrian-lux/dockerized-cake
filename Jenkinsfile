pipeline {
  agent any
  stages {
    stage('error') {
      steps {
        git(url: 'https://github.com/adrian-lux/dockerized-cake.git', branch: 'master')
      }
    }
  }
  environment {
    port = '80'
  }
}