pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                echo 'Code cloned from Git repository'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t node-cicd-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop node-cicd-app || true
                docker rm node-cicd-app || true
                docker run -d --name node-cicd-app -p 3000:3000 node-cicd-app
                '''
            }
        }
    }
}
