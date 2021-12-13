dpipeline {
     agent any
     parameters {
        string(name: 'saad', defaultValue: '10.0.0.0/23', description: 'VPC CIDR')  
     }
     
     stages {
         stage('Submit Stack') {
         steps {
         sh "aws cloudformation create-stack  --template-body file://VPC.yaml  --parameters ParameterKey=saad,ParameterValue=${params.vpccidr}
           }
          }
         }         
         }
