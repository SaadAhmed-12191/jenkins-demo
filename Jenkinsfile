pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
                 #!/bin/bash
                 aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE --query StackSummaries[].StackName --region us-east-1 > stacklist
                 cat stacklist
                 action_var="delete"
                 stack_name_var="something"
                 if [ "$action_var" = "create" ]
                  then 
                   cat stacklist | grep "${stack_name_var}"
                   if [[ $? = 1 ]]
                    then
                     echo "creating stack"
                   else
                    echo "stack with this name already exist"
                   fi
                 elif [[ "$action_var" = "delete" ]]
                  then
                   cat stacklist | grep "${stack_name_var}"
                    if [[ $? = 1  ]]
                     then
                      echo "No stack with this name found"
                    else
                      echo "deleting stack"
                    fi
                 fi
                
              
              '''
               }
                    }
           }         
         }
