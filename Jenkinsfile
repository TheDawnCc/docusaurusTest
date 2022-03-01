pipeline {
  agent {
    node {
      label 'agent1'
    }

  }
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
}