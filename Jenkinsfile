dpipeline {
     agent any
     
     
     stages {
         stage('Submit Stack') {
         steps {
         sh "aws cloudformation create-stack  --template-body file://VPC.yaml 
           }
          }
         }         
         }
