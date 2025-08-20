pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { git 'https://github.com/username/devops-project.git' }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t username/flask-app:$BUILD_NUMBER ./app'
                sh 'docker push username/flask-app:$BUILD_NUMBER'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f kubernetes/deployment.yaml'
                sh 'kubectl apply -f kubernetes/service.yaml'
            }
        }
    }
}
