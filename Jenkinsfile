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

    stage('Tests') {
      steps {
        sh 'sh \'./scripts/test.sh\''
      }
    }

    stage('Build image') {
      steps {
        sh 'docker.build("${registry}:${env.BUILD_ID}")'
      }
    }

    stage('Push image') {
      steps {
        sh '''docker.withRegistry(\'\', \'docker-hub\') {
            docker.image("${registry}:${env.BUILD_ID}").push(\'latest\')
            docker.image("${registry}:${env.BUILD_ID}").push("${env.BUILD_ID}")
          }'''
        }
      }

    }
    environment {
      registry = 'kkkhanenko/cicd-pipeline'
    }
  }