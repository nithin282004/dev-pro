pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { 
                git branch: 'main', url: 'https://github.com/nithin282004/dev-pro.git'
            }
        }
        stage('Build Docker Image') {
            steps { 
                bat 'docker build -t devops-hello-world .' 
            }
        }
        stage('Push Docker Image') {
            steps { 
                bat 'docker tag devops-hello-world nithin282004/devops-hello-world && docker push nithin282004/devops-hello-world' 
            }
        }
        stage('Deploy to Kubernetes') {
            steps { 
                bat 'kubectl apply -f deployment.yaml && kubectl apply -f service.yaml' 
            }
        }
    }
}

