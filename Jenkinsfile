pipeline {
    agent any
    stages {
        stage('Assume Role and Access AWS') {
            steps {
                // Use initial credentials to assume the target role
                withAWS(
                    credentials: 'aws-ecr-credentials',  // ID of the initial IAM user credentials
                    role: 'jenkins-sts',                     // Name of the role to assume
                    roleAccount: '992382399891',            // AWS account ID where the role exists
                    region: 'us-east-1'                    // AWS region
                    
                ) {
                    // Commands using the assumed role's temporary credentials
                    sh 'aws ecr get-login-password --region us-east-1 '
                    sh 'aws sts get-caller-identity'  // Verify the assumed role
                }
            }
        }
    }
}
