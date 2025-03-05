pipeline {
    agent any

    tools {
        terraform 'terra' // This will install Terraform automatically in Jenkins
    }
    environment {
        GOOGLE_APPLICATION_CREDENTIALS = credentials('gcp.json')
    }

    stages {
      
        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan'
            }
        }

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }
         stage('Terraform destroy') {
            steps {
                sh 'terraform destroy -auto-approve'
            }
        }
    }

    post {
        success {
            echo 'Terraform Infrastructure Deployed Successfully!'
        }
        failure {
            echo 'Terraform Infrastructure Deployment Failed!'
        }
    }
}
