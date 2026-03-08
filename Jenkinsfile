pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/chinnu866/devops-cicd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t cicd-app .'
            }
        }

        stage('Deploy to EC2') {
            steps {
                bat 'docker run -d -p 80:80 cicd-app'
            }
        }

    }
}
