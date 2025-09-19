pipeline {
    agent {
        docker {
            image 'node:22.11.0-alpine3.20'
            args '-u root'
            reuseNode true
        }
    }

    environment{
        NODE_ENV = 'test'
        VERCEL_TOKEN = credentials('VERCEL_TOKEN')
    }

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
                   npm install -g vercel
                   vercel --version
                   vercel --prod --token=${{ secrets.VERCEL_TOKEN }} --confirm --name=reactcicdproject
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