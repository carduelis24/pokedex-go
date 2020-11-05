pipeline {
    
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
               sh "git pull origin master"
              
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
            sh 'docker rm -f pokedex-go || true'
            sh 'docker run -d --rm -p 5555:5555 --name pokedex-go pokedex-go:latest'
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}

