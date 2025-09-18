pipeline{
  agent{
     docker {
      image 'node:22.11.0-alpine3.20'
      args '-u root'
      reuseNode true
    }
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
          which node
          which npm
          npm install
          npm run build
          ls -l
        '''
      }
    }
  }
}