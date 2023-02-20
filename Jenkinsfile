pipeline {
  agent any
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
          sh 'ls -ltr'
          sh 'cd code'
          sh 'ls -ltr'
          sh 'python code/test.py'
        }
      }

    }
    environment {
      CC = 'clang'
    }
  }