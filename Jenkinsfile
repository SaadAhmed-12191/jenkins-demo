pipeline {
     agent any
     
     
     stages {
         stage('Submit Stack') {
         steps {
              sh "aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE --query StackSummaries[].StackName --region us-east-1 > stacklist"
              cat stacklist
           }
          }
         }         
         }
