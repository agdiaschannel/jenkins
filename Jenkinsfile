pipeline {
  agent none
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
