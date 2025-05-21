pipeline {
    environment {
        DOCKERHUB_CREDENTIALS = credentials("dhubcred")
    }
    agent {
        label 'k_m'}
 
    stages {
        stage('Git') {
            steps {
                git(url: 'https://github.com/d2arshan/Website-PRT-ORG-1', branch: 'main') 
            }
        }
        stage('Docker') {
            steps {
                sh 'sudo dcoker login -u ${DOCKERHUB_CREDENTIALS_USR} -p ${DOKERHUB_CREDENTIALS_PSW}'
                sh 'sudo docker build /home/ubuntu/jenkins/workspace/prt -tintellipaatsai/prt-task'
                sh 'sudo docker push intellipaatsai/prt-task'
    }
}
 stage('k8s') {
            steps {
                sh 'kuectl apply -f deploy.yaml'
                sh 'kubectl apply service.yaml'
            }
        }
    }    
}
