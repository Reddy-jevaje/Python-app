pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('docker-hub')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh ' docker build -t Reddy-jevaje/python-app:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh ' docker push Reddy-jevaje/python-app:$BUILD_NUMBER'
            }
        }
    }
}
