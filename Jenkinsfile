pipeline {
    agent {
        docker {
            image 'node:22.11.0-alpine3.20'
            args '-u root'
            reuseNode true
        }
    }

    // options {
    //     skipDefaultCheckout(true) // Skip the default checkout
    // }
    stages {

        // stage('Checkout using SCM') {
        //     steps {
        //         checkout scm // Checkout the code
        //     }
        // }

        stage('Build') {

            steps {

                    sh '''
                        ls -l
                        node --version
                        npm --version
                        npm install
                        npm run build
                        ls -l
                    '''
                
            }
        }

        stage ('Clean up code') {
            steps {
                cleanWs()
            }   
        }
    }
}

// pipeline{
//   // agent any
//   agent{
//      docker {
//       image 'node:22.11.0-alpine3.20'
//       args '-u root'
//       reuseNode true
//     }
//   }

//   options{
//     skipDefaultCheckout(true)
//   }

//   stages{
//     stage('Clean up workspace'){
//       steps{
//          cleanWs()
//       }
//     }

//     stage('Checkout SCM'){
//       steps{
//         checkout scm
//       }
//     }

//     stage('Build'){
//       steps{
//         sh '''
//           ls -l
//           node --version
//           npm --version
//           ls -l
//         '''
//       }
//     }
//   }
// }