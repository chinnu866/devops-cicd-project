pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git 'git 'https://github.com/chinnu866/devops-cicd-project.git''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cicd-app .'
            }
        }

        stage('Deploy to EC2') {
            steps {
                sshagent(['ec2-key']) {
                    sh '''
                    ssh -o StrictHostKeyChecking=no ubuntu@15.206.124.10 "
                    docker stop cicd-container || true
                    docker rm cicd-container || true
                    docker run -d -p 80:80 --name cicd-container cicd-app
                    "
                    '''
                }
            }
        }

    }
}
