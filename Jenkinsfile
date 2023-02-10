pipeline {
    agent any
    environment { 
        CC = 'clang'
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
        BITBUCKET_COMMON_CREDS = credentials('jenkins-amirkhan-common-creds')
    }
    stages {
        stage('checkout') {
            checkout([$class: 'GitSCM', branches: [[name: 'https://github.com/jenkinstesting0123/jenkins/tree/Dev/code']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/jenkinstesting0123/jenkins.git']]])
            steps {
                sh 'python test.py'
            }
        }
    }
}
