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
            python3.8 -m venv venv 
            . venv/bin/activate
            pip install -r requirements.txt
            flask db upgrade
            python3.8 seed.py
            python3.8 -m unittest discover
            '''
          }
        }
    }

    stage("Test Coverage") {
      steps {
        script {
          sh '. venv/bin/activate'
          sh 'python3.8 -m unittest discover'
        }
      }
    }
  
  }
  


}
