pipeline {
    agent any
    stages {
        stage('Assume Role and Access AWS') {
            steps {
                // Use initial credentials to assume the target role
                withAWS(
                    credentials: 'aws-ecr-credentials',  // ID of the initial IAM user credentials
                    role: 'jenkins-sts',                     // Name of the role to assume
                    roleAccount: '<ommited>',            // AWS account ID where the role exists
                    region: 'us-east-1'                    // AWS region
                    
                ) {
                    // Commands using the assumed role's temporary credentials
                    sh 'aws ecr get-login-password --region <ommited> |  buildah login --username AWS --password-stdin <ommited>.dkr.ecr.us-east-1.amazonaws.com/myregistry'
                    sh 'aws sts get-caller-identity'  // Verify the assumed role
                }
            }
        }
    }
}
