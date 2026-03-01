pipeline {
    agent any

    stages {
        stage('deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5A735A784998DA1B9508DC40353562D3.gr7.us-west-2.eks.amazonaws.com']]) {
                     sh "kubectl apply -f deployment-service.yml" 
                     sleep 60
              }
            }
        }
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5A735A784998DA1B9508DC40353562D3.gr7.us-west-2.eks.amazonaws.com']]) {
                     sh "kubectl get all -n webapps"
               }
            }
        }
    }
}

