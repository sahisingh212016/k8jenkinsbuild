pipeline {
    agent any

    environment {
        KUBE_NAMESPACE = 'myfrontend'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/sahisingh212016/k8jenkinsbuild.git',
                    branch: 'master'
            }
        }

        stage('Deploy to my environment') {
            steps {
                script {
                    withCredentials([file(credentialsId: 'kubeconfig-id', variable: 'KUBECONFIG')]) {
                        sh """
                            kubectl apply -f ds.yaml --namespace=$KUBE_NAMESPACE
                        """
                    }
                }
            }
        }
    }
}

