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
          sh 'awscli --version' 
            
        }
      }
    }
    
  }
}