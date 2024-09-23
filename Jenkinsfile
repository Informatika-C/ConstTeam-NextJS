pipeline {
    agent any
    environment {
        IMAGE_NAME = 'constteam/web-app:latest'
        CONTAINER_NAME = 'constteam-web-app'
        NETWORK_NAME = 'outbound-constteam-network'
    }
    stages {
        stage('Build') {
            steps {
                sh "docker build -t ${IMAGE_NAME} ."
            }
        }
        stage('Clean Container') {
            steps {
                sh "docker rm -f ${CONTAINER_NAME} || true"
            }
        }
        stage('Run Container') {
            steps {
                sh "docker run -d --name ${CONTAINER_NAME} --network ${NETWORK_NAME} ${IMAGE_NAME}"
            }
        }
    }
}