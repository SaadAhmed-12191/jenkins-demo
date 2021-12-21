pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE --query StackSummaries[].StackName --region us-east-1 > stacklist 
              if [[ "$action" == create ]]
                then  cat stacklist | grep "${stack_name}" && echo "============ !!!! stack already created !!!! ============" || aws cloudformation create-stack --stack-name $stack_name --region us-east-1 --template-body file://VPC.yaml --parameters ParameterKey=VpcCIDR,ParameterValue=$VpcCIDR
                while [ "$var" != '"CREATE_COMPLETE"' ]
                do 
                 aws cloudformation describe-stacks --stack-name $stack_name --region us-east-1 > status.json; var=$(cat status.json | jq '.Stacks | .[].StackStatus'); echo $var
                 if [[ "$var" == '"ROLLBACK_IN_PROGRESS"' ]]
                  echo "Stack has been rolled back"
                  break
                 fi
                done

                    
                   
              elif [[ "$action" == delete ]]
               then cat stacklist | grep "${stack_name}" && aws cloudformation delete-stack --stack-name $stack_name --region us-east-1  || echo "============ !!!! No such stack exist !!!! ============"
                    
              fi


              '''
          }
        }
    }         
}
