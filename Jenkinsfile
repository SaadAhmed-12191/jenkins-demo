pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
                #!/bin/bash
                echo "somestack" > stacklist
                cat stacklist
                action_var="create"
                stack_name_var="teststack"
                if [ "$action_var" = "create" ]; then
                    result=$(cat stacklist | grep "${stack_name_var}")
                    if [ -z $result ]; then
                        echo "creating stack"
                    else
                        echo "stack with this name already exist"
                    fi
                fi
              '''
          }
        }
    }         
}
