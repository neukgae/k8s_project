node {
    stage('Clone Repository'){
        sh 'rm -rf k8s_project'
        sh 'git clone -b main https://github.com/neukgae/k8s_project'
    }

    stage('Build to ECR'){
	sh 'cd k8s_project'
        }
    }
    stage('Kubernetes'){
        withKubeConfig([credentialsId: "kubectl-deploy-credentials"]){
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
