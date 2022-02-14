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
        sh '''ssh-keygen -t rsa -P "" -f ~/.ssh/id_rsa
cp /var/jenkins_home/.ssh/id_rsa ~/.ssh/id_rsa
cp /var/jenkins_home/.ssh/id_rsa.pub ~/.ssh/id_rsa.pub
cp /var/jenkins_home/.ssh/known_hosts ~/.ssh/known_hosts'''
        sh 'npm install'
        input 'test'
      }
    }

    stage('Remote') {
      steps {
        sh 'scp -r -v /var/jenkins_home/workspace/docusaurusTest_main/dist/ root@100.42.64.222:/var/www/'
      }
    }

  }
}