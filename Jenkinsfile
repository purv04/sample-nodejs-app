pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t sample-nodejs-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                    docker rm -f sample-nodejs-app || true
                    docker run -d -p 3000:3000 --name sample-nodejs-app sample-nodejs-app
                '''
            }
        }
    }
}
