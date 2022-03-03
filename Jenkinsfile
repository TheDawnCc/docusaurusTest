pipeline {
  agent {
    label 'test'
  }
  
  environment {
    var1 = 'test var'
    environment = 'dev'
  }
  
  stages {
    stage('SSH') {
      steps {
        echo "${env.BRANCH_NAME}"
        echo "${env.WORKSPACE}"
        echo "${var1}"
        powershell  """
        Write-Host "test this"
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
        
        git describe --exact-match
        
        echo "test lastexitcode"
        
        echo "$LASTEXITCODE"
        echo "${LASTEXITCODE}"
        echo $LASTEXITCODE
        
        if("${environment}" -eq "qa"){
          if($LASTEXITCODE -eq 128){
            exit 0
          }else{
            Write-Host "Zero updates...abort"
            exit 1
          }
        }
        
        if(("${environment}" -eq "stage") -and \$LASTEXITCODE -ne 0){
          Write-Host "No tags detected...abort"
          exit \$LASTEXITCODE 
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
