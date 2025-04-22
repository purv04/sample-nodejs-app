pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/purv04/sample-nodejs-app'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t sample-nodejs-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 3000:3000 --name sample-nodejs-app sample-nodejs-app'
            }
        }
    }
}
