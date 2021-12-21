pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              aws cloudformation describe-stacks --stack-name $stack_name --region us-east-1 > status.json
              aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE --query StackSummaries[].StackName --region us-east-1  > stacklist.json 
              
              var=$(cat stacklist.json | jq '.StackSummaries | .[].StackName')
              var2=$(cat status.json | jq '.Stacks | .[].StackStatus')
              echo $var
              echo $var2


              '''
          }
        }
    }         
}
