pipeline {
    agent any

    options {
        skipDefaultCheckout(true) // Skip the default checkout
    }

    stages {
        stage("Check Ws"){
            steps{
                sh '''
                    ls -l
                '''
            }
        }

        stage('Checkout using SCM') {
            steps {
                checkout scm // Checkout the code
            }
        }

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

        stage("Test"){
            steps{
                sh '''
                  echo "Testing started...."
                  echo "Testing Ended......"
                '''
            }
        }

        stage('Deploy'){
            steps{
                sh '''
                   echo "Project deployment started..."
                   echo "Project deployment ended...."
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