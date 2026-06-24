pipeline {

    agent any

    stages {

        stage('Docker Build') {
            steps {
                sh 'docker build -t simple-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f simple-app || true
                docker run -d \
                --name simple-app \
                -p 80:80 \
                simple-app
                '''
            }
        }
    }
}
