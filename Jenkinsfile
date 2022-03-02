pipeline {
  agent {
    label 'test'
  }
  stages {
    stage('SSH') {
      steps {
        echo "${BRANCH_NAME}"
        echo ${WORKSPACE}
        powershell  '''
        echo "${BRANCH_NAME}"
        echo ${WORKSPACE}
        
        if((node -v).StartsWith("v10")){
            Write-Host "Node 10 detected...Try nvm use";
            exit 1;
        }
        '''
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
