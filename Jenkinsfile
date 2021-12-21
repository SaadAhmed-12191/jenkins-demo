pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              aws cloudformation describe-stacks --stack-name $stack_name --region us-east-1 > stacklist.json 
              cat stacklist.json
              jq 'length' stacklist.json
              


              '''
          }
        }
    }         
}
