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
        powershell  """
        echo "hello world"
        if("${var1}" -eq 'test var'){
          echo 'var1 equals'
        }
        echo "${env.BRANCH_NAME}"
        echo ${env.WORKSPACE}
        echo "${var1}"
        
        if((node -v).StartsWith("v10")){
            Write-Host "Node 10 detected...Try nvm use";
            exit 1;
        }
        """
        
        input 'test' 
        
        /*
        powershell 'npm install'
        */
      }
    }

    /*
    stage('Remote') {
      steps {
        powershell 'npm run build'
      }
    }
    */

  }
}
