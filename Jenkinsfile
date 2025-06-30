pipeline {
    agent any

    environment {
        IMAGE_NAME = 'cloud_native_monitoring_app'
        IMAGE_TAG = 'latest'
    }

        stage('Clone Repository') {
            steps {
        git branch: 'main', url: 'https://github.com/BasammaLyavi/cloud_native_monitoring_App'
            }
        }


        stage('Install Python Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat "docker build -t %IMAGE_NAME%:%IMAGE_TAG% ."
            }
        }

        stage('Run Docker Container') {
            steps {
                bat "docker run -d -p 5000:5000 %IMAGE_NAME%:%IMAGE_TAG%"
            }
        }
    }

    post {
        success {
            echo 'App built and running locally in a Docker container.'
        }
        failure {
            echo 'Build or run failed. Check logs above.'
        }
    }
}
