pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'default', contextName: '', credentialsId: '', namespace: 'webapps', serverUrl: 'https://192.168.1.6:6443']]) {
                    sh 'kubectl apply -f deployment-service.yml'
                    sleep 120
                }
            }
        }
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'default', contextName: '', credentialsId: '', namespace: 'webapps', serverUrl: 'https://192.168.1.6:6443']]) {
                    sh 'kubectl get svc -n webapps'
                }
            }
        }
    }
}
