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
cp /home/ssh_key/id_rsa ~/.ssh/id_rsa
cp /home/ssh_key/id_rsa.pub ~/.ssh/id_rsa.pub
cp /home/ssh_key/known_hosts ~/.ssh/known_hosts'''
        sh 'npm install'
        input 'test'
      }
    }

    stage('Remote') {
      steps {
        sh 'npm build'
        sh 'scp -r -v /var/jenkins_home/workspace/docusaurusTest_main/build/ root@100.42.64.222:/var/www/'
      }
    }

  }
}