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
                    if [[ $? -eq 1 ]]; then  echo "Creating Stack"; aws cloudformation create-stack --stack-name $stack_name --region us-east-1 --template-body file://VPC.yaml --parameters ParameterKey=VpcCIDR,ParameterValue=$VpcCIDR
                    aws cloudformation describe-stacks --stack-name $stack_name --region us-east-1 > status.json
                    cat status.json | jq .[] | jq ."StackStatus"
                   
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
