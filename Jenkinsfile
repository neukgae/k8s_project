node {
    stage('Checkout') {
        sh 'rm -rf k8s_project'
        sh 'git clone -b main https://github.com/neukgae/k8s_project'
    }
    
    stage('move') {
        sh 'cd k8s_project'
    }

    stage('Run kubectl') {
        withKubeConfig([credentialsId: "kubectl-deploy-credentials"]){

        }
    }
}
