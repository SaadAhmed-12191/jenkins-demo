pipeline {
     agent any 
     stages {
         stage('Testing') {
         steps {
              sh '''
               
               mkdir saadi
               ls
               [ -d "/saadi" ] && echo "Folder exist"
               [ -d "/saadi/saad" ] && echo "Folder exist" || echo "Folder does'nt exist"
              

              '''
          }
        }
    }         
}
