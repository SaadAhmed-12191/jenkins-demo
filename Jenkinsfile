pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              echo "saad"
              aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE --query StackSummaries[].StackName --region us-east-1 > stacklist
              cat stacklist
              if [[ "$action" == create ]]
               then echo "saad"
                if [[ "$? == 1 ]]
                  then echo "creating stack"
                else
                  echo "stack with this name already exist"
                fi

              fi

              '''
          }
        }
    }         
}
