pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              aws cloudformation describe-stacks --stack-name mytesting --region us-east-1
              echo $?

              '''
          }
        }
    }         
}
