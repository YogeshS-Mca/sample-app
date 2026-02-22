pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main',
                url: 'https://github.com/YogeshS-Mca/sample-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t sample-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f sample-app-container || true
                docker run -d -p 8080:80 --name sample-app-container sample-app
                '''
            }
        }
    }
}
