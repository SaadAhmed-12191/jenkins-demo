pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              aws cloudformation describe-stacks --stack-name $stack_name --region us-east-1
              if [[ "$?" == 0  ]]
               then echo "stack already exist"
              else
               echo "creating stack"
              fi

              '''
          }
        }
    }         
}
