pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout source code from Git repository
                git branch: 'main', url: 'https://github.com/HirunaD/3884-DeSilva'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                // Build Docker image from Dockerfile
                bat 'docker build -t dockerimage .'
            }
        }
        
        stage('Tag Image') {
            steps {
                // Tag Docker image with a unique identifier
                bat 'docker tag dockerimage hide72/dockerimage:latest'
            }
        }
        
        stage('Push Image') {
            steps {
                // Push Docker image to Docker Hub
                withCredentials([string(credentialsId: 'devops-ass2', variable: 'ass2pw')]) {
                    bat 'docker login -u hide72 -p %ass2pw%'
                    bat 'docker push hide72/dockerimage:latest'
                }
            }
        }
    }
}
