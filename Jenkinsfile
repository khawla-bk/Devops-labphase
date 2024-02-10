pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                script {
                    git branch: 'main',
                    credentialsId: 'khawla-bk',
                    url: 'https://github.com/khawla-bk/Devops-labphase.git'
                }
        }
        
        stage('Build') {
            steps {
                script {
                    docker.build('kbenkadida006/first-app-test')
                }
            }
        }
        
        stage('Push to Docker Hub') {
            steps {
                // Authentification Docker Hub
                withDockerRegistry([credentialsId: 'kbenkadida006', url: 'https://index.docker.io/v1/']) {
                    // Pousser l'image vers Docker Hub
                    script {
                        docker.image('kbenkadida006').push('latest')
                    }
                }
            }
        }
    }
}
}
