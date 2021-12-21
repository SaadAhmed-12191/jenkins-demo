pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE --query StackSummaries[].StackName --region us-east-1 > stacklist 
              if [[ "$action" == create ]]
                then cat stacklist | grep "${stack_name}"
                return_1_if_success.exe
                IF %ERRORLEVEL% EQU 1 (exit /B 0) ELSE (exit /B 1)
                    if [[ $? -eq 1 ]]; then  echo "Creating Stack"; aws cloudformation create-stack --stack-name $stack_name --region us-east-1 --template-body file://VPC.yaml --parameters ParameterKey=VpcCIDR,ParameterValue=$VpcCIDR ; while [ "$var14" != "CREATE_COMPLETE," ]; do  aws cloudformation describe-stacks --stack-name $stack_name --region us-east-1 > status ; eval $(awk '{print "var"NR"="$2}' status) ; echo $var14 ; done ; 
                    else echo "Stack already exist"
                    fi
              elif [[ "$action" == delete ]]
              then cat stacklist | grep "${stack_name}"
                    if [[ $? -eq 0 ]]; then echo "Deleting Stack"; aws cloudformation delete-stack --stack-name $stack_name --region us-east-1 ;  
                    else echo "Stack with this name does'nt exist"
                    fi
              fi

              '''
          }
        }
    }         
}
