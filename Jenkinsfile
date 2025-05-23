pipeline {
    agent any
    stages {
        stage('Git Checkout') {
            steps {
                cleanWs()
                git branch: 'develop', url: 'https://github.com/Shopping-App-Services/k8s-helm-istio.git'
            }
        }
        stage('Deploy on K8s Cluster') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'kind-kind', contextName: 'kind-kind', credentialsId: 'KUBECONFIG', namespace: 'default', restrictKubeConfigAccess: false, serverUrl: 'https://127.0.0.1:33285') {
                    sh 'kubectl apply -f .'
                }
            }
        }
    }
}
