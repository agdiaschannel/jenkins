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
            withCredentials([String(credentialsId: 'awsRoleArn': variable: 'AWS_ROLE_ARN' )]) {
                sh  '''
                  aws ecr describe-repositories
                '''
            } 
          }   
        }
    }    
  }     
}
