pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { 
                git 'https://github.com/nithin282004/dev-pro.git' 
            }
        }
        stage('Build Docker Image') {
            steps {
                // Use bat instead of sh for Windows
                bat 'docker build -t nithin282004/flask-app:%BUILD_NUMBER% .\\app'
                bat 'docker push nithin282004/flask-app:%BUILD_NUMBER%'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f .\\kubernetes\\deployment.yaml'
                bat 'kubectl apply -f .\\kubernetes\\service.yaml'
            }
        }
    }
}
