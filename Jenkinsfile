pipeline {
    agent any

    stages {
        stage('Setup Docker Permissions') {
            steps {
                script {
                    // Configure Docker permissions
                    sh 'sudo usermod -aG docker jenkins || true' // Add Jenkins to Docker group
                    sh 'sudo chown jenkins:docker /var/run/docker.sock || true' // Set ownership of Docker socket
                }
            }
        }

        stage('Checkout') {
            steps {
                script {
                    // Checkout the code from Git repository
                    git branch: 'main', credentialsId: 'khawla-bk', url: 'https://github.com/khawla-bk/Devops-labphase.git'
                }
            }
        }

        stage('Build the Docker image') {
            steps {
                script {
                    // docker.build('solash25/first-app-test')
                    sh 'docker build -t kbenkadida006/first-app-test-v2 .'
                }
            }
        }
    }
}
