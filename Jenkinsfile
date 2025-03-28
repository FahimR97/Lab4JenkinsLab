pipeline {
    agent any
    
    stages {
        stage('Clone') {
            steps {
                checkout scm
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nodeapp .'
            }
        }
        
        stage('Deploy') {
            steps {
                sh '''
                    docker stop nodeapp_container || true
                    docker rm nodeapp_container || true
                    docker run -d -p 5000:5000 --name nodeapp_container nodeapp
                '''
            }
        }
    }
}