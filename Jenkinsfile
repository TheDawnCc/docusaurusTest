pipeline {
  agent {
    docker {
      image 'node:14'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('error') {
      steps {
        input 'test'
        sh 'sshpass -p 19vTbOZRkmrB38TX scp -r -v /var/jenkins_home/workspace/angular-rss-reader_main/dist/ root@100.42.64.222:/var/www/'
      }
    }

  }
}