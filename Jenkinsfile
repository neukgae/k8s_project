pipeline {
    agent any
    
    stages() {
        stage('git clone') {
            steps() {
                git 'https://github.com/neukgae/k8s_project'
            }
        }
        
        stage('move') {
            steps {
                cd "k8s_project"


            }
        }
        
        stage('build') {
            steps {
				kubectl "create secret generic mysql-password --from-literal=password=test123"
				kubectl "create -f mysql.yaml"
				kubectl "create -f mysql-service.yaml"
				kubectl "create -f wordpress.yaml"
				kubectl "create -f wordpress-service.yaml"
            }
        }        
    }
}
