pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              
              echo $stack_name
              aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE  --region us-east-1  > stacklist.json 
              cat stacklist.json
              var=$(cat stacklist.json | jq -c -r --arg stackname $stack_name '.[][] | select(.StackName==$stack_name)')
              if [ "$var" != "" ]
               then
                echo "saad"
              else echo "ahmed"
              fi
              


              '''
          }
        }
    }         
}
