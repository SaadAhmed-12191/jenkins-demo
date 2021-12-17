pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
                #!/bin/bash
                bash --version
                echo "somestack" > stacklist.txt
                cat stacklist.txt
                stack_name="yasirstack"
                action_name="create"
                if [ "$action_name" == create ]; then
                    echo "SUCCESS JOB"
                fi
              '''
          }
        }
    }         
}
