pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE UPDATE_COMPLETE --query StackSummaries[].StackName --region us-east-1 > stacklist 
              if [[ "$action" == create ]]
                then [ cat stacklist | grep "${stack_name}" ] && echo "Creating Stack" || echo "============ !!!! stack already created !!!! ============"
                
                    
                   
              elif [[ "$action" == delete ]]
               then [ cat stacklist | grep "${stack_name}" ] && echo "deleting" || echo "============ !!!! No such stack exist !!!! ============"
                    
              fi


              '''
          }
        }
    }         
}
