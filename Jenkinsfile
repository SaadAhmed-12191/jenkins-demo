pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE  --region us-east-1 > stacklist 
              cat stacklist
              var=$(cat stacklist | jq .[] | jq .StackName)
              echo $var
              


              '''
          }
        }
    }         
}
