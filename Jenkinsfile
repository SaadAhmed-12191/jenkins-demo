pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE --query StackSummaries[].StackName --region us-east-1  > stacklist.json 
              cat stacklist.json
              var=$(cat stacklist.json | jq '.StackSummaries | .[].StackName')
              echo $var


              '''
          }
        }
    }         
}
