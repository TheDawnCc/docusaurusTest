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
        /*
        echo "${env.BRANCH_NAME}"
        echo "${env.WORKSPACE}"
        echo "${var1}"
        echo "${env.var1}"
        echo "${env.environment}"
        */
        
        powershell '''
        echo '1'
        echo ${env:var1}
        echo '2'
        echo "${env:var1}"
        
        echo '3'
        if($LASTEXITCODE -eq 0){
          echo 'lastexitcode = 0'
        }
        else if($LASTEXITCODE -eq $null){
          echoo 'lastexitcode = null'
        }
        else{
          echo 'lastexitcode != 0'
        }
        
        echo '5'
        echo $LASTEXITCODE
        Write-Output $LASTEXITCODE
        Write-Host $LASTEXITCODE
        
        echo '6'
        echo "$LASTEXITCODE"
        echo '7'
        echo ${LASTEXITCODE}
        echo '8'
        echo \${LASTEXITCODE}
        
        echo '11'
        echo $?
        echo '12'
        echo $error
        '''
        
        /*
        powershell  """
        Write-Host "test this"
        echo \${LASTEXITCODE}
        if(\${LASTEXITCODE} -eq 0){
          echo 'lastexitcode value is 0'
        }
        echo "${env.var1}"
        echo "${env.environment}"
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
       
        
        """
        
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
        */
    
        
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
