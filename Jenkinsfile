pipeline {
    agent any

    stages {
        stage('Deploy to kubernetees') {
            steps {
                  withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://313F0EFCFD0518400A8F9CF6F95D4EF6.gr7.us-east-1.eks.amazonaws.com']]) {
                      sh "kubectl apply -f deployment-service.yml"
                      sleep 60
                 }
            }
        }
   
        stage('verify deployment') {
            steps {
                  withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://313F0EFCFD0518400A8F9CF6F95D4EF6.gr7.us-east-1.eks.amazonaws.com']]) {
                      sh "kubectl get svc -n webapps"
                 }
            }
        }
    }
}
