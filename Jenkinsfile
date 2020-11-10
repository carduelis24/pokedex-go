pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh "docker build -t pokedex-go:latest ."
            }
        }
        stage('Test') {
            steps {
                sh "docker run --rm pokedex-go:latest npm test"
            }
        }
        stage('Deploy') {
            steps {
                sh "docker rm -f pokedex-go || true"
                sh "docker run --rm -d --name pokedex-go -p 5555:5555 pokedex-go:latest"
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}