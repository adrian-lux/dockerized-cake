pipeline {
  agent {
    dockerfile {
      filename 'Dockerfile'
    }

  }
  stages {
    stage('') {
      steps {
        git(url: 'https://github.com/adrian-lux/dockerized-cake.git', branch: 'master')
      }
    }
  }
  environment {
    port = '80'
  }
}