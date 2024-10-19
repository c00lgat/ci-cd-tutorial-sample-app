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
            /usr/local/bin/python3.8 -m pip install --upgrade pip
            python3.8 -m venv venv 
            . venv/bin/activate
            pip install -r requirements.txt
            flask db upgrade
            python3.8 seed.py
            '''
          }
        }
    }

    stage("Test Coverage") {
      steps {
        script {
          python3 -m unittest discover
        }
      }
    }
  
  }
  


}
