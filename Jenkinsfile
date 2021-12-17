pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
                #!/bin/bash
                echo "somestack" > stacklist
                cat stacklist
                action_var="delete"
                stack_name_var="teststack"
                if [ "$action_var" = "create" ]; then
                    cat stacklist | grep "${stack_name_var}"
                    if [ $? -eq 1 ]; then
                        echo "creating stack"
                    else
                        echo "stack with this name already exist"
                    fi
                elif [ "$action_var" = "delete" ]; then
                    cat stacklist | grep "${stack_name_var}"
                    if [ $? = 1  ]; then
                        echo "No stack with this name found"
                    else
                        echo "deleting stack"
                    fi
                fi
              '''
          }
        }
    }         
}
