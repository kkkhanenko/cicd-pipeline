pipeline {
  agent any
  stages {
    stage('Git checkout') {
      steps {
        sh 'checkout scm'
      }
    }

    stage('Application build') {
      steps {
        sh 'sh \'./scripts/build.sh\''
      }
    }

  }
}