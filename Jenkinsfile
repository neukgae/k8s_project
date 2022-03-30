node {
    stage('Clone Repository'){
        checkout scm
    }

    stage('Build to ECR'){

        }
    }
    stage('Kubernetes'){
        withKubeConfig([credentialsId: "kubectl-deploy-credentials",
                        serverUrl: "${EKS_API}",
                        clusterName: "${EKS_CLUSTER_NAME}"]){

            sh 'curl -LO "https://storage.googleapis.com/kubernetes-release/release/v1.20.5/bin/linux/amd64/kubectl"'
		    sh "chmod u+x ./kubectl"
            sh "./kubectl get pods"
            sh "kubectl create secret generic mysql-password --from-literal=password=test123"
            sh "kubectl create -f mysql.yaml"
            sh "kubectl create -f mysql-service.yaml"
		    sh "kubectl create -f wordpress.yaml"
		    sh "kubectl create -f wordpress-service.yaml"
        }
    }
}
