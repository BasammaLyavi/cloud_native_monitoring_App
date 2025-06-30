pipeline {
    agent any
    environment {
        IMAGE_NAME = 'flask-app'
        IMAGE_TAG = 'latest'
    }
    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/BasammaLyavi/cloud_native_monitoring_App'
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %flask-app%:%latest% .'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
            }
        }
        stage('Run Container') {
    steps {
        bat 'docker run -d -p 5000:5000 %flask-app%:%latest% '
    }
}
    }
}