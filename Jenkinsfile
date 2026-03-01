pipeline {
    agent any

    stages {
        stage('deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '''-----BEGIN CERTIFICATE-----
MIID...paste your actual EKS cluster CA cert here...
-----END CERTIFICATE-----''',
                    clusterName: 'EKS-1.us-west-2.eksctl.io',
                    contextName: '',
                    credentialsId: 'k8-token',
                    namespace: 'webapps',
                    serverUrl: 'https://5A735A784998DA1B9508DC40353562D3.gr7.us-west-2.eks.amazonaws.com'
                ]]) {
                    sh "kubectl apply -f deployment-service.yml -n webapps"
                    sleep 60
                }
            }
        }
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '''-----BEGIN CERTIFICATE-----
MIID...paste your actual EKS cluster CA cert here...
-----END CERTIFICATE-----''',
                    clusterName: 'EKS-1.us-west-2.eksctl.io',
                    contextName: '',
                    credentialsId: 'k8-token',
                    namespace: 'webapps',
                    serverUrl: 'https://5A735A784998DA1B9508DC40353562D3.gr7.us-west-2.eks.amazonaws.com'
                ]]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
