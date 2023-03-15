pipeline {
    agent any
    stages {
        stage('Deploy to Kubernetes') {
            steps {
                // Apply Kubernetes manifests using kubectl
                withCredentials([file(credentialsId: 'kubeconfig', variable: 'KUBECONFIG_FILE')]) {
                    sh 'kubectl apply -f tech-assignment-namespace.yaml --kubeconfig=${KUBECONFIG_FILE}'
                    sh 'kubectl apply -f elasticsearch/es-cm.yaml --kubeconfig=${KUBECONFIG_FILE}'
                    sh 'kubectl apply -f elasticsearch/es-svc.yaml --kubeconfig=${KUBECONFIG_FILE}'
                    sh 'kubectl apply -f elasticsearch/es-svc-headless.yaml --kubeconfig=${KUBECONFIG_FILE}'
                    sh 'kubectl apply -f elasticsearch/es-statefulset.yaml --kubeconfig=${KUBECONFIG_FILE}'
                    sh 'kubectl apply -f kibana/kibana-cm.yaml --kubeconfig=${KUBECONFIG_FILE}'
                    sh 'kubectl apply -f kibana/kibana-svc.yaml --kubeconfig=${KUBECONFIG_FILE}'
                    sh 'kubectl apply -f kibana/kibana-deployment.yaml --kubeconfig=${KUBECONFIG_FILE}'
                }
            }
        }
    }
}
