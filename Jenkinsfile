pipeline {
    agent any

    stages {
        stage('deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '''-----BEGIN CERTIFICATE-----
MIIDBTCCAe2gAwIBAgIISalXO0NOcwswDQYJKoZIhvcNAQELBQAwFTETMBEGA1UE
AxMKa3ViZXJuZXRlczAeFw0yNjAyMjgyMDM3MDJaFw0zNjAyMjYyMDQyMDJaMBUx
EzARBgNVBAMTCmt1YmVybmV0ZXMwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEK
AoIBAQDp+AaRs5nlmpYiEg5sCY810YhrGIXpDkuLNZY2fP4XimlBLxyWlmm/r6RL
DATU5aYGLe72puGxM08OEjIcHcHHXk1B+YrjEDIRb3aMjPlYAyh5lsItuDvJ3hAX
G55MkvnCqrF/PjX48feWr1wVll0hrBH3ptZcha7mLDxaPb62Akyo6w592X58JsdE
WWB0OxPoxZ683UtLdtjC/G8tpPm4L/3gzKE6irN7qei7+5mp0TC7mMAi2Ubv9ZhC
1qJZS6eHKDrJZnepALzieB6zx9oZdMzedk73dYUm84uDJzc6tito8FE4fIor60/s
CgRGln9wV/gNB8mgq/e3vwtPveerAgMBAAGjWTBXMA4GA1UdDwEB/wQEAwICpDAP
BgNVHRMBAf8EBTADAQH/MB0GA1UdDgQWBBR6e3FN3jxbmE/Xoc/NJG1YNoQ2BTAV
BgNVHREEDjAMggprdWJlcm5ldGVzMA0GCSqGSIb3DQEBCwUAA4IBAQCD9toDUkv9
0DeL302nontSQ3ZNCIFCikOTqXicDYBUpWXr9sO81po79A7OuNHSSIf7k36GrKsk
G3VJ2cZ5STG4CiVXFypg9Kv5qCutZo6qg4AKHIf0w5Vonf+zCZis3g+CmlQj+1VU
ezeYsbUvVo1dgVhEdKPQsK3unHfmW0WwG7aButWuN9ethQtFSJYh9BuI2m1llnYC
UduzcPwbJGObJ24aJcLinfMltuL9i8ZPPGnbpsZKXmz8qQgvdgORvZtLJ6PlQ1d8
O5wc/d48RnEWfMRMM6z3q9pfXqFPTy1TO0J7EgcBhK9ytyJ0uFWQ4PxsMQoNpcnO
3qS0PUevq75G
-----END CERTIFICATE-----''',
                    clusterName: 'EKS-1.us-west-2.eksctl.io',
                    credentialsId: 'k8-token',
                    namespace: 'webapps',
                    serverUrl: 'https://5A735A784998DA1B9508DC40353562D3.gr7.us-west-2.eks.amazonaws.com'
                ]]) {
                    sh "kubectl apply -f deployment-service.yml -n webapps"
                    
                }
            }
        }
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '''-----BEGIN CERTIFICATE-----
MIIDBTCCAe2gAwIBAgIISalXO0NOcwswDQYJKoZIhvcNAQELBQAwFTETMBEGA1UE
AxMKa3ViZXJuZXRlczAeFw0yNjAyMjgyMDM3MDJaFw0zNjAyMjYyMDQyMDJaMBUx
EzARBgNVBAMTCmt1YmVybmV0ZXMwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEK
AoIBAQDp+AaRs5nlmpYiEg5sCY810YhrGIXpDkuLNZY2fP4XimlBLxyWlmm/r6RL
DATU5aYGLe72puGxM08OEjIcHcHHXk1B+YrjEDIRb3aMjPlYAyh5lsItuDvJ3hAX
G55MkvnCqrF/PjX48feWr1wVll0hrBH3ptZcha7mLDxaPb62Akyo6w592X58JsdE
WWB0OxPoxZ683UtLdtjC/G8tpPm4L/3gzKE6irN7qei7+5mp0TC7mMAi2Ubv9ZhC
1qJZS6eHKDrJZnepALzieB6zx9oZdMzedk73dYUm84uDJzc6tito8FE4fIor60/s
CgRGln9wV/gNB8mgq/e3vwtPveerAgMBAAGjWTBXMA4GA1UdDwEB/wQEAwICpDAP
BgNVHRMBAf8EBTADAQH/MB0GA1UdDgQWBBR6e3FN3jxbmE/Xoc/NJG1YNoQ2BTAV
BgNVHREEDjAMggprdWJlcm5ldGVzMA0GCSqGSIb3DQEBCwUAA4IBAQCD9toDUkv9
0DeL302nontSQ3ZNCIFCikOTqXicDYBUpWXr9sO81po79A7OuNHSSIf7k36GrKsk
G3VJ2cZ5STG4CiVXFypg9Kv5qCutZo6qg4AKHIf0w5Vonf+zCZis3g+CmlQj+1VU
ezeYsbUvVo1dgVhEdKPQsK3unHfmW0WwG7aButWuN9ethQtFSJYh9BuI2m1llnYC
UduzcPwbJGObJ24aJcLinfMltuL9i8ZPPGnbpsZKXmz8qQgvdgORvZtLJ6PlQ1d8
O5wc/d48RnEWfMRMM6z3q9pfXqFPTy1TO0J7EgcBhK9ytyJ0uFWQ4PxsMQoNpcnO
3qS0PUevq75G
-----END CERTIFICATE-----''',
                    clusterName: 'EKS-1.us-west-2.eksctl.io',
                    credentialsId: 'k8-token',
                    namespace: 'webapps',
                    serverUrl: 'https://5A735A784998DA1B9508DC40353562D3.gr7.us-west-2.eks.amazonaws.com'
                ]]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
