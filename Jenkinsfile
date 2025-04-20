pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/purv04/sample-nodejs-app', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("sample-nodejs-app")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                sh "docker rm -f sample-nodejs-app || true"
                sh "docker run -d -p 3000:3000 --name sample-nodejs-app sample-nodejs-app"
            }
        }
    }
}
