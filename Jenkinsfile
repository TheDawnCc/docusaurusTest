pipeline {
  agent {
    label 'test'
  }
  stages {
    stage('SSH') {
      steps {
        powershell 'npm install'
        input 'test'
      }
    }

    stage('Remote') {
      steps {
        powershell 'npm run build'
      }
    }

  }
}
