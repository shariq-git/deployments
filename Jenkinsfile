pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/shariq-git/deployments.git',
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
