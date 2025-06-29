pipeline {
    environment {
        DOCKERHUB_CREDENTIALS = credentials("dhubcred")
    }
    agent {
        label 'k_m'
    }
    stages {
        stage('Git') {
            steps {
                git url: 'https://github.com/d2arshan/Website-PRT-ORG-1', branch: 'main'
            }
        }
        stage('Docker') {
            steps {
                sh 'sudo docker login -u ${DOCKERHUB_CREDENTIALS_USR} -p ${DOCKERHUB_CREDENTIALS_PSW}'
                // Adjust path to your Dockerfile location
                sh 'sudo docker build . -t intellipaatsai/prt-task'
            }
        }
        stage('k8s') {
            steps {
                sh 'kubectl apply -f deploy.yaml -f service.yaml'
            }
        }
    }
}
