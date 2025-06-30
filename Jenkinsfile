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
                sh 'docker build -t basammalyavi12345/app1-k8s:latest .'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
        stage('Run Container') {
    steps {
        sh 'docker run -d -p 5000:5000 basammalyavi12345/app1-k8s:latest'
    }
}
    }
}