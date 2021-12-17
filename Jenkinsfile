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
                    cat stacklist | grep "${stack_name_var}"
                    if [ $? -eq 1 ]; then
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
