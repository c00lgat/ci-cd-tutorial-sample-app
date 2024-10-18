pipeline {
  agent any 
  stages {
    stage("Checkout") {
      steps {  
        echo "potato"
        checkout scmGit(
          branches: [[name: '*/master']], 
          extensions: [], 
          userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/c00lgat/ci-cd-tutorial-sample-app']]
        )
      }
    }
  }


}
