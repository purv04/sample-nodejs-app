pipeline {
    agent {
        docker {
            image 'node:14' // Optional: runs steps in this container
        }
    }

    environment {
        IMAGE_NAME = "sample-nodejs-app"
    }

    stages {
        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/purv04/sample-nodejs-app', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t $IMAGE_NAME ."
            }
        }

        stage('Run Docker Container') {
            steps {
                sh "docker rm -f $IMAGE_NAME || true"
                sh "docker run -d -p 3000:3000 --name $IMAGE_NAME $IMAGE_NAME"
            }
        }
    }
}
