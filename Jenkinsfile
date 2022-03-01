pipeline {
  agent any
  stages {
    stage('SSH') {
      steps {
        sh 'npm install'
        input 'test'
      }
    }

    stage('Remote') {
      steps {
        sh 'npm run build'
      }
    }

  }
  environment {
    label = 'agent1'
  }
}