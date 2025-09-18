pipeline{
  // agent any
  agent{
     docker {
      image 'node:22.11.0-alpine3.20'
      args '-u root'
      reuseNode true
    }
  }

  options{
    skipDefaultCheckout(true)
  }

  stages{
    stage('Clean up workspace'){
      steps{
         cleanWs()
      }
    }

    stage('Checkout SCM'){
      steps{
        checkout scm
      }
    }

    stage('Build'){
      steps{
        sh '''
          ls -l
          node --version
          npm --version
          ls -l
        '''
      }
    }
  }
}