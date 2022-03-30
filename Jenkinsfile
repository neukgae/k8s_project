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
				sh 'curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"'
				sh 'curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"'
				sh 'echo "$(<kubectl.sha256) kubectl" | sha256sum --check'
				sh 'sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl'
            }
        }
        
        stage('build') {
            steps {
		        sh 'kubectl create secret generic mysql-password --from-literal=password=test123'
		    	sh 'kubectl create -f mysql.yaml'
		    	sh 'kubectl create -f mysql-service.yaml'
		    	sh 'kubectl create -f wordpress.yaml'
		    	sh 'kubectl create -f wordpress-service.yaml'
            }
        }
    }
}
