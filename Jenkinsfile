pipeline {
    agent any
    environment { 
        CC = 'clang'
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
        BITBUCKET_COMMON_CREDS = credentials('jenkins-amirkhan-common-creds')
    }
    stages {
        stage('Checkout') {
            steps {
              checkout([$class: 'GitSCM', 
                branches: [[name: '*/Dev']],
                extensions: [
                    [$class: 'SparseCheckoutPaths', 
                    sparseCheckoutPaths:[[$class:'SparseCheckoutPath', path:'/code']]]
                    ],
                userRemoteConfigs: [[url: 'https://github.com/jenkinstesting0123/jenkins.git']]])
              sh "ls -ltr"
              sh "python test.py"
          }
        }
    }
}
