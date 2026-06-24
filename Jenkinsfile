pipeline {

    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/nagarajkhairate/simple-app.git'
            }
        }


        stage('Docker Build') {
            steps {
                sh 'docker build -t simple-app .'
            }
        }


        stage('Deploy') {
            steps {
                sh '''
                docker stop simple-app || true
                docker rm simple-app || true

                docker run -d \
                --name simple-app \
                -p 80:80 \
                simple-app
                '''
            }
        }
    }
}
