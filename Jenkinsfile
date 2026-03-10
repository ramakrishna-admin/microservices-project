pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'server', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://087C60FD37E13CF9941EB43433BF6C51.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'server', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://087C60FD37E13CF9941EB43433BF6C51.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
