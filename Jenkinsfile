pipeline {
    agent any
	
    environment {
        GOOGLE_APPLICATION_CREDENTIALS = credentials('gcp-key')
	GIT_TOKEN = credentials('git-token')
    }
	
    stages {
        stage('Git Checkout') {
            steps {
               git "https://${GIT_TOKEN}@github.com/AnuraggKamdi/GCP-DevOps-Project-CICD-with-TF-Jenkins.git"
            }
        }
        
        stage('Terraform Init') {
            steps {
                script {
                    sh 'terraform init'
                }
            }
        }
        
        stage('Terraform Plan') {
            steps {
                script {
                    sh 'terraform plan -out=tfplan'
                }
            }
        }
	    
        stage('Terraform Apply') {
            steps {
                script {
                    sh 'terraform apply -auto-approve'
                }
            }
        }
    }
}
