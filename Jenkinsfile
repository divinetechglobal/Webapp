pipeline{
    agent any
    options{
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    environment{
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }
    stages{
        stage('Build'){
            steps{
                sh 'docker build -t dvtech470/webapp1 .'
            }
        }
        stage('Login'){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin' 
            }
        }
        stage('Push'){
            steps{
                sh 'docker push dvtech470/webapp1'
            }
        }
        stage('Monitor'){
            steps{
                echo "This is a monitor stage"
            }
        }
    }
}