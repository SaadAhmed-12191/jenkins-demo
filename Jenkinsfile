pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              set -e
              echo "saad"
              aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE --query StackSummaries[].StackName --region us-east-1 > stacklist
              cat stacklist
              if [[ "$action" == create ]]
               then cat stacklist | grep "${stack_name}"
               if [[ "$?" -eq 1 ]]
                then echo "creating stack"
               else echo "stack already created"
               fi
                

              fi

              '''
          }
        }
    }         
}
