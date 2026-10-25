pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t jenkins-docker-demo .'
            }
        }

        stage('Deploy Web Application') {
            steps {
                script {
                    bat(
                        returnStatus: true,
                        script: 'docker rm -f jenkins-docker-demo'
                    )
                }

                bat 'docker run -d --name jenkins-docker-demo -p 8082:80 jenkins-docker-demo'
            }
        }
    }
}
