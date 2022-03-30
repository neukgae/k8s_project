pipeline {
    agent any
    
    stages() {
        stage('git clone') {
            steps() {
		sh 'rm -rf k8s_project'
                sh 'git clone -b main https://github.com/neukgae/k8s_project'
            }
        }
        
        stage('move & install') {
            steps {
                sh 'cd k8s_project'
            }
        }
        
        stage('build') {
	    steps() {
		withKubeConfig([credentialsId: 'neukgae']) {
		    sh 'kubectl create secret generic mysql-password --from-literal=password=test123'
	    	    sh 'kubectl create -f mysql.yaml'
	    	    sh 'kubectl create -f mysql-service.yaml'
	    	    sh 'kubectl create -f wordpress.yaml'
		    sh 'kubectl create -f wordpress-service.yaml'
		}
            }
        }
    }
}
