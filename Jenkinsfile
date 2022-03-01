pipeline {
  agent {
    docker {
      image 'node:14'
      args '''-p 3000:3000
-v C:\\Users\\qiaoxh2\\home:/home'''
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