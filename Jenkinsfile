pipeline {
  agent none
  environment {
    AWS_DEFAULT_REGION="us-east-1"
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
          sh  '''
           aws ecr describe-repositories
          '''
            
        }
      }
    }
    
  }
}
