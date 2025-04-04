pipeline {
  agent none
  environment {
    AWS_DEFAULT_REGION="us-east-1"
    AWS_ROLE_ARN="ecr-operator"
  }
  stages {
    stage('awscli test') {
      agent {
        kubernetes {
          yamlFile 'manifests/awscli.yaml'
        }
      }

      steps {      
        container('awscli') {
          script {
            
           withAWS(credentials: 'jenkins-sts', roleArn: 'arn:aws:iam::992382399891:role/ECROperator' roleSessionName: 'Jenkins') {
    
                sh  '''
                  aws ecr describe-repositories
                '''
            } 
          }   
        }
      }    
    }     
  }
}


