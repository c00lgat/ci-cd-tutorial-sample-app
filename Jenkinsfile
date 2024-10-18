pipeline {
  agent {label 'jenkins_slave'}
  stages {
    stage("Checkout") {
      steps {  
        checkout scmGit(
          branches: [[name: '*/master']], 
          extensions: [], 
          userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/c00lgat/ci-cd-tutorial-sample-app']]
        )
      }
    }

    stage("Build") {
        steps {
          script {
            sh '''
            pwd
            python -m venv venv 
            source venv/bin/activate
            pip install -r requirements.txt
            '''
          }
        }
    }
  }


}
