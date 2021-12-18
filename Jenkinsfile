pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
              #!/bin/bash
              
              cat stacklist | grep "${stack_name}" | true
              echo $?

              '''
          }
        }
    }         
}
