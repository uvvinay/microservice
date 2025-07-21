pipeline {
    agent any

    stages {
        stage('deploy to kuberenetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'micro.k8s.local', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: ' https://api-micro-k8s-local-0emamb-71d598401d025efc.elb.ap-south-1.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 30
                }
            }
        }
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'micro.k8s.local', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: ' https://api-micro-k8s-local-0emamb-71d598401d025efc.elb.ap-south-1.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
                
            }
        }
    }
}
