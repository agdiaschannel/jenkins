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
            
           withAWS(region: 'us-east-1', role: 'ecr-operator',roleAccount: '992382399891', roleSessionName: 'JenkinsSession') {
    
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
