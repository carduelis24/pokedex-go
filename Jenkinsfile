pipeline {
    
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
               sh "git pull"
              
            }
        }
         stage('Build') {
            steps {
               sh "npm install"
            }
        }
        stage('Test') {
            steps {
               sh "npm test"
            }
        }
        stage('Deploy') {
            steps {
               sh "doccker "
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}

/
// Build: build a docker image using the Dockerfile you created in step 2
// Test: run the unit tests within the image using npm test
// Deploy: run a container from your image, publishing port 5555, run npm start