pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t tomato-app .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh '''
                docker stop tomato-container || true
                docker rm tomato-container || true
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker run -d \
                --name tomato-container \
                -p 80:80 \
                tomato-app
                '''
            }
        }
    }
}