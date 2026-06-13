pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
               git branch: 'main', url: 'https://github.com/a250078-amina/AttendanceSystem.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t attendance-system .'
            }
        }

        stage('Run Container') {
            steps {
                bat '''
                docker stop attendance-container 2>nul
                docker rm attendance-container 2>nul
                docker run -d --name attendance-container -p 3000:80 attendance-system
                '''
            }
        }
    }
}