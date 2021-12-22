pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              
              
              aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE  --region us-east-1  > stacklist.json 
              if [[ "$action" == create ]]
               then
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
                      echo "===================== !!!!!! STACK HAS BEEN ROLLED BACK !!!!!! ====================="
                      break
                    elif [ "$var" == '"CREATE_COMPLETE"' ]
                     then
                      echo "===================== !!!!!! STACK HAS BEEN CREATED !!!!!! ====================="
                    fi
                    
                   done
                 fi
              elif  [[ "$action" == create ]]
               then
                check=$(cat stacklist.json | jq -c -r --arg stack_name $stack_name '.[][] | select(.StackName==$stack_name)')
                 if [ "$check" != "" ]
                  then
                   echo "===================== !!!!!! DELETING STACK !!!!!! ====================="
                   aws cloudformation delete-stack --stack-name $stack_name --region us-east-1
                 else 
                  echo "===================== !!!!!! NO STACK WITH THIS NAME FOUND !!!!!! ====================="
                  
              
                 fi
              fi


              '''
          }
        }
    }         
}
