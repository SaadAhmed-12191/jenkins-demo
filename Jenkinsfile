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
                
                    
                   
              elif [[ "$action" == delete ]]
               then cat stacklist | grep "${stack_name}" && jq --version || echo "============ !!!! No such stack exist !!!! ============"
                    
              fi


              '''
          }
        }
    }         
}
