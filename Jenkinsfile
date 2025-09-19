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
                        rm -rf node_modules
                        rm -f package-lock.json

                        ls -l
                        node --version
                        npm --version
                        npm install
                        npm run build
                        ls -l
                    '''
                
            }
        }
    }
    
    post {
        always {
            echo "Final cleanup..."
            cleanWs() // safe now, deploy has already used the build
        }
    }
}