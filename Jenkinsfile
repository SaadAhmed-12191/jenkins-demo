pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              x=aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE --query StackSummaries[].StackName --region us-east-1 > stacklist 
              echo $x
             

              '''
          }
        }
    }         
}
