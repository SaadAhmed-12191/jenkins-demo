pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              
              echo $stack_name
              aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE  --region us-east-1  > stacklist.json 
              
              check=$(cat stacklist.json | jq -c -r --arg stack_name $stack_name '.[][] | select(.StackName==$stack_name)')
              if [ "$check" != "" ]
               then
                echo "===================== !!!!!! STACK ALREADY CREATED !!!!!! ====================="
              else  aws cloudformation create-stack --stack-name $stack_name --region us-east-1 --template-body file://VPC.yaml --parameters ParameterKey=VpcCIDR,ParameterValue=$VpcCIDR
                while [ "$var" != '"CREATE_COMPLETE"' ]
                do 
                 aws cloudformation describe-stacks --stack-name $stack_name --region us-east-1 > status.json; var=$(cat status.json | jq '.Stacks | .[].StackStatus'); echo $var
                 if [ "$var" == '"ROLLBACK_IN_PROGRESS"' ]
                  then
                   echo "Stack has been rolled back"
                   break
                 elif [ "$var" == '"CREATE_COMPLETE"' ]
                  then
                   echo "Stack has been created"
                 
                 fi
                done
               
              fi
              


              '''
          }
        }
    }         
}
