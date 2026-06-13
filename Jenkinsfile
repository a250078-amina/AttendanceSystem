pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t attendance-system .'
            }
        }

        stage('Deploy Using Ansible') {
            steps {
                bat '''
                wsl bash -c "cd '/mnt/c/ProgramData/Jenkins/.jenkins/workspace/AttendancePipeline' &&
                ansible-playbook ansible/deploy.yml"
                '''
            }
        }
    }
}