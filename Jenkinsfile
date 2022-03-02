pipeline {
  agent {
    label 'test'
  }
  
  environment {
    var1 = 'test var'
  }
  
  stages {
    stage('SSH') {
      steps {
        echo "${env.BRANCH_NAME}"
        echo "${env.WORKSPACE}"
        echo "${var1}"
        powershell  '''
        echo "${env.BRANCH_NAME}"
        echo ${env.WORKSPACE}
        echo "${var1}"
        
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
