pipeline {
     agent any
     
     
     stages {
         stage('Testing') {
         steps {
              sh '''
                 #!/bin/bash
                 aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE --query StackSummaries[].StackName --region us-east-1 > stacklist
                 cat stacklist
                 if [[ "$action" == "create" ]]
                 then 
                  cat stacklist | grep "${stack_name}"
                  if [[ $? -eq 1 ]]
                  echo "creating stack"
                 elif [[ "$action" == "delete" ]]
                 then
                  cat stacklist | grep "${stack_name}"
                  if [[ $? -eq 1  ]]
                   then
                    echo "No stack with this name found"
                 fi
                
              
              '''
               }
                    }
           }         
         }
