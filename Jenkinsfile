pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              #aws cloudformation describe-stacks --stack-name $stack_name --region us-east-1 > status.json
              #cat status.json
              aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE  --region us-east-1  > stacklist.json 
              cat stacklist.json
              var=$(cat stacklist.json | jq '.StackSummaries | .[0].StackName')
              #var2=$(cat status.json | jq '.Stacks | .[].Parameters')
              echo $var
              #echo $var2


              '''
          }
        }
    }         
}
