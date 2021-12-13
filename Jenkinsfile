dpipeline {
     agent any
     
     
     stages {
         stage('Submit Stack') {
         steps {
         sh "aws cloudformation create-stack  --template-body file://VPC.yaml  --parameters ParameterKey=saad,ParameterValue=10.0.0.0/23
           }
          }
         }         
         }
