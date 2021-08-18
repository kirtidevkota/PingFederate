pipeline{
    agent any
    environment {     
            registry = "K8sConfig/k8scicd"
      }
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                  sh 'docker build -t pkjack/my-app-1.0 .'
                }
            }
        }
        
        
 stage('Deploy App on k8s') {
      steps {
            sshagent(['k8s']) {
            sh "scp -o StrictHostKeyChecking=no nodejsapp.yaml ec2-user@65.2.35.23:/home/ec2-user"
            script {
                try{
                    sh "ssh ec2-user@65.2.35.23 kubectl create -f ."
                }catch(error){
                    sh "ssh ec2-user@65.2.35.23kubectl create -f ."
            }
}
        }
      
    }
	}
      
        }
    }
