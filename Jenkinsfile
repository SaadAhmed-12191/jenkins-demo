pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
                #!/bin/bash
                echo "somestack" > stacklist.txt
                cat stacklist.txt
              '''
          }
        }
    }         
}
