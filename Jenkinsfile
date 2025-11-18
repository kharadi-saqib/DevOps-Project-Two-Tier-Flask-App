pipeline {
    agent { label 'remote-server' }
    
    stages {
        stage('Check Docker Access') {
            steps {
                sh 'whoami'
                sh 'groups'
                sh 'docker info'
            }
        }
        
        stage('Clone repo') {
            steps {
                git branch: 'main', url: 'https://github.com/kharadi-saqib/DevOps-Project-Two-Tier-Flask-App.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }
        
        stage('Deploy with Docker Compose') {
            steps {
                sh 'docker compose down || true'
                sh 'docker compose up -d --build'
            }
        }
    }
}
