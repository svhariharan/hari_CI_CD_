pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('docker_creds')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/priya-commit-08/jenkins-cicd.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t priya-commit-08/nodeapp:$BUILD_NUMBER .'
            }
        }
        
        stage('Run Container') {
            steps {
                    sh "docker run -d --name node_app_$BUILD_NUMBER priya-commit-08/nodeapp:$BUILD_NUMBER"
            }
        }   
}
post {
        always {
            sh 'docker logout'
        }
    }
}
