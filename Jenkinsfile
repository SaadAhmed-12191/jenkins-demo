pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
               mkdir saad
               ls
               [ -d "/saad" ] && echo "Folder exist"
               [ -d "/saad/saad" ] && echo "Folder exist" || echo "Folder does'nt exist"
              

              '''
          }
        }
    }         
}
