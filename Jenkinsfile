pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t attendance-system .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat '''
                docker stop attendance-container 2>nul
                docker rm attendance-container 2>nul
                exit /b 0
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker run -d --name attendance-container -p 3000:80 attendance-system'
            }
        }
    }
}