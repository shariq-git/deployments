pipeline {
    agent any

    environment {
        KUBE_CONFIG = credentials('kubeconfig-secret-text')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/shariq-git/jenkins.git', credentialsId: 'github-pat'
            }
        }        
        stage('Deploy to Kubernetes') {
            steps {
                script {
                     
                        sh 'kubectl apply -f k8s/deployment.yaml'
                    
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
