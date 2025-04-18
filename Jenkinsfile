pipeline {
    agent any

    environment {
        IMAGE_NAME = 'java-hello-jenkins'
        IMAGE_TAG = 'v1'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/YASHHARMALKAR/java-docker-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run --rm $IMAGE_NAME:$IMAGE_TAG'
                }
            }
        }

        stage('Cleanup') {
            steps {
                script {
                    sh 'docker rmi $IMAGE_NAME:$IMAGE_TAG'
                }
            }
        }
    }

    post {
        success {
            echo "✅ Build and run successful!"
        }
        failure {
            echo "❌ Build failed!"
        }
    }
}
