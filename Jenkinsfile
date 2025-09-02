pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('docker_creds')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/svhariharan/hari_CI_CD_.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t svhariharan/nodeapp_3:$BUILD_NUMBER .'
            }
        }
        
        stage('Run Container') {
            steps {
                    sh "docker run -d --name node_app_3$BUILD_NUMBER svhariharan/nodeapp:$BUILD_NUMBER"
            }
        }   
}
post {
        always {
            sh 'docker logout'
        }
    }
}
