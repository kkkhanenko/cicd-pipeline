pipeline {
  agent {
    node {
      label 'node1'
    }

  }
  stages {
    stage('Git checkout') {
      steps {
        sh 'checkout scm'
      }
    }

  }
}